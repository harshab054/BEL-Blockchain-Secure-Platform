# BEL TrustGrid 2.0 — Blockchain-Based Secure Platform

> **Bharat Electronics Limited (BEL) Defense Governance & Cybersecurity Platform**  
> Problem Statement: **SIH26125** · Smart India Hackathon  
> TrustGrid 2.0 is a next-generation Zero-Trust enterprise platform combining **Decentralized Identity (DID)**, **Smart-Contract Access Governance**, **ERC-721 Defense Asset Custody**, **Cryptographic Integrity Verification**, and a real-time **Tactical Radar Interface** with verifiable on-chain proof.

---

## 🌐 Live Production Deployment

| Component | Service | Status / Link |
| :--- | :--- | :--- |
| **Primary Frontend (TrustGrid 2.0)** | **Vercel** | **[https://bel-blockchain-secure-platform-kkef.vercel.app/](https://bel-blockchain-secure-platform-kkef.vercel.app/)** |
| **Backend REST API** | **Render** | **[https://bel-blockchain-backend.onrender.com](https://bel-blockchain-backend.onrender.com)** |
| **Backend Health Check** | **Render** | **[https://bel-blockchain-backend.onrender.com/api/health](https://bel-blockchain-backend.onrender.com/api/health)** |
| **Cloud Database** | **Turso (libSQL)** | AWS Asia-Pacific (Mumbai) Serverless Instance |
| **Blockchain Network** | **Polygon Amoy Testnet** | Public EVM (Chain ID: `80002`) |

> **24/7 Cloud Availability:** The deployed platform operates 100% autonomously in the cloud across Vercel, Render, Turso, and Polygon Amoy without requiring any local developer PC or workstation to remain online.

---

## 📜 Deployed Smart Contracts (Polygon Amoy Testnet)

All smart contracts are verified and deployed on the **Polygon Amoy Testnet** (Chain ID: `80002`):

| Contract | Address | Polygonscan Explorer |
| :--- | :--- | :--- |
| **`IdentityRegistry`** | `0xC928127C89339269645217cC7aAB8c604Fa717f3` | [View on Amoy Polygonscan](https://amoy.polygonscan.com/address/0xC928127C89339269645217cC7aAB8c604Fa717f3) |
| **`AccessControlManager`** | `0x2FFD26016cb9F1638f86d03Fb118B90288B8bf64` | [View on Amoy Polygonscan](https://amoy.polygonscan.com/address/0x2FFD26016cb9F1638f86d03Fb118B90288B8bf64) |
| **`AssetRegistry` (ERC-721)** | `0xb2A2D16CbE6B56c278341d40ee70f1F723Bfe62f` | [View on Amoy Polygonscan](https://amoy.polygonscan.com/address/0xb2A2D16CbE6B56c278341d40ee70f1F723Bfe62f) |

---

## 🏗️ Production Architecture & Codebase Structure

The repository maintains the primary TrustGrid 2.0 application alongside legacy components:

```
BEL-Blockchain-Secure-Platform/
├── trustgrid/               # ⭐ Primary Production Frontend (Next.js 16 + React 19 + Tailwind CSS)
│   ├── src/app/             # Next.js App Router (19 static & dynamic routes)
│   │   ├── (workspace)/     # Zero-trust workspace (/dashboard, /assets, /documents, /approvals, /audit, /architecture)
│   │   ├── api/auth/        # Edge/Serverless authentication & persona routes
│   │   └── login/           # Tactical Radar persona login portal
│   └── package.json         # Next.js build scripts ("next build")
│
├── frontend/                # 📦 Legacy Frontend (Preserved Vite + React 19 SPA)
│
├── backend/                 # ⚙️ Production REST API (Node.js + Express + Ethers.js)
│   ├── routes/              # Modular REST routes (auth, identities, access, assets, audit, erp)
│   ├── blockchain.js        # Polygon Amoy / EVM JSON-RPC provider & contract integration
│   └── server.js            # Express API entry point
│
├── contracts/               # 📜 Solidity Smart Contracts (Identity, AccessControl, AssetNFT)
├── scripts/                 # Deployment, wallet configuration, seeding, and migration scripts
└── test/                    # Comprehensive Hardhat smart contract test suites
```

### Important Architecture Clarification:
- **Primary Production Frontend (`trustgrid/`):** The modern Next.js 16 application is the primary frontend deployed to Vercel.
- **Legacy Frontend (`frontend/`):** The original Vite single-page application is preserved in the repository for backwards compatibility.
- **Vercel Production Deployment:** Vercel is configured with **Root Directory = `trustgrid`** and framework preset **Next.js**. Builds are triggered automatically upon pushing commits to the `main` branch via `next build`.
- **Render Backend Deployment:** Node.js Express service running 24/7 on Render connected to Turso libSQL and Polygon Amoy testnet.
- **Blockchain Connectivity:** Production uses **Polygon Amoy Testnet (Chain ID `80002`)**. Local Hardhat nodes (`127.0.0.1:8545`) are utilized exclusively for offline automated testing and development.

---

## ⚡ Key TrustGrid 2.0 Capabilities

1. **Zero-Trust Workspace:** Every resource access is explicitly evaluated through cryptographic policy engines rather than static implicit role permissions.
2. **Role-Based Defense Personas:** Pre-configured defense personas (Commander, Radar Engineer, Quality Officer, Security Admin, External Auditor) for seamless evaluation.
3. **Dynamic Policy Evaluation:** Visual policy inspector and evaluator tracing clearance levels, project compartmentalization, and two-person approval rules.
4. **Enterprise Dashboard (`/dashboard`):** Real-time metrics on registered identities, active asset passports, pending approval requests, and security alerts.
5. **Defense Asset Passport & Custody Tracking (`/assets`):** ERC-721 NFT digital passports tracking high-value defense hardware, custody transfers, and maintenance logs.
6. **Cryptographic Document Registry & Verification (`/documents`):** Off-chain classified technical schematics anchored by immutable SHA-256 hashes on Polygon Amoy for bit-for-bit tamper detection.
7. **Access Request & Approval Workflows (`/approvals`, `/requests`):** Time-bound, mission-justified access requests with separation of duties and dual-approver rules.
8. **Tamper-Evident Audit Trail (`/audit`):** Complete chronological event ledger with SHA-256 hash chaining and on-chain event replay capability.
9. **Interactive Blockchain Architecture & Flow (`/architecture`):** Live diagram showing real-time tokenized asset movements, state mutations, and relayer confirmation pipelines.
10. **Tactical Radar Themed Interface:** Defense-grade dark visual design with CRT sweep radar animation, low-latency status feeds, and accessible data views.
11. **Blockchain Ledger Visibility:** Real-time ticker and X-Ray inspector showing transaction hashes, block numbers, gas metrics, and contract execution proof.

---

## 🚀 TrustGrid 2.0 Routes

The Next.js App Router in `trustgrid/` compiles and serves the following core routes:

- `/dashboard` — Enterprise zero-trust governance dashboard
- `/assets` — Defense asset passport registry & custody lifecycle
- `/documents` — Cryptographic document registry & tamper-verification tool
- `/approvals` — Access request approval queue & dual-signature decisions
- `/audit` — Immutable audit trail & ledger event history
- `/architecture` — Interactive system architecture & cryptographic data flow
- `/identity` — DID personnel directory & role assignments
- `/hierarchy` — Organizational command hierarchy & clearance tree
- `/verify` — Public document & asset integrity verifier
- `/login` — Tactical radar persona selector & authentication

---

## 🛠️ Local Development

### Prerequisites
- Node.js `v18.0.0+`
- npm `v9.0.0+`
- Git

### 1. Repository Setup
```bash
git clone https://github.com/harshab054/BEL-Blockchain-Secure-Platform.git
cd BEL-Blockchain-Secure-Platform
npm install
npm --prefix backend install
npm --prefix trustgrid install
npm --prefix frontend install
```

### 2. Run Smart Contract Tests
```bash
npm test
```
*Executes all 13 Hardhat smart contract tests covering identity registration, access control lifecycle, and ERC-721 asset custody.*

### 3. Run TrustGrid 2.0 Frontend (Primary)
```bash
cd trustgrid
npm run dev
```
*Accessible at `http://localhost:3000`*

### 4. Build TrustGrid 2.0 for Production
```bash
cd trustgrid
npm run build
```
*Builds all 19 static and dynamic routes with Next.js Turbopack.*

### 5. Run Full Local Stack (Hardhat + Backend + Frontend)
```bash
npm run dev
```
- Local Blockchain Node: `http://127.0.0.1:8545`
- Backend Express API: `http://localhost:5001`
- Legacy Frontend SPA: `http://localhost:5173`

---

## 🔒 Security & Environment Hygiene

- **Zero Secrets Committed:** All credentials, private keys, database URLs, and API tokens are managed strictly via environment variables (`.env`, Vercel Environment Variables, Render Secret Configs).
- **Git Ignore Safeguards:** All `.env*` files (except `.env.example` templates) are permanently excluded via [`.gitignore`](.gitignore).
- **Client Safety:** Private keys and relayer credentials are restricted to server-side runtimes. No private keys are bundled or exposed in client-side code or documentation.
- **Public Testnet Scope:** Polygon Amoy is a public testnet (Chain ID: `80002`) used for demonstration and evaluation purposes.
- **Fictional Demonstration Data:** All personnel names, defense asset identifiers, and project specifications are fictional and created solely for the SIH 2026 demonstration.

---

## 📊 Current Production Status

- **TrustGrid 2.0 Frontend:** **Operational** on **Vercel** ([Live URL](https://bel-blockchain-secure-platform-kkef.vercel.app/))
- **Express Backend API:** **Operational** on **Render** ([Health Endpoint](https://bel-blockchain-backend.onrender.com/api/health))
- **Database:** **Operational** on **Turso Cloud (libSQL AWS Mumbai)**
- **Smart Contracts:** **Live & Verified** on **Polygon Amoy Testnet (Chain ID `80002`)**

---

## 📄 License & Attribution

Developed for the **Smart India Hackathon (SIH)** — **Bharat Electronics Limited (BEL)** Problem Statement (SIH26125).  
All rights reserved © Bharat Electronics Limited / SIH Project Team.
