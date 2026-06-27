# Publer (publer)

Publer is a social-media scheduling and management platform for planning, creating, and publishing content across networks like Facebook, Instagram, X, LinkedIn, TikTok, YouTube, Pinterest, and more. The Publer API (v1) lets Business customers programmatically schedule and publish posts, manage connected social accounts and workspaces, work with media libraries, and track asynchronous jobs.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/publer/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/publer/refs/heads/main/apis.yml)

## Tags

- Social Media
- Scheduling
- Publishing
- Content Management
- Marketing

## Timestamps

- **Created:** 2026-06-25
- **Modified:** 2026-06-25

## APIs

### Publer Posts & Scheduling API

List, filter, and search posts, then schedule posts for future publication (including drafts) or publish content immediately across connected social networks. Scheduling and publishing run asynchronously and return a job id.

- **Human URL:** [https://publer.com/docs/api-reference/posts](https://publer.com/docs/api-reference/posts)
- **Base URL:** `https://app.publer.com/api/v1`

#### Tags

- Posts
- Scheduling
- Publishing

#### Properties

- [Documentation](https://publer.com/docs/api-reference/posts)
- [API Reference](https://publer.com/docs/posting/create-posts)
- [OpenAPI](openapi/publer-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/publer.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/publer.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Publer Accounts API

Retrieve the list of connected social media accounts available in the selected workspace across providers such as Facebook, Instagram, X, LinkedIn, TikTok, YouTube, Pinterest, Bluesky, Threads, Mastodon, and more.

- **Human URL:** [https://publer.com/docs/api-reference/accounts](https://publer.com/docs/api-reference/accounts)
- **Base URL:** `https://app.publer.com/api/v1`

#### Tags

- Accounts
- Social Accounts
- Connections

#### Properties

- [Documentation](https://publer.com/docs/api-reference/accounts)
- [OpenAPI](openapi/publer-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/publer.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/publer.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Publer Workspaces API

Retrieve the list of workspaces the authenticated user has access to, including owner, members, plan, and picture, used to scope all other API requests via the Publer-Workspace-Id header.

- **Human URL:** [https://publer.com/docs/api-reference/workspaces](https://publer.com/docs/api-reference/workspaces)
- **Base URL:** `https://app.publer.com/api/v1`

#### Tags

- Workspaces
- Organization
- Teams

#### Properties

- [Documentation](https://publer.com/docs/api-reference/workspaces)
- [OpenAPI](openapi/publer-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/publer.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/publer.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Publer Media API

Retrieve a paginated list of media items from the workspace library, filter by type (photo, video, gif), usage status, source, and search term, or fetch specific media items by their IDs.

- **Human URL:** [https://publer.com/docs/api-reference/media](https://publer.com/docs/api-reference/media)
- **Base URL:** `https://app.publer.com/api/v1`

#### Tags

- Media
- Library
- Assets

#### Properties

- [Documentation](https://publer.com/docs/api-reference/media)
- [OpenAPI](openapi/publer-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/publer.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/publer.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Publer Jobs API

Poll the status of asynchronous operations (such as scheduling and publishing) by job id, returned as 202 Accepted responses, to monitor completion and retrieve results.

- **Human URL:** [https://publer.com/docs/api-reference/posts](https://publer.com/docs/api-reference/posts)
- **Base URL:** `https://app.publer.com/api/v1`

#### Tags

- Jobs
- Async
- Status

#### Properties

- [Documentation](https://publer.com/docs/posting/create-posts)
- [OpenAPI](openapi/publer-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/publer.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/publer.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [GitHub Organization](https://github.com/Publer)
- [LinkedIn](https://www.linkedin.com/company/publer)
- [Website](https://publer.com/)
- [Documentation](https://publer.com/docs)
- [Plans](plans/publer-plans-pricing.yml)
- [Rate Limits](rate-limits/publer-rate-limits.yml)
- [Fin Ops](finops/publer-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
