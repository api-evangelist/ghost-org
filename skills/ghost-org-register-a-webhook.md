---
name: ghost-register-a-webhook
description: Subscribe to Ghost content and member events by registering, updating and deleting webhooks through the Admin API.
api: Ghost Admin API
generated: '2026-08-13'
method: generated
source: openapi/ghost-org-admin-webhooks-api-openapi.yml, asyncapi/ghost-org-webhooks-asyncapi.yml, https://docs.ghost.org/webhooks
operations:
  - addAdminWebhook
  - editAdminWebhook
  - deleteAdminWebhook
---

# Register a Ghost webhook

Base URL: `https://{admin_domain}/ghost/api/admin/`
Auth: `Authorization: Ghost <jwt>`. Webhooks belong to an **integration**, so the JWT must be signed with that integration's Admin API key — a staff access token will not attach the webhook to the right owner.
`Accept-Version: v6.0`.

## 1. Pick the event

Ghost fires one event per subscription. The catalogue is in `asyncapi/ghost-org-webhooks-asyncapi.yml`; the ones that matter most:

| Event | Fires when |
| --- | --- |
| `post.published` | A post goes live |
| `post.published.edited` | A live post is edited |
| `post.unpublished` | A post is taken down |
| `post.added` / `post.edited` / `post.deleted` | Any post write, published or not |
| `page.*` | Same set, for pages |
| `tag.added` / `tag.edited` / `tag.deleted` | Taxonomy changes |
| `post.tag.attached` / `post.tag.detached` | A tag is applied or removed |
| `member.added` / `member.edited` / `member.deleted` | Audience changes |
| `site.changed` | Any content or settings change — the rebuild trigger for static sites |

Use `site.changed` for cache busting and static rebuilds. Use the specific `post.*` events when you care what changed.

## 2. Create it

`addAdminWebhook` — `POST /admin/webhooks/`

```json
{"webhooks":[{
  "event": "post.published",
  "target_url": "https://example.com/hooks/ghost",
  "name": "Rebuild site",
  "secret": "<your shared secret>",
  "api_version": "v6"
}]}
```

`target_url` must be reachable from the public internet. `secret` is optional but you want it — it is how you verify the delivery came from Ghost.

## 3. Handle the delivery

Ghost POSTs a JSON body containing the affected resource. Respond **2xx** or Ghost treats the delivery as failed; anything you return in the body is discarded.

Return the 2xx fast and do the work asynchronously. A slow handler shows up in `last_triggered_status` and `last_triggered_error` on the webhook record.

## 4. Update or remove

`editAdminWebhook` — `PUT /admin/webhooks/{id}/` (echo the current `updated_at`; a stale value is a **409**).
`deleteAdminWebhook` — `DELETE /admin/webhooks/{id}/` → 204.

There is no browse operation for webhooks in the published reference — keep the id you got back from the create call, or read the integration in Ghost Admin.

## Local testing

`ghst webhook listen` (from `@tryghost/ghst`) surfaces events at the terminal. For the Stripe side of members, Ghost documents `stripe listen --forward-to http://localhost:2368/members/webhooks/stripe/`.

## Caveats

- No delivery retry policy is published. Assume at-most-once and reconcile with a periodic Content API sync (see `ghost-sync-published-content`).
- No signature header format is documented; the `secret` is the only shared material. Verify defensively and do not trust the payload alone.
- Webhooks are per-site. A multi-site estate needs one registration per site.
