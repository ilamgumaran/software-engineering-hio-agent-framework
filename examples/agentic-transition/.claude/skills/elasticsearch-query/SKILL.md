---
description: >
  Designs Elasticsearch / OpenSearch indices, mappings, analyzers, and
  queries. Use when adding search functionality, optimizing query
  latency, or rolling out a new index.
---

## Elasticsearch Query & Index Design

### Mapping Rules
- **Always explicit mappings.** Disable dynamic mapping (`"dynamic": "strict"`).
- **Field types matter:**
  - `keyword` for exact match, aggregations, sorting.
  - `text` for full-text search; pair with a `keyword` sub-field for aggregations.
  - `date` with explicit format. Avoid `date_nanos` unless needed.
  - `wildcard` for high-cardinality patterns (logs, IDs).
- **No `_source` disable** unless you've measured. Re-indexing later is expensive.
- **`doc_values: false`** only for fields never used in aggregations/sorting.

### Analyzer Rules
- Custom analyzers per language. Don't rely on the default standard analyzer
  for anything multilingual.
- Synonyms via synonym graph, loaded at index time AND query time.
- Stemming: language-specific (English snowball, etc.).
- Stopwords: include only if measured to help recall.

### Query Patterns
- **Use the Query DSL** — never `query_string` on user input (injection risk).
- **`match` for full-text**, `term` for exact matches, `bool` to compose.
- **`function_score` or `rank_feature`** for custom scoring; avoid script_score
  for hot paths (slow).
- **Filters in `bool.filter`** (cached, no scoring) vs. `bool.must` (scored).
- **Pagination:**
  - `from + size` for shallow (≤ 10K).
  - `search_after` with sort tiebreaker for deep.
  - NEVER `from: 100000` — it's a per-shard sort.
- **Aggregations:** put filter clause first to limit doc count before agg.

### Index Lifecycle
- ILM policies for time-series indices (logs, events).
- Hot → warm → cold tier, with shard merge at rollover.
- Snapshot to S3/GCS before deletion.
- Force-merge to 1 segment for read-only indices to maximize cache.

### Performance
- Shard sizing: 10–50GB per shard. More shards ≠ faster.
- `refresh_interval`: `30s` for write-heavy; default `1s` only when needed.
- Track slow queries (`index.search.slowlog.threshold`).
- Use `_explain` to debug scoring; `profile: true` for query timing.

### Anti-patterns
- Don't use `parent/child` if `nested` works.
- Don't put everything in one big index; partition by tenant/time.
- Don't store binary blobs (>1MB).
- Don't expose raw query DSL to end users.

### Verification
- `_validate/query` on new queries before deploy.
- Load test with realistic data volume.
- Monitor query latency p99 and circuit breakers.

### Model Tier
Default: Sonnet. Escalate to Opus for relevance tuning, multi-tenant
shard design, or query plan analysis at scale.
