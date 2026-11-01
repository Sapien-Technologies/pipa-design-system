---
prd: docs/prd/2026-11-01-orb-tokens.md
audited: 2026-11-01
status: resolved
---

# Open Questions: orb tokens

PRD: [Orb tokens](../2026-11-01-orb-tokens.md)
Predictions: [independent research](2026-11-01-orb-tokens-predictions.md). Corroborated default adopted by /epic; this does not close the KB or implementation issue.

## Audit findings
Verified the fourteen-token name/value block in pipa-app-official at `83dfc1bdd4a6169513ec5166c99bef28de9c64a5` and its matching Atlas prototype block at `e55361f7ecaee8307a19ee74a5b0d0f1484289e9`. Neither inspected source file has local edits. The package baseline `a3ef894` lacks orb tokens. The source consumer actually uses image, shadow and color types, so a generic color bridge for every orb alias would be incorrect.

Corrected README's ambiguous both-theme wording: thirteen aliases inherit their root definitions in dark and only orb-core remaps; do not invent fourteen dark colors. Confirmed that reduced motion and animation classes live in the Orb consumer and do not belong in this tokens-only story. Confirmed that the package has no build/test scripts; validation must not claim those nonexistent commands ran. Source pinning does not authorize editing a consumer, creating the held component library, or bypassing KB issue #2.

## OQ001: Which plain-color orb aliases should get named Tailwind bridge utilities?

- **Category:** scope
- **State:** folded
- **Spawned by:** Token contract bridge default and FR003
- **Why unverifiable:** The current pipa-app-official bridge exposes only orb-ring-cyan, while the package README/AGENTS permit either bridge entries for new color tokens or direct/arbitrary-property consumption. The Board voice PRD requires token consumption but does not enumerate named utility requirements. No source establishes whether all six color aliases need named utilities.
- **Default for the researcher to assess:** add the six plain-color aliases to the existing inline color bridge, preserving variable references and omitting the three gradients and five shadows. This is an additive convenience, not evidence that current consumers already need every named utility. An equally valid narrower choice would bridge only orb-ring-cyan and document direct var consumption for the rest; independent research should select and grade the default.

## Resolution

The proposed six-utility expansion was replaced with the narrower source-compatible orb-ring-cyan bridge. All fourteen token aliases remain in scope.
