# Cloak

**Private transactions on Solana.**

Cloak is a privacy protocol built on Solana, enabling confidential transfers and shielded interactions through zero-knowledge proofs. Transact without exposing your on-chain footprint.

---

## What We're Building

- **Shield Pool** — deposit and withdraw SPL tokens privately using ZK proofs (Groth16)
- **Stealth Addresses** — one-time addresses that break the link between sender and recipient
- **Protocol SDK** — TypeScript and Rust SDKs for integrating Cloak into any Solana app
- **Relay Service** — off-chain relay that handles proof submission and commitment syncing
- **ZK Circuits** — Groth16 verifier circuits deployed on Solana with altbn syscalls

## Repositories

| Repo | Description |
|------|-------------|
| [`sdk`](https://github.com/cloak-ag/sdk) | TypeScript SDK for the Cloak Protocol |
| [`rustsdk`](https://github.com/cloak-ag/rustsdk) | Rust SDK for the Cloak Protocol |
| [`programs`](https://github.com/cloak-ag/programs) | On-chain Solana programs (Shield Pool, etc.) |
| [`services`](https://github.com/cloak-ag/services) | Relay and backend services |
| [`docs`](https://github.com/cloak-ag/docs) | Protocol documentation |
| [`groth16-solana`](https://github.com/cloak-ag/groth16-solana) | Groth16 verifier with Solana altbn syscalls |
| [`surfpool`](https://github.com/cloak-ag/surfpool) | Where developers start their Solana journey |

## Links

- [Documentation](https://github.com/cloak-ag/docs)
- [Surfpool — Start your Solana journey](https://github.com/cloak-ag/surfpool)
