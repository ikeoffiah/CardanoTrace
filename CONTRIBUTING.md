# Contributing to CardanoTrace

Thank you for your interest in improving CardanoTrace! 🎉  
We welcome contributions from everyone — whether you’re fixing a bug, refining docs, adding tests, contributing to smart contracts, or building new API/SDK features.

CardanoTrace is an open-source supply chain traceability platform built on the Cardano blockchain with components in Python (FastAPI), Haskell/Plutus (smart contracts), and a Python SDK. This guide explains how to contribute effectively and responsibly.

## Ways to Contribute
- **Bug reports**: Found a defect? Open an issue with a minimal reproduction, logs, and environment details.
- **Feature requests**: Propose enhancements with clear motivation, scope, and alternatives considered.
- **Documentation**: Improve README, tutorials, API docs, and examples.
- **Testing**: Add unit/integration tests for API, SDK, or smart contracts.
- **Code**: Backend (FastAPI), QR service, SDK, and Haskell/Plutus smart contracts.

Before starting substantial work, please open or comment on an issue to align on approach.

## Project Expectations and Norms
- **License**: MIT. By submitting a contribution, you agree it will be licensed under the project’s MIT License.
- **Code of Conduct**: Be respectful and inclusive. See our [Code of Conduct](CODE_OF_CONDUCT.md).
- **Versioning**: We follow Semantic Versioning (SemVer) for releases.

## Development Workflow

### 1) Fork and Clone
```bash
git clone https://github.com/ikeoffiah/CardanoTrace.git
cd CardanoTrace
git remote add upstream https://github.com/ikeoffiah/CardanoTrace.git
```

### 2) Create a Topic Branch
- Branch from `dev` for active development; use `main` only for stable releases.
- Use clear prefixes: `feat/`, `fix/`, `docs/`, `test/`, `chore/`, `refactor/`.
```bash
git checkout -b feat/your-feature-name upstream/dev
```

### 3) Keep Your Branch Up-to-date
Prefer rebasing to keep a clean history:
```bash
git fetch upstream
git rebase upstream/dev
```

### 4) Local Setup

Backend (FastAPI):
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env  # then edit values as needed
alembic upgrade head
uvicorn app.main:app --reload
```

Smart Contracts (Plutus/Haskell):
```bash
cd smart-contracts
cabal build
cabal test
# (optional) deploy to testnet with scripts as documented
```

QR Code Service:
```bash
cd qr-service
pip install -r requirements.txt
uvicorn qr_service.main:app --reload
```

Python SDK:
```bash
cd sdk/python
pip install -e .
pytest tests/
```

Refer to `README.md` for more details.

## Coding Standards

### Conventional Commits
Use conventional commits for clear history and automated tooling:
- `feat: add QR signature validation`
- `fix: correct transaction ID parsing`
- `docs: update API authentication section`
- `test: add coverage for event ingestion`
- `chore: bump dependencies`

### Python (API, QR Service, SDK)
- Use type hints and docstrings for public functions/classes.
- Lint with `ruff` and ensure no warnings before pushing:
```bash
ruff check .
```
- Run tests with coverage:
```bash
pytest --cov=app tests/
```

### Haskell/Plutus (Smart Contracts)
- Run `hlint` and fix suggestions:
```bash
hlint .
```
- Ensure `cabal test` passes locally.

### Database Migrations (Alembic)
- Generate and apply migrations:
```bash
alembic revision --autogenerate -m "describe change"
alembic upgrade head
```
- Keep migrations small, reversible, and reviewed.

### API Changes
- Maintain backward compatibility where possible.
- Update request/response models and ensure OpenAPI docs reflect changes.
- Add or update examples in `docs/examples` and Postman collections under `docs/postman/` if applicable.

## Documentation Guidelines
- Keep `README.md` and component READMEs up to date.
- Write clear, step-by-step instructions.
- If using MkDocs, ensure the site builds locally:
```bash
mkdocs serve
```

## Issue Reporting
Before filing an issue:
- Search existing issues and the roadmap.
- Include environment details (OS, Python/Haskell versions, DB), reproduction steps, expected vs. actual behavior, logs, and screenshots if helpful.

Bug report template (use in issue body):
```
Environment:
- OS:
- Python:
- Haskell/Plutus:
- Database:

Steps to reproduce:
1.
2.
3.

Expected:
Actual:
Logs/Trace:
```

## Pull Request (PR) Guidelines
- Keep PRs focused and reasonably small. Draft early, iterate often.
- Link related issues (e.g., "Fixes #123").
- Use a descriptive title following Conventional Commits.
- Provide context: motivation, approach, trade-offs, screenshots for UI (if any).

PR Checklist:
- [ ] Branch is up-to-date with `upstream/dev` (rebased)
- [ ] Linting passes (`ruff`, `hlint`)
- [ ] Tests added/updated and pass locally (`pytest`, `cabal test`)
- [ ] Migrations added/updated (if schema changed) and tested
- [ ] API docs/examples updated (if endpoints changed)
- [ ] No secrets or private keys committed

All PRs must pass CI (lint, test, and any type/static checks) before review and merge.

## Security and Responsible Disclosure
- Never commit secrets, private keys, or `.env` files. Rotate any leaked credentials immediately.
- Report vulnerabilities privately via GitHub Security Advisories ("Report a vulnerability" in the repo). Do not open public issues for security findings.
- Provide details to reproduce, potential impact, affected versions, and proposed mitigations.

## Community and Communication
- Primary channels: GitHub Issues/PRs and the Cardano community forum (see contacts in `README.md`).
- Be patient and constructive. Maintainers are volunteers and may need time to review.

## Recognition
Contributors are acknowledged in release notes and the GitHub contributors list. Your help makes the project better for everyone — thank you!

---
If you’re unsure about anything, open an issue to discuss before starting work. Even small improvements are welcome!

