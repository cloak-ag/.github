# Cloak

**Private financial infrastructure for enterprises on Solana.**

Private transfers, shielded swaps, and compliant treasury operations — powered by zero-knowledge proofs. Privacy by default, auditable when required.

---

## What is Cloak?

Cloak is a UTXO shielded pool on Solana. Senders, recipients, and amounts are hidden from public explorers. A Groth16 zero-knowledge proof guarantees validity without revealing any plaintext. Viewing keys let you disclose your full transaction history to auditors or compliance officers — and no one else.

- **Private transfers** — Send SOL, USDC, or USDT from your wallet. No trace on explorer.
- **B2B payments** — Keep internal and neobank payments off the radar.
- **Cross-border** — Move stablecoins globally. Amounts vanish mid-route.
- **Treasury** — Govern funds without leaking your next move.
- **Payroll** — Pay your team privately. No one sees who got what.
- **Compliance** — Audit privately. Share only what regulators need.

## How it works

- **Deposit** — SOL, USDC, or USDT enters the shielded pool. A UTXO note is created and encrypted to your viewing key.
- **ZK Proof** — Your browser generates a Groth16 proof in under 3 seconds. No server involved.
- **Relay** — The relay validates the proof and submits the signed transaction to Solana.
- **Withdraw** — Recipient claims privately. A nullifier prevents double-spending without revealing the note.

Proof generation: ~4.4s total · Groth16 verified on Solana in < 50ms

## SDK

Integrate Cloak privacy into any dApp in minutes with `@cloak.dev/sdk`.

```ts
import { transact, createZeroUtxo, createUtxo, NATIVE_SOL_MINT } from "@cloak.dev/sdk";

await transact(
  {
    inputUtxos: [await createZeroUtxo(NATIVE_SOL_MINT)],
    outputUtxos: [await createUtxo(amount, owner, NATIVE_SOL_MINT)],
    externalAmount: amount,
    depositor: wallet.publicKey,
  },
  { connection, wallet, relayUrl, programId }
);
```

## Repositories

| Repo | Description |
|------|-------------|
| [`sdk`](https://github.com/cloak-ag/sdk) | TypeScript SDK — the primary integration surface |
| [`rustsdk`](https://github.com/cloak-ag/rustsdk) | Rust SDK |
| [`programs`](https://github.com/cloak-ag/programs) | On-chain Solana programs (Shield Pool) |
| [`services`](https://github.com/cloak-ag/services) | Relay API and commitment sync |
| [`packages`](https://github.com/cloak-ag/packages) | Circuit pipeline and ZK build tooling |
| [`docs`](https://github.com/cloak-ag/docs) | Documentation site |
| [`monorepo`](https://github.com/cloak-ag/monorepo) | Monorepo workspace |
| [`groth16-solana`](https://github.com/cloak-ag/groth16-solana) | Groth16 verifier with Solana altbn syscalls |
| [`surfpool`](https://github.com/cloak-ag/surfpool) | Where developers start their Solana journey |

## Links

- [Website](https://cloak.ag)
- [Documentation](https://docs.cloak.ag)
- [X / Twitter](https://x.com/cloak_xyz)
- [Discord](https://discord.gg/cloak)
