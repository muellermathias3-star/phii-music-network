# Security and Secret Hygiene

The public repo must never become a storage place for secrets or private raw
state. Treat every commit as potentially public and permanent.

## Never Commit

- `.env` files
- API keys, tokens, passwords, cookies, recovery codes, private keys
- Local databases
- Raw logs
- Raw memory exports
- Private conversations
- Unreleased restricted details
- Runtime bridge data
- Dependency folders and generated outputs

## Required Before Commit

```bash
git status --short
git diff --stat
git diff --cached --stat
git diff --cached
```

Stage only reviewed files. Avoid broad staging of the workspace.

## GitHub Rules

- Use PRs for public repo updates.
- Keep issue bodies public-safe.
- Do not paste credentials into issues, comments, commits, or PRs.
- Security incidents should be summarized abstractly unless a private channel is
  explicitly required.

## Useful Checks

```bash
git check-ignore -v <path>
gh pr diff <number> --repo muellermathias3-star/phii-music-network --name-only
```

## Review Checklist

- [ ] Only intended files are staged
- [ ] No secret-like values are visible in diff
- [ ] No raw memory/network/log data is included
- [ ] Public repo boundaries are respected
- [ ] PR description states safety scope

Tracks: #7
