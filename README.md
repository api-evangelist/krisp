# Krisp

Krisp is a Voice AI platform whose real-time speech-enhancement models run on over 200 million devices,
licensed by Discord, Twilio, and VMware among others. Beyond its consumer AI Note Taker, Krisp ships a
developer surface: the AI Voice SDK family (VIVA for voice AI agents; RTC for human-to-human calls) across
Windows, macOS, Linux, Web (JS/WASM), iOS, and Android with C++, Python, Node.js, Go, Rust, and JavaScript
bindings, plus a self-serve Voice Translation API and a programmatic SDK/model download API.

- Website — https://krisp.ai/
- Developer portal — https://krisp.ai/developers/
- SDK documentation — https://sdk-docs.krisp.ai/
- Developer dashboard — https://developers.krisp.ai/
- Playground — https://lab.krisp.ai/
- GitHub — https://github.com/krispai

Backed by: sierra-ventures

## APIs

| API | Base URL | Shape |
|---|---|---|
| Voice Translation | `https://api.developers.krisp.ai` + `wss://streaming.krisp.ai/vt` | REST session mint + streaming WebSocket |
| SDK & Model Downloads | `https://api.developers.krisp.ai` | REST |

## Artifacts

| Dir | Artifact | Method |
|---|---|---|
| `llms/` | `/llms.txt` from both sdk-docs.krisp.ai and krisp.ai, verbatim | searched |
| `well-known/` | `/.well-known/` index + RFC 9116 security.txt, verbatim | searched |
| `packages/` | 2 first-party npm packages + licensed distribution channel | searched |
| `changelog/` | 5 recent SDK releases from sdk-docs.krisp.ai/changelog | searched |
| `authentication/` | two-stage API key → session key model | searched |
| `conventions/` | streaming protocol, versioning, tracing, error envelope | searched |
| `errors/` | 5-code error registry from the Voice Translation reference | searched |
| `lifecycle/` | versioning, SLA, known limitations | searched |
| `conformance/` | standards posture + published compliance claims | searched |
| `sandbox/` | Krisp Lab playground + free tier | searched |
| `security/` | domain security probe, HackerOne VDP, Vanta trust center | probed / searched |
| `openapi/` | 3 REST operations transcribed from prose docs — **not provider-published** | derived |
| `asyncapi/` | Voice Translation WebSocket protocol — **not provider-published** | derived |
| `data-model/` | 9-entity graph | derived |
| `mcp/` | candidate tool surface — Krisp ships **no** official MCP server | derived |
| `agentic-access/` | `x-agentic-access` recommendations for 3 operations | generated |
| `overlays/` | API Evangelist annotations over the derived OpenAPI | generated |
| `skills/` | 2 agent skills grounded in real operationIds | generated |

### Provenance caveat

Krisp publishes **no** OpenAPI and **no** AsyncAPI document. `openapi/krisp-developers-openapi.yml` and
`asyncapi/krisp-voice-translation-asyncapi.yml` are faithful transcriptions by the API Evangelist
enrichment pipeline of the endpoints, parameters, and message shapes Krisp documents in prose at
sdk-docs.krisp.ai. Paths, fields, and examples are verbatim; operationIds and schema names were assigned
by the pipeline. Both files carry `x-apievangelist-provenance` recording this.

### Deliberately absent

No public status page (status.krisp.ai is Cloudflare Access-gated), no deprecation policy, no OAuth scope
surface, no first-party CLI, no webhooks, no published rate-limit values, and no idempotency contract —
so no `StatusPage`, `Deprecation`, `OAuthScopes`, `CLI`, `Webhooks`, `RateLimits`, or `Idempotency`
pointer is emitted.
