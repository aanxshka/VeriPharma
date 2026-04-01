# VeriPharma (HackHarvard 2024)

A blockchain-based pharmaceutical supply chain verification system built to combat counterfeit drugs. VeriPharma enables manufacturers, retailers, and end-users to register, track, and verify the authenticity of medications on the Ethereum blockchain.

## Problem

Counterfeit medications are a global health crisis. Traditional supply chains lack transparency and are vulnerable to fraud. VeriPharma leverages blockchain immutability to create a tamper-proof, auditable record of every drug's journey from manufacture to patient.

## Features

- **Role-based authentication** — Clients, Retailers, and Manufacturers each have dedicated dashboards
- **Drug batch registration** — Manufacturers register batches on-chain with manufacture/expiration dates
- **Ownership tracking** — Every transfer between manufacturer → retailer → patient is recorded on the blockchain
- **Authenticity verification** — Users verify any drug using its serial number
- **Faulty batch reporting** — Flag recalled or counterfeit drugs, with alerts propagated through the chain
- **Full audit trail** — Immutable event log for every action (creation, transfer, verification, flagging)

## Tech Stack

| Layer | Technology |
|---|---|
| Smart Contracts | Solidity ^0.8, Hardhat, Ethers.js |
| Blockchain Network | Ethereum Sepolia Testnet (via Alchemy) |
| Frontend | HTML5, CSS3, Vanilla JS, MetaMask |
| Backend | Python Flask, Flask-CORS |
| Database | Supabase (PostgreSQL) |
| Auth | bcrypt password hashing + wallet address |

## Smart Contracts (Deployed on Sepolia)

| Contract | Address |
|---|---|
| Registration | `0xA1e2c31c5cac1c40c8EC5432e1bf25924B10D2b4` |
| DrugTracking | `0x906A44927Da9062F9f95f29A28e75fbD74e6792a` |
| EventLogging | `0x52c5a21fe44caD23C61725a44101077b925519fb` |
| DrugVerification | `0x07820A69829B71d70c443B8D1604c5DC5fe533E6` |

## Getting Started

**Prerequisites:** Node.js, Python 3.7+, MetaMask browser extension, Sepolia testnet ETH

```bash
# Install Node dependencies
npm install

# Install Python dependencies
pip install flask flask-cors supabase python-dotenv bcrypt requests

# Set up environment variables
cp .env.example .env
# Fill in: PRIVATE_KEY, ALCHEMY_API_KEY, ETHERSCAN_API_KEY

# Deploy smart contracts
npx hardhat run scripts/deploy.js --network sepolia

# Start the backend
python src/app.py

# Open the frontend
python -m http.server 8000
# Visit http://localhost:8000/html/User.html
```

## Architecture

```
User (MetaMask) ──► Frontend (HTML/JS)
                         │
              ┌──────────┴──────────┐
              ▼                     ▼
      Flask REST API         Ethers.js / Alchemy
              │                     │
        Supabase DB         Ethereum Sepolia
```
