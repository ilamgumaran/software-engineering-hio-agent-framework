---
description: >
  Reviews code for performance issues specific to batch jobs and APIs.
  Use when reviewing performance-sensitive code, optimizing throughput,
  or investigating latency issues. Escalates to Opus tier per model-routing.
---

## Performance Review Checklist

### Batch Jobs
- N+1 queries: lazy fetches in processor → use JOIN FETCH or batch fetching.
- Chunk size tuning: default 100; for IO-heavy try 500/1000. Measure throughput/min.
- Thread pool: multi-threaded steps must not share mutable state.
- Memory: streaming/cursor-based readers for tables > 100K rows.
- Database locks: short transactions per chunk; avoid blocking API traffic.

### APIs
- Query patterns: every WHERE clause on indexed column. Attach EXPLAIN if unclear.
- Connection pools: `pool_size = (core_count * 2) + disk_spindles`.
- Serialization: response caching or pre-serialized for >1000 req/s paths.
- Pagination: every list endpoint paginates. Default 20, max 100. Cursor-based for feeds.
- Caching: Cache-Control headers on read-heavy endpoints; Redis for shared caches.
