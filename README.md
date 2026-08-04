# Ghost (ghost-org)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Ghost is an open-source (MIT) publishing platform for professional publications, newsletters, memberships, and paid subscriptions. It can be run for free by self-hosting the software ([github.com/TryGhost/Ghost](https://github.com/TryGhost/Ghost)) or used as the managed **Ghost(Pro)** service, whose revenue funds the non-profit Ghost Foundation that maintains the project.

Every Ghost site - self-hosted or on Ghost(Pro) - exposes **two documented public REST APIs** under `https://{admin_domain}/ghost/api/`:

- **Content API** (`/ghost/api/content/`) - read-only, authenticated with a **Content API key** passed as the `key` query parameter. Safe for browser use because it only reads public, published data. Serves posts, pages, authors, tags, tiers, and public settings. Supports browse, read-by-id, and read-by-slug, plus `filter`, `include`, `fields`, `order`, and pagination.
- **Admin API** (`/ghost/api/admin/`) - read-write, authenticated with a short-lived **JWT** signed from an **Admin API key** (`id:secret`) and sent as `Authorization: Ghost {token}`. A staff access token or an authenticated user session may also be used. Manages posts, pages, members, tags, labels, tiers, offers, newsletters, users, images, themes, and webhooks.

The `{admin_domain}` is the site's own domain; on Ghost(Pro) this is typically a `*.ghost.io` domain. All requests must use HTTPS, and clients should send an `Accept-Version` header (for example `v5.0`). This entry documents Ghost 5.x.

**Access model:** the APIs are a feature of the software, not a separately billed product. Self-hosting gives you the full Content and Admin APIs for free (you provide infrastructure and, for newsletters, an email provider). Ghost(Pro) includes the same APIs on every plan; its tiers are priced mainly by staff-user count and member (audience) size, not by API usage.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/ghost-org/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/ghost-org/refs/heads/main/apis.yml)

## Tags

- Publishing
- Newsletters
- Memberships
- Subscriptions
- CMS
- Open Source
- Content

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

### Ghost Content API

Read-only, key-authenticated REST API that delivers published content - posts, pages, authors, tags, tiers, and public settings - to front-ends, static site generators, and apps.

- **Human URL:** [https://docs.ghost.org/content-api](https://docs.ghost.org/content-api)
- **Base URL:** `https://{admin_domain}/ghost/api/content`

### Ghost Admin Posts API

Read-write management of posts - browse, read by id or slug, create, update, and delete. Content is stored as Lexical and can be supplied or requested as HTML.

- **Human URL:** [https://docs.ghost.org/admin-api/posts](https://docs.ghost.org/admin-api/posts)
- **Base URL:** `https://{admin_domain}/ghost/api/admin`

### Ghost Admin Pages API

Read-write management of static pages, which share the post data model but sit outside the chronological feed.

- **Human URL:** [https://docs.ghost.org/admin-api/pages](https://docs.ghost.org/admin-api/pages)
- **Base URL:** `https://{admin_domain}/ghost/api/admin`

### Ghost Admin Members API

Manage the membership audience - browse, read, create, and update members, their newsletter subscriptions, labels, and paid/comp status.

- **Human URL:** [https://docs.ghost.org/admin-api/members](https://docs.ghost.org/admin-api/members)
- **Base URL:** `https://{admin_domain}/ghost/api/admin`

### Ghost Admin Tags and Labels API

Read-write management of tags (content taxonomy) and labels (member segmentation).

- **Human URL:** [https://docs.ghost.org/admin-api/tags](https://docs.ghost.org/admin-api/tags)
- **Base URL:** `https://{admin_domain}/ghost/api/admin`

### Ghost Admin Tiers and Offers API

Manage subscription tiers and promotional offers that define paid access, pricing, benefits, and discounts.

- **Human URL:** [https://docs.ghost.org/admin-api/tiers](https://docs.ghost.org/admin-api/tiers)
- **Base URL:** `https://{admin_domain}/ghost/api/admin`

### Ghost Admin Newsletters API

Manage the newsletters a publication sends, including sender details, design, and subscription behavior. A single site can run multiple newsletters.

- **Human URL:** [https://docs.ghost.org/admin-api/newsletters](https://docs.ghost.org/admin-api/newsletters)
- **Base URL:** `https://{admin_domain}/ghost/api/admin`

### Ghost Admin Users and Site API

Read-only access to staff users and to public site metadata (`/site/` returns title, url, and version).

- **Human URL:** [https://docs.ghost.org/admin-api/users](https://docs.ghost.org/admin-api/users)
- **Base URL:** `https://{admin_domain}/ghost/api/admin`

### Ghost Admin Media and Themes API

Upload assets and manage presentation - multipart image uploads via `/images/upload/`, and theme upload plus activation via `/themes/`.

- **Human URL:** [https://docs.ghost.org/admin-api/images](https://docs.ghost.org/admin-api/images)
- **Base URL:** `https://{admin_domain}/ghost/api/admin`

### Ghost Admin Webhooks API

Register outbound webhooks that fire on Ghost events (for example `post.published`, `member.added`) to trigger site rebuilds, notifications, or automation. Supports create, update, and delete; there is no endpoint to read existing webhooks.

- **Human URL:** [https://docs.ghost.org/admin-api/webhooks](https://docs.ghost.org/admin-api/webhooks)
- **Base URL:** `https://{admin_domain}/ghost/api/admin`

## Authentication

- **Content API:** append `?key={content_api_key}` (from a Custom Integration in Ghost Admin). Read-only, public data.
- **Admin API:** create a Custom Integration to get an Admin API key (`id:secret`), sign a short-lived JWT with it, and send `Authorization: Ghost {token}`. Staff access tokens and user sessions are also accepted.

## WebSocket Review

Ghost does **not** expose a documented public WebSocket API. The Content and Admin APIs are request/response REST over HTTPS. Ghost's event surface for integrators is **outbound webhooks** (server-to-endpoint HTTP POSTs), not a client-connected WebSocket stream. See [review.yml](review.yml).

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/ghost-foundation)
- [Website](https://ghost.org)
- [Documentation](https://docs.ghost.org)
- [GitHub Organization](https://github.com/TryGhost)
- [Plans](plans/ghost-org-plans-pricing.yml)
- [Rate Limits](rate-limits/ghost-org-rate-limits.yml)
- [Fin Ops](finops/ghost-org-finops.yml)
- [Blog](https://ghost.org/blog)
- [Change Log](https://ghost.org/changelog)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
