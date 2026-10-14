# PrintFlow agent guide

## Project overview
Thai independent ERP prototype for folding carton and sheet sticker printing. Static HTML/CSS/JavaScript with browser-local fixture data; it has no central business database or external business integration.

## Project structure and entry points
| Feature | Entry |
|---|---|
| Shell and navigation | docs/index.html, docs/app.js |
| Pricing, materials and transitions | docs/core.js |
| Components and responsive layout | docs/style.css |
| Business checks | tests/core.test.cjs |
| Publication configuration | GitHub Pages: main /docs |

## Baseline setup
Node.js 18+ for tooling. No package install or compilation. Serve docs/ through any local HTTP static server. Run `node --test tests/core.test.cjs` and `node --check docs/app.js` after behavior changes.

## Top-level principles
- Keep Thai UI and carton-specific specifications. <!-- user-specified -->
- Use the authoring skill sources in SOURCES.md as development tools; the ERP architecture is independent of every other business system. <!-- user-specified -->
- Use fixtures only until a separately verified business integration exists. Preserve units: pieces for product, sheets for paper, THB for price.
- Browser-local data is a prototype tradeoff, never multi-user inventory authority. Production authorization belongs on the server.
- Separate reservation from consumption. Refuse negative stock, repeated receipt and unapproved production starts.
- Keep credentials outside source, archives and logs. Preserve the GitHub repository identity and Pages source when publishing.
- Verify the calculator and inventory invariants with the focused tests. Use semantic labels, keyboard focus and Thai messages explaining corrective action.

## Reference index
- [PRD.md](PRD.md): scope, acceptance and handoff contract; read before changing behavior.
- [ARCHITECTURE.md](ARCHITECTURE.md): actual prototype boundaries and proposed independent ERP; read before integration changes.
- [DESIGN_SYSTEM.md](DESIGN_SYSTEM.md): tokens and component states; read before UI changes.
- [SOURCES.md](SOURCES.md): primary research and pinned skill sources; read when updating assumptions.
- [AGENTS_OPEN_QUESTIONS.md](AGENTS_OPEN_QUESTIONS.md): unresolved business decisions; read before production planning.
