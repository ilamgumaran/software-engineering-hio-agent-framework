# api-customer-service — Agent Instructions (template)

This file extends the org-level `AGENTS.md`. Org rules apply unless
explicitly overridden here.

## Repo-Specific Rules
- p99 latency budget: 200ms. Any change that risks regression must include
  a load test result in the PR.
- All PII (email, phone, address) is masked in logs.
- New endpoints require OpenAPI + internal API catalog update.
- Cache invalidation is the responsibility of the writer; do not assume
  the reader will refresh.

## Skills to Prefer
- `.claude/skills/api-scaffold/`
- `.claude/skills/perf-review/`
