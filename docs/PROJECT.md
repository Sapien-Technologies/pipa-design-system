# pipa-design-system — Project Documentation

**Version:** 0.1.0
**Framework:** none (plain CSS package, git-dep installable)
**Architecture:** two files — token definitions + Tailwind v4 bridge

## Quick Start

```bash
npm install github:Sapien-Technologies/pipa-design-system
```

Wiring and rules: see the repo `README.md` (the authoritative doc).

## Project Structure

- `tokens.css` — two-tier tokens, light + dark
- `theme-bridge.css` — Tailwind v4 `@theme inline` color bridge
- `docs/changelog/` — per-day change entries

## Documentation Index

| Component | Documentation | Status |
|---|---|---|
| Tokens + bridge (consumption contract) | [README.md](../README.md) | ✅ Documented |
| Agent reference | [AGENTS.md](../AGENTS.md) / [CLAUDE.md](../CLAUDE.md) | ✅ Documented |
