---
prd: docs/prd/2026-11-01-orb-tokens.md
open_questions: docs/prd/audits/2026-11-01-orb-tokens-open-questions.md
predicted: 2026-11-01
---

# Predictions: Orb tokens

## OQ001: Which plain-color orb aliases should get named Tailwind bridge utilities?

- **Prediction:** Bridge only --color-orb-ring-cyan: var(--orb-ring-cyan), matching the existing source consumer. Publish all fourteen aliases unchanged; document direct variable or appropriate arbitrary-property consumption for the rest. Keep gradients and shadow lists out of the color namespace. Further utilities can follow a demonstrated consumer need.
- **Confidence:** corroborated
- **Evidence:** pipa-app-official/src/Styles/globals.css:105-108; pipa-app-official/src/Components/Orb/Orb.module.css:38-44,63,84,115-116; README.md:8,35,40 permits unbridged consumption; AGENTS.md:6-7 permits arbitrary-token consumption; atlas-web/docs/prd/2026-10-30-atlas-web-board-voice.md:348 requires the fourteen tokens, not six bridge utilities.
- **Refutation attempt:** Neither the package rules nor the voice PRD requires every color to be bridged. Six aliases are technically permitted, but no evidence found that this promotion needs them. Matching the actual source is the narrower supported choice.
