---
description: >
  Designs and reviews Apache Beam pipelines for Google Cloud Dataflow.
  Use when building or modifying batch / streaming data pipelines on
  Dataflow.
---

## Dataflow / Apache Beam Pipeline Design

### Structure
- One pipeline per business outcome. Don't bundle unrelated transforms.
- `pipeline.py` (or `Pipeline.java`) reads options from `PipelineOptions`.
- Custom DoFns in their own modules with unit tests.
- Schema definitions versioned alongside the pipeline.

### Requirements
1. **Runner:** Use Runner v2 (`--experiments=use_runner_v2`).
2. **Windowing:** Choose explicitly:
   - Fixed windows for periodic aggregations.
   - Sliding windows for moving averages.
   - Sessions for user-activity grouping.
   - Global window only for batch.
3. **Triggers:** Default trigger fires at watermark; specify early/late triggers
   when latency or completeness requires.
4. **DoFn lifecycle:**
   - Heavy setup in `setup()` / `start_bundle()`, not `process()`.
   - Stateful processing via Beam state API (not module globals).
   - Side inputs for small, slowly changing reference data.
5. **Schemas:** Use Beam Schema (Java) or `apache_beam.typehints` (Python).
   Avoid raw `PCollection<String>` for structured data.
6. **Error handling:**
   - Tag failures into a separate PCollection (`with_outputs`).
   - Dead-letter to BigQuery or Pub/Sub for inspection.
   - Never silently drop records.
7. **Cost / performance:**
   - FlexRS templates for non-urgent batch (50% cheaper).
   - Autoscaling enabled; set `max_num_workers` ceiling.
   - Combine before GroupByKey when possible (combiner lifting).
   - Avoid hot keys — add salt + double-aggregation if needed.
8. **Streaming-only:**
   - Watermark progress monitored; alert on drift > 10 min.
   - Exactly-once via Pub/Sub Lite or Pub/Sub with `idAttribute`.
   - Bounded state via TTL on stateful DoFns.
9. **Testing:**
   - `TestPipeline` with `assert_that` for transform tests.
   - Sample data committed to repo for repeatability.
   - Integration tests against a test project before prod deploy.

### Templates
- Build classic templates for parameterized batch jobs.
- Build Flex templates when non-trivial dependencies are needed.
- Version templates and pin in scheduler config.

### Anti-patterns
- Don't read DB in `process()` per element — use side input or batched lookup.
- Don't use mutable global state in DoFns.
- Don't `time.sleep` in DoFns.
- Don't write directly to BigQuery without `WriteDisposition` set.

### Verification
- Unit tests pass with TestPipeline.
- Dry-run cost estimate via Dataflow CLI.
- Smoke run on staging with sampled data.

### Model Tier
Default: Opus (high blast radius, complex windowing/state semantics).
