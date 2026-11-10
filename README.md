# DOCS — Workspace Documentation, Findings & Reference Vault

Centralized documentation, system inspection findings, operational checklists, and cloud/tooling reference guides for the `bubblini-ux` Termux + PRoot multi-container development environment.

---

## Repository Index

### Core Workspace & Audit Docs
- **[`FINDINGS.md`](./FINDINGS.md)** — Repository & system inspection findings across Termux (`$HOME`), PRoot containers (`debian`, `archlinuxarm`, `alpine`), and `bubblini-ux` GitHub repositories.
- **[`TODOS.md`](./TODOS.md)** — Prioritized workspace tasks, agent operational directives, and repository sync checklists.
- **[`ARCHITECTURE.md`](./ARCHITECTURE.md)** — Multi-container workspace architecture (`Termux` host + `proot-distro` environments) and repository topology.
- **[`ROADMAP.md`](./ROADMAP.md)** — Phased roadmap for repository consolidation, automation, and project milestones.

### Cloud & Tooling Reference Guides
- **[`billing.md`](./billing.md)** — GitHub Codespaces billing model, compute/storage quotas, and cost management reference.
- **[`prebuilds.md`](./prebuilds.md)** — GitHub Codespaces prebuilds architecture, workflow concurrency, and `devcontainer.json` lifecycle.
- **Rclone Google Drive Custom Client Guide** — <https://rclone.org/drive/#making-your-own-client> (see [`.env.example`](./.env.example) for environment variable placeholders).

### Repository Governance & Maintenance
- **[`CONTRIBUTING.md`](./CONTRIBUTING.md)** — Branching workflow, PR guidelines, and secret-scanning checks.
- **[`SECURITY.md`](./SECURITY.md)** — Credential hygiene, secret scanning commands, and vulnerability reporting policy.
- **[`CHANGELOG.md`](./CHANGELOG.md)** — Chronological record of documentation updates and repository maintenance.
- **[`CODE_OF_CONDUCT.md`](./CODE_OF_CONDUCT.md)** — Community and contributor standards.
- **[`LICENSE.md`](./LICENSE.md)** — MIT License.

---

## Quick Maintenance Commands

```bash
# 1. Check repository status and sync latest changes
git status
git pull --ff-only

# 2. Scan staged changes for accidental secrets before committing
git diff --cached | grep -nE 'ghp_|github_pat_|api[_-]?key|secret|password|AIza'

# 3. Create a feature branch and open a pull request (branch protection enabled on master)
git checkout -b docs/update-notes
git add -A && git commit -m "docs: update workspace notes"
git push -u origin HEAD
gh pr create --fill
```
