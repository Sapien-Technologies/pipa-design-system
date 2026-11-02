---
prd: docs/prd/2026-11-01-pipa-design-system-knowledge-base.md
open_questions: docs/prd/audits/2026-11-01-pipa-design-system-knowledge-base-open-questions.md
predicted: 2026-11-01
---

# Predictions: pipa-design-system KB bootstrap

## OQ001: How does automation discover a centrally owned KB without a copied repo-local skill?

- **Prediction:** Keep the sole KB in Skills/pipa-design-system-kb, use skill-sync for runtime links, and set the epic KB reference to ../Skills/pipa-design-system-kb relative to its checkout. Preflight reads and records the resolved canonical path. Verify discovery on both machines before releasing the orb story. No copied router, absolute committed symlink or loader change is required by the inspected implementation.
- **Confidence:** corroborated
- **Evidence:** Glen's global Skills ownership instruction; Skills/atlas-mobile-kb/SKILL.md, Location and maintenance; atlas-mobile/docs/PROJECT.md; Skills/skill-sync/scripts/sync.sh:23-34; Skills/epic/scripts/epic.py:105; Skills/feature-chain/scripts/chain.sh:211-216, which accepts kb_path or the bootstrap's kb_story.
- **Refutation attempt:** Searched for a hard-coded repo-local KB requirement; none in the inspected epic/chain code. The mobile manifest's local KB path conflicts with its central documentation, so it is not a reliable path precedent. Metadata checks do not establish path existence; explicit machine checks remain necessary.
