# batch-order-processing — Agent Instructions (template)

This file extends the org-level `AGENTS.md`. Org rules apply unless
explicitly overridden here.

## Repo-Specific Rules
- Money is always in integer cents.
- Use `EncryptionService` for any new PII field.
- Schedule changes require runbook update + on-call notification.
- Default chunk size is 500.

## Skills to Prefer
- `.claude/skills/batch-job-scaffold/`
- `.claude/skills/perf-review/`
