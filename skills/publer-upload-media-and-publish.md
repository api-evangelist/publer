---
name: publer-upload-media-and-publish
description: Get an image or video into the Publer media library and publish it immediately to connected social accounts, handling both async job hops.
api: Publer API v1
base_url: https://app.publer.com/api/v1
generated: '2026-08-13'
method: generated
source: openapi/_original/publer-openapi.yml, https://publer.com/docs/posting/create-posts/media-handling.md
operations:
  - listAccounts
  - listMedia
  - uploadAMediaFileDirectly
  - uploadMediaFromURL
  - getJobStatus
  - createPost
---

# Upload media and publish it with Publer

Two async hops, not one: media upload can itself return a `job_id`, and the
publish that follows returns another. Do not chain them optimistically.

## Prerequisites

- Scopes: `workspaces`, `accounts`, `media`, `posts`.
- Headers on every call: `Authorization: Bearer-API YOUR_API_KEY` and
  `Publer-Workspace-Id: <workspace id>`.

## Steps

### 1. Reuse before you upload — `listMedia`

```
GET /media?types[]=photo&used[]=false
```

`types[]` and `used[]` are **required** query parameters — a bare `GET /media`
is not a valid call. Optional filters: `page` (0-based), `search`,
`source[]` (`canva`, `vista`, `postnitro`, `contentdrips`, `openai`,
`favorites`, `upload`), and `ids[]`. Passing `ids[]` ignores pagination and every
other filter — use it to fetch known assets directly.

The response is `{"media": [...], "total": n}`. Each item carries `id`, `type`,
`path`, `caption` and `thumbnails[]`.

### 2a. Upload a local file — `uploadAMediaFileDirectly`

```
POST /media
Content-Type: multipart/form-data
```

Returns the media object with its `id`, `path`, `thumbnail`, `width`, `height`
and `validity`. A file over the accepted size returns **413**.

### 2b. Or upload from a URL — `uploadMediaFromURL`

```
POST /media/from-url
```

```json
{ "media": "https://example.com/asset.jpg", "type": "photo", "in_library": true }
```

This path is **asynchronous** — it returns a `job_id`. Poll it exactly like a
post job (step 3) before you reference the media. A `422` here means Publer
could not fetch the remote URL.

Prefer `from-url` for agent use: it needs no multipart file body.

### 3. Resolve the media job — `getJobStatus`

```
GET /job_status/{job_id}
```

Wait for `complete`. Check `payload.failures` even on `complete`.

### 4. Publish with the media attached — `createPost`

```
POST /posts/schedule/publish
```

Attach the media inside the network content block. Photo items use
`{id, type, path, caption, thumbnail}`; video items use `{id, type, path,
caption, thumbnails[]}` where each thumbnail is `{id, small, real}`.

```json
{
  "bulk": {
    "state": "scheduled",
    "posts": [
      {
        "networks": {
          "instagram": {
            "type": "photo",
            "text": "Launch day.",
            "media": [
              { "id": "MEDIA_ID", "type": "photo", "path": "https://cdn.publer.com/...", "caption": null, "thumbnail": "https://cdn.publer.com/..." }
            ]
          }
        },
        "accounts": [ { "id": "ACCOUNT_ID" } ]
      }
    ]
  }
}
```

`POST /posts/schedule/publish` publishes **immediately** — there is no
`scheduled_at` to hold it back. It returns 202 and a second `job_id`.

### 5. Resolve the publish job — `getJobStatus`

Same endpoint, same rule: a `complete` job with a non-empty `payload.failures[]`
is a failed publish for those accounts.

## Rules that will bite you

- Two `job_id`s, two polls. Never pass a media job id where a post job id is
  expected — ids carry no type prefix and both are 24-char hex, so the API will
  not catch the mistake for you.
- Free-trial accounts see placeholder data from `GET /media` unless specific
  query filters are supplied.
- Each network constrains media differently (aspect ratio, duration, count).
  Read `https://publer.com/docs/posting/create-posts/networks.md` before
  fanning one asset across providers.
- Immediate publish is irreversible and there is no idempotency key. Confirm
  intent before calling `createPost`.
