---
applyTo: "**"
---

# Error Handling Rules

- Catch only what you can handle. Re-throw or wrap others with context.
- API errors return RFC 7807 problem details (`type`, `title`, `status`, `detail`, `instance`).
- Batch jobs distinguish: (a) bad record → skip + DLQ; (b) systemic failure →
  fail the run, alert.
- Retries: bounded, exponential backoff with jitter. Max attempts and
  per-attempt timeout MUST be set.
- Circuit breakers on every outbound call to a service that can be slow.
- Never swallow an exception silently. If you really mean to ignore it,
  log at DEBUG with the reason.
