---
name: ghost-sync-published-content
description: Pull every published post, page, tag and author out of a Ghost site through the read-only Content API, with correct pagination and filtering.
api: Ghost Content API
generated: '2026-08-13'
method: generated
source: openapi/ghost-org-content-posts-api-openapi.yml, openapi/ghost-org-content-pages-api-openapi.yml, openapi/ghost-org-content-tags-api-openapi.yml, openapi/ghost-org-content-authors-api-openapi.yml, openapi/ghost-org-content-settings-api-openapi.yml
operations:
  - browseContentSettings
  - browseContentPosts
  - readContentPostBySlug
  - browseContentPages
  - browseContentTags
  - browseContentAuthors
---

# Sync published content out of Ghost

Base URL: `https://{admin_domain}/ghost/api/content/`
Auth: `?key=<content api key>` as a query parameter. These keys are browser-safe — they only ever return public data.
Send `Accept-Version: v6.0`. Ghost answers with `Content-Version` naming the version that served you.

The admin domain can differ from the site domain. On Ghost(Pro) it is a `*.ghost.io` host. Using the wrong one causes CORS surprises in browsers.

## 1. Read the site settings first

`browseContentSettings` — `GET /content/settings/?key=<key>`

Unlike every other endpoint this returns an object, not an array. Use it to learn the site title, timezone, navigation and locale before you interpret anything else.

## 2. Page through the posts

`browseContentPosts` — `GET /content/posts/?key=<key>&limit=100&page=1&include=tags,authors`

- Default `limit` is 15. `limit=all` disables pagination entirely — fine for a one-off export, bad for a site with thousands of posts.
- Read `meta.pagination` on every response: `{page, limit, pages, total, next, prev}`. Stop when `next` is `null`.
- `include=tags,authors` adds `tags[]`, `primary_tag`, `authors[]` and `primary_author`. Without it you get ids only.
- `formats=html,plaintext` if you need the plaintext body as well; `html` is the default and the only format returned by default.
- `fields=title,url,published_at` trims the payload — but Ghost documents that `fields` does not combine well with `include`, so pick one.

## 3. Filter instead of downloading everything

`filter` takes NQL and **must be URL-encoded**. An unencoded filter is a **400**.

```
filter=published_at:>'2026-01-01'
filter=tag:getting-started+featured:true
order=published_at desc
```

For an incremental sync, filter on `published_at` (or `updated_at`) greater than your last watermark rather than re-walking every page.

## 4. Read one post

`readContentPostBySlug` — `GET /content/posts/slug/{slug}/?key=<key>`
`readContentPostById` — `GET /content/posts/{id}/?key=<key>`

A post that exists but is not published returns **404**, not 403. Do not treat a 404 as "deleted" during a sync.

## 5. Repeat for the other collections

- `browseContentPages` — `GET /content/pages/` (same shape as posts)
- `browseContentTags` — `GET /content/tags/?include=count.posts`
- `browseContentAuthors` — `GET /content/authors/?include=count.posts`

## Caching

Ghost documents the Content API as fully cacheable and says it can be fetched as often as you like without limitation. Responses carry a weak `ETag` and `Cache-Control: public, max-age=0`. Send `If-None-Match` and honour a 304 — that, not a request budget, is the polite way to poll.

No rate-limit headers are returned. Do not build retry logic around `X-RateLimit-*`; it does not exist here.
