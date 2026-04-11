<div align="center">
  <img src="https://cloak.ag/logo.png" alt="Cloak" width="120" />
  <h3>Private financial infrastructure for enterprises on Solana</h3>
  <p>Accept private transfers, execute shielded swaps, and stay compliant —<br>from your first transaction to your billionth.</p>

  <a href="https://cloak.ag">Website</a> &nbsp;·&nbsp;
  <a href="https://docs.cloak.ag">Docs</a> &nbsp;·&nbsp;
  <a href="https://x.com/cloak_xyz">X / Twitter</a> &nbsp;·&nbsp;
  <a href="https://discord.gg/cloak">Discord</a>
</div>

---

Cloak is a UTXO shielded pool on Solana. Senders, recipients, and amounts are hidden from public explorers. A Groth16 zero-knowledge proof guarantees validity without revealing any plaintext. Viewing keys let you selectively disclose transaction history to auditors or compliance officers — and no one else.

**Private transfers** — Send SOL, USDC, or USDT from your wallet. No trace on explorer.
**B2B payments** — Keep internal and neobank payments off the radar.
**Cross-border** — Move stablecoins globally. Amounts vanish mid-route.
**Treasury** — Govern funds without leaking your next move.
**Payroll** — Pay your team privately. No one sees who got what.
**Compliance** — Audit privately with viewing keys. Share only what regulators need.

## How it works

| Step | What happens |
|------|-------------|
| **Deposit** | SOL, USDC, or USDT enters the shielded pool. A UTXO note is created and encrypted to your viewing key. |
| **ZK Proof** | Your browser generates a Groth16 proof in under 3 seconds. No server involved. |
| **Relay** | The relay validates the proof and submits the signed transaction to Solana. |
| **Withdraw** | Recipient claims privately. A nullifier prevents double-spend without revealing the note. |

Proof generation: ~4.4s total &nbsp;·&nbsp; Groth16 verified on Solana in < 50ms

## SDK

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

→ [Quickstart](https://docs.cloak.ag) &nbsp; [API Reference](https://docs.cloak.ag/sdk)
