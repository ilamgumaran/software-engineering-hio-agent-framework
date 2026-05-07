---
applyTo: "**"
---

# PII Handling (api-customer-service)

Stricter than the org default.

- `customer.email`, `customer.phone`, `customer.address` are PII.
- Mask in logs (`a***@b.com`, last-4 only for phone).
- Never include PII in metric labels or trace tags.
- Encrypt at rest via `EncryptionService`.
- Access requires audit log entry (`pii.access` event).
- Bulk export of PII is forbidden through this API — use the dedicated
  data-export service.
