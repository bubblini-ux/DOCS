# Security Policy (`SECURITY.md`)

## Secret & Credential Hygiene

This repository and all associated `bubblini-ux` workspaces enforce strict secret prevention rules:

1. **Never commit credentials or tokens**:
   - Do not commit `.env`, `.env.local`, `.secrets`, OAuth tokens (`antigravity-oauth-token`), Rclone `rclone.conf`, or Google Cloud `client_secret*.json` files.
   - Use [`.env.example`](./.env.example) strictly for placeholder variable names.

2. **Mandatory Pre-Commit Scan**:
   Run the following check on staged changes prior to committing:
   ```bash
   git diff --cached | grep -nE 'ghp_|github_pat_|api[_-]?key|secret|password|AIza'
   ```
   If any matches are returned, unstage the file immediately (`git restore --staged <file>`) and redact the sensitive value.

3. **Protected Host Paths**:
   Keep the following paths out of all Git repositories:
   - `~/.gemini/antigravity-cli/antigravity-oauth-token`
   - `~/.config/gh/hosts.yml`
   - `~/.config/rclone/rclone.conf`
   - `arc:/root/.secrets` and `arc:/root/.env`

## Reporting a Vulnerability or Leaked Credential

If a credential is ever accidentally committed:
1. Revoke/rotate the affected token or key immediately in the provider console (GitHub, Google Cloud / AI Studio).
2. Remove the secret from Git history (`git filter-repo` or BFG) before pushing.
