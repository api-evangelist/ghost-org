# Ghost

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Ghost is an open-source (MIT) publishing platform for professional publications, newsletters, memberships, and paid subscriptions. It can be self-hosted for free or run as the managed Ghost(Pro) service, with all Ghost(Pro) revenue funding the non-profit Ghost Foundation. Every Ghost site exposes two documented public REST APIs under https://{site}/ghost/api/. The Content API is a read-only, key-authenticated interface for delivering published posts, pages, tags, authors, tiers, and settings to front-ends and static sites. The Admin API is a read-write, token-authenticated (JWT) interface for managing posts, pages, members, tags, tiers, offers, newsletters, users, media, themes, and webhooks.

**Areas:** Publishing · Newsletters · Membership · Subscription · CMS · Open Source · Content · A2A

## Ghost on APIs.io

Everything profiled for Ghost is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/ghost-org/](https://apis.io/providers/ghost-org/)** — or go straight to one of the APIs or properties below.

### APIs (33)

- [Ghost Admin - Images API](https://apis.io/apis/ghost-org/ghost-org-admin-images-api/) — Image uploads.
- [Ghost Admin - Labels API](https://apis.io/apis/ghost-org/ghost-org-admin-labels-api/) — Read-write member labels.
- [Ghost Admin - Members API](https://apis.io/apis/ghost-org/ghost-org-admin-members-api/) — Read-write members.
- [Ghost Admin - Newsletters API](https://apis.io/apis/ghost-org/ghost-org-admin-newsletters-api/) — Read-write newsletters.
- [Ghost Admin - Offers API](https://apis.io/apis/ghost-org/ghost-org-admin-offers-api/) — Read-write promotional offers.
- [Ghost Admin - Pages API](https://apis.io/apis/ghost-org/ghost-org-admin-pages-api/) — Read-write pages.
- [Ghost Admin - Posts API](https://apis.io/apis/ghost-org/ghost-org-admin-posts-api/) — Read-write posts.
- [Ghost Admin - Site API](https://apis.io/apis/ghost-org/ghost-org-admin-site-api/) — Read-only public site metadata.
- [Ghost Admin - Tags API](https://apis.io/apis/ghost-org/ghost-org-admin-tags-api/) — Read-write tags.
- [Ghost Admin - Themes API](https://apis.io/apis/ghost-org/ghost-org-admin-themes-api/) — Theme upload and activation.
- [Ghost Admin - Tiers API](https://apis.io/apis/ghost-org/ghost-org-admin-tiers-api/) — Read-write subscription tiers.
- [Ghost Admin - Users API](https://apis.io/apis/ghost-org/ghost-org-admin-users-api/) — Read-only staff users.
- [Ghost Admin - Webhooks API](https://apis.io/apis/ghost-org/ghost-org-admin-webhooks-api/) — Outbound webhook management.
- [Ghost Content - Authors API](https://apis.io/apis/ghost-org/ghost-org-content-authors-api/) — Read-only authors.
- [Ghost Content - Pages API](https://apis.io/apis/ghost-org/ghost-org-content-pages-api/) — Read-only published pages.
- [Ghost Content - Posts API](https://apis.io/apis/ghost-org/ghost-org-content-posts-api/) — Read-only published posts.
- [Ghost Content - Settings API](https://apis.io/apis/ghost-org/ghost-org-content-settings-api/) — Read-only public site settings.
- [Ghost Content - Tags API](https://apis.io/apis/ghost-org/ghost-org-content-tags-api/) — Read-only tags.
- [Ghost Content - Tiers API](https://apis.io/apis/ghost-org/ghost-org-content-tiers-api/) — Read-only public subscription tiers.
- [Ghost Authors API](https://apis.io/apis/ghost-org/ghost-org-authors-api/) — Authors represent the staff users who create content in a Ghost publication.
- [Ghost Images API](https://apis.io/apis/ghost-org/ghost-org-images-api/) — Upload images to the Ghost publication for use in posts, pages, and settings.
- [Ghost Members API](https://apis.io/apis/ghost-org/ghost-org-members-api/) — Manage publication members including creating, reading, updating, and deleting member records. Members are people who have signed up for the publication.
- [Ghost Newsletters API](https://apis.io/apis/ghost-org/ghost-org-newsletters-api/) — Manage email newsletters that members can subscribe to. Each newsletter has its own design, sender details, and subscription list.
- [Ghost Offers API](https://apis.io/apis/ghost-org/ghost-org-offers-api/) — Manage promotional offers for paid membership tiers, including discounts and trial periods.
- [Ghost Pages API](https://apis.io/apis/ghost-org/ghost-org-pages-api/) — Create, read, update, and delete pages. Pages share the same structure as posts but are used for static content.
- [Ghost Posts API](https://apis.io/apis/ghost-org/ghost-org-posts-api/) — Create, read, update, and delete posts. Posts are the primary content resource in Ghost and support rich content via the Lexical editor format.
- [Ghost Settings API](https://apis.io/apis/ghost-org/ghost-org-settings-api/) — Settings provide access to global publication settings including title, description, navigation, and other configuration values.
- [Ghost Site API](https://apis.io/apis/ghost-org/ghost-org-site-api/) — Read basic information about the Ghost site.
- [Ghost Tags API](https://apis.io/apis/ghost-org/ghost-org-tags-api/) — The Tags API from Ghost — 3 operation(s) for tags.
- [Ghost Themes API](https://apis.io/apis/ghost-org/ghost-org-themes-api/) — Upload, activate, and manage themes that control the front-end appearance of the Ghost publication.
- [Ghost Tiers API](https://apis.io/apis/ghost-org/ghost-org-tiers-api/) — Manage membership tiers including creating, reading, and updating tier configurations with pricing and benefits.
- [Ghost Users API](https://apis.io/apis/ghost-org/ghost-org-users-api/) — Read staff user accounts for the Ghost publication.
- [Ghost Webhooks API](https://apis.io/apis/ghost-org/ghost-org-webhooks-api/) — Create, update, and delete webhooks that send HTTP POST notifications when events occur within the publication.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Ghost Webhooks](https://apis.io/asyncapis/ghost-org/ghost-org-webhooks-asyncapi/)

#### Event channels (29)

Individual events and webhooks the provider emits.

- [/webhook/member.added](https://apis.io/channels/ghost-org/webhook-member-added/)
- [/webhook/member.deleted](https://apis.io/channels/ghost-org/webhook-member-deleted/)
- [/webhook/member.edited](https://apis.io/channels/ghost-org/webhook-member-edited/)
- [/webhook/page.added](https://apis.io/channels/ghost-org/webhook-page-added/)
- [/webhook/page.deleted](https://apis.io/channels/ghost-org/webhook-page-deleted/)
- [/webhook/page.edited](https://apis.io/channels/ghost-org/webhook-page-edited/)
- [/webhook/page.published](https://apis.io/channels/ghost-org/webhook-page-published/)
- [/webhook/page.published.edited](https://apis.io/channels/ghost-org/webhook-page-published-edited/)
- [/webhook/page.rescheduled](https://apis.io/channels/ghost-org/webhook-page-rescheduled/)
- [/webhook/page.scheduled](https://apis.io/channels/ghost-org/webhook-page-scheduled/)
- [/webhook/page.tag.attached](https://apis.io/channels/ghost-org/webhook-page-tag-attached/)
- [/webhook/page.tag.detached](https://apis.io/channels/ghost-org/webhook-page-tag-detached/)
- [/webhook/page.unpublished](https://apis.io/channels/ghost-org/webhook-page-unpublished/)
- [/webhook/page.unscheduled](https://apis.io/channels/ghost-org/webhook-page-unscheduled/)
- [/webhook/post.added](https://apis.io/channels/ghost-org/webhook-post-added/)
- [/webhook/post.deleted](https://apis.io/channels/ghost-org/webhook-post-deleted/)
- [/webhook/post.edited](https://apis.io/channels/ghost-org/webhook-post-edited/)
- [/webhook/post.published](https://apis.io/channels/ghost-org/webhook-post-published/)
- [/webhook/post.published.edited](https://apis.io/channels/ghost-org/webhook-post-published-edited/)
- [/webhook/post.rescheduled](https://apis.io/channels/ghost-org/webhook-post-rescheduled/)
- [/webhook/post.scheduled](https://apis.io/channels/ghost-org/webhook-post-scheduled/)
- [/webhook/post.tag.attached](https://apis.io/channels/ghost-org/webhook-post-tag-attached/)
- [/webhook/post.tag.detached](https://apis.io/channels/ghost-org/webhook-post-tag-detached/)
- [/webhook/post.unpublished](https://apis.io/channels/ghost-org/webhook-post-unpublished/)
- [/webhook/post.unscheduled](https://apis.io/channels/ghost-org/webhook-post-unscheduled/)
- …and 4 more published on APIs.io

#### GraphQL (1)

GraphQL schemas.

- [Moved to /providers/ghost-org/](https://apis.io/graphqls/ghost-org/ghost-org-graphql/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [ghost-org-mcp.yml](https://apis.io/servers/ghost-org/ghost-org-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Ghost Org Agentic Access](https://apis.io/agentic-access/ghost-org/ghost-org-agentic-access/)

#### JSON Schema (25)

The data models the API reads and writes.

- [Author](https://apis.io/schemas/ghost-org/ghost-org-author/)
- [ErrorResponse](https://apis.io/schemas/ghost-org/ghost-org-errorresponse/)
- [Label](https://apis.io/schemas/ghost-org/ghost-org-label/)
- [Ghost Member](https://apis.io/schemas/ghost-org/ghost-org-member/)
- [MemberInput](https://apis.io/schemas/ghost-org/ghost-org-memberinput/)
- [NavigationItem](https://apis.io/schemas/ghost-org/ghost-org-navigationitem/)
- [Newsletter](https://apis.io/schemas/ghost-org/ghost-org-newsletter/)
- [NewsletterInput](https://apis.io/schemas/ghost-org/ghost-org-newsletterinput/)
- [Offer](https://apis.io/schemas/ghost-org/ghost-org-offer/)
- [OfferInput](https://apis.io/schemas/ghost-org/ghost-org-offerinput/)
- [Page](https://apis.io/schemas/ghost-org/ghost-org-page/)
- [PaginationMeta](https://apis.io/schemas/ghost-org/ghost-org-paginationmeta/)
- [Ghost Post](https://apis.io/schemas/ghost-org/ghost-org-post/)
- [PostInput](https://apis.io/schemas/ghost-org/ghost-org-postinput/)
- [Settings](https://apis.io/schemas/ghost-org/ghost-org-settings/)
- [Site](https://apis.io/schemas/ghost-org/ghost-org-site/)
- [Subscription](https://apis.io/schemas/ghost-org/ghost-org-subscription/)
- [Tag](https://apis.io/schemas/ghost-org/ghost-org-tag/)
- [TagInput](https://apis.io/schemas/ghost-org/ghost-org-taginput/)
- [Theme](https://apis.io/schemas/ghost-org/ghost-org-theme/)
- [Tier](https://apis.io/schemas/ghost-org/ghost-org-tier/)
- [TierInput](https://apis.io/schemas/ghost-org/ghost-org-tierinput/)
- [User](https://apis.io/schemas/ghost-org/ghost-org-user/)
- [Webhook](https://apis.io/schemas/ghost-org/ghost-org-webhook/)
- [WebhookInput](https://apis.io/schemas/ghost-org/ghost-org-webhookinput/)

#### JSON Structure (1)

Data models expressed in JSON Structure.

- [Ghost Org Structure](https://apis.io/json-structure/ghost-org/ghost-org-structure/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Ghost Org Context](https://apis.io/jsonld/ghost-org/ghost-org-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Ghost Domain Vocabulary](https://apis.io/vocabularies/ghost-org/ghost-org-vocabulary/)

#### Collections (36)

Postman and Open Collection request collections.

- [Ghost Content and Admin APIs](https://apis.io/collections/ghost-org/open-ghost-org/)
- [Ghost Admin API](https://apis.io/collections/ghost-org/open-ghost-org-admin-api/)
- [Ghost Content and Admin APIs Admin - Images API](https://apis.io/collections/ghost-org/open-ghost-org-admin-images-api/)
- [Ghost Content and Admin APIs Admin - Images Admin - Labels API](https://apis.io/collections/ghost-org/open-ghost-org-admin-labels-api/)
- [Ghost Content and Admin APIs Admin - Images Admin - Members API](https://apis.io/collections/ghost-org/open-ghost-org-admin-members-api/)
- [Ghost Content and Admin APIs Admin - Images Admin - Newsletters API](https://apis.io/collections/ghost-org/open-ghost-org-admin-newsletters-api/)
- [Ghost Content and Admin APIs Admin - Images Admin - Offers API](https://apis.io/collections/ghost-org/open-ghost-org-admin-offers-api/)
- [Ghost Content and Admin APIs Admin - Images Admin - Pages API](https://apis.io/collections/ghost-org/open-ghost-org-admin-pages-api/)
- [Ghost Content and Admin APIs Admin - Images Admin - Posts API](https://apis.io/collections/ghost-org/open-ghost-org-admin-posts-api/)
- [Ghost Content and Admin APIs Admin - Images Admin - Site API](https://apis.io/collections/ghost-org/open-ghost-org-admin-site-api/)
- [Ghost Content and Admin APIs Admin - Images Admin - Tags API](https://apis.io/collections/ghost-org/open-ghost-org-admin-tags-api/)
- [Ghost Content and Admin APIs Admin - Images Admin - Themes API](https://apis.io/collections/ghost-org/open-ghost-org-admin-themes-api/)
- [Ghost Content and Admin APIs Admin - Images Admin - Tiers API](https://apis.io/collections/ghost-org/open-ghost-org-admin-tiers-api/)
- [Ghost Content and Admin APIs Admin - Images Admin - Users API](https://apis.io/collections/ghost-org/open-ghost-org-admin-users-api/)
- [Ghost Content and Admin APIs Admin - Images Admin - Webhooks API](https://apis.io/collections/ghost-org/open-ghost-org-admin-webhooks-api/)
- [Ghost Admin Authors API](https://apis.io/collections/ghost-org/open-ghost-org-authors-api/)
- [Ghost Content API](https://apis.io/collections/ghost-org/open-ghost-org-content-api/)
- [Ghost Content and Admin APIs Admin - Images Content - Authors API](https://apis.io/collections/ghost-org/open-ghost-org-content-authors-api/)
- [Ghost Content and Admin APIs Admin - Images Content - Pages API](https://apis.io/collections/ghost-org/open-ghost-org-content-pages-api/)
- [Ghost Content and Admin APIs Admin - Images Content - Posts API](https://apis.io/collections/ghost-org/open-ghost-org-content-posts-api/)
- [Ghost Content and Admin APIs Admin - Images Content - Settings API](https://apis.io/collections/ghost-org/open-ghost-org-content-settings-api/)
- [Ghost Content and Admin APIs Admin - Images Content - Tags API](https://apis.io/collections/ghost-org/open-ghost-org-content-tags-api/)
- [Ghost Content and Admin APIs Admin - Images Content - Tiers API](https://apis.io/collections/ghost-org/open-ghost-org-content-tiers-api/)
- [Ghost Admin Authors Images API](https://apis.io/collections/ghost-org/open-ghost-org-images-api/)
- [Ghost Admin Authors Members API](https://apis.io/collections/ghost-org/open-ghost-org-members-api/)
- …and 11 more published on APIs.io

#### Overlays (52)

OpenAPI overlays, including conversational phrasing for each operation.

- [Ghost Org Admin Images Api Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-images-api-overlay/)
- [Ghost Org Admin Images Api Phrasing Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-images-api-phrasing-overlay/)
- [Ghost Org Admin Labels Api Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-labels-api-overlay/)
- [Ghost Org Admin Labels Api Phrasing Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-labels-api-phrasing-overlay/)
- [Ghost Org Admin Members Api Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-members-api-overlay/)
- [Ghost Org Admin Members Api Phrasing Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-members-api-phrasing-overlay/)
- [Ghost Org Admin Newsletters Api Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-newsletters-api-overlay/)
- [Ghost Org Admin Newsletters Api Phrasing Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-newsletters-api-phrasing-overlay/)
- [Ghost Org Admin Offers Api Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-offers-api-overlay/)
- [Ghost Org Admin Offers Api Phrasing Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-offers-api-phrasing-overlay/)
- [Ghost Org Admin Pages Api Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-pages-api-overlay/)
- [Ghost Org Admin Pages Api Phrasing Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-pages-api-phrasing-overlay/)
- [Ghost Org Admin Posts Api Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-posts-api-overlay/)
- [Ghost Org Admin Posts Api Phrasing Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-posts-api-phrasing-overlay/)
- [Ghost Org Admin Site Api Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-site-api-overlay/)
- [Ghost Org Admin Site Api Phrasing Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-site-api-phrasing-overlay/)
- [Ghost Org Admin Tags Api Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-tags-api-overlay/)
- [Ghost Org Admin Tags Api Phrasing Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-tags-api-phrasing-overlay/)
- [Ghost Org Admin Themes Api Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-themes-api-overlay/)
- [Ghost Org Admin Themes Api Phrasing Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-themes-api-phrasing-overlay/)
- [Ghost Org Admin Tiers Api Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-tiers-api-overlay/)
- [Ghost Org Admin Tiers Api Phrasing Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-tiers-api-phrasing-overlay/)
- [Ghost Org Admin Users Api Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-users-api-overlay/)
- [Ghost Org Admin Users Api Phrasing Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-users-api-phrasing-overlay/)
- [Ghost Org Admin Webhooks Api Overlay](https://apis.io/overlays/ghost-org/ghost-org-admin-webhooks-api-overlay/)
- …and 27 more published on APIs.io

#### Governance rules (2)

Spectral rulesets for the provider's contracts.

- [Ghost — asyncapi rules](https://apis.io/rules/ghost-org/ghost-org-asyncapi-spectral-rules/)
- [Ghost — jsonschema rules](https://apis.io/rules/ghost-org/ghost-org-jsonschema-spectral-rules/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Ghost Org Authentication](https://apis.io/security/ghost-org/ghost-org-authentication/)
- [Ghost Org Domain Security](https://apis.io/security/ghost-org/ghost-org-domain-security/)
- [Ghost Org Vulnerability Disclosure](https://apis.io/security/ghost-org/ghost-org-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Ghost Org Plans Pricing](https://apis.io/plans/ghost-org/ghost-org-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Ghost Org Rate Limits](https://apis.io/rate-limits/ghost-org/ghost-org-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Ghost Org Finops](https://apis.io/finops/ghost-org/ghost-org-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://ghost.org)
- [Documentation](https://docs.ghost.org)
- [Getting started](https://docs.ghost.org/install)
- [API reference](https://docs.ghost.org/content-api)
- [Pricing](https://ghost.org/pricing/)
- [Sign up](https://ghost.org/signup/)
- [Support](https://ghost.org/help/)
- [Changelog](https://ghost.org/changelog)
- [Blog](https://ghost.org/resources/)
- [Terms of service](https://ghost.org/terms/)
- [Privacy policy](https://ghost.org/privacy/)
- [GitHub](https://github.com/TryGhost)
- [Status](https://status.ghost.org)

## API Evangelist rating

**Kin Score 77.1** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 80.0 |
| Contract quality | 66.7 |
| Contract governance | 31.8 |
| Operational transparency | 89.5 |
| Developer ergonomics | 86.9 |
| Access clarity | 76.3 |

**Agent readiness 32.3** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | derived (partial credit) |
| Agent Skills | yes |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 30.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/ghost-org/](https://apis.io/providers/ghost-org/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Ghost: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/ghost-org/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
