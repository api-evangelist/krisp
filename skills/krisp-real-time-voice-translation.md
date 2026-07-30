---
name: Run a Krisp real-time voice translation session
description: Mint a Krisp session key, open the Voice Translation WebSocket, stream 16 kHz mono audio, and
  consume transcript, translation, and synthesized-speech events correctly.
api: openapi/krisp-developers-openapi.yml
asyncapi: asyncapi/krisp-voice-translation-asyncapi.yml
operations:
- createVoiceTranslationSessionToken
- listVoiceTranslationLanguages
generated: '2026-07-19'
method: generated
source: https://sdk-docs.krisp.ai/docs/voice-translation-api.md
---

# Run a Krisp real-time voice translation session

Krisp's Voice Translation API is a **streaming** API, not a request/response one. A REST call mints a
short-lived credential; all the actual work happens over one WebSocket that carries JSON control frames
and binary audio frames at the same time.

## Prerequisites

- An account API key from the developer dashboard at <https://developers.krisp.ai/>.
- Audio you can deliver as **16 kHz, mono, `pcm_s16le`** (or Opus). Nothing else is confirmed to work.

## Step 1 — Confirm the language pair is supported

Call `listVoiceTranslationLanguages` (`GET /voice-translation/languages`) with header
`Authorization: api-key {API_KEY}`.

Use the returned `language_code` values verbatim. They are **BCP 47 locale codes** (`en-US`, `fr-FR`) —
a bare `en` will be rejected. Krisp documents this list as dynamic, so fetch it at session start rather
than hard-coding it.

## Step 2 — Mint a session key on your backend

Call `createVoiceTranslationSessionToken`
(`GET /v2/sdk/voice-translation/session/token?expiration_ttl=100`) with the same header.

- `expiration_ttl` is in **minutes** — minimum 5, maximum 1440.
- The response carries `session_key`, `expires_at`, `key_id`, `status`, and `type` under `data`.

**Never ship the account API key to a browser or agent runtime.** Mint the session key server-side and
hand out only that. Use a short TTL so a leaked key expires fast.

## Step 3 — Open the socket

Connect to:

```
wss://streaming.krisp.ai/vt?authorization=Api-Key SESSION_KEY
```

The credential rides on the query string because browsers cannot set headers on a WSS handshake.

## Step 4 — Send exactly one config frame, before any audio

```json
{
  "config": {
    "audio": { "format": "pcm_s16le", "sample_rate": 16000, "channels": 1 },
    "source_language": "en-US",
    "target_language": "fr-FR",
    "voice": "female",
    "transcript": { "interim": true, "final": true, "translate": true },
    "metadata": { "reference_id": "your-correlation-id" }
  }
}
```

- `source_language`, `target_language`, and `voice` (`male` | `female`) are required.
- Optional: `vocabulary` (array of domain terms to boost ASR), `translation_dictionary` (array of
  `{source, target}` forced translations), and `features.background_voice_cancellation` to filter other
  speakers server-side.
- Watch this gotcha: if you omit the `transcript` object entirely, `interim` defaults to `true`. If you
  supply a `transcript` object **without** `interim`, it defaults to `false`.
- Set `metadata.reference_id` — it is echoed on every event and is what support will ask for.

## Step 5 — Stream audio in real time

Send raw binary frames. **Pace them in real time**: one chunk per `input_frame_duration` ms. At 16 kHz
mono s16le that is **640 bytes per 20 ms chunk**. Do not blast a whole file at the socket.

## Step 6 — Consume the four event kinds

Distinguish frames by WebSocket opcode: `0x2` (binary) is translated audio, `0x1` (text) is a JSON event.

| Frame | Meaning |
|---|---|
| binary | Synthesized translated speech, same encoding as inbound, 16 kHz mono |
| `{"transcript": {...}}` | Source-language text; `final: false` means interim |
| `{"translate": {...}}` | Target-language text; `final: false` means interim |
| `{"error": {...}}` | `code`, `reason`, `description`, `reference_id` |

Correlate interim events with their final transcript and translation using **`utterance_id`**. Do not
assume ordering across utterances.

## Step 7 — Drain, then close

Allow roughly **2 seconds** after your last audio chunk for the final transcript, translation, and audio
to land, then close. Close is idempotent.

## Error handling

Errors arrive as JSON frames on the socket — **not** as HTTP responses, and **not** as RFC 9457
`application/problem+json`. See `errors/krisp-error-codes.yml`.

| Code | Do this |
|---|---|
| 400 | Fix the config frame — format, language codes, or voice |
| 401 | Session key missing, invalid, or expired — mint a new one |
| 402 | Balance exhausted or subscription expired |
| 429 | Back off; you hit a rate limit or the concurrent-connection cap |
| 500 | Retry with backoff; quote `reference_id` to support |

Krisp publishes no numeric rate limits and no `RateLimit` response headers, so cap concurrency yourself
and treat 429 as the only signal.

## Notes

- There is no idempotency contract and no sandbox host — sessions run against production, metered against
  the free 60-minute allowance.
- Try the models interactively first at <https://lab.krisp.ai/>.
