# EigenDA (eigenda)

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
