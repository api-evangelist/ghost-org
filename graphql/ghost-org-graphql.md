# Ghost GraphQL API

Ghost does not provide a native GraphQL API. Ghost exposes two RESTful HTTP APIs: the read-only Content API, intended for public browser clients, and the write-capable Admin API, intended for server-side integrations. Both APIs return JSON over HTTP and use query parameters or JWT-based tokens for authentication. As of June 2026, no GraphQL endpoint, no GraphQL gateway layer, and no official plans for GraphQL support appear in Ghost's changelog, documentation, or public GitHub repository.

The Content API is accessible at `https://{your_ghost_domain}/ghost/api/content/` and accepts a `key` query parameter for authentication. The Admin API is accessible at `https://{your_ghost_domain}/ghost/api/admin/` and uses short-lived JWTs derived from Admin API keys or staff access tokens. Both APIs require an `Accept-Version` header to pin the API version.

Despite the absence of a native GraphQL layer, Ghost's data model is well-defined and maps cleanly to GraphQL SDL types. The conceptual schema below documents the confirmed resource types — Post, Page, Tag, Author, Tier, Settings, Member, Newsletter, Offer, Label, User, and Webhook — as they appear in Ghost's REST responses. This schema is provided as a data-model reference; it does not represent an operational GraphQL endpoint.

**Endpoint:** None — Ghost does not expose a GraphQL endpoint.

**Documentation:** https://docs.ghost.org/

**References:**
- Documentation: https://docs.ghost.org/
- GettingStarted: https://docs.ghost.org/content-api/
- ContentAPI: https://docs.ghost.org/content-api/
- AdminAPI: https://docs.ghost.org/admin-api/
