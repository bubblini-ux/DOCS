# Workspace Findings, Agent Directives & TODOs (`TODOS.md`)

_Last updated: 2026-11-09 | Account: `bubblini-ux` | See also: [FINDINGS.md](./FINDINGS.md)_

---

## 1. Repository & Environment Inspection Findings

### A. Container & CLI Environments
- **Termux Host (`/data/data/com.termux/files/home`)**:
  - `agy` (`v1.5.3`) installed at `~/.local/bin/agy` and authenticated via `~/.gemini/antigravity-cli/antigravity-oauth-token`.
  - GitHub CLI (`gh`) authenticated for `bubblini-ux`.
  - Reference docs saved in `$HOME`: `~/billing.md` (GitHub Codespaces billing/quotas) and `~/prebuilds.md` (GitHub Codespaces prebuilds).
- **Debian Container (`proot-distro login debian` / alias `deb`)**:
  - `agy` (`v1.5.3`) installed at `/root/.local/bin/agy`.
  - **Fixed**: Installed `ca-certificates` and `openssl` to resolve `x509: certificate signed by unknown authority` TLS errors, and synced `antigravity-oauth-token` + `settings.json` into `/root/.gemini/antigravity-cli/`.
- **Arch Linux ARM Container (`proot-distro login archlinuxarm` / alias `arc`)**:
  - Contains Claude Code (`/root/.local/bin/claude`) and local unpushed working directories under `/root/` (`dotfiles`, `daily`, `personas`, `motorcycle-mechanics-school`, `rust-engineer`, `security-officer-training`, `stunt-man-training`, etc.).
- **Alpine Container (`proot-distro login alpine` / alias `alp`)**:
  - Installed and available via `proot-distro`.

---

### B. GitHub Repositories Audit (`~/gh/repo/` & `$HOME`)

| Repository | Location(s) | Status | Findings |
| :--- | :--- | :--- | :--- |
| **`Roman`** | `~/gh/repo/Roman` | **Populated** | *Colosseum: Arena of the Empire* — 3D Roman Colosseum combat game built with React 19, Three.js, Vite, Tailwind v4, and `@google/genai`. |
| **`war-chest`** | `~/gh/repo/war-chest`, `arc:/root/war-chest` | **Populated** | Obsidian-style working vault for rare WWII weapons collector business (`Client`, `Compliance`, `Inventory`, `Marketing`, `Operations`, `Templates`, `Website`, `Home.md`). |
| **`today-i-learned`** | `~/today-i-learned`, `arc:/root/today-i-learned` | **Populated** | Matrix-themed Jekyll TIL blog deployed to GitHub Pages (`AGENTS.md`, `cards.json`, `_data/cards.json`, `_posts/`, `.github/workflows/jekyll-gh-pages.yml`). Note: removed from `~/gh/repo/` after moving/consolidating to `~/today-i-learned`. |
| **`bubblini-ux`** | `~/gh/repo/bubblini-ux` | **Scaffolded (Untracked)** | Contains 39 zero-byte index/topic `.md` files (`README.md`, `INBOX.md`, `VAULT.md`, `ROMAN.md`, `WAR_CHEST.md`, etc.) plus a few typo filenames with trailing commas/braces (`ARCHIVE,`, `BACKUPS,`, `TEMPLATES,`, `THANKS}.md`) that need cleanup before committing. |
| **`dotfiles`** | `~/gh/repo/dotfiles`, `arc:/root/dotfiles` | **Empty on Remote / Local in Arch** | Remote repo is empty, but `arc:/root/dotfiles` has a local commit (`.bashrc`, `.gitconfig`, `.gitignore`, `install.sh`) ready to push. |
| **`ai-studio`** | `~/gh/repo/ai-studio`, `~/ai-studio` | **Empty** | Initialized `.git` repo; ready for AI Studio exports/projects (or linking with `Roman`). |
| **`goodwill`** | `~/gh/repo/goodwill`, `arc:/root/goodwill` | **Empty** | Empty repository on GitHub and in Arch `/root/goodwill`. |
| **`trap`** | `~/gh/repo/trap`, `arc:/root/trap` | **Empty** | Empty repository on GitHub and in Arch `/root/trap`. |
| **`petey`** | `~/gh/repo/petey`, `arc:/root/petey` | **Empty** | Empty repository on GitHub and in Arch `/root/petey`. |
| **`harley`** | `~/gh/repo/harley`, `arc:/root/harley` | **Empty** | Empty repository on GitHub and in Arch `/root/harley`. |
| **`pitbulls`** | `~/gh/repo/pitbulls`, `arc:/root/pitbulls` | **Empty** | Empty repository on GitHub and in Arch `/root/pitbulls`. |
| **`redteam`** | `~/gh/repo/redteam`, `arc:/root/redteam` | **Empty** | Empty repository on GitHub and in Arch `/root/redteam`. |
| **`chat-history`** | `~/gh/repo/chat-history`, `arc:/root/chat-history` | **Empty** | Empty repository on GitHub and in Arch `/root/chat-history`. |
| **`business`** (local) | `~/business` | **Local Git Repo** | Contains `IDEAS.md` (`#2026110 apps shopping`). No remote configured yet. |

