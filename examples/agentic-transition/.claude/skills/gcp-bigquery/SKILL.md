---
description: >
  Designs BigQuery schemas, partitioning, clustering, and queries.
  Use when adding tables, optimizing slot usage, building scheduled
  transformations, or designing data warehouse layouts.
---

## BigQuery Schema & Query Design

### Schema Rules
- **Explicit schemas only.** No autodetect in production loads.
- **Use `STRUCT` and `ARRAY`** for nested data; avoid JSON columns unless schema is
  truly unbounded.
- **`STRING` over `BYTES`** unless storing actual binary data.
- **`NUMERIC`/`BIGNUMERIC`** for money. Never `FLOAT64`.
- **`TIMESTAMP`** for points in time; `DATE` for calendar dates.
- **`description` on every column.** This is your data dictionary.

### Partitioning
- Partition every table > 1 GB.
- **Time partitioning** (`_PARTITIONTIME` or business date column) is the default.
- **Integer-range partitioning** for tenant_id or hashed user_id when time isn't a useful filter.
- Set `require_partition_filter = TRUE` to prevent full scans by accident.

### Clustering
- Cluster on the columns most often used in WHERE / JOIN.
- Up to 4 columns; order matters (most selective first).
- Re-cluster after large bulk updates.

### Query Patterns
- **Never `SELECT *` on wide tables.** Specify columns. Saves slots and bytes.
- **Filter on partition column first.** `WHERE date >= '...'` reduces scan cost dramatically.
- **CTEs over subqueries** for readability.
- **`APPROX_QUANTILES` / `APPROX_COUNT_DISTINCT`** for analytics on large data.
- **`MERGE`** for upserts, but watch for non-idempotent matches.
- **`QUALIFY` with window functions** for top-N per group.

### Materialized Views & Scheduled Queries
- Materialized views for hot, deterministic aggregations.
- Scheduled queries for ETL transforms; pin destination table.
- Use authorized views to expose subsets without exposing the base table.

### Cost Management
- **Always dry-run** new queries: `bq query --dry_run` to see bytes processed.
- **Set per-user / per-project byte caps.**
- **Slots reservation** for predictable workloads; on-demand for spiky.
- **INFORMATION_SCHEMA.JOBS** for who/what is burning slots.
- **Query plan inspection** for slow queries.

### Security
- Column-level security and row-level access policies for PII.
- Authorized views to expose only needed columns.
- Audit logs always on; export to a separate, locked-down project.
- DLP scans for accidental PII landing.

### Anti-patterns
- No `SELECT *` in production code.
- No unpartitioned tables that grow indefinitely.
- No dynamic SQL via string concatenation. Use parameterized queries.
- No JOIN of two big tables on a low-cardinality key without filter.

### Verification
- Dry-run shows expected bytes scanned.
- Slot ms within budget.
- Query plan shows expected partition pruning.

### Model Tier
Default: Sonnet. Escalate to Opus for warehouse re-architecture, slot
reservation strategy, or PII / security policy design.
