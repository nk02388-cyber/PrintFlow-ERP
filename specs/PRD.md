# PRD: PrintFlow independent print-shop ERP / v0.2

14 October 2026 / Local pilot implementation; business go-live not approved.

## Overview
### Problem
The requested system connects carton and sticker specifications, pricing, approved revisions, production, QC and actual cost. Actual company rates and performance baselines were not supplied; these are requested capabilities, not findings from a company audit.
### Solution
Extend PrintFlow and add its own Node.js API and shared SQLite database for testing on this machine. The user cancelled Odoo as the foundation. Authoring skills create no dependency on another business system.
### Users
Write roles: admin, sales, planner, warehouse, operator, qc, accountant and viewer. Authenticated roles currently share read access to the business dataset.

## Goals & Success Metrics
| Goal / metric | Baseline | Target | Checkpoint |
|---|---|---|---|
| Invalid stock/proof/QC changes accepted | Fixture testing | Zero accepted in defined regression cases | Every release |
| Shared quote/job persistence | No previous backend | Retained through login/reload in walkthrough | Local pilot |
| Estimate turnaround | Unknown | Measure before choosing target | Business pilot |
| Jobs closed with actual cost | Unknown | Proposed >=95% within 3 working days | Business pilot |

Non-goals: Odoo foundation, roll calculations, automated CAD/preflight, tax filing or optimized machine scheduling. Local testing is not production certification.

## User Stories
Sales estimates and accepts quotes; planners manage tools/revisions and approval evidence; operators use consolidated job sheets; QC records counts and results; accountants compare actual category costs; admins manage pilot accounts. These stories are P0 except additional support registries (P1).

## Scope
Implemented: five specialist features below, customer/CRM and supplier registries, machines, BOM planning, subcontract/maintenance tracking, accepted-quote sales-order records. Local server includes cookie sessions, CSRF/write roles, version checks, idempotency, transaction validation, audit and file BLOB storage.

Boundaries: BOM is planning information, not automatic consumption. Subcontract tracking does not perform stock transfers. Actual sheet use updates stock; auxiliary ink/glue/foil amounts are costing entries without separate inventory ledgers. Seven cost categories aggregate time and rates. Routing does not detect machine conflicts. QC requires inspection quantities equal to the job quantity, with no sampling/partial-delivery policy. Password recovery and granular financial read permissions remain future work.

## Solution Design
| ID | Requirement | Verification / verifier |
|---|---|---|
| FR-1 | Size/Ups/spoilage/setup, plates, special inks, tools and finishing in gross-margin estimate | Fixture calculator tests + browser / automated and QA |
| FR-2 | Tool code, type, owner, dimensions, status and reference cost | Form save and server validation / QA |
| FR-3 | Revision uploads and approval evidence; block mismatched revision or unavailable tool at start | Domain tests + upload/start walkthrough / automated and QA |
| FR-4 | Job routing with machine/actor, planned hours and due date; export consolidated printable job | Form + HTML download / QA |
| FR-5 | Four QC checks and full good/reject counts; no delivery until all pass and zero reject | Domain tests + browser gate / automated and QA |
| FR-6 | Seven actual-cost categories and actual-sheet issue/return; compare estimate and sale price | Domain tests + browser write / automated and QA |
| FR-7 | Sessions, CSRF, role writes; reject forged stock/files and stale writes | API test / automated |
| FR-8 | Duplicate request result and transaction rollback | API test / automated |
| FR-9 | Core registries with explicit planning/tracking limits | Forms and scope text / QA |

UX: Thai mode banners distinguish browser-local demo and central mode. API failure never falls back to a claimed successful local write. Current revision, approval and QC status are visible in job details. Dialog messages explain corrective actions.

| Edge case | Behavior |
|---|---|
| Another employee updated first | HTTP 409, reload latest, no silent overwrite |
| Wrong role or CSRF | HTTP 403, no write |
| Fake attachment metadata | Reject absent server BLOB |
| Change revision after start | Reject |
| Failed/incomplete QC | Preserve failure, hold delivery |
| Actual material exceeds availability | Reject with rollback |
| JSON backup lacks browser-local file content | Report missing file on download |

## Technical Considerations
Node.js 24.19 and built-in SQLite were tested. Records use one versioned JSON snapshot plus users, sessions, request results, audit and file BLOB tables. BEGIN IMMEDIATE commits validated changes atomically. Snapshot contention and database/file growth require measurement before scaling; normalized entities are future work. The server binds 127.0.0.1 and validates local Host/Origin. No external account credentials are required.

## Agent Execution Contract
Authoritative order: latest user instructions; current implementation/tests; PRD/architecture; research. Do not import real records or touch unrelated systems. Never publish data/ or reuse fixture credentials. Every FR above names verification. Escalate actual-data migration/UOM reinterpretation to the print-shop owner; pricing/accounting policy to owner/accountant; public hosting, TLS and retention to system owner.

## Dependencies & Risks
Actual rates, QC criteria and machine limits: owner validates completed jobs. Loopback is unavailable to other computers: owner decides future deployment. All employee roles read financial data: owner agrees access policy before real records. Backup/restore guarantees are untested: system owner completes restore drill before go-live. Multi-device loading and contention: developer performs pilot/load tests before scaling.

## Timeline & Milestones
Local code and fixture checks: this delivery. First real admin: user-controlled setup. Business pilot: reconcile inventory and confirm rates/QC. Office/public deployment and go-live dates: pending owner decisions.

## Open Questions
[AGENTS_OPEN_QUESTIONS.md](AGENTS_OPEN_QUESTIONS.md). Prices and QC gates are deterministic; no AI model produces app calculations.

## Appendix
[Architecture](ARCHITECTURE.md), [design system](DESIGN_SYSTEM.md), [sources](SOURCES.md), [verification](VERIFICATION.md), [agent index](AGENTS.md). Version 0.2 implements the five specialist workflows and local central backend.
