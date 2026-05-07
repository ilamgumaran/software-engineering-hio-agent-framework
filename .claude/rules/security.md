---
applyTo: "**"
---

# Security Rules

- Never commit secrets, tokens, API keys, or credentials. Use AWS Secrets Manager / SSM.
- Validate all input at trust boundaries (HTTP, queue consumers, file ingestion).
- Use parameterized queries; never string-concatenate SQL.
- Sanitize logs — no PII, tokens, or full credit card numbers in log output.
- Apply least-privilege IAM. Agents must NOT modify IAM, security groups, or
  VPC routing; propose the diff and stop for human review.
- Dependency upgrades that touch crypto, auth, or serialization libraries
  require a security review label on the PR.
- All public-facing endpoints behind WAF + rate limiting.
