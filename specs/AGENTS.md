# PrintFlow contributor index

## Overview
Independent Thai ERP for cartons and sheet stickers. GitHub Pages serves the browser-local demo; Node.js serves the same frontend with a shared SQLite database on loopback for a local pilot.

## Structure / entry points from repository root
| Area | Entry |
|---|---|
| Navigation, quotes, jobs and materials | docs/app.js |
| Pricing and material rules | docs/core.js, docs/production-core.js |
| Tools, files, approvals, routing, QC and costs | docs/workshop.js |
| Customers, suppliers, machines, BOM and support registries | docs/masters.js |
| Connected login and users | docs/backend-client.js |
| Central authorization and transactional validation | server/server.cjs |
| Interface styles | docs/style.css |
| Business/API checks | tests/ |

## Baseline setup
Node.js 24.14+; tested 24.19.0. No dependencies to install. Run `node server/server.cjs` for http://127.0.0.1:8787. Run `node --test tests/*.test.cjs` after behavior changes. Pages source is main /docs; the local server overrides runtime-config.js.

## Principles
- PrintFlow is independent of other business systems. <!-- user-specified -->
- Support cartons and sheet stickers. Roll material requires a separate model. <!-- user-specified -->
- Apply the four authoring skills in SOURCES.md to current implementation evidence. <!-- user-specified -->
- Authorize writes on the server; UI visibility is not a permission boundary.
- Preserve sheets, pieces/labels and hours as distinct units. Keep quote snapshots and approved revisions.
- Test stock reservations, once-only consumption/receipts, stale versions and rollback.
- Keep data/, passwords, sessions and fixture databases out of commits and deliverable archives.
- The first real admin chooses their own password. Never reuse fixture credentials for live users.

## References
- [PRD.md](PRD.md): scope and acceptance; read before behavior changes.
- [ARCHITECTURE.md](ARCHITECTURE.md): actual data boundaries; read before backend changes.
- [DESIGN_SYSTEM.md](DESIGN_SYSTEM.md): components/states; read before UI changes.
- [SOURCES.md](SOURCES.md): research and skill provenance; read when changing assumptions.
- [VERIFICATION.md](VERIFICATION.md): release evidence; read before publication.
- [AGENTS_OPEN_QUESTIONS.md](AGENTS_OPEN_QUESTIONS.md): pilot decisions; read before business deployment.
