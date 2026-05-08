---
description: >
  Deploys a service to Google Cloud Run with sensible defaults for
  concurrency, scaling, secrets, traffic splitting, and observability.
  Use when creating a new Cloud Run service or migrating a service
  to Cloud Run.
---

## GCP Cloud Run Deployment

### Container Requirements
- Multi-stage Dockerfile. Final stage: distroless or `alpine` non-root.
- `EXPOSE 8080`. Cloud Run uses `PORT` env var — read it in the app.
- Image stored in Artifact Registry, scanned for vulnerabilities.
- Image digest pinned in deployment, never `:latest`.

### Service Config
1. **Concurrency:**
   - Target 80–150 for typical IO-bound services.
   - 1 for stateful or CPU-pinned workloads.
   - Measure with load test before production.
2. **Scaling:**
   - `min-instances` > 0 for latency-sensitive services (avoid cold start).
   - `max-instances` set to protect downstream (DB, APIs).
   - CPU "always allocated" for streaming / background work.
3. **Resources:**
   - Start at 1 vCPU / 512 MiB; tune from real metrics.
   - Memory headroom 2x peak; OOM-killed instance is much worse than oversize.
4. **Networking:**
   - VPC connector for private DB access. Direct VPC egress preferred (newer).
   - Cloud Armor for public services. WAF rules + rate limit.
   - Internal services: ingress = `internal` or `internal-and-cloud-load-balancing`.
5. **Auth:**
   - Public APIs: API Gateway or Cloud Endpoints in front.
   - Internal: IAM-based service-to-service with `Authorization: Bearer <id_token>`.
   - Identity-Aware Proxy for human access to internal UIs.
6. **Secrets:** Secret Manager mounted as env or file. Rotation documented.
7. **Traffic management:**
   - New revisions get 0% traffic by default.
   - Canary: 10% → 50% → 100% with metric checks between steps.
   - Always keep 1 known-good revision pinned for fast rollback.
8. **Observability:**
   - Structured logs (JSON) to Cloud Logging; severity field set correctly.
   - Cloud Trace via OTel; propagate `traceparent` to downstreams.
   - SLO + alerting policy in Monitoring (see `slo-error-budget` skill).
   - Custom metrics via OTel → Cloud Monitoring.

### Cost Guardrails
- `max-instances` cap per service (review quarterly).
- Always-on CPU only when justified.
- Egress to internet metered — keep traffic within VPC where possible.
- Idle instance billing: `min-instances` > 0 has steady cost.

### Anti-patterns
- Don't deploy `:latest`. Pin image digest.
- Don't store request-scoped state in process memory.
- Don't ignore `SIGTERM` — Cloud Run sends it before shutdown.
- Don't mount the same secret in many services; use IAM-scoped secrets.

### Verification
- `gcloud run services describe` output matches IaC.
- Smoke test new revision before traffic shift.
- Rollback playbook tested quarterly.

### Model Tier
Default: Sonnet. Escalate to Opus for multi-region, traffic-management,
or migrating high-traffic services.
