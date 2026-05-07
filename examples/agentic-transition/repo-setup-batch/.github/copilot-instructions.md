# Copilot — batch-order-processing (template)

Inherits from org-level Copilot instructions.

## Repo Rules
- Money values are integer cents.
- PII goes through `EncryptionService`.
- Schedule changes require runbook update.
- Logs are JSON-structured (logstash-logback-encoder).
