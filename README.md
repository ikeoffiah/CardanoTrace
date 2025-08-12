# CardanoTrace – Open Source Supply Chain Traceability API & SDK

CardanoTrace is an open-source, modular supply chain traceability platform built on the **Cardano blockchain**.  
It provides **Haskell (Plutus) smart contracts**, a **REST API**, a **QR code service**, and a **Python SDK** to help developers and businesses rapidly build transparent and interoperable supply chain solutions.

## 🚀 Features
- **Smart Contracts (Haskell/Plutus)** – Record immutable product lifecycle events (origin, transport, compliance, ownership changes).
- **REST API (FastAPI)** – Interact with smart contracts via secure, well-documented endpoints.
- **QR Code Service** – Generate and scan QR codes linked to blockchain transaction IDs.
- **Python SDK** – Simplified integration for Python projects.
- **Interoperability** – Standardized data models for easy integration with ERP, IoT, and mobile/web apps.
- **Open Source** – Released under the MIT License.

---

## 🏗 Architecture Overview
```
[Client Apps / ERP / IoT Devices]
             |
         REST API
      (FastAPI Backend)
             |
   ------------------------
   |         |            |
 Smart   QR Code     SDK Layer
 Contracts  Service  (Python API wrapper)
 (Haskell/Plutus)   (FastAPI endpoint)
             |
         Cardano Blockchain
```

---

## 📦 Tech Stack
- **Blockchain Layer:** Cardano / Haskell (Plutus)
- **Backend:** Python 3.11+, FastAPI
- **Database:** PostgreSQL (prod), SQLite (dev/test)
- **QR Code:** `qrcode` Python lib
- **SDK:** Python, published on PyPI
- **CI/CD:** GitHub Actions
- **Documentation:** Swagger/OpenAPI, MkDocs

---

## 🔧 Setup & Installation

### 1. Clone the Repository
```bash
git clone https://github.com/<your-org>/cardanotrace.git
cd cardanotrace
```

### 2. Backend (FastAPI + Smart Contract Integration)
```bash
# Create virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run migrations
alembic upgrade head

# Start server
uvicorn app.main:app --reload
```
API docs available at:  
`http://localhost:8000/docs` (Swagger)  
`http://localhost:8000/redoc` (ReDoc)

---

### 3. Smart Contracts (Haskell/Plutus)
```bash
cd smart-contracts
cabal build
cabal test
# Deploy to Cardano testnet
scripts/deploy-testnet.sh
```

---

### 4. QR Code Service
```bash
cd qr-service
pip install -r requirements.txt
uvicorn qr_service.main:app --reload
```

---

### 5. Python SDK
```bash
cd sdk/python
pip install -e .
# Test the SDK
pytest tests/
```

---

## 🔐 Environment Variables
Copy `.env.example` to `.env` and configure:
```env
DATABASE_URL=postgresql://user:pass@localhost:5432/cardanotrace
CARDANO_NODE_URL=https://testnet.cardano.org/api
API_SECRET_KEY=supersecret
QR_CACHE_TTL=3600
```

---

## 📚 API Reference
- Auto-generated Swagger docs: `/docs`
- OpenAPI spec file: `openapi.json`
- Example requests in `docs/examples` and Postman collection in `docs/postman/`

---

## 🧪 Testing
Run all tests with coverage:
```bash
pytest --cov=app tests/
```

Smart contract tests (Haskell/Plutus):
```bash
cabal test
```

---

## 🛠 Development Guidelines
- **Branching:** `main` (stable) → `dev` (active development) → feature branches (`feat/*`)
- **Commits:** Follow [Conventional Commits](https://www.conventionalcommits.org/) (`feat:`, `fix:`, `docs:`, etc.)
- **Linting:** `ruff` for Python, `hlint` for Haskell
- **CI:** All PRs must pass lint, test, and type checks before merging

---

## 🤝 Contributing
1. Fork the repository
2. Create a feature branch: `git checkout -b feat/my-feature`
3. Commit changes: `git commit -m "feat: add new feature"`
4. Push to your fork and open a PR
5. Ensure tests and lint pass in CI

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for details.

---

## 📜 License
This project is licensed under the [MIT License](LICENSE).

---

## 📢 Roadmap
- ✅ Milestone 1 – Smart Contracts + Architecture Docs
- 🚧 Milestone 2 – API Development
- ⏳ Milestone 3 – QR Code Service
- ⏳ Milestone 4 – Python SDK
- ⏳ Milestone 5 – Public Release & Maintenance

---

## 📬 Contact
- GitHub: [ikeoffiah](https://github.com/ikeoffiah)
- Cardano Forum: *(link to be added)*
