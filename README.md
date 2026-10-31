# Publer

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

Publer is a social-media scheduling and management platform for planning, creating, publishing and analyzing content across Facebook, Instagram, X/Twitter, LinkedIn, TikTok, YouTube, Pinterest, Threads, Bluesky, Mastodon, Google Business Profiles, WordPress and Telegram. The Publer API (v1) is a RESTful JSON interface at https://app.publer.com/api/v1 covering 21 operations: schedule and publish posts, update and delete them, manage connected social accounts and workspaces, upload and list media, resolve asynchronous jobs, and read analytics including post insights, hashtag performance, best times to post and competitor comparison. Authentication is an API key sent as Authorization: Bearer-API with a Publer-Workspace-Id header, scoped per key. Publer also ships a first-party hosted MCP server in beta. API access is limited to Enterprise plan users, Business plan users in good standing, and Top Ambassadors.

**Areas:** Social Media · Scheduling · Publishing · Content Management · Marketing · Social Media Management · Analytics · Agents · MCP · Automation

## Publer on APIs.io

Everything profiled for Publer is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/publer/](https://apis.io/providers/publer/)** — or go straight to one of the APIs or properties below.

### APIs (8)

- [Publer Accounts API](https://apis.io/apis/publer/publer-accounts-api/) — The Accounts API from Publer — 1 operation for listing the social media accounts (Facebook, Instagram, X/Twitter, LinkedIn, TikTok, YouTube, Pinterest,…
- [Publer Analytics API](https://apis.io/apis/publer/publer-analytics-api/) — The Analytics API from Publer — 7 operations for social analytics: available charts and chart data, per-post insights, hashtag insights and top hashtag…
- [Publer Competitors API](https://apis.io/apis/publer/publer-competitors-api/) — The Competitors API from Publer — 2 operations for listing the competitor accounts tracked against one of your social accounts and comparing followers,…
- [Publer Jobs API](https://apis.io/apis/publer/publer-jobs-api/) — The Jobs API from Publer — 1 operation for resolving the asynchronous job returned by every write on the Publer API. Scheduling, publishing and…
- [Publer Media API](https://apis.io/apis/publer/publer-media-api/) — The Media API from Publer — 3 operations for the workspace media library: list and filter photos, videos and GIFs by type, usage, source and search term,…
- [Publer Posts API](https://apis.io/apis/publer/publer-posts-api/) — The Posts API from Publer — 5 operations covering the content lifecycle: list posts with state, date, account, member and full-text filters, schedule a bulk…
- [Publer Users API](https://apis.io/apis/publer/publer-users-api/) — The Users API from Publer — 1 operation returning the profile of the currently authenticated user (id, email, name and picture), used to adapt an…
- [Publer Workspaces API](https://apis.io/apis/publer/publer-workspaces-api/) — The Workspaces API from Publer — 1 operation listing every workspace the authenticated user can reach, with owner, members, plan and picture. The workspace…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Publer MCP Server](https://apis.io/servers/publer/publer-mcp-server/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Publer Agentic Access](https://apis.io/agentic-access/publer/publer-agentic-access/)

#### Collections (9)

Postman and Open Collection request collections.

- [Publer API](https://apis.io/collections/publer/open-publer/)
- [Publer Accounts API](https://apis.io/collections/publer/open-publer-accounts-api/)
- [Publer Analytics API](https://apis.io/collections/publer/open-publer-analytics-api/)
- [Publer Competitors API](https://apis.io/collections/publer/open-publer-competitors-api/)
- [Publer Jobs API](https://apis.io/collections/publer/open-publer-jobs-api/)
- [Publer Media API](https://apis.io/collections/publer/open-publer-media-api/)
- [Publer Posts API](https://apis.io/collections/publer/open-publer-posts-api/)
- [Publer Users API](https://apis.io/collections/publer/open-publer-users-api/)
- [Publer Workspaces API](https://apis.io/collections/publer/open-publer-workspaces-api/)

#### Overlays (8)

OpenAPI overlays, including conversational phrasing for each operation.

- [Publer Accounts Overlay](https://apis.io/overlays/publer/publer-accounts-overlay/)
- [Publer Analytics Overlay](https://apis.io/overlays/publer/publer-analytics-overlay/)
- [Publer Competitors Overlay](https://apis.io/overlays/publer/publer-competitors-overlay/)
- [Publer Jobs Overlay](https://apis.io/overlays/publer/publer-jobs-overlay/)
- [Publer Media Overlay](https://apis.io/overlays/publer/publer-media-overlay/)
- [Publer Posts Overlay](https://apis.io/overlays/publer/publer-posts-overlay/)
- [Publer Users Overlay](https://apis.io/overlays/publer/publer-users-overlay/)
- [Publer Workspaces Overlay](https://apis.io/overlays/publer/publer-workspaces-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Publer Authentication](https://apis.io/security/publer/publer-authentication/)
- [Publer Domain Security](https://apis.io/security/publer/publer-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Publer Scopes](https://apis.io/scopes/publer/publer-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Publer Plans Pricing](https://apis.io/plans/publer/publer-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Publer Rate Limits](https://apis.io/rate-limits/publer/publer-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Publer Finops](https://apis.io/finops/publer/publer-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://publer.com/)
- [Documentation](https://publer.com/docs)
- [Getting started](https://publer.com/docs/getting-started/quickstart)
- [API reference](https://publer.com/docs/api-reference/introduction)
- [Pricing](https://publer.com/pricing)
- [Support](https://publer.com/help)
- [Blog](https://publer.com/blog/feed/)
- [Terms of service](https://publer.com/terms)
- [Privacy policy](https://publer.com/privacy)
- [GitHub](https://github.com/Publer)
- [Status](https://status.publer.com)

## API Evangelist rating

**Kin Score 38.9** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 71.7 |
| Contract quality | 51.9 |
| Contract governance | 4.5 |
| Operational transparency | 50.0 |
| Developer ergonomics | 22.0 |
| Access clarity | 31.6 |

**Agent readiness 29.9** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 26.5** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/publer/](https://apis.io/providers/publer/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Publer: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/publer/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
