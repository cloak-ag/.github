<div align="center">
  <img src="https://cloak.ag/logo.png" alt="Cloak" width="120" />
  <h3>Private financial infrastructure for enterprises.</h3>
  <p>Accept private transfers, execute shielded swaps, and stay compliant —<br>from your first transaction to your billionth.</p>

  <a href="https://cloak.ag">Website</a> &nbsp;·&nbsp;
  <a href="https://docs.cloak.ag">Docs</a> &nbsp;·&nbsp;
  <a href="https://x.com/cloak_ag">X / Twitter</a> &nbsp;·&nbsp;
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
| **01 Deposit** | SOL, USDC or USDT enters that token's shielded pool. A UTXO note is created and encrypted to your viewing key. |
| **02 ZK Proof** | Your browser generates a Groth16 proof in under 3 seconds. No server involved. |
| **03 Relay** | A relayer submits your transaction, so your wallet never signs the on-chain spend. The program verifies the proof on-chain. |
| **04 Withdraw** | Recipient claims privately. A nullifier prevents double-spending without revealing the note. |

Sender and recipient addresses stay private · Amounts hidden from on-chain observers · Groth16 proof verified on Solana in < 50ms

## Compliance

Private by default. Auditable when required.

Viewing keys let you disclose your transaction history to any auditor or compliance officer — without revealing anything to the public. Generate a viewing key from your wallet. Share it with your counterparty. They can verify every transaction, and nothing else.

## Security & verification

Audited, ceremony-keyed, and checkable by anyone.

- **Audited program.** The live shield-pool program is built from independently audited source. Program ID `zh1eLd6rSphLejbFfJEneUwzHRfMKxgzrgkfwA6qRkW` — unchanged since launch.
- **Ceremony-keyed verifying key.** Proofs are checked against a verifying key from a multi-party trusted setup (`cloak-transaction-0.2.0`: 6 contributors plus a public final beacon). vkey sha256 `d65073d44064ed3be10d79e52d60a06d6be6d6c01afcd5ce52cdfcfc97c5585d` (`transaction.vkey.bin`), `deb40e7b94eae17db2975d23dcf26c26db2a36a4f02d14a25830dee3e88fb93c` (`transaction.vkey.json`).
- **Sealed artifact, multisig upgrades.** On-chain bytecode sha256 `d0f68613a08d7e0913aea67d95f04598bc070911a0e84fedd43cc6bfa18e6cf6` (239,032 bytes). Upgrades require the Squads multisig `F6HWeX5i2KjYQag6wCtxzQXeGewv6vXZihZR3EWdRL7s` (3-of-4, 1-hour time lock).

Verify it yourself:

```sh
# 1. Hash the deployed program
solana program dump -u m zh1eLd6rSphLejbFfJEneUwzHRfMKxgzrgkfwA6qRkW /tmp/cloak.so \
  && head -c 239032 /tmp/cloak.so | shasum -a 256
# expect d0f68613a08d7e0913aea67d95f04598bc070911a0e84fedd43cc6bfa18e6cf6

# 2. Hash the public proving artifacts
B=https://storage.googleapis.com/cloak-circuits/circuits/0.2.0
curl -sL $B/transaction_final.zkey          | shasum -a 256
# expect 9da7db8cb1370fc497d36a0365f1f107ab0b0c13ca66fa9f0287e5f96ee68d25
curl -sL $B/transaction_js/transaction.wasm | shasum -a 256
# expect 02ec02e954ae3932827ad9de51afa597ca95569aa97fec8410879c937a58aa2b

# 3. Compare with the hashes above. The SDK performs the same check before every proof.
```

## SDK

Shielded flows in your product. We own the hard parts.

```ts
import {
  CLOAK_PROGRAM_ID,
  NATIVE_SOL_MINT,
  createUtxo,
  createZeroUtxo,
  generateUtxoKeypair,
  transact,
} from "@cloak.dev/sdk";

const owner = await generateUtxoKeypair();

await transact(
  {
    inputUtxos: [await createZeroUtxo(NATIVE_SOL_MINT)],
    outputUtxos: [await createUtxo(amount, owner, NATIVE_SOL_MINT)],
    externalAmount: amount,
    depositor: wallet.publicKey,
  },
  {
    connection,
    programId: CLOAK_PROGRAM_ID,
    walletPublicKey: wallet.publicKey,
    signTransaction: wallet.signTransaction,
    signMessage: wallet.signMessage,
  },
);
```

→ [Quickstart](https://docs.cloak.ag/quickstart) &nbsp; [API Reference](https://docs.cloak.ag/sdk/api-reference)
