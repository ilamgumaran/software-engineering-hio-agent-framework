---
description: >
  Reviews code for performance issues specific to batch jobs and APIs.
  Use when reviewing performance-sensitive code, optimizing throughput,
  or investigating latency issues. Escalates to Opus tier per model-routing.
---

## Performance Review Checklist

### Batch Jobs
- N+1 queries: Does the reader fetch associations lazily inside the processor?
  Use JOIN FETCH or batch fetching instead.
- Chunk size tuning: Default 100. For IO-heavy jobs, test 500 and 1000.
  Measure throughput/minute, not just completion time.
- Thread pool: Multi-threaded steps must not share mutable state.
  Verify thread safety of all processors and writers.
- Memory: Does the job hold entire datasets in memory?
  Use streaming / cursor-based readers for tables > 100K rows.
- Database locks: Long-running transactions during batch processing
  can block API traffic. Use short transactions per chunk.

### APIs
- Query patterns: Check for full table scans. Every WHERE clause should use
  an indexed column. Attach EXPLAIN output if unclear.
- Connection pools: HikariCP default (10) is often too low for
  high-throughput services. `pool_size = (core_count * 2) + disk_spindles`.
- Serialization: Jackson is fine for most cases. For hot paths (>1000 req/s),
  consider response caching or pre-serialized responses.
- Pagination: All list endpoints must paginate. Default page size 20,
  max 100. Use cursor-based pagination for real-time feeds.
- Caching: Identify read-heavy, write-light endpoints. Apply Cache-Control
  headers. Use Redis for shared caches.
