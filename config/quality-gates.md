# Quality Gates — What Agents Must Verify

## Before Proposing Any Change
- [ ] Build compiles without errors
- [ ] All existing tests pass
- [ ] New code has tests (unit at minimum, integration if IO-bound)
- [ ] No new linter warnings introduced
- [ ] No secrets or credentials in the diff

## Additional Gates for Batch Jobs
- [ ] Job is idempotent — rerunning produces same result
- [ ] Checkpoint/restart logic is present for jobs > 10 min
- [ ] Failure notifications are configured (SNS/PagerDuty)
- [ ] Runbook in `docs/` is updated with new/changed behavior
- [ ] Backfill strategy documented if processing historical data

## Additional Gates for APIs
- [ ] OpenAPI spec updated if contract changed
- [ ] Breaking changes are versioned (v1 → v2), not modified in place
- [ ] Rate limiting and circuit breaker config reviewed
- [ ] Response times validated against SLA (p99 < 500ms default)
- [ ] Error responses follow RFC 7807

## Additional Gates for Database Changes
- [ ] Migration script is reversible (up + down)
- [ ] No locking DDL on tables > 1M rows without review
- [ ] Index impact analyzed (explain plan attached or described)
- [ ] Data backfill is separate from schema migration
