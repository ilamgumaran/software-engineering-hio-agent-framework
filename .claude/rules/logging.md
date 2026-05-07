---
applyTo: "**"
---

# Logging Rules

- INFO: business events (job started, order created, payment captured).
- WARN: recoverable issues (retryable failure, fallback used).
- ERROR: failures requiring human attention.
- DEBUG: developer diagnostics; off in production.
- Log structured key-value pairs (slf4j MDC for Java, structlog for Python).
- Always include correlation/request ID. Propagate via Datadog headers.
- Never log secrets, tokens, full PAN/SSN, or full PII payloads.
- Don’t use logs as a primary metric source — emit metrics for things you
  want to alert on.
