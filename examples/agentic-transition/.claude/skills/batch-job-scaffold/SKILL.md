---
description: >
  Scaffolds a new batch job with idempotency, checkpoint/restart,
  error handling, and observability. Use when asked to create a new
  batch job, scheduled task, or data pipeline step.
---

## Batch Job Scaffold

### Structure
- `src/main/java/<package>/batch/<JobName>Job.java` — main job class
- `src/main/java/<package>/batch/<JobName>Config.java` — Spring Batch config
- `src/main/java/<package>/batch/<JobName>Reader.java` — item reader
- `src/main/java/<package>/batch/<JobName>Processor.java` — item processor
- `src/main/java/<package>/batch/<JobName>Writer.java` — item writer
- `src/test/java/<package>/batch/<JobName>JobTest.java` — integration test
- `docs/runbooks/<job-name>.md` — operational runbook

### Requirements
1. **Idempotency:** Use a processing checkpoint table. Use `batch_checkpoint`
   with columns: job_name, run_id, record_id, status, processed_at.
2. **Restart:** Spring Batch restartability. Failed jobs resume from the last
   successful chunk.
3. **Observability:**
   - Datadog metrics: `batch.<job_name>.records_processed`,
     `batch.<job_name>.records_failed`, `batch.<job_name>.duration_ms`.
   - Log INFO: job start, chunk completion, job end.
   - Log ERROR: individual record failures with record identifier.
4. **Error handling:** skip policy (default 1%), DLQ via SQS, SNS alert on threshold breach.
5. **Configuration:** chunk size, skip limit, thread pool externalized to `application.yml`.

### Runbook Template
Must include: purpose, schedule, dependencies (upstream/downstream),
expected duration, monitoring dashboard link, restart procedure, escalation path.

### Model Tier
Default: Sonnet. Escalate to Opus for cross-service refactors or jobs that
touch >1 database. See `config/model-routing.md`.
