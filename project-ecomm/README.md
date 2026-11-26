# Project-Ecomm

B2B2C real-estate aggregator and automated CRM. Owners, agents and developers list
inventory. Buyers search and enquire. Every enquiry goes to a central CRM, and buyers
never see supply-side contact details.

| | |
|---|---|
| Architecture | [docs/architecture](docs/architecture/README.md) |
| Repo layout | [docs/architecture/repository-structure.md](docs/architecture/repository-structure.md) |
| Database (ER, indexes, partitions) | [docs/database](docs/database/README.md) |
| RBAC matrix | [docs/architecture/rbac.md](docs/architecture/rbac.md) |
| Decisions | [docs/adr](docs/adr/) |

## Quick start

Prerequisites: Node 22+, pnpm 9, Docker, Python 3.12 (for `apps/ai-service`).

```bash
cp .env.example .env
pnpm install
pnpm infra:up            # postgres(pgvector) · redis · minio · mailpit
pnpm db:generate
pnpm db:migrate          # applies 0001 baseline + 0002 raw SQL
pnpm db:seed             # roles & permissions (+ first Super Admin if SEED_SUPER_ADMIN_* set)
pnpm dev
```

- API: http://localhost:4000/api/v1 · Swagger: http://localhost:4000/api/docs
- Web: http://localhost:3000 · Mail: http://localhost:8025 · MinIO: http://localhost:9001

> **OneDrive note:** keep the working copy **outside** OneDrive (for example `C:\dev\project-ecomm`).
> OneDrive sync interferes with `node_modules`, `.next` and Docker bind mounts.

## Delivery plan

| Phase | Scope | Status |
|---|---|---|
| 0 | Foundation: repo, architecture, DB schema + migrations, RBAC | ✅ |
| 1 | Authentication & role management | ⏭ next |
| 2 | Property management | |
| 3 | Unique property ID engine | |
| 4 | AI duplicate detection | |
| 5 | Super Admin CRM | |
| 6 | Buyer portal (SEO) | |
| 7 | WhatsApp automation | |
| 8 | Instagram automation | |
| 9 | Appointments | |
| 10 | Developer SaaS portal | |
| 11 | Cross-cutting: frontend system, API standards, security hardening | |
| 12 | CI/CD, Docker (prod), AWS deployment, DR | |
| 13 | Test strategy: performance, load, security suites | |
