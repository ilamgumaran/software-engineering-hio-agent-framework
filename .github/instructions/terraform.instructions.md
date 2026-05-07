---
applyTo: "**/*.tf"
---

# Terraform Conventions

- Pin provider and module versions.
- One module per logical resource group; no monolithic root modules.
- State stored in remote backend (S3 + DynamoDB locking).
- Never put secrets in variables or tfvars. Use AWS Secrets Manager / SSM.
- All changes require `terraform plan` review.
- Agents do NOT modify IAM policies, security groups, or VPC routing without
  explicit human approval. Propose the diff and stop.
