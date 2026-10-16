<p align="center">
  <img src="assets/logo.png" alt="Oath Network" width="96">
</p>

<h1 align="center">Oath Network</h1>

<p align="center">
  <b>Ask in private. Get every answer under oath.</b><br>
  Private AI you can check. The machine that answers cannot read your prompt, every answer comes back with a signed receipt, and witnesses who lie about a receipt lose their stake.
</p>

<p align="center">
  <a href="https://oathnetwork.tech">Website</a> ·
  <a href="https://app.oathnetwork.tech">App</a> ·
  <a href="https://oathnetwork.tech/docs">Docs</a> ·
  <a href="https://x.com/OathNetworkRH">X</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/chain-Robinhood%20Chain%204663-8b5cf6?style=flat-square" alt="Robinhood Chain">
  <img src="https://img.shields.io/badge/%24OATH-live-8b5cf6?style=flat-square" alt="$OATH live">
  <img src="https://img.shields.io/badge/app-sandbox-8b5cf6?style=flat-square" alt="Sandbox">
  <img src="https://img.shields.io/badge/launch%20buy-burned-8b5cf6?style=flat-square" alt="Launch buy burned">
</p>

![Oath Network landing page](assets/banner.png)

---

## About

People now type their most sensitive material into AI: trading plans, wallet lists, contracts before launch, legal drafts, health questions. The service on the other side can read all of it, and its promise not to look is a policy page, not a mechanism.

Oath Network treats privacy that cannot be checked as marketing. So the product is the check itself. This is how it is built to work:

1. Your browser checks the sealed machine before it sends anything.
2. Your prompt is encrypted to a key that exists only inside that machine.
3. The machine answers inside a hardware enclave and signs the answer with its own key.
4. You get the answer and a receipt.
5. Three witnesses, drawn at random, check that receipt. Two of three must agree.
6. The receipt becomes public record on Robinhood Chain. The prompt never does.

The receipt is public. The prompt never is.