---

## 2. Directives for Next Session / Autonomous Agents

1. **Never Commit Secrets**:
   - Before staging or pushing in any repo, scan staged diffs:
     ```bash
     git diff --cached | grep -nE 'ghp_|github_pat_|api[_-]?key|secret|password|AIza'
     ```
   - Keep `arc:/root/.secrets`, `arc:/root/.env`, and `~/.gemini/antigravity-cli/antigravity-oauth-token` strictly out of version control.
2. **Respect Branch Protection on `today-i-learned`**:
   - Always work on a feature branch (`feat/<slug>` or `til/<slug>`) in `~/today-i-learned` and open a PR via `gh pr create --fill` per `~/today-i-learned/AGENTS.md`.
3. **Cross-Container Awareness**:
   - Use `proot-distro login debian -- <cmd>` (or alias `deb`) for Debian tasks (`agy` is pre-authenticated there).
   - Use `proot-distro login archlinuxarm -- <cmd>` (or alias `arc`) when syncing local work from `/root/` (`dotfiles`, `daily`, `personas`, training dirs).
4. **Keep `~/gh/repo/` as the Canonical Inspection Mirror**:
   - Before starting work on any `bubblini-ux` repo, run `git status` and `git pull --ff-only` inside `~/gh/repo/<repo>`.

---

## 3. Prioritized TODOs Checklist

### Priority 1 — Cleanup & Sync Existing Local Work
- [ ] **`bubblini-ux` profile repo (`~/gh/repo/bubblini-ux`)**:
  - [ ] Remove accidental typo filenames created during brace expansion: `ARCHIVE,`, `BACKUPS,`, `TEMPLATES,`, `THANKS}.md`, and `VAULT` (non-`.md`).
  - [ ] Populate `README.md` and `INBOX.md` with an index of all `bubblini-ux` repositories, commit, and push to `origin/main`.
- [ ] **`dotfiles` (`arc:/root/dotfiles` -> `~/gh/repo/dotfiles`)**:
  - [ ] Push the existing commit in `arc:/root/dotfiles` (`.bashrc`, `.gitconfig`, `.gitignore`, `install.sh`) to `https://github.com/bubblini-ux/dotfiles` and include Termux `.bashrc` aliases (`deb`, `arc`, `alp`).
- [ ] **Arch `/root/` Non-Git Directories**:
  - [ ] Decide whether to version-control `arc:/root/daily`, `arc:/root/personas`, `arc:/root/rust-engineer`, `arc:/root/security-officer-training`, `arc:/root/stunt-man-training`, and `arc:/root/motorcycle-mechanics-school` (either inside `bubblini-ux` vault docs or dedicated repos).

### Priority 2 — Active Project Repositories
- [ ] **`today-i-learned` (`~/today-i-learned`)**:
  - [ ] Execute the feature prompts in `~/today-i-learned/AGENTS.md`:
    - [ ] Prompt 1: Add new TIL post for fixing Debian `proot-distro` `agy` TLS `ca-certificates` & OAuth setup.
    - [ ] Prompt 2: Add interactive tag filtering & `$ grep -i` search bar (`feat/tag-filter-search`).
    - [ ] Prompt 3: Add `[copy]` buttons to code blocks (`feat/code-copy`).
    - [ ] Prompt 4: Add CI validation for `_data/cards.json` & secret scanning (`ci/validate-cards-and-secrets`).
    - [ ] Prompt 5: Add RSS/Atom (`feed.xml`) & JSON Feed (`feed.json`) (`feat/syndication-feeds`).
- [ ] **`Roman` (`~/gh/repo/Roman`)**:
  - [ ] Configure `.env.local` from `.env.example` (`GEMINI_API_KEY`) and test build (`bun install && bun run build`).
  - [ ] Add a comprehensive `README.md` documenting architecture, controls, and deployment.
- [ ] **`war-chest` (`~/gh/repo/war-chest`)**:
  - [ ] Resolve `"To confirm"` items in `Client/`, `Compliance/`, and `Operations/`.

### Priority 3 — Initialize Empty Repositories
- [ ] Add initial `README.md` + `.gitignore` and push `main` branch for empty repos:
  - [ ] `ai-studio`
  - [ ] `chat-history`
  - [ ] `goodwill`
  - [ ] `harley`
  - [ ] `petey`
  - [ ] `pitbulls`
  - [ ] `redteam`
  - [ ] `trap`
- [ ] **`~/business`**:
  - [ ] Merge `~/business/IDEAS.md` into `~/gh/repo/bubblini-ux/BUSINESS.md` or create a remote GitHub repo for `business`.
