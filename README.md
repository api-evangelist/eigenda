# EigenDA (eigenda)

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

EigenDA is a secure, high-throughput, decentralized data availability (DA) service built on Ethereum via EigenLayer restaking primitives. Developed by Eigen Labs and operated as the flagship product of the EigenCloud suite, EigenDA accepts rollup data blobs, erasure-codes them across a restaked operator network, and anchors aggregated BLS attestations to Ethereum L1. Designed for hyperscale rollup DA, EigenDA advertises 1 GB/s of throughput, is secured by 4M+ ETH of restaked stake, and is integrated by rollups including Celo, MegaETH, and Aevo.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/eigenda/refs/heads/main/apis.yml)

## Tags

 - Blockchain, Data Availability, Ethereum, Restaking, EigenLayer, Rollups, Layer 2, Web3, gRPC, Decentralized Infrastructure, KZG Commitments, Cryptography

## Timestamps

- **Created:** 2026-05-24
- **Modified:** 2026-05-24

## APIs

The canonical EigenDA API surface is a set of gRPC services defined in protobuf under [`Layr-Labs/eigenda/api/proto/`](https://github.com/Layr-Labs/eigenda/tree/master/api/proto). v1 services remain in place while v2 (under `disperser/v2`, `retriever/v2`, `validator/`) ships as a fundamental redesign of the protocol — adding a payment vault, validator signing-rate telemetry, and a path toward permissionless dispersers and data availability sampling.

### EigenDA Disperser API
The on-ramp for rollups. `DisperseBlob` accepts a raw blob; `GetBlobStatus` returns the dispersal lifecycle (queued, encoded, dispersing, confirmed, finalized). v2 adds `GetBlobCommitment`, `GetPaymentState` (payment vault accounting), and `GetValidatorSigningRate`.

- [Protobuf — v1](https://github.com/Layr-Labs/eigenda/blob/master/api/proto/disperser/disperser.proto)
- [Protobuf — v2](https://github.com/Layr-Labs/eigenda/blob/master/api/proto/disperser/v2/disperser_v2.proto)
- [Docs — Disperser v2 API overview](https://docs.eigencloud.xyz/products/eigenda/api/disperser-v2-API/overview)

### EigenDA Retriever API
`RetrieveBlob` fans chunk-retrieval requests out to EigenDA operator nodes and reconstructs the original blob from the returned chunks.

- [Protobuf](https://github.com/Layr-Labs/eigenda/blob/master/api/proto/retriever/retriever.proto)

### EigenDA Relay API
Read path for blobs and chunks: `GetBlob`, `GetChunks`, and `GetValidatorChunks` against the relay layer that sits between rollups and validators.

- [Protobuf](https://github.com/Layr-Labs/eigenda/blob/master/api/proto/relay/relay.proto)

### EigenDA Churner API
Operator registration and eviction. `Churn` decides which operators may join the EigenDA quorum and which existing operators are evicted when registered stake exceeds protocol capacity.

- [Protobuf](https://github.com/Layr-Labs/eigenda/blob/master/api/proto/churner/churner.proto)

### EigenDA Validator Node API
gRPC API served by EigenDA operator nodes — chunk receipt, attestation signing, and chunk retrieval. v2 introduces `node_v2.proto` and a separate `signing_rate.proto` for measuring per-validator availability.

- [Protobuf — Node v2](https://github.com/Layr-Labs/eigenda/blob/master/api/proto/validator/node_v2.proto)
- [Protobuf — Signing Rate](https://github.com/Layr-Labs/eigenda/blob/master/api/proto/validator/signing_rate.proto)

## Common Properties

- [Website — eigenda.xyz](https://www.eigenda.xyz)
- [Website — EigenCloud DA](https://eigencloud.xyz/da)
- [Portal — EigenDA docs](https://docs.eigencloud.xyz/products/eigenda/overview)
- [Documentation — Protocol Spec (mdBook)](https://layr-labs.github.io/eigenda/)
- [Blog — Intro to EigenDA](https://www.blog.eigenlayer.xyz/intro-to-eigenda-hyperscale-data-availability-for-rollups/)
- [BlobExplorer](https://blobs.eigenda.xyz/)
- [GitHubOrganization — Layr-Labs](https://github.com/Layr-Labs)
- [SourceCode — eigenda](https://github.com/Layr-Labs/eigenda)
- [SDK — EigenDA TypeScript SDK (beta)](https://github.com/Layr-Labs/eigenda-sdk)
- [SDK — EigenDA Rust Tooling](https://github.com/Layr-Labs/eigenda-rs)
- [SDK — EigenDA Rust Client](https://github.com/Layr-Labs/eigenda-client-rs)
- [SDK — EigenLayer Go SDK](https://github.com/Layr-Labs/eigensdk-go)
- [SDK — EigenLayer Rust SDK](https://github.com/Layr-Labs/eigensdk-rs)
- [Tool — EigenDA Proxy](https://github.com/Layr-Labs/eigenda-proxy)
- [Tool — EigenDA Orbit SDK](https://github.com/Layr-Labs/eigenda-orbit-sdk)
- [Tool — EigenDA Orbit Setup Script](https://github.com/Layr-Labs/eigenda-orbit-setup-script)
- [Tool — Arbitrum Nitro for EigenDA](https://github.com/Layr-Labs/nitro)
- [Tool — Operator Setup Guide](https://github.com/Layr-Labs/eigenda-operator-setup)
- [Tool — Hokulea (OP Stack fault proofs)](https://github.com/Layr-Labs/hokulea)
- [CodeExamples — eigenda-examples](https://github.com/Layr-Labs/eigenda-examples)
- [Forum — EigenLayer forum (EigenDA Research)](https://forum.eigenlayer.xyz/c/eigenda-research/36)
- [Twitter — @eigen_da](https://x.com/eigen_da)
- [Twitter — @eigenlayer](https://x.com/eigenlayer)
- [Support — eigenda-support@eigenlabs.org](mailto:eigenda-support@eigenlabs.org)
- [Whitepaper](https://github.com/Layr-Labs/whitepaper)

## Integrations

- **Celo** — L2 using EigenDA for data availability
- **MegaETH** — real-time Ethereum L2 built on EigenDA
- **Aevo** — derivatives L2 using EigenDA
- **Arbitrum Orbit** — via [`eigenda-orbit-sdk`](https://github.com/Layr-Labs/eigenda-orbit-sdk) and forked [`nitro`](https://github.com/Layr-Labs/nitro) / [`nitro-contracts`](https://github.com/Layr-Labs/nitro-contracts)
- **OP Stack** — via [Hokulea](https://github.com/Layr-Labs/hokulea) fault-proof integration
- **Sovereign SDK** — first-party DA adapter in the EigenDA `rust/` tree
- **zkSync** — proof-of-concept integration in [`zksync-eigenda-m1`](https://github.com/Layr-Labs/zksync-eigenda-m1)

## Notes

- The canonical API contract is the protobuf schema in [`Layr-Labs/eigenda/api/proto/`](https://github.com/Layr-Labs/eigenda/tree/master/api/proto). EigenDA does not publish an OpenAPI/REST surface — clients integrate over gRPC using the language SDKs above or via the [`eigenda-proxy`](https://github.com/Layr-Labs/eigenda-proxy) which adapts EigenDA to standard rollup DA-server interfaces.
- v2 is currently marked experimental in the protocol README and represents the forward path for the protocol (payment vault, permissionless dispersers, DAS).
- The reference implementation is open source; node operators self-host using the [`eigenda-operator-setup`](https://github.com/Layr-Labs/eigenda-operator-setup) guide.

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
