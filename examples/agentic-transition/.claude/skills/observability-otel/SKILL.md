---
description: >
  Instruments a service with OpenTelemetry: traces, metrics, logs.
  Use when adding observability to a new service or upgrading legacy
  log-only instrumentation. Aligns logs/metrics/traces via trace_id
  correlation.
---

## OpenTelemetry Instrumentation

### Three Pillars
- **Traces:** Per-request causal chain across services.
- **Metrics:** Aggregated time-series for alerting and capacity.
- **Logs:** Discrete events for forensic debugging.

All three correlate via `trace_id`.

### Setup
1. **SDK:** Use the official OTel SDK for the language. Auto-instrumentation
   for HTTP, DB, queue clients where available.
2. **Resource attributes:** `service.name`, `service.version`,
   `deployment.environment` set on every emitter.
3. **Exporter:** OTLP to the org's collector. Don't ship directly to vendors
   from app code — the collector enables vendor swap and policy enforcement.
4. **Propagation:** W3C Trace Context (`traceparent`, `tracestate`).

### Spans
- One span per logical unit of work.
- Name spans by operation, not data: `http.server.request`, `db.query`,
  `cache.get`. Use `attributes` for the variable parts.
- Add semantic-convention attributes: `http.method`, `http.status_code`,
  `db.system`, `messaging.system`.
- **No PII in span attributes** — traces are widely accessible.
- Record exceptions: `span.record_exception(e)`.

### Metrics (RED + USE)
- **RED for services:** Rate (req/s), Errors (err/s), Duration (latency histogram).
- **USE for resources:** Utilization, Saturation, Errors.
- Histograms for latency (not gauges or counters).
- Cardinality discipline: limit unique label combinations < 10K per metric.
  No user_id or request_id as labels.

### Logs
- Structured (JSON), one record per event.
- Required fields: `timestamp`, `severity`, `message`, `trace_id`, `span_id`,
  `service.name`.
- DEBUG off in prod. INFO for business events. WARN for retryable. ERROR for
  human attention.
- See `.claude/rules/logging.md` for details.

### Sampling
- **Head sampling** for cost control on high-volume traffic (e.g., 10%).
- **Tail sampling** at the collector to keep all errors and slow requests
  regardless of head decision.
- Always-sample: errors, requests above latency threshold, debug-flagged.

### Common Pitfalls
- Forgetting context propagation across async boundaries (queues, workers).
  Spans become orphans.
- Cardinality explosion (per-user labels) blowing up metrics backend cost.
- Logging the entire request body — PII risk + log volume.
- Using only logs for SLO calculation — use metrics, far cheaper.

### Backend
- Vendor (Datadog, Grafana, New Relic, Cloud Operations) chosen at the
  collector layer.
- App emits OTLP only. No vendor SDKs in app code.

### Verification
- Trace visible end-to-end across services for a synthetic request.
- RED dashboard exists per service.
- Log correlated to trace via `trace_id` in dashboard click-through.
- Cardinality monitor on metrics.

### Model Tier
Default: Sonnet.
