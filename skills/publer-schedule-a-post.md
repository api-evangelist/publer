---
name: publer-schedule-a-post
description: Schedule a social media post to one or more connected Publer accounts and confirm it actually landed, using the Publer API v1 submit-and-poll pattern.
api: Publer API v1
base_url: https://app.publer.com/api/v1
generated: '2026-08-13'
method: generated
source: openapi/_original/publer-openapi.yml, https://publer.com/docs/getting-started/quickstart.md
operations:
  - listWorkspaces
  - listAccounts
  - schedulePosts
  - getJobStatus
  - listPosts
---

# Schedule a post with Publer

Publish or schedule content to connected social accounts. Every write on this
API is asynchronous: you submit, you get a `job_id`, and you are not done until
you have polled the job **and inspected `payload.failures`**.

## Before you start

- The Publer API is available only to Enterprise plan users, Business plan users
  in good standing, and Top Ambassadors.
- The API key must carry the `workspaces`, `accounts` and `posts` scopes.
- Every request needs both headers:
  - `Authorization: Bearer-API YOUR_API_KEY` — note the non-standard
    `Bearer-API` prefix; a plain `Bearer` will fail with 401.
  - `Publer-Workspace-Id: <workspace id>` — omitting it returns **403**, not 401.

## Steps

### 1. Resolve the workspace — `listWorkspaces`

```
GET /workspaces
```

Pick the `id` of the workspace you are operating in. Send it as
`Publer-Workspace-Id` on every subsequent call.

### 2. Resolve the target accounts — `listAccounts`

```
GET /accounts
```

Returns each connected account with `id`, `provider` (facebook, instagram,
twitter, linkedin, tiktok, youtube, pinterest, google, wordpress, telegram,
mastodon, threads, bluesky) and `type` (page, profile, group, business, channel,
location, blog). You need the `id` values, and you need `provider` to choose the
right network content shape in step 3.

### 3. Submit the post — `schedulePosts`

```
POST /posts/schedule
```

The body is one bulk envelope. `networks` is keyed by provider name, `accounts`
lists the targets with an optional per-account `scheduled_at`:

```json
{
  "bulk": {
    "state": "scheduled",
    "posts": [
      {
        "networks": {
          "facebook": { "type": "status", "text": "Status Update Post" }
        },
        "accounts": [
          { "id": "ACCOUNT_ID", "scheduled_at": "2026-09-06T14:16+02:00" }
        ]
      }
    ]
  }
}
```

- `bulk.state` must be one of `scheduled`, `draft`, `draft_private`,
  `draft_public`, `recurring`. Use `draft` to stage without publishing.
- `scheduled_at` is ISO 8601 **with a timezone offset**:
  `YYYY-MM-DDThh:mm:ss±hh:mm`.
- Response is **202 Accepted** with `{"job_id": "..."}`. Nothing has published
  yet.

### 4. Poll the job — `getJobStatus`

```
GET /job_status/{job_id}
```

`status` is `working`, `complete` or `failed`. Poll with backoff until it leaves
`working`.

### 5. Check for partial failure — this is the step people skip

A job can report `"status": "complete"` while individual accounts failed. The
failures are in `payload.failures[]`:

```json
{
  "status": "complete",
  "payload": {
    "failures": [
      {
        "account_id": "...",
        "account_name": "Test Page",
        "provider": "facebook",
        "message": "There's another post at this time. A one minute gap is required between posts"
      }
    ]
  }
}
```

**Treat a non-empty `failures` array as a failure** regardless of `status` and
regardless of the HTTP status. Report the per-account messages to the user; do
not claim the post published.

### 6. Verify — `listPosts`

```
GET /posts?state=scheduled
```

Confirms the created records. Note `from` and `to` are mutually dependent — pass
both or neither.

## Rules that will bite you

- **No idempotency key exists.** Publer documents none. A retried
  `POST /posts/schedule` can publish twice. Track your own client-side key and
  do not blind-retry a write whose response you did not read. If you must
  reconcile, use `listPosts` filtered by `account_ids[]` and time window before
  re-submitting.
- **Rate limit is 100 requests per 2-minute fixed window per user account**,
  across all API keys. Read `X-RateLimit-Remaining` and `X-RateLimit-Reset`
  (UNIX timestamp) and back off. On 429 the body is
  `{"error": "..."}` — singular `error`, not the `errors` array every other
  error uses. No `Retry-After` is sent.
- **Daily post limits apply per network per plan**, on a rolling 24-hour UTC
  window (for example Twitter/X: 25 Free, 50 Professional, 100 Business). These
  surface as job failures, not as HTTP errors.
- **Batch instead of looping.** One bulk request with many accounts costs one
  request against the rate limit; a loop costs one per account.
- Errors are `{"errors": ["message"]}` with no machine-readable code. 403 means
  missing scope **or** missing workspace header **or** missing plan entitlement —
  read the message string to tell them apart.
