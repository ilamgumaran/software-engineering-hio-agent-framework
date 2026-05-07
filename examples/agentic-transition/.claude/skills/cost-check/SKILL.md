---
description: >
  Sanity-checks the resource cost of a change before merge: compute,
  storage, network egress, third-party API calls, and model usage.
  Use when reviewing infra-touching PRs or anything that adds new SaaS calls.
---

## Cost Check

### What to Examine
- New AWS resources: instance class, RDS size, S3 lifecycle policy,
  Lambda memory/timeout. Flag any new resource without a cost-center tag.
- Network egress: cross-AZ or cross-region traffic introduced.
- Third-party APIs: per-call cost × expected QPS × retention.
- Model usage: respects `config/model-routing.md`. Flag code paths defaulting
  to Opus when Sonnet would suffice.

### Output
A short table in the PR description: change → unit cost → expected monthly impact → owner.

### Model Tier
Default: Sonnet.
