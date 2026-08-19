---
name: ghost-onboard-a-member
description: Add a member to a Ghost site, label them, subscribe them to the right newsletters, and read back their tier and subscription state.
api: Ghost Admin API
generated: '2026-08-13'
method: generated
source: openapi/ghost-org-admin-members-api-openapi.yml, openapi/ghost-org-admin-labels-api-openapi.yml, openapi/ghost-org-admin-newsletters-api-openapi.yml, openapi/ghost-org-admin-tiers-api-openapi.yml, openapi/ghost-org-admin-offers-api-openapi.yml
operations:
  - browseAdminNewsletters
  - browseAdminLabels
  - addAdminLabel
  - addAdminMember
  - readAdminMemberById
  - editAdminMember
  - browseAdminTiers
  - browseAdminOffers
---

# Onboard a member

Base URL: `https://{admin_domain}/ghost/api/admin/`
Auth: `Authorization: Ghost <jwt>`, signed from an Admin API key. Server-side only — member records are personal data.
`Accept-Version: v6.0`, trailing slashes on every path.

## 1. Learn the site's shape before you write

- `browseAdminNewsletters` — `GET /admin/newsletters/` → the newsletters this site sends, and which have `subscribe_on_signup: true`.
- `browseAdminTiers` — `GET /admin/tiers/` → the priced access levels, with `monthly_price`, `yearly_price`, `currency`, `trial_days` and `benefits`.
- `browseAdminOffers` — `GET /admin/offers/` → discount codes, each bound to exactly one tier and cadence.
- `browseAdminLabels` — `GET /admin/labels/` → existing segmentation labels.

Never hard-code a tier or newsletter id. Look them up each run — they differ per site.

## 2. Create the label if you need one

`addAdminLabel` — `POST /admin/labels/` with `{"labels":[{"name":"..."}]}`. Ghost derives the slug.

## 3. Create the member

`addAdminMember` — `POST /admin/members/`

```json
{"members":[{
  "email": "person@example.com",
  "name": "...",
  "note": "...",
  "labels": [{"name": "<existing label>"}],
  "newsletters": [{"id": "<newsletter id from step 1>"}]
}]}
```

Only `email` is required. `status` is derived by Ghost (`free`, `paid`, `comped`) — do not try to set it.

A duplicate email is a **422 ValidationError**, not a silent merge. Because Ghost has no idempotency key, check with `GET /admin/members/?filter=email:'person@example.com'` before you POST if the caller might retry.

## 4. Read the member back

`readAdminMemberById` — `GET /admin/members/{id}/`

The member object embeds the relationships you care about:

- `labels[]` — segmentation
- `newsletters[]` — per-newsletter subscription state
- `subscriptions[]` — Stripe-backed paid subscriptions, each with a nested `tier` and a `customer` projection from Stripe

There is no top-level `/subscriptions/` collection. If you want subscription state, you read the member.

## 5. Update

`editAdminMember` — `PUT /admin/members/{id}/`

Echo the current `updated_at` in the body. A stale value is a **409 UpdateCollisionError** — re-read and retry.

To unsubscribe someone from a newsletter, send the `newsletters` array without it. Sending an empty array unsubscribes them from everything.

## Do not do this through the API

Ghost does not create paid subscriptions over the Admin API — money moves through Stripe, and Ghost reconciles it. To make someone paid without charging them, use a comped tier in Ghost Admin rather than trying to write a `subscriptions` entry.

## Errors

| Status | type | Cause |
| --- | --- | --- |
| 401 | UnauthorizedError | Expired JWT or regenerated key. |
| 403 | NoPermissionError | Integration role cannot manage members. |
| 409 | UpdateCollisionError | Stale `updated_at` on the PUT. |
| 422 | ValidationError | Duplicate email, missing email, unknown newsletter id. |
