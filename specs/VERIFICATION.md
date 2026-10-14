# Verification: PrintFlow v0.2

14 October 2026. Test data only; real administrator account remains for the user to create.

## Automated evidence
17 Node tests: nine original carton/sticker/stock cases, six specialist pricing/approval/QC/cost cases, one multi-assertion central API test, and one SQLite backup reopen test. They cover authenticated reads, write roles, CSRF, version conflicts, idempotency, stock tampering rejection, fake evidence rejection, approval revision matching, full-quantity QC and rollback. The backup test reopens the downloaded SQLite file and verifies account/state/file-table integrity; it is not a production restore guarantee.

## Browser evidence
Separate fixture server at port 8788: logged in a fixture account, estimated a quote with plates and spot inks, saved it centrally, converted it to a job/order, uploaded fixture approval evidence to SQLite, approved the current revision, reserved 2,825 sheets and started production. Advanced stages to QC; the delivery action opened a QC form instead of shipping without results. Recorded four passing checks and 10,000 good / zero rejects. Recorded 2,850 actual sheets, 4 machine hours × 1,500 THB and 8 labour hours × 150 THB. Saved actual cost and delivered after QC. No real orders, employee credentials or approval evidence were used.

## Boundaries
Actual shop rates, inventory, process criteria, arbitrary materials/UOMs, machine capacity, lot/location operations and public deployment are not verified. Full financial read segregation and recovery/MFA are not implemented. Pilot remains local to loopback. Visual QA includes dialogs, role/login states and responsive inherited layouts; full WCAG certification is not claimed.

## Skill checkpoints
| Skill / requirement | Result |
|---|---|
| deliver-prd: problem, goals, unknown baselines, scope, stories, FR verification, contract and owners | Passed |
| agents-md-creator: concise entry points, runnable commands, flat reference links and separate open questions | Passed |
| agents-md-creator: existing file splitting approval | Not applicable: concise existing index; no split |
| architecture analysis: actual code/data diagram, observed/unknown ledger, no copied outside implementation | Passed with bounded prototype-analysis scope |
| design-system-doc: anatomy, variants, state, tokens, examples, accessibility limits and changelog | Passed / inherited tokens; additions documented |
| Third-party authoring skill global installation | Not performed; pinned source instructions used |

Fixture credentials exist only in test source and the separate fixture database. Runtime data, test databases and secrets are excluded from source delivery.


## Visual refresh v2.1
Inspected Odoo 20 Community archive styles. Checked new theme locally in browser: dashboard, app launcher navigation to production, retained Thai labels and demo backup. No business state or backend logic changed. Theme script passes Node syntax check.
