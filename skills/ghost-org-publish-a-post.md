---
name: ghost-publish-a-post
description: Create a Ghost post from content you already have, attach a feature image, tag it, and publish it — using the Ghost Admin API.
api: Ghost Admin API
generated: '2026-08-13'
method: generated
source: openapi/ghost-org-admin-posts-api-openapi.yml, openapi/ghost-org-admin-images-api-openapi.yml, openapi/ghost-org-admin-tags-api-openapi.yml
operations:
  - uploadAdminImage
  - browseAdminTags
  - addAdminTag
  - addAdminPost
  - readAdminPostById
  - editAdminPost
---

# Publish a post to Ghost

Base URL: `https://{admin_domain}/ghost/api/admin/`
Auth: `Authorization: Ghost <jwt>` — sign a short-lived JWT from an Admin API key (`id:secret`). Never do this in a browser.
Always send `Accept-Version: v6.0`. Every path ends in a trailing slash.

## 1. Upload the feature image (optional)

`uploadAdminImage` — `POST /admin/images/upload/`, `multipart/form-data` with a `file` part.
Returns the hosted URL. A wrong content type is rejected with **415**.

Keep the returned `url`; you will set it as `feature_image` in step 3.

## 2. Make sure the tags exist

`browseAdminTags` — `GET /admin/tags/?filter=slug:<slug>` to check.
If it is missing, `addAdminTag` — `POST /admin/tags/` with `{"tags":[{"name":"...","slug":"..."}]}`.

Tags whose name starts with `#` are internal and are hidden from readers.

## 3. Create the post as a draft

`addAdminPost` — `POST /admin/posts/`

```json
{"posts":[{
  "title": "...",
  "lexical": "...",
  "status": "draft",
  "feature_image": "<url from step 1>",
  "tags": [{"slug": "..."}],
  "visibility": "public"
}]}
```

Ghost stores bodies as Lexical. If you only have HTML, send `html` and add `?source=html` to the request so Ghost converts it.

A malformed body comes back **422** with the failing field in `errors[0].property`.

## 4. Publish it

Publishing is not a separate operation — it is a status transition on the edit call.

`readAdminPostById` — `GET /admin/posts/{id}/` first, to read the current `updated_at`.
`editAdminPost` — `PUT /admin/posts/{id}/`

```json
{"posts":[{
  "status": "published",
  "updated_at": "<the value you just read>"
}]}
```

**This is the step that goes wrong.** `updated_at` is Ghost's optimistic concurrency token. Omit it or send a stale one and you get **409 UpdateCollisionError**. The fix is always the same: re-read the post, copy the fresh `updated_at`, retry. Do not retry blindly — Ghost has no idempotency key, so a retried create in step 3 makes a second post.

To schedule instead of publishing now, send `"status": "scheduled"` with a future `published_at`.

## 5. Verify

`browseAdminPosts` — `GET /admin/posts/?filter=status:published&limit=1&order=published_at%20desc`

`filter` values are NQL and must be URL-encoded.

## Errors you will actually hit

| Status | type | What to do |
| --- | --- | --- |
| 401 | UnauthorizedError | JWT expired (they are short-lived) or the key was regenerated. Re-sign. |
| 403 | NoPermissionError | The integration's role cannot write posts. |
| 409 | UpdateCollisionError | Stale `updated_at`. Re-read, retry. |
| 415 | UnsupportedMediaTypeError | Image upload was not multipart/form-data. |
| 422 | ValidationError | Read `property` and `details`. |

Quote `errors[0].id` when reporting a problem — it is a per-response UUID.
