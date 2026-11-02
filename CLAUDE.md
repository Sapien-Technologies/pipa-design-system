# CLAUDE.md — pipa-design-system

Read the canonical [knowledge base](https://github.com/Sapien-Technologies/Skills/blob/main/pipa-design-system-kb/SKILL.md) before changes. [README.md](README.md) is the short installation guide; the KB owns the detailed contract.

Hard rules:
- `tokens.css` is the only home of raw color values. Every new token must be considered for the dark remap — an unremapped token deliberately renders identically in both themes (the production semantics).
- A new Tier-2 color token needs a matching `theme-bridge.css` line (or consumers use `bg-(--token)`).
- Do NOT wire this package into pipa-web before the S21 cutover completes — its gates point at local copies.
- Changes merge via PR (`/pr-creation` + `/pr-review-cycle`); push-on-commit applies.
