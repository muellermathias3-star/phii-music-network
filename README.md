# PHII Music Network

Public, reviewable coordination repository for the PHII Multi-Agent Network.

This repo is the clean GitHub layer for safe operating docs, workflow notes,
sanitized reports, issue tracking, and GitHub-based review flow. It is not the
raw runtime workspace.

## What Belongs Here

- High-level operating docs
- Sanitized workflow descriptions
- Public-safe checklists and templates
- GitHub Issues for tracked network work
- PRs for reviewed documentation and automation changes

## What Does Not Belong Here

- Secrets, tokens, passwords, cookies, private keys, or `.env` files
- Raw memory exports, private conversations, local databases, or runtime logs
- Unreleased release details, confidential pitch details, or private agreements
- Local dependency folders, generated exports, or bridge runtime state

The `.gitignore` is intentionally conservative. Sensitive working areas such as
`memory/`, `network/`, logs, bridge runtime data, local databases, and generated
outputs stay local unless a specific file is reviewed, sanitized, and
deliberately allowlisted.

## Current Workflow

1. Use GitHub Issues to track network work.
2. Stage only reviewed files.
3. Check staged diffs before every commit.
4. Use pull requests for public repo updates.
5. Keep operational secrets and private raw data out of GitHub.

See [docs/github-commit-flow.md](docs/github-commit-flow.md) for the commit
flow.

## Initial Areas

- MOLTEBOOK workflow
- Music distribution pipeline
- Security and secret hygiene
- Memory consolidation and audit rules
- PHII content tone and editorial rules
