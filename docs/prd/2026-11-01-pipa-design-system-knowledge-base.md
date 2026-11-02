# [APPROVED] PRD: Bootstrap the canonical pipa-design-system knowledge base

**Status:** Approved
**Active phase:** KB created; repository pointers and remote discovery validation
**Last transition:** 2026-11-01 (approved by /epic atlas-v2; independent audit default adopted)
**Ticket:** [pipa-design-system#2](https://github.com/Sapien-Technologies/pipa-design-system/issues/2)
**Audit:** [open questions](audits/2026-11-01-pipa-design-system-knowledge-base-open-questions.md)
**Predictions:** [independent research](audits/2026-11-01-pipa-design-system-knowledge-base-predictions.md)

## Problem and evidence
The tokens package has no KB; #2 holds the orb-token story (#3). Its real documentation is `README.md`, `AGENTS.md`, `CLAUDE.md`, `docs/PROJECT.md`, `tokens.css`, `theme-bridge.css`, `package.json` and `docs/reviews/2026-08-30-pr1-pipa-atlas-operations-hub.md`. The package exports two CSS files with no build/test script. README's blanket dark-definition wording differs from AGENTS' deliberate inherited-token semantics.

## Fix
Create the planned canonical skill in the sibling Skills repository at `pipa-design-system-kb/SKILL.md`, with matching YAML name/description, routed references and indexed decisions. Document token tiers, explicit theme selection, typed color/gradient/shadow consumption, git-ref pinning, package exports, update verification and the pipa-web S21 non-adoption guard. Ground claims in the target checkout; document inherited dark values rather than inventing remaps. Preserve the two-file package and every existing hard rule.

Glen's global instruction makes Skills the source of truth; follow the existing `Skills/atlas-mobile-kb` and `atlas-mobile/docs/PROJECT.md` pattern. Repo `docs/PROJECT.md` and agent instructions point to the canonical KB; README retains quick-start/package entry information and routes detailed explanation there. Do not create a second router or copied KB under this repo's `.claude/skills/`. Runtime links are machine-local. OQ001 records how the epic and chain discover the canonical location.

## Acceptance
| ID | Check | Status |
|---|---|---|
| FR001 | Canonical KB in Skills has routed references and decision index; current code and planned orb work are explicitly distinguished | Open |
| FR002 | Repo pointers resolve to the canonical KB, hard rules remain intact, and no source CSS/package behavior changes | Open |
| FR003 | Run `bash ~/development/Skills/skill-sync/scripts/sync.sh push pipa-design-system-kb` and `status`; expected laptop and mini runtime discovery is verified without committing absolute-path links | Open |
| FR004 | KB lint passes with the explicit canonical `--kb` path; explain cross-repo path checks; set the epic KB path to `../Skills/pipa-design-system-kb` relative to its checkout after the KB exists; chain preflight records the resolved canonical `kb_path`, never a fabricated local copy | Open |
| FR005 | Commit and push Skills changes; land both Skills and repo documentation PRs before closing #2 or releasing #3; no merge is inferred from this PRD | Open |

## Test
Run the canonical KB linter against this repo with `--kb ../Skills/pipa-design-system-kb`; verify all links, named commands and package exports by inspection, then verify runtime symlink resolution on the laptop and mini. No application test suite exists in this package; do not claim `npm test` passed. `git diff --check` must pass in both repos.

## Scope and rollback
Documentation and skill registration only. No orb implementation, component library, dependency change, consumer migration, mobile or deployment work. Revert the documentation commits together and retain #2 as open if discovery fails; never remove unrelated runtime links or replace another skill.

## Bootstrap implementation evidence

Canonical KB created in [Skills commit fe1671d](https://github.com/Sapien-Technologies/Skills/commit/fe1671d). Local KB lint reports zero errors/checks and skill-sync reports parity. README, PROJECT and agent instructions now point to the canonical router in this docs PR. Runtime source is unchanged. Issue #2 remains open until the pointer PR merges and mini discovery is verified.
