---
name: Ghost
description: Use when building or managing Ghost publications, creating and publishing content, developing custom themes, integrating with external services via APIs or webhooks, configuring memberships and newsletters, or migrating content from other platforms.
metadata:
    mintlify-proj: ghost
    version: "1.0"
---

# Ghost Skill Reference

## Product Summary

Ghost is an open-source, Node.js-based publishing platform designed for independent creators and professional publishers. It combines a modern REST API with a powerful editor, built-in memberships and newsletters, and a Handlebars-based theme system. Ghost runs on a recommended stack of Ubuntu, Node.js 22 LTS, MySQL 8.0+, and NGINX. Key files include `config.production.json` and `config.development.json` for configuration, and the `content/` directory for themes, images, and data. Primary CLI tool is `ghost-cli` for installation, updates, and management. Access the full documentation at https://docs.ghost.org.

## When to Use

Reach for this skill when:

- **Publishing workflows**: Creating, scheduling, publishing, or sending posts via email; managing drafts and revisions
- **Content management**: Building tag hierarchies, managing authors and contributors, setting up custom routing
- **Theme development**: Building custom Handlebars themes, adding custom settings, validating with GScan
- **API integrations**: Reading published content via Content API, managing content via Admin API, building headless frontends
- **Membership & monetization**: Creating tiers, managing subscribers, setting up payment workflows, creating offers
- **Newsletters**: Configuring newsletters, sending to segments, managing subscriber lists
- **Webhooks & automation**: Triggering external services on publish events, syncing content to search indexes
- **Configuration & deployment**: Setting up mail, database, storage adapters, SSL, environment variables
- **Migration**: Importing content from WordPress, Substack, Medium, or other platforms

## Quick Reference

### Ghost-CLI Commands

| Command | Purpose |
|---------|---------|
| `ghost install` | Install Ghost (production or local) |
| `ghost install local` | Install for development with SQLite |
| `ghost start` | Start Ghost instance |
| `ghost stop` | Stop Ghost instance |
| `ghost restart` | Restart Ghost (required after config changes) |
| `ghost update [version]` | Update to latest or specific version |
| `ghost config [key] [value]` | View or set configuration |
| `ghost setup [stages]` | Configure MySQL, NGINX, SSL, systemd |
| `ghost backup` | Create full backup (content, members, themes, images) |
| `ghost log [-e] [-n 100]` | View access or error logs |
| `ghost doctor` | Check system for compatibility issues |

### Configuration Files

| File | Purpose |
|------|---------|
| `config.production.json` | Production environment settings |
| `config.development.json` | Development environment settings |
| `config.local.json` | Local overrides (ignored in git) |
| `content/settings/routes.yaml` | Custom routing configuration |
| `content/themes/[name]/package.json` | Theme metadata and custom settings |

### Required Configuration (Production)

```json
{
  "url": "https://example.com",
  "database": {
    "client": "mysql",
    "connection": {
      "host": "127.0.0.1",
      "user": "ghost_user",
      "password": "password",
      "database": "ghost_prod"
    }
  },
  "mail": {
    "transport": "SMTP",
    "options": {
      "service": "Mailgun",
      "auth": {
        "user": "postmaster@example.mailgun.org",
        "pass": "password"
      }
    },
    "from": "noreply@example.com"
  }
}
```

### API Authentication

| Method | Use Case | Security |
|--------|----------|----------|
| **Content API Key** | Read-only public data (posts, pages, tags, authors) | Safe for browsers; passed as query parameter |
| **Admin API Token** | Create/edit content, manage members, webhooks | Server-side only; generated from API key |
| **Staff Access Token** | User-specific operations with role permissions | Server-side only; found in user settings |
| **User Authentication** | Session-based with email/password | Browser-safe with 2FA support |

### API Base URLs

```
Content API:  https://{admin_domain}/ghost/api/content/
Admin API:    https://{admin_domain}/ghost/api/admin/
```

### Theme Helpers (Common)

| Helper | Purpose |
|--------|---------|
| `{{#foreach posts}}` | Loop through posts |
| `{{#if @member}}` | Conditional for logged-in members |
| `{{@custom.setting_name}}` | Access custom theme settings |
| `{{img_url feature_image}}` | Generate responsive image URLs |
| `{{#match primary_tag.name "News"}}` | Match tag names |
| `{{reading_time}}` | Calculate reading time |
| `{{pagination}}` | Render pagination controls |

## Decision Guidance

### When to Use Content API vs Admin API

| Scenario | Use Content API | Use Admin API |
|----------|-----------------|--------------|
| Display published posts on frontend | ✅ | ❌ |
| Create/edit posts programmatically | ❌ | ✅ |
| Fetch member data | ❌ | ✅ |
| Build headless frontend | ✅ | ❌ |
| Manage webhooks | ❌ | ✅ |
| Read-only public data | ✅ | ❌ |

### When to Use Token vs User Authentication

| Scenario | Token Auth | User Auth |
|----------|-----------|-----------|
| Server-side integration | ✅ | ❌ |
| Browser-based app | ❌ | ✅ |
| Automated workflows | ✅ | ❌ |
| User-specific operations | ❌ | ✅ |
| Requires 2FA | ❌ | ✅ |
| Single integration | ✅ | ❌ |

### When to Use Handlebars Theme vs Headless

| Scenario | Handlebars Theme | Headless (API) |
|----------|------------------|----------------|
| Traditional blog site | ✅ | ❌ |
| Custom frontend framework | ❌ | ✅ |
| Static site generation | ❌ | ✅ |
| Mobile app backend | ❌ | ✅ |
| Quick deployment | ✅ | ❌ |
| Full design control | ✅ | ✅ |

## Workflow

### Publishing a Post via Admin API

