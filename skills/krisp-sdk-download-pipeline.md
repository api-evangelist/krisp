---
name: Pull Krisp SDK and model artifacts into a CI/CD pipeline
description: Use the Krisp SDK & Model Downloads API to fetch a licensed SDK version package and its model
  files via short-lived URLs, without checking binaries into source control.
api: openapi/krisp-developers-openapi.yml
operations:
- getSdkVersionDownloadUrls
generated: '2026-07-19'
method: generated
source: https://sdk-docs.krisp.ai/docs/programmatic-sdk-model-downloads-api.md
---

# Pull Krisp SDK and model artifacts into a CI/CD pipeline

Krisp's core AI Voice SDKs (VIVA and RTC) are **licensed distribution** — they are not on npm, PyPI,
Maven, or crates.io. This API is how you get them into a build without a human clicking through the
dashboard.

## Prerequisites

- An account API key from <https://developers.krisp.ai/>, stored as a CI secret.
- The **SDK version ID** you want. This is a numeric id listed in the SDK Dashboard — it identifies one
  build of one SDK family for one platform (e.g. VIVA, `windows_x64`, server).

## Step 1 — Request the download URLs

Call `getSdkVersionDownloadUrls` (`GET /v2/sdk/versions/{id}/download-urls`):

```bash
curl --location 'https://api.developers.krisp.ai/v2/sdk/versions/329/download-urls' \
  --header 'Authorization: api-key YOUR-API_KEY'
```

## Step 2 — Read the response

```json
{
  "success": true,
  "data": {
    "expires_in": 300,
    "version": {
      "id": 42, "version": "1.3.4", "display_name": "VIVA",
      "os": "windows_x64", "platform": "server",
      "technologies": ["viva"], "filename": "release.zip",
      "download_url": "s3.amazonaws.com..."
    },
    "models": [
      { "id": 1, "technology": "voice_isolation", "product": "viva",
        "filename": "model.zip", "download_url": "s3.amazonaws.com..." }
    ]
  }
}
```

- `data.version.download_url` — the SDK package itself.
- `data.models[]` — one entry per AI model file the SDK needs. **Fetch all of them.** A VIVA build without
  its model files will not run.
- `data.expires_in` — URL lifetime in **seconds** (e.g. 300 = 5 minutes).

## Step 3 — Consume immediately

Download inside the same pipeline step that requested the URLs. Because they expire in minutes:

- Do **not** write the URLs into a build cache, artifact manifest, or log line.
- Do **not** pass them between jobs that may be queued.
- Re-request rather than retry a stale URL.

Cache the *downloaded files* keyed by SDK version id if you need build speed — never cache the URLs.

## Step 4 — Pin the version id

Treat the SDK version id like a lockfile entry. Bumping it is a deliberate change, and Krisp's release
notes show why: several recent releases carry **breaking model compatibility** (the updated
`krisp-viva-ip-v1.1` Interrupt Prediction model file is not compatible with older SDKs, and VIVA Go
v1.4.0 requires VIVA C/C++ v9.19.0 or above). Check `changelog/krisp-changelog.yml` before you bump.

## Error handling

Same envelope as the rest of the developer surface (`errors/krisp-error-codes.yml`):

| Code | Do this |
|---|---|
| 401 | API key missing, invalid, or expired |
| 429 | Back off — rate limited |
| 500 | Retry with backoff |

A 401 in CI usually means the secret was rotated in the dashboard but not in the pipeline.
