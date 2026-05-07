# HIO Organization — Agent Instructions

## Core Rules
- Produce production-ready code. Do not leave TODOs or placeholder logic.
- Every function/method must include error handling appropriate to its context.
- Batch jobs: always implement idempotency. Use checkpoint/restart patterns.
- APIs: validate all inputs. Return RFC 7807 problem details on errors.
- Test coverage minimum: 80% line coverage for new code.

## Language Conventions
- Java: follow Google Java Style. Use records for DTOs. Prefer Optional
  over null returns. Use slf4j for logging.
- Python: follow PEP 8. Use type hints on all function signatures.
  Use structured logging (structlog).
- SQL: use explicit column lists (never SELECT *). Always include
  WHERE clauses on UPDATE/DELETE. Use CTEs over nested subqueries.

## What Not To Do
- Do not auto-approve your own suggestions.
- Do not refactor code outside the scope of the current task.
- Do not upgrade dependency versions unless the task requires it.
- Do not generate code that depends on network calls during unit tests.

## Reference
- Governing principles, model routing, and quality gates: see `transition-playbook.md` and `config/`.
