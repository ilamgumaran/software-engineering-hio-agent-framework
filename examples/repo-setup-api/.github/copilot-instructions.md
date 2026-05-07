# Copilot — api-customer-service (template)

Inherits from org-level Copilot instructions.

## Repo Rules
- p99 latency budget: 200ms. Load-test any change that touches a hot path.
- Mask PII (email, phone, address) in logs.
- New endpoints require OpenAPI + internal API catalog update.
- Writers are responsible for cache invalidation.
