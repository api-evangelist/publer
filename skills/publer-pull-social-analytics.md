---
name: publer-pull-social-analytics
description: Pull Publer analytics — charts, post insights, hashtag performance, best times to post, member activity and competitor comparison — for reporting or dashboards.
api: Publer API v1
base_url: https://app.publer.com/api/v1
generated: '2026-08-13'
method: generated
source: openapi/_original/publer-openapi.yml, https://publer.com/docs/analytics/charts.md
operations:
  - listWorkspaces
  - listAccounts
  - getAvailableAnalyticsCharts
  - getAnalyticsChartData
  - getPostInsights
  - getHashtagInsights
  - getHashtagPerformingPosts
  - getBestTimesToPostForAccount
  - getAnalyticsMembersData
  - listCompetitors
  - getCompetitorsAnalytics
---

# Pull Publer analytics

## Prerequisites

- Scopes: `workspaces`, `accounts`, and `analytics`.
- Headers: `Authorization: Bearer-API YOUR_API_KEY`,
  `Publer-Workspace-Id: <workspace id>`.
- Entitlement is checked separately from scope: analytics endpoints return
  **403 "Permission denied - requires analytics access or paying subscription"**
  even with a correctly scoped key on an ineligible plan. Do not retry a 403
  here — it will not clear.

## Steps

### 1. Resolve the account — `listAccounts`

```
GET /accounts
```

Every per-account analytics endpoint takes `account_id` as a **path** parameter.
Get it here first.

### 2. Discover what is available — `getAvailableAnalyticsCharts`

```
GET /analytics/charts
```

Ask what charts exist for this workspace before requesting data. Chart
availability varies by network — do not hardcode a chart list.

### 3. Fetch chart data — `getAnalyticsChartData`

```
GET /analytics/chart_data
```

Drives dashboards. Pair each series with the chart descriptor from step 2 so
labels and units stay correct.

### 4. Per-post metrics — `getPostInsights`

```
GET /analytics/{account_id}/post_insights
```

Supports filtering, sorting and pagination (`page`, 0-based). Also supports a
competitor mode. This is the endpoint behind "which posts performed best".

### 5. Hashtags — `getHashtagInsights`, `getHashtagPerformingPosts`

```
GET /analytics/{account_id}/hashtag_insights
GET /analytics/{account_id}/hashtag_performing_posts
```

Aggregate hashtag performance, then the top posts per hashtag. Run them as a
pair: the first tells you which hashtags matter, the second tells you why.

### 6. Timing — `getBestTimesToPostForAccount`

```
GET /analytics/{account_id}/best_times
```

Returns a day-of-week × hour-of-day heatmap. Optional `competitors=true` and
`competitor_id` switch it to competitor posting patterns.

Feed the result straight into `scheduled_at` on
`publer-schedule-a-post` — this is the highest-value composition on the whole
API.

### 7. Team activity — `getAnalyticsMembersData`

```
GET /analytics/members
```

Per-member posts, reach and engagements. Workspace-scoped, not account-scoped.

### 8. Competitors — `listCompetitors`, `getCompetitorsAnalytics`

```
GET /competitors/{account_id}
GET /competitors/{account_id}/analytics
```

List the competitors tracked against one of your accounts, then compare
followers, engagement, reach and posting mix.

## Rules that will bite you

- **Budget your calls.** A full report across 10 accounts × 6 analytics
  endpoints is 60 requests against a 100-request / 2-minute window. Sequence the
  pulls, read `X-RateLimit-Remaining`, and pause until `X-RateLimit-Reset`.
- All analytics operations are **read-only**. Nothing here mutates state, so
  they are safe to retry once the window resets — with the exception of 403,
  which is an entitlement decision, not a transient error.
- Timestamps are ISO 8601 with offset; daily aggregation windows are UTC.
- These endpoints are synchronous — no `job_id`, no polling. Only writes are
  async on this API.
