# pipa-design-system

Canonical pipa CSS tokens and Tailwind v4 bridge. Read the [knowledge base](https://github.com/Sapien-Technologies/Skills/blob/main/pipa-design-system-kb/SKILL.md) for token semantics, theme ownership, consumption and change validation.

## Install

```bash
npm install github:Sapien-Technologies/pipa-design-system#<commit-or-tag>
```

## Tailwind v4 imports

```css
@import 'tailwindcss';
@import 'pipa-design-system/tokens.css';
@import 'pipa-design-system/theme-bridge.css';
```

Non-Tailwind consumers import tokens only. Consumers own theme switching through the root data-theme attribute. Consider light and dark behavior on every change; a token with no dark override intentionally inherits its root value.

**pipa-web adoption remains gated:** do not wire this package into pipa-web until its S21 cutover and legacy retirement gate is cleared. This KB bootstrap does not establish that gate's status.

See [agent rules](AGENTS.md), [PRDs](docs/prd/INDEX.md) and [changelog](docs/changelog/). This package exports CSS only and has no npm test/build scripts.

## Orb tokens

The package includes the fourteen orb aliases from pipa-app-official (source commit `83dfc1bdd4a6169513ec5166c99bef28de9c64a5`). Use body aliases as background images, glow aliases as box shadows, and ring/wave/dot/core aliases as colors. Only orb-core remaps in dark; other values inherit. The named Tailwind bridge is orb-ring-cyan; all aliases are directly consumable as CSS variables. Pin the merged package commit when adopting these additions.