1. **Authenticate**: Generate JWT token from Admin API key (id:secret split, HS256 algorithm, 5-minute expiry)
2. **Create draft**: POST to `/admin/posts/` with title, html, and status: "draft"
3. **Add metadata**: Update post with tags, authors, feature_image, meta_title, meta_description
4. **Schedule or publish**: PUT to `/admin/posts/{id}/` with status: "published" and published_at timestamp
5. **Send via email** (optional): Include `?newsletter=slug` query parameter and email_segment filter
6. **Verify**: Fetch post from Content API to confirm visibility

### Building a Custom Theme

1. **Create structure**: Set up `package.json`, `default.hbs`, `post.hbs`, `page.hbs`, `index.hbs`, `author.hbs`, `tag.hbs`, `error.hbs`
2. **Define custom settings**: Add `config.custom` array to `package.json` with select, boolean, color, image, or text types (max 20 settings)
3. **Write templates**: Use Handlebars with Ghost helpers (`{{#foreach}}`, `{{#if}}`, `{{@custom}}`, `{{img_url}}`)
4. **Add assets**: Create `assets/css/` and `assets/js/` directories; reference with `{{asset}}` helper
5. **Validate**: Run `gscan /path/to/theme` or upload to Ghost Admin for automatic validation
6. **Upload**: ZIP theme folder and upload via Admin API or Ghost Admin UI
7. **Activate**: PUT to `/admin/themes/{name}/activate` to set as active theme

### Configuring Webhooks for Content Sync

1. **Create integration**: Go to Settings > Integrations > Add custom integration
2. **Copy Admin API key**: Store key securely for token generation
3. **Create webhook**: POST to `/admin/webhooks/` with event (e.g., "post.published") and target_url
4. **Handle payload**: Receive POST at target_url with post data; respond with 2xx status
5. **Test**: Publish a post and verify webhook delivery in Ghost Admin
6. **Implement logic**: Parse webhook payload and trigger external actions (rebuild search index, notify Slack, etc.)

### Setting Up Memberships & Tiers

1. **Connect Stripe**: Settings > Memberships > Connect Stripe account
2. **Create tiers**: Admin API POST to `/admin/tiers/` with name, monthly_price, yearly_price, currency
3. **Define benefits**: Add benefits array to tier (strings describing tier benefits)
4. **Create offers**: POST to `/admin/offers/` with tier_id, discount_type, duration for promotions
5. **Configure Portal**: Settings > Portal settings to customize signup/login UI
6. **Add to theme**: Use `{{#if @member}}` and `{{tiers}}` helpers to show member-only content
7. **Manage members**: Browse `/admin/members/` to view, edit, or segment subscribers

## Common Gotchas

- **Config changes require restart**: Always run `ghost restart` after editing `config.json` files; environment variables take priority over file values
- **JWT tokens expire in 5 minutes**: Regenerate tokens for each request; don't cache them
- **Admin API key is secret**: Never expose in browser or version control; use server-side only
- **Content API key is public**: Safe to embed in frontend code; only provides access to published content
- **Theme upload fails silently**: Use GScan to validate before uploading; check Ghost Admin for fatal errors
- **Routes.yaml requires restart**: Edit via Ghost Admin UI for automatic reload, or restart if editing file directly
- **Mail not configured**: Transactional emails (invites, password resets) won't send without mail config; test with Mailgun sandbox first
- **Database connections**: Default pool is min 2, max 10; adjust for high-traffic sites
- **Image storage**: Default is local filesystem; configure S3 or other adapters in config for scalability
- **Member imports**: Create tiers before importing paid subscribers; Ghost won't find tier/product in Stripe otherwise
- **Newsletter segments**: Use NQL filters (e.g., `status:free`, `status:-free`, `all`) to target member subsets
- **Custom storage adapters**: Must inherit from `ghost-storage-base` and implement save, exists, serve, delete, read methods
- **Deprecated patterns**: `@blog`, `@price`, `@products`, `@product`, `@member.product` removed in v5+; use new tier/price syntax
- **CORS in browser**: Ensure correct domain and protocol in API URLs; Ghost(Pro) requires https

## Verification Checklist

Before submitting work:

- [ ] Configuration file is valid JSON and uses correct environment (production/development)
- [ ] `ghost restart` has been run after config changes
- [ ] API keys are stored securely and not exposed in code or version control
- [ ] JWT tokens are generated server-side with correct header, payload, and HS256 signature
- [ ] Theme passes GScan validation (no fatal errors)
- [ ] Theme `package.json` has correct structure and custom settings are defined
- [ ] Webhooks are receiving POST requests and responding with 2xx status
- [ ] Mail is configured and transactional emails are being sent
- [ ] Database backups exist before major updates or migrations
- [ ] Content API requests include correct Accept-Version header
- [ ] Admin API requests include Authorization header with Ghost token
- [ ] Member tiers and Stripe products are synced
- [ ] Routes.yaml is valid YAML and reloaded (via Admin UI or restart)
- [ ] Images are stored in configured location (local, S3, etc.)
- [ ] SSL certificate is valid and renewed (Let's Encrypt auto-renewal via acme.sh)

## Resources

- **Comprehensive navigation**: https://docs.ghost.org/llms.txt — page-by-page listing of all documentation
- **Admin API reference**: https://docs.ghost.org/admin-api — full endpoint documentation with examples
- **Content API reference**: https://docs.ghost.org/content-api — read-only API for published content
- **Theme development**: https://docs.ghost.org/themes — Handlebars templating, helpers, and custom settings
- **Configuration guide**: https://docs.ghost.org/config — all config options, mail setup, adapters, and environment variables

---

> For additional documentation and navigation, see: https://docs.ghost.org/llms.txt