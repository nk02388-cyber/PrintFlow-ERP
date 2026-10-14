# Research and skill provenance

Retrieved 14 October 2026. Research informs the design; vendor claims are not independent measurements of this print shop. No real customer orders, warehouse quantities or credentials were imported. The ERP is independent; other systems do not determine its architecture.

## Industry primary sources
| Source | Supported design consideration |
|---|---|
| [HEIDELBERG Prinect](https://www.heidelberg.com/global/en/print_and_packaging/software/workflow/prinect_3.jsp) | Connected business-to-production workflow |
| [PrintVis estimating](https://learn.printvis.com/Legacy/Estimation/Estimating/) | Estimate by operations and materials |
| [PrintVis job costing](https://learn.printvis.com/Legacy/JobCosting/JobCosting/) | Compare estimated and actual time, inventory and external purchases |
| [PrintVis item reservations](https://learn.printvis.com/Legacy/Purchasing/ItemRes/) | Distinguish requirement, reservation and consumed material |
| [PrintVis production plan](https://learn.printvis.com/Legacy/Planning/ProductionPlan/) | Plan work against machine capacity |
| [PrintVis tools](https://learn.printvis.com/Pages/pvstools/) | Die/tool master information and packaging parameters |
| [Esko packaging prepress](https://www.esko.com/en/blog/the-complete-overview-of-packaging-prepress) | Structural dieline, colour, proof and approval workflow |
| [GWG packaging specification](https://gwg.org/technical-specifications/gwg-2015-packaging-specification/) | Packaging-specific file requirements |
| [CIP4 workflow resources](https://www.cip4.org/Books_Slides) | JDF/XJDF workflow exchange |

## Pinned skills read and applied
The four directories are absent from this machine's current global skill installation. Exact pinned source instructions were retrieved through the GitHub connector and used directly. No global installation was performed.

| Skill and pinned source | Application in this delivery |
|---|---|
| [deliver-prd](https://github.com/product-on-purpose/pm-skills/blob/1cef1a9eae10017389863d51e289e0ae41e17fcb/skills/deliver-prd/SKILL.md) | PRD structure, metrics with unknown baselines, FR verification map and execution contract |
| [agents-md-creator](https://github.com/chenkumi/agents-md-creator/blob/01fbc14ca1610e163118234177b77ec63405416d/SKILL.md) | Concise AGENTS index, separate open questions, reference existence and token estimator |
| [software-architecture-analysis](https://github.com/magnus919/agent-skills/blob/c545c2b61d4d1e22377bd5db240843a25c1b5764/software-architecture-analysis/SKILL.md) | Observed/proposed/unknown evidence classification for the independent ERP prototype; full codebase reverse engineering is outside scope |
| [design-system-doc](https://github.com/qa-aman/claude-skills/blob/72ef27fe4fe791363be7c811a16c25ffaa6ea9c0/skills/by-role/designer/design-system-doc/SKILL.md) | Component anatomy, current tokens, states, examples and accessibility limits |

Additional skill references read: deliver-prd references/TEMPLATE.md; agents-md-creator references/writing-framework.md and scripts/estimate_tokens.py. Architecture analysis is scoped to the current frontend, local API and SQLite evidence and their independent data boundaries. Authoring skills do not imply a business-system dependency.

The built-in Sites skill was applied to private site creation, source packaging and publication. No third-party runtime code from these skill repositories is included in the website.

## Runtime primary source
[Node.js v24 SQLite API](https://nodejs.org/docs/latest-v24.x/api/sqlite.html) — built-in DatabaseSync, transactions and SQLite backup mechanisms. Runtime verified locally with Node 24.19.0.
