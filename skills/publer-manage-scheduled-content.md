---
name: publer-manage-scheduled-content
description: Find, update and delete existing Publer posts safely — the read/edit/remove half of the content lifecycle.
api: Publer API v1
base_url: https://app.publer.com/api/v1
generated: '2026-08-13'
method: generated
source: openapi/_original/publer-openapi.yml, https://publer.com/docs/posting/update-posts.md, https://publer.com/docs/posting/delete-posts.md
operations:
  - listWorkspaces
  - listAccounts
  - listPosts
  - updatePost
  - deleteMultiplePosts
  - getJobStatus
---

# Manage scheduled Publer content

## Prerequisites

- Scopes: `workspaces`, `accounts`, `posts`.
- Headers: `Authorization: Bearer-API YOUR_API_KEY`,
  `Publer-Workspace-Id: <workspace id>`.

## Steps

### 1. Find the posts — `listPosts`

```
GET /posts?state=scheduled&page=0
```

Filters:

| parameter | notes |
|---|---|
| `state` / `state[]` | single or multiple post states |
| `from`, `to` | ISO dates — **mutually dependent**, pass both or neither |
| `account_ids[]` | restrict to specific accounts |
| `query` | full-text keyword |
| `postType` | filter by post type |
| `member_id` | filter by workspace member |
| `page` | 0-based, default 0 |

The response envelope is `{"posts": [...], "total", "page", "per_page",
"total_pages"}`. There is **no way to request a page size** — `per_page` is
reported, not settable. Walk pages until you have `total`.

List results are `PostSummary` objects (`id`, `text`, `state`, `type`,
`account_id`, `scheduled_at`, `post_link`, `has_media`, `network`) — a thinner
shape than the full `PostDetail`. Do not assume a listed post carries its media
array.

### 2. Update one post — `updatePost`

```
PUT /posts/{id}
```

One post at a time; there is no bulk update. A post is bound to exactly one
account, so editing a message that went to five accounts means five calls —
budget them against the 100-request / 2-minute window.

Failure modes specific to this call:
- **403** — "You cannot update a post that has been published with approval."
- **422** — the post cannot be updated in its current state.

### 3. Delete posts — `deleteMultiplePosts`

```
DELETE /posts
```

Bulk delete by post ids. Unlike update, this one **is** batched — one request
for many posts.

Deletion is destructive and has no undo, no soft-delete state and no
confirmation step in the API. Confirm intent with the user, listing the posts by
`id`, `account_id` and `scheduled_at`, before you send it.

### 4. Poll if you get a job back — `getJobStatus`

```
GET /job_status/{job_id}
```

If the response is 202 with a `job_id` rather than a synchronous body, resolve
it and check `payload.failures[]` before reporting success.

## Rules that will bite you

- **One post per account.** A single bulk create fans out into N Post records.
  "Update the post" almost always means "update N posts".
- **No idempotency key.** Re-issuing a delete you already sent is harmless;
  re-issuing an update is not necessarily.
- Errors are `{"errors": ["message"]}`. There is no machine-readable code, so
  branch on HTTP status plus message text.
- Watch `X-RateLimit-Remaining`; a fan-out edit across many accounts is the
  easiest way to exhaust the window.
