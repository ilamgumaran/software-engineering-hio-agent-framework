---
description: >
  Scaffolds a new batch job with idempotency, checkpoint/restart,
  error handling, and observability. Use when asked to create a new
  batch job, scheduled task, or data pipeline step.
---

## Batch Job Scaffold

### Structure
Create the job following this structure:
- `src/main/java/<package>/batch/<JobName>Job.java` — main job class
- `src/main/java/<package>/batch/<JobName>Config.java` — Spring Batch config
- `src/main/java/<package>/batch/<JobName>Reader.java` — item reader
- `src/main/java/<package>/batch/<JobName>Processor.java` — item processor
- `src/main/java/<package>/batch/<JobName>Writer.java` — item writer
- `src/test/java/<package>/batch/<JobName>JobTest.java` — integration test
- `docs/runbooks/<job-name>.md` — operational runbook

### Requirements
1. **Idempotency:** Use a processing checkpoint table. Before processing
   a record, check if it was already processed in this run. Use
   `batch_checkpoint` table with columns: job_name, run_id, record_id, status, processed_at.
2. **Restart:** Implement Spring Batch restartability. Failed jobs resume
   from the last successful chunk, not from the beginning.
3. **Observability:**
   - Datadog metrics: `batch.<job_name>.records_processed`,
     `batch.<job_name>.records_failed`, `batch.<job_name>.duration_ms`
   - Log INFO: job start, chunk completion (every N records), job end
   - Log ERROR: individual record failures with record identifier
4. **Error handling:**
   - Skip policy for bad records (configurable threshold, default 1%)
   - Dead letter queue (SQS) for failed records
   - Alert via SNS if failure rate exceeds threshold
5. **Configuration:** All tunable parameters (chunk size, skip limit,
   thread pool size) externalized to `application.yml` with sensible defaults.

### Runbook Template
The runbook must include: purpose, schedule, dependencies (upstream/downstream),
expected duration, monitoring dashboard link, restart procedure, escalation path.

### Model Tier
Default: Sonnet. Escalate to Opus for cross-service refactors or jobs that
touch >1 database. See `config/model-routing.md`.
