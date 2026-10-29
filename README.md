# EigenDA

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

EigenDA is a secure, high-throughput, decentralized data availability (DA) service built on top of Ethereum using EigenLayer restaking primitives. Developed by Eigen Labs and operated as the flagship product of EigenCloud, EigenDA accepts blobs of rollup data from rollup sequencers, erasure-codes them, distributes the chunks across a network of EigenLayer-restaked operators, and produces aggregate BLS signatures that anchor data availability on Ethereum L1. The service is positioned as a hyperscale DA layer for rollups, advertising 1 GB/s of design throughput and is secured by 4M+ ETH restaked through EigenLayer with validators that include Coinbase, Google, Nethermind, and Puffer. EigenDA is consumed today by rollups and chains including Celo, MegaETH, and Aevo, with integrations available for Arbitrum Orbit, OP Stack, Nitro, and the Sovereign SDK. The protocol exposes a gRPC API surface across a Disperser (blob ingest and status), Relays (blob and chunk retrieval), Retriever (reconstructive retrieval), Churner (operator registration), and Validator/Node endpoints. v2 of the protocol introduces a payment vault and the GetPaymentState RPC on the Disperser, replacing per-account static throughput reservations with a programmatic payments surface. The reference implementation is open source in Go (with a Rust client and SDKs in Rust and TypeScript), licensed Apache-2.0 / MIT, and developed in the open on GitHub.

**Areas:** Blockchain · Data Availability · Ethereum · Restaking · EigenLayer · Rollup · Layer 2 · Web3 · gRPC · Decentralized Infrastructure · KZG Commitments · Cryptography

## EigenDA on APIs.io

Everything profiled for EigenDA is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/eigenda/](https://apis.io/providers/eigenda/)** — or go straight to one of the APIs or properties below.

### APIs (5)

- [EigenDA Disperser API](https://apis.io/apis/eigenda/disperser-api/) — gRPC API exposed by the EigenDA Disperser. Rollups submit raw blobs to DisperseBlob, then poll GetBlobStatus until the blob is confirmed and dispersed…
- [EigenDA Retriever API](https://apis.io/apis/eigenda/retriever-api/) — gRPC service that fans out chunk requests to EigenDA operator nodes and reconstructs the original blob from the retrieved chunks via the RetrieveBlob RPC.
- [EigenDA Relay API](https://apis.io/apis/eigenda/relay-api/) — gRPC service exposing GetBlob, GetChunks, and GetValidatorChunks against blobs stored by the relay layer. Relays sit between rollups and validators and…
- [EigenDA Churner API](https://apis.io/apis/eigenda/churner-api/) — gRPC service that handles operator registration via the Churn RPC. The Churner decides whether new operators may join the EigenDA operator set and which…
- [EigenDA Validator Node API](https://apis.io/apis/eigenda/validator-node-api/) — gRPC API served by EigenDA operator nodes. Validators receive chunk dispersals from the Disperser, sign aggregated attestations, and serve chunk retrieval.…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Security (1)

Authentication, trust centre, and vulnerability disclosure.

- [Eigenda Domain Security](https://apis.io/security/eigenda/eigenda-domain-security/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.eigenda.xyz)
- [Documentation](https://docs.eigencloud.xyz/products/eigenda/api/disperser-v2-API/overview)
- [Blog](https://www.blog.eigenlayer.xyz/intro-to-eigenda-hyperscale-data-availability-for-rollups/)
- [GitHub](https://github.com/Layr-Labs)

## API Evangelist rating

**Kin Score 18.6** — emerging · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 62.5 |
| Contract quality | 6.5 |
| Contract governance | 0.0 |
| Operational transparency | 28.9 |
| Developer ergonomics | 41.7 |
| Access clarity | 0.0 |

**Agent readiness 1.3** — human-only

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | — |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | — |
| Idempotency | — |
| Error Semantics | — |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | — |
| Event Surface Described | — |
| Agent Skills | — |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 5.9** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/eigenda/](https://apis.io/providers/eigenda/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for EigenDA: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/eigenda/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
