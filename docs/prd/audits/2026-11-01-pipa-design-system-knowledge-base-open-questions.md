---
prd: docs/prd/2026-11-01-pipa-design-system-knowledge-base.md
audited: 2026-11-01
status: resolved
---

# Open Questions: pipa-design-system KB bootstrap

PRD: [KB bootstrap](../2026-11-01-pipa-design-system-knowledge-base.md)
Predictions: [independent research](2026-11-01-pipa-design-system-knowledge-base-predictions.md). Corroborated default adopted by /epic; this does not close the KB or implementation issue.

## Audit findings
Verified the absent KB, two-file CSS exports, lack of build/test scripts, current README/agent rules and source theme behavior. Corrected the generic repo-KB template: Glen's explicit global rule requires the canonical skill under Skills, and the existing atlas-mobile-kb follows that pattern. This PRD does not create a duplicate local router or invent new package behavior. The proposed bootstrap spans a Skills change and repo documentation pointers; neither is already implemented.

## OQ001: How does automation discover a centrally owned KB without requiring a copied repo-local skill?

- **Category:** integration
- **State:** folded
- **Spawned by:** Fix and FR003–FR005
- **Why unverifiable:** `Skills/atlas-mobile-kb/SKILL.md` and atlas-mobile's docs use canonical Skills ownership, while `Skills/epics/atlas-mobile-phase1.json` still names a repo-local `.claude/skills/atlas-mobile-kb` KB path. `Skills/feature-chain/scripts/chain.sh` requires a recorded `kb_path` or `kb_story` during preflight but does not itself prove the path resolves on both machines. No pipa-design-system-kb runtime link exists yet.
- **Default for the researcher to assess:** use the canonical named skill via skill-sync and record its resolved machine-local path in preflight; update the epic's KB reference/context so it points at that source. Repo documentation uses a portable GitHub link. Do not commit an absolute symlink or copy the router to satisfy an outdated path convention. If a loader actually requires a compatibility link, validate a machine-local link rather than create a second source.

## Resolution

Canonical Skills ownership, explicit relative epic discovery path and laptop/mini verification adopted. No loader change or duplicate router is assumed.
