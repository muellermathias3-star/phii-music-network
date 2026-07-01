# Memory and Audit Trail

Memory is operational continuity, not public raw storage. GitHub may contain
sanitized process docs, but not raw memory exports or private workspace state.

## Memory Boundaries

Keep local/private:

- Raw `memory/` content
- Raw `network/` state
- Local databases and snapshots
- Logs and outbox payloads
- Private conversations
- E2/E3 details

Public-safe:

- Abstract process descriptions
- Sanitized templates
- High-level audit rules
- Issue-level tracking without private raw data

## Audit Principles

- Record what changed, who/what triggered it, why it changed, and the source
  category.
- Do not record secrets or raw personal data.
- Use abstraction for security incidents and credential events.
- Keep raw operational logs local unless explicitly sanitized.

## Consolidation Checklist

- [ ] Secrets removed
- [ ] Private raw data removed
- [ ] Embargo level checked
- [ ] Duplicates merged
- [ ] Source noted
- [ ] Audit entry created locally

## GitHub Use

GitHub Issues may track that a memory process exists or needs review. They must
not contain sensitive memory payloads.

Tracks: #8
