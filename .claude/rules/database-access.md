---
applyTo: "**"
---

# Database Access Rules

- All schema changes go through migration scripts. No ad-hoc DDL in production.
- Reads use the read replica when available; writes go to primary.
- Transactions are short — long-running transactions block other traffic.
- Use cursor / streaming reads for tables > 100K rows.
- Every UPDATE / DELETE must have a WHERE clause. Reject any agent-generated
  statement that doesn’t.
- Connection pools sized via formula: `(core_count * 2) + disk_spindles`.
- For new indexes, attach EXPLAIN before/after to the PR.
