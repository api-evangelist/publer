# Publer (publer)

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
