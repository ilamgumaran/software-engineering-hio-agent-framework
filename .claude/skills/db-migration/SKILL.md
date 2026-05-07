---
description: >
  Generates reversible PostgreSQL migrations with explicit lock and index
  impact analysis. Use when asked to add/alter columns, indexes, or tables.
---

## DB Migration

### Requirements
- Migration script is reversible: paired up + down (or `safe-drop` plan).
- No locking DDL on tables > 1M rows without explicit human review.
- Index changes include EXPLAIN analysis (before/after) attached to PR.
- Data backfill is a SEPARATE migration from the schema change.
- Online schema changes (`pg_repack`, `lock_timeout`, `CONCURRENTLY`) preferred
  for any change touching hot tables.

### Output
- `db/migration/V<version>__<description>.sql` (Flyway-style).
- `db/migration/V<version>__<description>_down.sql` if not auto-reversible.
- PR description includes: row count estimate, expected lock duration,
  rollback plan, post-deploy verification query.

### Model Tier
Default: Opus (high blast radius).
