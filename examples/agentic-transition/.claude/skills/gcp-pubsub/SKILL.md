---
description: >
  Designs Pub/Sub publisher and subscriber patterns with proper
  acknowledgement, dead-letter, ordering, and exactly-once delivery.
  Use when adding event-driven flows or async processing.
---

## GCP Pub/Sub Patterns

### Topic & Subscription Design
- **One topic per event type.** Don't multiplex unrelated events.
- **Schemas attached to topics** (Avro or Protobuf). Publishers and consumers
  share the schema.
- **Naming:** `<domain>.<entity>.<event>` (e.g., `orders.order.created`).
- **Subscription per consumer.** Multiple consumers → multiple subscriptions on
  the same topic.

### Push vs. Pull
- **Pull (recommended):** Long-lived workers, complex error handling,
  high-throughput or batch processing.
- **Push:** Cloud Run / Functions endpoints; simpler scaling but harder to debug
  and requires the endpoint to be idempotent.

### Acknowledgement
- **Default ack deadline 10s** — increase only if processing is genuinely slow.
- **Modify deadline** for long-running work; don't set deadline to hours.
- **Exactly-once delivery** enabled when at-least-once is unsafe (financial,
  inventory). Adds latency; measure.
- **Idempotent consumers always.** Even with exactly-once, design as if
  duplicates can happen.

### Ordering
- Ordering keys when you need per-key sequence (per-user, per-account).
- Don't enable ordering globally — it serializes all messages on one shard.
- Ordering keys partition throughput; balance key cardinality.

### Dead-Letter Topics (DLT)
- **Always configure a DLT.** No exceptions.
- Max delivery attempts: 5–10 typical.
- DLT topic monitored — alert on any messages landing.
- Replay tool to drain DLT after fix.

### Performance
- Batch publishes (size + time threshold).
- Flow control on subscribers: `max_outstanding_messages`,
  `max_outstanding_bytes`.
- Multi-region for global producers; regional endpoints for low-latency consumers.

### Observability
- Metrics: publish latency, subscription backlog, oldest unacked age, DLT count.
- Trace context propagation: include `traceparent` in attributes.
- Alert on backlog growth (e.g., ≥5 minutes of growth).

### Anti-patterns
- Don't use Pub/Sub for request-response (use HTTP or gRPC).
- Don't put large payloads (>10 MB) — store in GCS, send pointer.
- Don't share a single subscription across unrelated consumers — they steal
  each other's messages.
- Don't ignore `expirationPolicy` on subscriptions — unused subs accumulate.

### Verification
- Smoke publish + consume in staging.
- Chaos test: kill consumer mid-process, verify redelivery.
- DLT replay tested for at least one failure mode.

### Model Tier
Default: Sonnet. Escalate to Opus for cross-region designs or
exactly-once correctness review.
