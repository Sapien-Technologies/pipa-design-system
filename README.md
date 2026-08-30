# pipa-design-system

Canonical home of the pipa design tokens. Two files, no build step:

| File | What it is |
|---|---|
| `tokens.css` | The two-tier token system: Tier-1 raw values and Tier-2 semantic tokens, complete light palette on `:root` plus the dark remap (`[data-theme="dark"]` and the system-preference guard). The **only** place raw color values live. |
| `theme-bridge.css` | The Tailwind v4 `@theme inline` bridge: every Tier-2 **color** token exposed as a token-named utility (`bg-surface-card`, `text-ink-strong`, `border-border-subtle`, …) emitting `var(--…)` at use-point so utilities follow theme switching. Shadows and fonts are deliberately not bridged (their names live in Tailwind's own `--shadow-*` / `--font-*` namespaces); consume those as `var(--shadow-card)` or `shadow-(--shadow-card)`. |

Source of truth lineage: extracted verbatim from `pipa-web` (`styles/tokens.css` and the `@theme` block of `app/globals.css`) on 2026-08-30 under the pipa-atlas PRD.

## Install (git dependency — no registry)

```bash
npm install github:Sapien-Technologies/pipa-design-system
```

Pin a ref for reproducible installs once you depend on a specific state:

```bash
npm install github:Sapien-Technologies/pipa-design-system#<commit-or-tag>
```

## Wiring (Tailwind v4 consumer)

Import order matters — Tailwind first, tokens before the bridge:

```css
/* app/globals.css */
@import 'tailwindcss';
@import 'pipa-design-system/tokens.css';
@import 'pipa-design-system/theme-bridge.css';
```

Non-Tailwind consumers import `tokens.css` alone and reference tokens with `var(--…)`.

## Rules

- **Colors come from tokens only.** Consumers never hardcode color values; a missing token is a change request here, not a local hex.
- **Changes land here first.** Edit token values or add Tier-2 tokens in this repo (a new color token needs a matching `theme-bridge.css` line to get a named utility, or consumers use the arbitrary form `bg-(--token)` which needs none). Consumers then upgrade by bumping the git ref.
- **Both themes always.** Any new token must be defined for light and dark in `tokens.css`; a token defined for one theme only is a bug.

## pipa-web adoption is deliberately deferred

`pipa-web` remains on its local copies (`styles/tokens.css`, `app/globals.css`) until the S21 AWS cutover and legacy retirement complete — its token gates, inline-style ratchet, and check scripts point at local paths, and that repo must stay boring through the cutover QA gate. Until then, changes made here that pipa-web also needs must be mirrored into pipa-web by hand (expected to be rare). After S21, pipa-web adopts this package as a standalone chore and its local copies are deleted. Do not wire this package into pipa-web before that.

Consumers today: `pipa-atlas`. Planned: `pipa-app-official` (desktop modernization token pass), future pipa surfaces.
