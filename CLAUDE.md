# CLAUDE.md — pipa-design-system

`README.md` is the single source of truth for this repo (consumption contract, change process, the pipa-web non-adoption guard). Read it before any change.

Hard rules:
- `tokens.css` is the only home of raw color values; every token must be defined for both themes.
- A new Tier-2 color token needs a matching `theme-bridge.css` line (or consumers use `bg-(--token)`).
- Do NOT wire this package into pipa-web before the S21 cutover completes — its gates point at local copies.
- Changes merge via PR (`/pr-creation` + `/pr-review-cycle`); push-on-commit applies.
