# Contributing to DOCS

Thank you for maintaining and updating the `bubblini-ux/DOCS` documentation vault.

## Branch Protection & Workflow

The `master` branch is protected against force-pushes and branch deletion. Please follow these steps when proposing updates:

1. **Sync the latest changes**:
   ```bash
   git checkout master
   git pull --ff-only
   ```
2. **Create a descriptive branch**:
   ```bash
   git checkout -b docs/<topic-slug>
   ```
3. **Run the secret check before committing**:
   ```bash
   git diff --cached | grep -nE 'ghp_|github_pat_|api[_-]?key|secret|password|AIza'
   ```
4. **Commit with a clear message**:
   - `docs: ...` for documentation additions or edits
   - `chore: ...` for repo configuration or maintenance
5. **Push and open a Pull Request**:
   ```bash
   git push -u origin HEAD
   gh pr create --fill
   ```

## Formatting Guidelines

- Follow `.editorconfig` (UTF-8, LF line endings, 2-space indentation).
- Use relative links (`./TODOS.md`, `./FINDINGS.md`) when linking between repository files so links work both locally and on GitHub.
- Keep `CHANGELOG.md` updated when making structural additions.
