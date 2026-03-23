# 🔒 DustLock — Cyber Gold Coin veToken dApp

> **Lock GOLDCOIN. Earn rewards. Govern the protocol.**
> A neon-casino styled veToken interface built on [Monad](https://monad.xyz).

---

## 🌐 Live App

> Deploy via GitHub Pages and paste your URL here.

---

## 📸 Overview

DustLock is a single-file Web3 dApp that lets holders of **Cyber Gold Coin (GOLDCOIN)** lock their tokens into **veNFT positions** to:

- 🗳 **Vote** on governance proposals
- 💰 **Earn** weekly epoch revenue rewards (GOLDCOIN + MON)
- 💎 **Hold** a veNFT representing their locked position
- ⚡ **Delegate** voting power to any address

The UI features a neon-casino aesthetic with cyan/magenta/gold accents on a deep navy background — built for Monad Mainnet.

---

## 🔗 Deployed Contracts — Monad Mainnet

| Contract | Address |
|---|---|
| **GOLDCOIN Token** | `0x0E85DD8252C5c734E6E9a0c9D4b9351868fb9Cbe` |
| **DustLock (veNFT)** | `0x5C706D1efb5ea5c3dccE1cc424aCBB6c3FbA0cDD` |
| **Governance** | `0x164f06672b55C25f181257e3015eFD9CC5929297` |
| **Revenue Distributor** | `0x3f19d37D4b0eA54667583683c0Ddf2f988C59588` |

> 🔍 Explorer: [explorer.monad.xyz](https://explorer.monad.xyz)

---

## ✨ Features

### 🔒 Locking
- Lock GOLDCOIN for 1 week up to 4 years
- Voting power decays linearly over the lock period
- Preview estimated VP and unlock date before confirming
- Extend lock duration on existing positions (`+TIME`)
- Add more GOLDCOIN to existing positions (`+MOTO`)
- Early exit with 10% penalty

### 💎 veNFT Positions
- Each lock mints a unique veNFT
- View all active positions with voting power bars
- Withdraw expired locks gas-efficiently

### 💰 Rewards
- Weekly epoch distribution of GOLDCOIN + MON
- Claim individual rewards per veNFT per epoch
- **Batch claim** all pending rewards in a single transaction
- Live epoch progress bar and pool size display
- Estimated APR shown in real time

### 🗳 Governance
- Vote FOR / AGAINST / ABSTAIN on proposals
- Votes automatically cast across all your veNFTs
- Signal proposals and on-chain proposals supported
- Delegate your voting power to any address

---

## 🚀 How to Use

### Requirements
- [MetaMask](https://metamask.io) or any EIP-1193 compatible wallet
- Monad Mainnet added to your wallet
- GOLDCOIN tokens in your wallet

### Getting Started

1. Open `dustlock-app.html` in your browser (or visit the GitHub Pages URL)
2. Click **[ CONNECT ]** in the top right
3. MetaMask will prompt you to switch to / add **Monad Mainnet** automatically
4. Once connected, your GOLDCOIN balance and positions will load

### Locking Tokens

1. Go to **Lock** tab
2. Enter amount of GOLDCOIN
3. Select a lock duration (longer = more voting power)
4. Click **LOCK TOKENS →**
5. Approve GOLDCOIN spend → confirm lock transaction

### Claiming Rewards

1. Go to **Rewards** tab
2. Claimable rewards appear per veNFT per epoch
3. Click **CLAIM** on individual rows, or **⚡ CLAIM ALL REWARDS** to batch everything in one tx

### Voting

1. Go to **Vote** tab
2. Active proposals show live vote tallies
3. Click **VOTE FOR**, **VOTE AGAINST**, or **ABSTAIN**
4. Your vote is cast across all your veNFTs automatically

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML / CSS / JS (single file) |
| Web3 Library | [ethers.js v6](https://docs.ethers.org/v6/) via CDN |
| Wallet | MetaMask / EIP-1193 |
| Network | Monad Mainnet (`chainId: 0x8f` / 143) |
| Fonts | Share Tech Mono + Syne (Google Fonts) |
| Hosting | GitHub Pages |

---

## 📁 File Structure

```
dustlock-app.html   ← entire app in one file
README.md           ← this file
```

No build step. No dependencies to install. Open and run.

---

## ⚙️ Function Reference

### Wallet
| Function | Description |
|---|---|
| `connectWallet()` | Connect MetaMask, switch to Monad |

### Data
| Function | Description |
|---|---|
| `refreshAll()` | Refresh all data in parallel |
| `refreshStats()` | Update stats bar (locked, epoch, NFT count) |
| `refreshMyNFTs()` | Load veNFT positions |
| `refreshRewards()` | Scan epochs for claimable rewards |
| `getBalance()` | Fetch GOLDCOIN wallet balance |
| `getAPR()` | Calculate estimated APR |

### Locking
| Function | Description |
|---|---|
| `lockTokens()` | Create new lock position |
| `extendLock(tokenId)` | Extend duration of existing lock |
| `increaseLockAmount(tokenId)` | Add GOLDCOIN to existing lock |
| `withdrawNFT(tokenId)` | Withdraw expired lock |
| `earlyWithdraw(tokenId)` | Exit early with 10% penalty |

### Rewards
| Function | Description |
|---|---|
| `claimReward(tokenId, epochId)` | Claim single reward |
| `batchClaimRewards()` | Claim all pending rewards in one tx |

### Governance
| Function | Description |
|---|---|
| `castVote(proposalId, choice)` | Vote on a proposal |
| `batchVote(proposalId, choice)` | Vote with all veNFTs |
| `delegateVotingPower()` | Delegate VP to an address |

### UI
| Function | Description |
|---|---|
| `updatePreview()` | Live VP + unlock date preview |
| `showPage(name)` | Navigate between pages |
| `toast(msg, type)` | Show notification |
| `loadEthers()` | Dynamically load ethers.js |
| `getContract(addr, abi)` | Get contract instance |

---

## 🔐 Security Notes

- This app is **read-only** until you click a button and sign a transaction in your wallet
- No private keys are ever touched or stored
- `mint()` is owner-only on the GOLDCOIN contract — only the deployer wallet can mint
- Early exit penalty is enforced at the **contract level** — the UI cannot bypass it
- Always verify contract addresses before approving token spend

---

## 📄 License

MIT — free to use, fork, and build on.

---

*Built with 💛 for the Cyber Gold Coin ecosystem on Monad.*
