# GitHub Commit Flow

This workspace uses `muellermathias3-star/phii-music-network` as the GitHub home for safe, reviewable PHII Multi-Agent Network material.

## Safety Rules

- Never commit secrets, tokens, passwords, cookies, private keys, `.env` files, raw logs, local databases, or unfiltered memory exports.
- Treat `memory/`, `network/`, bridge runtime data, generated exports, and dependency folders as local working state unless a file has been reviewed and deliberately allowlisted.
- Use GitHub noreply email for commits to avoid exposing a private address.

## Standard Flow

1. Inspect changes:
   ```bash
   git status --short
   git diff --stat
   ```
2. Check for sensitive paths before staging:
   ```bash
   git check-ignore -v <path>
   ```
3. Stage only reviewed files:
   ```bash
   git add AGENTS.md SOUL.md TOOLS.md MEMORY.md USER.md IDENTITY.md docs/
   ```
4. Review staged content:
   ```bash
   git diff --cached --stat
   git diff --cached
   ```
5. Commit with a clear message:
   ```bash
   git commit -m "docs: update PHII network operating docs"
   ```
6. Push:
   ```bash
   git push origin main
   ```

## Current Default Remote

```bash
origin  https://github.com/muellermathias3-star/phii-music-network.git
```