> **Today the app runs as a sandbox.** OATH AI answers for real and every answer is signed and witnessed, but the machine is an ordinary server, not sealed hardware yet, and credits and stake are test numbers. Type nothing private until the sealed machine is live. See [Status](#status).

![The sealed lane](assets/art-sealed.jpg)

**Chain:** Robinhood Chain (EVM, chain id 4663) · **Ticker:** $OATH · **Contract:** `0xDE97752448FD7d958CAA7749DAE91A6FE14a3133`

---

## Features

### Sealed chat with OATH AI
- Ask OATH AI, the assistant of Oath Network. Five free answers a day. No wallet, no signup.
- The browser checks the machine's proof against the public signer registry before it encrypts the prompt.
- The prompt is encrypted end to end (X25519, HKDF-SHA256, XChaCha20-Poly1305). The relay in the middle only ever sees ciphertext.
- No database table holds a prompt or an answer. There is nothing to leak, because it was never written.

![Sealed chat in the app](assets/app-chat.png)

### Token check
Paste any token address from Robinhood Chain into the chat and ask about it.

- **Your browser reads the token straight from the chain:** supply, owner, whether it is upgradeable, mint, pause, blacklist or fee-setting functions found in its code, its stage on the launchpad, the creator fee and who receives it, and how much of the supply the deployer, the curve and the burn address hold.
- **Sell test:** for a coin on the launchpad's curve, the browser simulates a small buy and an immediate sell of everything received. It shows whether selling works, whether the token takes a cut on transfer, and how much ETH comes back. Nothing is sent, signed or paid.
- **Private by design:** the facts are sealed together with your question, so the relay never sees which token you checked. The receipt covers the facts the answer was given.
- OATH AI explains the risks from those facts, says what chain data cannot show, and never predicts a price.

![Token check in the app](assets/app-token-check.png)

### Signed receipts
Every answer comes with a receipt on its own public page.

| In the receipt (public) | Never in the receipt |
|---|---|
| Receipt id and time | Your prompt |
| Model name | The answer text |
| Code fingerprint of the sealed machine | Who you are |
| Hash of the hardware attestation | |
| Hash of the answer, salted hash of the prompt | |
| The machine's signing address and signature | |
| Three witness signatures, once the round closes | |

Anyone can press **Check it yourself** on a receipt page and re-run the check in their own browser. A receipt can be shared without sharing the question.

<table>
  <tr>
    <td><img src="assets/app-receipt.png" alt="A receipt page"></td>
    <td><img src="assets/app-receipt-fields.png" alt="The eight public fields of a receipt"></td>
  </tr>
  <tr>
    <td align="center"><sub>A receipt page: answered under oath, 3 of 3 witnesses agreed</sub></td>
    <td align="center"><sub>Eight fields and no words. Check it yourself.</sub></td>
  </tr>
</table>

![Every answer leaves a receipt](assets/app-receipts.png)

### Witness network
Today the witnesses are house witnesses on test stake. Staking real $OATH opens once the bond contract is deployed.

![Three witnesses](assets/art-witnesses.jpg)

- Witnesses run in a browser tab. Each one recovers the signer, checks the code fingerprint against the registry, checks the attestation hash, and signs what it found.
- Witnesses are drawn from a public seed, so the operator cannot pick them, and a witness is never told who the other two are.
- **Planted forgeries:** one receipt in every twenty is a forgery planted on purpose. A witness that signs one has proven, with its own signature, that it did not check.
- **Cuts:** 10%, then 50%, then 100% of the stake. Half goes to the witnesses who checked correctly, half is burned.
- Witnesses are paid every hour for correct checks, with no fixed rate. Nothing is paid for simply holding.
- Public ranks based on clean checks in a row: Sworn, Steady, Trusted, Unbroken. A rank changes nothing about pay or the draw. It is a record.

<table>
  <tr>
    <td><img src="assets/app-witness.png" alt="The witness tab in the app"></td>
    <td><img src="assets/site-witness.png" alt="How a witness works"></td>
  </tr>
  <tr>
    <td align="center"><sub>Keep a tab open. Tell the truth.</sub></td>
    <td align="center"><sub>Stake the bond, leave the tab open, get paid by the hour</sub></td>
  </tr>
</table>

Try the whole round in your browser on the landing page: a key signs a receipt, three witnesses recover the signer, and a forged receipt fails the check.

![The bench on the landing page](assets/site-bench.png)

### The Perjury board
A public page listing every witness caught signing a forgery: the address, the forged receipt and what was wrong with it, the witness's own signature, the size of the cut and where it went. Each case has a button that re-checks the evidence in your browser.

<table>
  <tr>
    <td><img src="assets/site-perjury.png" alt="One receipt in twenty is a planted forgery"></td>
    <td><img src="assets/app-perjury.png" alt="The Perjury board in the app"></td>
  </tr>
  <tr>
    <td align="center"><sub>One receipt in twenty is a forgery we planted</sub></td>
    <td align="center"><sub>The board: every cut, with the evidence</sub></td>
  </tr>
</table>

### A vault with no keys
Every fee, from trading and from usage, is meant to land in one vault with a fixed split and no owner, no pause, no upgrade and no withdraw path. The vault is deployed: [`0x577401fCea5d2Dc40dd99f13960985cf4B6FC988`](https://robin.etherscan.io/address/0x577401fCea5d2Dc40dd99f13960985cf4B6FC988).

> **Today the token's 2% creator fee goes to the team wallet** [`0xAf2819e31fC853e8AB3909267C7707f27Fc4e833`](https://robin.etherscan.io/address/0xAf2819e31fC853e8AB3909267C7707f27Fc4e833). It will be moved to the vault, and this page will say so when it is.

| Share | Goes to |
|---|---|
| 40% | Witness pay |
| 30% | Buyback and burn of $OATH |
| 20% | Upkeep |
| 10% | Breach pot |

![Every fee goes into one vault](assets/site-vault.png)

### Breach pot
Each sealed machine creates a random secret at start-up and publishes only its hash. Anyone who submits the secret itself is paid the pot by the contract. The only way to have it is to have read the machine's memory. The pot is a price tag on the hardware promise.

![The vault](assets/art-vault.jpg)

### For developers and agents
- Create an API key from the app with a wallet signature.
- Call the sealed lane over a standard chat completions API.
- Verify every answer in your own code: recover the signer and compare it with the registry.
- Public endpoints for receipts, counters and the signer registry, no key needed.

<table>
  <tr>
    <td><img src="assets/app-keys.png" alt="API keys and the first call"></td>
    <td><img src="assets/app-credits.png" alt="Credits"></td>
  </tr>
  <tr>
    <td align="center"><sub>The same sealed lane, from your own code</sub></td>
    <td align="center"><sub>Pay for what you use, nothing more</sub></td>
  </tr>
</table>

### $OATH
$OATH is live on Robinhood Chain: [`0xDE97752448FD7d958CAA7749DAE91A6FE14a3133`](https://robin.etherscan.io/token/0xDE97752448FD7d958CAA7749DAE91A6FE14a3133). It launched on the Robinhood Chain launchpad and trades on its bonding curve, paired with ETH.

It is meant to be the stake a witness puts at risk, not a ticket. The tiers below open once the sealed chat and the bond contract are live; holding $OATH unlocks nothing yet.

| Tier | Requirement | Opens |
|---|---|---|
| Open | No wallet | 5 sealed answers a day, every receipt, every check |
| Holder | Hold 25,000 $OATH | 20 sealed answers a day, platform fee 10% instead of 20% |
| Witness | Stake 100,000 $OATH | Run a witness tab, paid per correct check, stake can be cut. 7-day exit |

What the token can never do: buy a different answer, buy a ruling, skip an audit, pay for sitting in a wallet, or vote. More stake does not mean being drawn more often.

![Tiers and what the token may never do](assets/site-tiers.png)

**Fair launch.** 1,000,000,000 supply, fixed, no mint, no presale, no team allocation. The launch transaction bought 29.4M $OATH, and all of it was sent to the burn address. The launch wallet holds none.

### Smart contracts
Seven Solidity contracts for Robinhood Chain, none with an owner over money. Six are deployed:

| Contract | Role | Address |
|---|---|---|
| `SignerRegistry` | Which machine keys and code fingerprints count. Held by a cold operator wallet | [`0x1EBB…7A82`](https://robin.etherscan.io/address/0x1EBBcfa909E4b1690b815FD367710A6257eF7A82) |
| `ReceiptLog` | One root per batch of witnessed receipts | [`0xc60d…6275`](https://robin.etherscan.io/address/0xc60df65e8efc52F76ada607C2a497D9Dd4B46275) |
| `BreachPot` | Pays whoever reveals a sealed machine's start-up secret | [`0x1254…6845`](https://robin.etherscan.io/address/0x12540a5C6b67679dA117Dc2194a1151C64426845) |
| `WitnessPay` | Hourly pay epochs, published with a public delay | [`0x618E…825e`](https://robin.etherscan.io/address/0x618E5451075c5d6bcCf2f64266631A135Ac0825e) |
| `OathVault` | Splits every fee 40/30/20/10 once the fee reaches it | [`0x5774…C988`](https://robin.etherscan.io/address/0x577401fCea5d2Dc40dd99f13960985cf4B6FC988) |
| `OathBurner` | Buys $OATH back and burns it | [`0xF39c…56f3`](https://robin.etherscan.io/address/0xF39cD7Bf125b5D8Dd6F46C75f74715641f3056f3) |
| `WitnessBond` | Stake, the 7-day exit, and cuts proven by a signed forgery | Not deployed yet |

### On every screen
The app and the site are built for a phone first.

![Oath Network on a phone](assets/mobile.png)

### Docs
Everything above, in full, at [oathnetwork.tech/docs](https://oathnetwork.tech/docs).

![The docs](assets/site-docs.png)

---

## What "sealed" means, and what it does not

**It means** the answer is produced inside a hardware enclave whose memory the machine's operator cannot read, the enclave proves which code it runs before it is given anything, and every answer is signed by a key born inside it.

**It does not mean** "cannot be broken". Enclaves rest on the chip maker, and published research has broken them with physical access to the server. We say hardware-attested, never more. A signed answer proves where it came from, not that it is true. And paying from a wallet is public on chain.

**The sealed machine is written, not running.** Its code runs the machine inside a confidential VM with no shell, where a signed attestation names the exact container image, and the browser checks that attestation before it seals anything. Until it runs, the app says "Sandbox" on every screen.

**v1 is not decentralised.** The coordinator is ours. We can delay or refuse an answer and choose which models are offered. We cannot pick the witnesses, cut a stake by decree, or move the vault's fees.

---

## Status

| Part | State |
|---|---|
| Website and docs | Live at [oathnetwork.tech](https://oathnetwork.tech) |
| App | Live at [app.oathnetwork.tech](https://app.oathnetwork.tech) as a **sandbox**: OATH AI answers for real, every answer is signed and checked by 3 witnesses, token check with sell test works. Credits and stake are test numbers, the witnesses are house witnesses, and the machine is not sealed hardware yet. |
| Sealed machine and its browser check | Written and tested, not running yet |
| $OATH | **Live** at `0xDE97752448FD7d958CAA7749DAE91A6FE14a3133`, on the launchpad's bonding curve |
| Creator fee | 2%, goes to the team wallet for now, to be moved to the vault |
| Contracts | Six deployed (see above). The witness bond is not deployed yet |
| Holder tier, staking, witness pay | Not live yet |

Official channels are X, GitHub and the docs. Nothing else is ours. The only $OATH contract is `0xDE97752448FD7d958CAA7749DAE91A6FE14a3133`.

---

## Disclaimer

Oath Network is experimental software. Nothing here is financial advice or a promise of returns. $OATH is meant to be the stake that lets a witness work, and a stake can be cut. The token check reports public chain data and one small simulated trade; it cannot promise a token is safe.
