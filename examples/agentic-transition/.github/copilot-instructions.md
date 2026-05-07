# Copilot Org Instructions — HIO

These instructions are inherited by every repo. Repo-level
`.github/copilot-instructions.md` overrides on conflict.

## Governing Principles
- Quality over quantity. Correctness, tests, and shippability beat raw output volume.
- Reliability and performance of the application are priority. Do not
  introduce latency, flakiness, or non-determinism.
- Cost is managed centrally via `config/model-routing.md` and `config/cost-policy.md`.
  Do not opt-in to higher tiers without need.

## Universal Rules
- Never commit secrets, tokens, or credentials. Use AWS Secrets Manager.
- Every change must include tests.
- Batch jobs must be idempotent. Document retry behavior.
- APIs must return RFC 7807 problem details on errors.
- All database changes go through migration scripts, never ad-hoc DDL.
- Log INFO for business events, WARN for recoverable issues, ERROR for
  failures requiring human attention.
- Do not introduce new dependencies without license-compatibility check.

## Language Conventions
See `AGENTS.md` and the path-scoped files in `.github/instructions/`.

## What Copilot Must NOT Do
- Auto-approve its own suggestions.
- Refactor code outside the scope of the current task.
- Upgrade dependency versions unless the task requires it.
- Generate code that depends on network calls during unit tests.
- Modify CI/CD, IAM, security groups, or network rules without human review.
