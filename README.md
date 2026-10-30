# Krisp

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

Krisp is a Voice AI platform whose real-time speech-enhancement models run on over 200 million devices, licensed by Discord, Twilio, and VMware among others. Beyond its consumer AI Note Taker, Krisp ships a developer surface: the AI Voice SDK family (VIVA for voice AI agents — voice isolation, turn prediction, interruption prediction, VAD; and RTC for human-to-human calls — accent conversion, bidirectional noise cancellation, background voice cancellation) across Windows, macOS, Linux, Web (JS/WASM), iOS, and Android with C++, Python, Node.js, Go, Rust, and JavaScript bindings, plus framework integrations for LiveKit, WebRTC, and Pipecat. Krisp also runs a self-serve Voice Translation API — a streaming WebSocket speech-to-speech translation service covering 61 languages behind a REST session-token mint — and a programmatic SDK and model download REST API for CI/CD pipelines.

**Areas:** Company · Artificial Intelligence · Voice AI · Speech · Audio · Noise Cancellation · Speech Translation · Real-Time Communication · WebRTC · Conversational AI · SDK · Machine Learning

## Krisp on APIs.io

Everything profiled for Krisp is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/krisp/](https://apis.io/providers/krisp/)** — or go straight to one of the APIs or properties below.

### APIs (2)

- [Krisp SDK Distribution API](https://apis.io/apis/krisp/krisp-sdk-distribution-api/) — Programmatic retrieval of licensed SDK packages and model files.
- [Krisp Voice Translation API](https://apis.io/apis/krisp/krisp-voice-translation-api/) — Session minting and language discovery for the real-time voice translation service.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Krisp Voice Translation WebSocket API](https://apis.io/asyncapis/krisp/krisp-voice-translation-asyncapi/)

#### Event channels (1)

Individual events and webhooks the provider emits.

- [/vt](https://apis.io/channels/krisp/vt/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [krisp](https://apis.io/servers/krisp/krisp/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Krisp Agentic Access](https://apis.io/agentic-access/krisp/krisp-agentic-access/)

#### Collections (2)

Postman and Open Collection request collections.

- [Krisp Developers SDK Distribution API](https://apis.io/collections/krisp/open-krisp-sdk-distribution-api/)
- [Krisp Developers SDK Distribution Voice Translation API](https://apis.io/collections/krisp/open-krisp-voice-translation-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Krisp Developers Overlay](https://apis.io/overlays/krisp/krisp-developers-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Krisp Authentication](https://apis.io/security/krisp/krisp-authentication/)
- [Krisp Domain Security](https://apis.io/security/krisp/krisp-domain-security/)
- [Krisp Trust Center](https://apis.io/security/krisp/krisp-trust-center/)
- [Krisp Vulnerability Disclosure](https://apis.io/security/krisp/krisp-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Krisp Plans Pricing](https://apis.io/plans/krisp/krisp-plans-pricing/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://krisp.ai/)
- [Documentation](https://sdk-docs.krisp.ai/)
- [Getting started](https://sdk-docs.krisp.ai/docs/getting-started.md)
- [API reference](https://sdk-docs.krisp.ai/docs/voice-translation-api.md)
- [Pricing](https://krisp.ai/pricing/)
- [Sign up](https://account.krisp.ai/trial/signup)
- [Support](https://help.krisp.ai)
- [Changelog](https://sdk-docs.krisp.ai/changelog)
- [Blog](https://krisp.ai/blog/)
- [Security](https://krisp.ai/security/)
- [Compliance](https://krisp.ai/security-for-ai-meeting-assistant/)
- [Trust centre](https://trust.krisp.ai/)
- [Terms of service](https://krisp.ai/terms-of-use/)
- [Privacy policy](https://krisp.ai/privacy-policy/)
- [GitHub](https://github.com/krispai)

## API Evangelist rating

**Kin Score 48.5** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 22.4 |
| Contract governance | 18.2 |
| Operational transparency | 21.1 |
| Developer ergonomics | 56.5 |
| Access clarity | 85.5 |

**Agent readiness 31.8** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | na |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | — |
| Event Surface Described | derived (partial credit) |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 32.7** — AI & Biometrics

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/krisp/](https://apis.io/providers/krisp/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Krisp: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/krisp/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
