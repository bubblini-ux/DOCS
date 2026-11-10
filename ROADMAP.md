# Roadmap (`ROADMAP.md`)

Tracked milestones for the `bubblini-ux` workspace and repository ecosystem. See [`TODOS.md`](./TODOS.md) for granular checklists.

---

## Phase 1 — Repository Hygiene & Documentation Baseline (Current)
- [x] Consolidate system audit (`FINDINGS.md`), task directives (`TODOS.md`), and Codespaces guides (`billing.md`, `prebuilds.md`) into `~/DOCS`.
- [x] Populate all repository governance and configuration files (`README.md`, `ARCHITECTURE.md`, `CONTRIBUTING.md`, `SECURITY.md`, `CHANGELOG.md`, `CODE_OF_CONDUCT.md`, `LICENSE.md`, `.gitignore`, `.gitattributes`, `.editorconfig`, `.env.example`).
- [x] Enable branch protection on `bubblini-ux/DOCS` (`master`).
- [ ] Clean up typo filenames in `~/gh/repo/bubblini-ux` and push initial index.
- [ ] Sync `arc:/root/dotfiles` to `bubblini-ux/dotfiles`.

## Phase 2 — Active Project Enhancements
- [ ] **`today-i-learned`**:
  - Publish TIL post on Debian `proot-distro` TLS (`ca-certificates`) and OAuth setup.
  - Add tag filtering, search bar, code copy buttons, and RSS/JSON feeds.
  - Add GitHub Actions CI for `_data/cards.json` validation and secret scanning.
- [ ] **`Roman`**:
  - Document 3D Colosseum architecture, controls, and Gemini integration in `README.md`.
  - Verify local and production Vite builds.
- [ ] **`war-chest`**:
  - Complete pending compliance and operations checklists.

## Phase 3 — Ecosystem Expansion
- [ ] Version-control Arch Linux `/root/` knowledge vaults (`daily`, `personas`, training directories).
- [ ] Initialize remaining empty repositories (`ai-studio`, `chat-history`, `goodwill`, `harley`, `petey`, `pitbulls`, `redteam`, `trap`) with baseline `README.md`, `.gitignore`, and branch protection rules.
