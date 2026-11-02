# [APPROVED] PRD: Publish the existing orb tokens from pipa-design-system

**Status:** Approved
**Review record:** [PR #4 review](../reviews/2026-11-01-pr4-orb-tokens.md)
**Active phase:** Implemented and validated; review/merge pending
**Last transition:** 2026-11-01 (approved by /epic atlas-v2; independent audit default adopted)
**Ticket:** [pipa-design-system#3](https://github.com/Sapien-Technologies/pipa-design-system/issues/3)
**Epic:** atlas-v2 phase 1
**Depends on:** [KB bootstrap #2](2026-11-01-pipa-design-system-knowledge-base.md), canonical KB created and discoverable; user authorized completing tokens with the pointer docs in the same PR
**Audit:** [open questions](audits/2026-11-01-orb-tokens-open-questions.md)
**Predictions:** [independent research](audits/2026-11-01-orb-tokens-predictions.md)

## Overview and confirmed scope
Promote the fourteen existing orb aliases from pipa-app-official into the canonical CSS package so Atlas web can consume the approved visual tokens without local raw colors. This is an additive tokens change, not a new component or visual redesign. The shared component-library hold remains in force. Mobile setup and initial deployment belong to other agents and are not touched.

## Context pack
Sibling-repo paths below identify inspected evidence, not files this story changes. The package baseline is `a3ef894`; the source file has no local edits at the cited revision.

| Source | What it establishes |
|---|---|
| `README.md` | Two CSS exports, git dependency consumption, import order and pipa-web non-adoption guard |
| `AGENTS.md` and `CLAUDE.md` | Raw colors belong in tokens.css; inherited theme values may be deliberate; no premature pipa-web adoption |
| `package.json` | Private package, only tokens.css and theme-bridge.css in files/exports, no build scripts |
| `tokens.css` | Tier-1 ramps and Tier-2 aliases, root defaults and explicit data-theme dark overrides; no orb aliases yet |
| `theme-bridge.css` | Tailwind inline color bridge; shadow/font types are not color aliases |
| `docs/reviews/2026-08-30-pr1-pipa-atlas-operations-hub.md` | Review record for the original package extraction |
| `pipa-app-official/src/Styles/tokens.css` at `83dfc1bdd4a6169513ec5166c99bef28de9c64a5`, lines 447–470 | Exact fourteen aliases and their values; only orb-core changes in dark |
| `pipa-app-official/src/Styles/globals.css` at the same commit, lines 105–108 | Existing consumer bridges only orb-ring-cyan |
| `pipa-app-official/src/Components/Orb/Orb.module.css` and `Orb.tsx` at the same commit | Actual property types and idle/listening/thinking/speaking usage; reduced motion is consumer CSS |
| `atlas/docs/design-system/generators/board/chat.py` at `e55361f7ecaee8307a19ee74a5b0d0f1484289e9`, ORB_TOKENS | Prototype embeds matching source values; that copy is not a new design specification |
| `atlas-web/docs/prd/2026-10-30-atlas-web-board-voice.md`, token dependency and Orb sections | Board voice consumes these tokens through packages/design after this story lands |
| `Skills/epics/atlas-v2.json`, pds-orb-tokens | Phase-one dependency of Board voice, held by the missing KB |

The canonical Skills/pipa-design-system-kb now exists and is discoverable on laptop and mini. This implementation was reconciled with it; Glen authorized completing the design-system work using pipa-app-official. Pointer docs and tokens ship together in PR #4. No dependency on mobile setup, deployment or the Board API is introduced.

## Token contract
Copy values exactly from the pinned pipa-app-official source, preserving gradients, alpha values, shadow lists and referenced Tier-1 ramps. Record that source commit beside the new block and in the changelog. Do not resolve aliases into hard-coded approximations or add a new palette.

| Tokens | CSS value type | Theme behavior |
|---|---|---|
| `--orb-body`, `--orb-body-listening`, `--orb-body-thinking` | Background images/gradients | Root definitions inherited in dark |
| `--orb-glow-idle`, `--orb-glow-listening-min`, `--orb-glow-listening-max`, `--orb-glow-speaking`, `--orb-glow-thinking` | Box-shadow values | Root definitions inherited in dark |
| `--orb-ring-cyan`, `--orb-ring-cyan-soft`, `--orb-wave-purple`, `--orb-wave-cyan`, `--orb-dot-amber` | Colors | Root definitions inherited in dark |
| `--orb-core` | Color | Source root value and its distinct dark override |

All fourteen resolve in both themes; this does not mean writing fourteen redundant dark declarations. The source changes only orb-core. Theme switching remains `[data-theme="dark"]`; do not add a system-preference media query or a theme controller.

Adopted OQ001 default (corroborated): add only `--color-orb-ring-cyan: var(--orb-ring-cyan)`, matching the source consumer. The other five plain-color aliases remain directly consumable through CSS variables or arbitrary-property utilities. Gradient bodies and shadow glows must not enter Tailwind's color namespace. Direct CSS consumers continue using `var(--orb-*)`; the package adds no Orb classes, keyframes, component, animation state machine or reduced-motion rules.

## Functional requirements

| ID | Requirement | Status | Observable acceptance |
|---|---|---|---|
| FR001 | Add exactly the fourteen source aliases to tokens.css | Implemented | Declaration-name set and normalized values match the pinned source; no missing/extra orb names or undefined Tier-1 references |
| FR002 | Preserve both-theme semantics | Implemented | Light and dark resolution match source for every alias; only orb-core has the source's dark override; switching back restores root value |
| FR003 | Preserve CSS property types and the bridge decision | Implemented | OQ001 is folded; only selected plain-color aliases get `--color-*` entries, each references its token; no gradient/shadow masquerades as a color |
| FR004 | Keep the existing package contract and non-orb values | Implemented | Existing declarations remain semantically identical, files/exports/import order remain valid, and package archive contains both CSS files |
| FR005 | Publish consumption and provenance documentation | Implemented | KB and changelog name the source commit and resolved bridge policy; consumers are told to pin the new merged commit; no consumer is actually upgraded here |

## Validation and edge cases
- Compare the new orb declaration set and values to `git show 83dfc1bdd4a6169513ec5166c99bef28de9c64a5:src/Styles/tokens.css` in pipa-app-official, not a mutable working-tree file. If that object cannot be resolved, stop validation rather than silently pick a new source.
- Compare pre-existing declarations before/after the change. Reject accidental overrides, duplicate orb declarations within the same selector and unresolved references.
- Use a temporary local fixture that loads this package and consumes the image, shadow and color families in their correct CSS properties. Check light, dark and dark-to-light computed values against the source fixture. No new permanent application/test framework is required.
- Run `npm pack --dry-run` to check exports/package contents and `git diff --check`; this repo has no npm build/test script. Record actual commands/results in the PR rather than claiming a nonexistent suite passed.
- Font rules, semantic contrast decisions and motion behavior remain the consuming component's work. This token promotion does not assert that every possible contrast pairing is accessible or that token existence proves full Orb visual parity.

## Delivery and rollback
The canonical KB is created and validated. Per Glen's instruction to complete the design-system work, the token implementation joins the KB pointers in PR #4; both issues remain open until that PR merges. No deployment or package-registry publication occurs. Consumers pinned to older commits remain unchanged; Board voice updates its own dependency when ready. Revert this additive commit before adoption, or pin affected consumers back through their own reviewed changes after adoption.

## Assumptions and completion
Independent research folded OQ001: only the existing source consumer's orb-ring-cyan receives a named color bridge utility; all fourteen tokens remain available. No exact consumer delivery date or downstream adoption is assumed. The story is complete when the reviewed tokens and documentation are merged and the commit is available to consumers; it does not implement Board voice, mobile, or the shared component library.

## Validation evidence

Exact declaration comparison against the pinned source passed: fourteen unique orb aliases plus one dark override; existing CSS is an unchanged prefix and package.json is unchanged. A temporary Chromium fixture compared all fourteen computed image/shadow/color values in light, dark and light again (42 comparisons), all equal to the pinned desktop source. npm pack --dry-run includes both CSS exports. KB lint and diff whitespace checks pass. No npm test/build scripts exist.
