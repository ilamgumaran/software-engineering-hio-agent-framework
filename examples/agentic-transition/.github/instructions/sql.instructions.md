---
applyTo: "**/*.sql"
---

# SQL Conventions

- PostgreSQL 16 syntax.
- Use explicit column lists. Never `SELECT *` in production code.
- Always include `WHERE` clauses on `UPDATE` / `DELETE`.
- Prefer CTEs over deeply nested subqueries.
- All schema changes go through migration scripts under `db/migration/`.
- For migrations follow `.claude/skills/db-migration/SKILL.md`:
  reversible (up + down), no locking DDL on >1M-row tables without review,
  attach EXPLAIN plan when adding indexes.
