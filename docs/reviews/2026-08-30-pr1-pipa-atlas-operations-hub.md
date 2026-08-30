# Review Record: PR #1 — feat: canonical pipa tokens package (tokens.css + Tailwind v4 theme bridge)

**PR:** https://github.com/Sapien-Technologies/pipa-design-system/pull/1
**Reviewed:** 2026-08-30
**PRD:** pipa-atlas `docs/prd/2026-08-30-pipa-atlas-operations-hub.md` (Group A, FR001–FR003)
**Verdict:** ✅ at review — 0 BLOCKER / 1 IMPROVEMENT / 3 NIT; all 4 fixed
**Resolution commits:** `2bb03c5`, `74d2289`
**Merged:** 2026-08-30, squash merge `5698ee6` (Glen approved in-session)

## Reviewer verification highlights

Both verbatim-extraction claims verified byte-for-byte against `pipa-web@origin/main` (tokens.css 434/434 lines; theme-bridge = globals.css lines 6–92 incl. leading blank line). Zero raw colors outside tokens.css; zero PRD IDs in shipped files; non-adoption guard present in README + both agent docs; scratch-project git-dep install ships exactly 4 files with both exports resolving.

## Findings and resolutions

### 1. [IMPROVEMENT] README.md:7 — claimed a "system-preference guard" that does not exist
- **Issue:** tokens.css has no `prefers-color-scheme` media query (nor does the pipa-web source); dark activates only via `data-theme="dark"`. First consumers would expect OS dark mode to work with no wiring.
- **Verdict:** VALID
- **Resolution:** fixed in `2bb03c5` — README now states there is no system-preference query and that consumers own theme switching (ThemeProvider pattern or light-only). Agent docs' "both themes" rule aligned to the real remap semantics in `74d2289`.

### 2. [NIT] README.md:8 — "every Tier-2 color token exposed" overbroad
- **Verdict:** VALID (~30 color-bearing tokens unbridged)
- **Resolution:** fixed in `2bb03c5` — "commonly-consumed" wording + explicit unbridged families with the `var()`/arbitrary-form path.

### 3. [NIT] theme-bridge.css:10 — verbatim comments reference pipa-web-internal paths
- **Verdict:** VALID observation; files deliberately unchanged (byte-parity is the extraction guarantee)
- **Resolution:** fixed in `2bb03c5` — README lineage note documents the internal references and why they stay.

### 4. [NIT] package.json:5 — no `"private": true` on an UNLICENSED unscoped name
- **Verdict:** VALID
- **Resolution:** fixed in `2bb03c5` — `"private": true` added; git-dep installs unaffected.
