# Repository & System Inspection Findings (`FINDINGS.md`)

_Generated: 2026-11-09 | See also: [TODOS.md](./TODOS.md)_

## 1. Summary of Findings

1. **GitHub Repositories (`bubblini-ux`)**:
   - **13 total remote repositories** listed under `bubblini-ux`.
   - **4 populated repositories**:
     - `Roman` (`~/gh/repo/Roman`): Three.js + React 19 + Vite + Gemini API 3D Colosseum game (*Colosseum: Arena of the Empire*).
     - `war-chest` (`~/gh/repo/war-chest`): Structured Markdown vault for WWII collector weapons compliance, client discovery, cataloging, and website planning.
     - `today-i-learned` (`~/today-i-learned`): Matrix-themed Jekyll blog with automated GitHub Pages deployment, JSON card API (`_data/cards.json`), and agent workflow prompts (`AGENTS.md`).
     - `bubblini-ux` (`~/gh/repo/bubblini-ux`): Contains 39 untracked 0-byte Markdown placeholder files in the working tree (`README.md`, `INBOX.md`, `VAULT.md`, etc.) plus 5 malformed filenames (`ARCHIVE,`, `BACKUPS,`, `TEMPLATES,`, `THANKS}.md`, `VAULT`) from a shell brace-expansion typo.
   - **9 empty remote repositories**:
     - `dotfiles` (empty on GitHub, **but has committed files locally inside Arch Linux** at `/root/dotfiles`: `.bashrc`, `.gitconfig`, `.gitignore`, `install.sh`).
     - `ai-studio`, `chat-history`, `goodwill`, `harley`, `petey`, `pitbulls`, `redteam`, `trap`.

2. **Termux `$HOME` Workspace**:
   - `~/today-i-learned`: Active working clone of `bubblini-ux/today-i-learned` with `AGENTS.md` and `cards.json`.
   - `~/business/IDEAS.md`: Local Git repository with initial app shopping note (`#2026110 apps shopping`).
   - `~/billing.md` & `~/prebuilds.md`: Saved documentation on GitHub Codespaces billing quotas and prebuild workflows.
   - `~/dojo`: C++20 practice binaries and source files (`hello.cpp`, `hello.2.cpp`).

3. **PRoot Containers (`proot-distro`)**:
   - **Debian (`deb`)**: `agy` (`v1.5.3`) installed in `/root/.local/bin/agy`. Previously failing with `x509: certificate signed by unknown authority` and missing OAuth token; resolved by installing `ca-certificates` + `openssl` and copying `antigravity-oauth-token` and `settings.json` to `/root/.gemini/antigravity-cli/`.
   - **Arch Linux ARM (`arc`)**: Contains `claude` CLI in `/root/.local/bin/claude`, committed `dotfiles` in `/root/dotfiles`, and local directories `/root/daily` (`checklist`, `routines`, `workflows`), `/root/personas` (`block_chain`, `clark_kent`, `jordan_belfort`, `junior_dev`, `lord_vader`, `morpheus`, `white_hat`, `yoda`), `/root/rust-engineer`, `/root/security-officer-training`, `/root/stunt-man-training`, and `/root/motorcycle-mechanics-school`.
   - **Alpine (`alp`)**: Installed and available.
