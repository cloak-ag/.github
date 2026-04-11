<div align="center">
  <img src="https://cloak.ag/logo.png" alt="Cloak" width="120" />
  <h3>Private financial infrastructure for enterprises.</h3>
  <p>Accept private transfers, execute shielded swaps, and stay compliant —<br>from your first transaction to your billionth.</p>

  <a href="https://cloak.ag">Website</a> &nbsp;·&nbsp;
  <a href="https://docs.cloak.ag">Docs</a> &nbsp;·&nbsp;
  <a href="https://x.com/cloak_xyz">X / Twitter</a> &nbsp;·&nbsp;
  <a href="https://discord.gg/cloak">Discord</a>
</div>

---

**Flexible privacy for every use case.** Shield transactions from your wallet, move stablecoins across borders undetected, and govern treasuries without telegraphing your next move.

| Use case | What it does |
|---|---|
| **Private transfers** | Send from your wallet. No trace on explorer. |
| **B2B payments** | Keep internal and neobank payments off the radar. |
| **Cross-border** | Move USDC, USDT and SOL globally. Amounts vanish mid-route. |
| **Treasury** | Govern funds without leaking your next move. |
| **Payroll** | Pay your team privately. No one sees who got what. |
| **Compliance** | Audit privately. Share only what regulators need. |

## How it works

Zero-knowledge, end to end.

| Step | What happens |
|---|---|
| **01 Deposit** | SOL enters the shielded pool. A UTXO note is created and encrypted to your viewing key. |
| **02 ZK Proof** | Your browser generates a Groth16 proof in under 3 seconds. No server involved. |
| **03 Relay** | The relay validates the proof and submits the signed transaction to Solana. |
| **04 Withdraw** | Recipient claims privately. A nullifier prevents double-spending without revealing the note. |

Sender and recipient addresses stay private · Amounts hidden from on-chain observers · Groth16 proof verified on Solana in < 50ms

## Compliance

Private by default. Auditable when required.

Viewing keys let you disclose your transaction history to any auditor or compliance officer — without revealing anything to the public. Generate a viewing key from your wallet. Share it with your counterparty. They can verify every transaction, and nothing else.

## SDK

Shielded flows in your product. We own the hard parts.

```ts
import { transact, createZeroUtxo, createUtxo, NATIVE_SOL_MINT } from "@cloak.ag/sdk";

await transact(
  {
    inputUtxos: [await createZeroUtxo(NATIVE_SOL_MINT)],
    outputUtxos: [await createUtxo(amount, owner, NATIVE_SOL_MINT)],
    externalAmount: amount,
    depositor: wallet.publicKey,
  },
  { connection, wallet, relayUrl, programId },
);
```

→ [Quickstart](https://docs.cloak.ag/quickstart) &nbsp; [API Reference](https://docs.cloak.ag/api)
