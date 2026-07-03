# Yeldra

<div align="center">
  <img src="https://i.postimg.cc/nhSSNc9S/IMG-20260702-175620.png" width="80" height="80" />
  <h1>Yeldra</h1>
  <p><strong>Professional DeFi Staking Protocol on Ethereum</strong></p>

  

![Solidity](https://img.shields.io/badge/Solidity-0.8.20-363636?style=flat&logo=solidity)


  

![React](https://img.shields.io/badge/React-18-61DAFB?style=flat&logo=react)


  

![Vite](https://img.shields.io/badge/Vite-5-646CFF?style=flat&logo=vite)


  

![TailwindCSS](https://img.shields.io/badge/TailwindCSS-3-06B6D4?style=flat&logo=tailwindcss)


  

![Network](https://img.shields.io/badge/Network-Sepolia-8B5CF6?style=flat)


  

![License](https://img.shields.io/badge/License-MIT-green?style=flat)


</div>

---

## Overview

Yeldra is a non-custodial DeFi staking protocol built on Ethereum where users can stake USDC and earn passive rewards over time. The protocol uses the battle-tested **reward-per-token accumulator pattern** (pioneered by Synthetix) for gas-efficient, fair reward distribution regardless of the number of stakers.

> **Live Demo:** [https://yeldra-sigma.vercel.app](https://yeldra-sigma.vercel.app)
> **Contract:** `0x9bD14eA64dEA9b130f7978b1D0498cc013427EBB`
> **Network:** Ethereum Sepolia Testnet

---

## Features

- Stake USDC and earn passive rewards instantly
- Claim rewards anytime — no lock-up period
- Unstake anytime with full flexibility
- Live APR calculated directly from the contract
- Emergency withdraw available even when paused
- Multi-wallet support via Reown AppKit (MetaMask, Rabby, WalletConnect)
- Dark / Light theme toggle
- Fully mobile responsive

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Smart Contract | Solidity 0.8.20 |
| Frontend | React 18 + Vite 5 |
| Styling | TailwindCSS 3 |
| Web3 | ethers.js v6 |
| Wallet | Reown AppKit |
| Deployment | Vercel |
| Network | Ethereum Sepolia Testnet |

---

## Contract Addresses

| | Address |
|--|---------|
| Staking Contract | `0x9bD14eA64dEA9b130f7978b1D0498cc013427EBB` |
| USDC (Sepolia) | `0x1c7D4B196Cb0C7B01d743Fbc6116a902379C7238` |

---

## Security

- Non-custodial — users always control their funds
- Reentrancy protection on all state-changing functions
- Emergency withdraw available even when paused
- Reward rate safety check prevents over-distribution

---

## Author

Built by [@BappyOnchain](https://twitter.com/BappyOnchain)

---

## License

MIT
