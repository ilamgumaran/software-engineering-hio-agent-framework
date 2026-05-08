---
description: >
  Defines SLOs and error budgets following Google SRE practice. Use
  when adding a new service, changing reliability targets, or setting
  up production alerting based on user-facing reliability.
---

## SLO & Error Budget

### Definitions
- **SLI (Service Level Indicator):** A measurable property of the service.
  E.g., "the proportion of HTTP requests that succeed within 500ms."
- **SLO (Service Level Objective):** A target for the SLI over a window.
  E.g., "99.9% of requests succeed within 500ms over a 28-day window."
- **Error budget:** 100% − SLO. The acceptable failure rate. At 99.9%,
  budget is 0.1% — ~43 minutes/month of downtime.
- **SLA:** Contractual; usually looser than SLO. Don't conflate.

### Choosing SLIs
- **Request-based:** good for APIs. (`good_requests / total_requests`).
- **Window-based:** good for batch jobs / pipelines. ("X% of 5-minute windows
  meet target").
- **Pick metrics that map to user pain.** Internal latency 99th percentile is
  not as good as "p95 of user-perceived response time."
- **One critical SLI per user journey.** More than 3 SLIs per service is hard
  to action on.

### Setting Targets
- Start from the user's expectation, not the system's current state.
- Work backward from business impact: how much downtime can we afford
  per quarter?
- Don't aim for 99.999% unless the cost is justified — each nine roughly
  10×s the engineering cost.
- New services often start at 99.0% or 99.5% and tighten as they mature.

### Error Budget Policy
A written policy (signed off by eng + product) covering:
- What happens when budget is healthy (≥50% remaining): teams ship freely.
- What happens when burn rate is high or budget is exhausted:
  - Code freeze on non-reliability work.
  - Incident review; reliability fixes prioritized.
  - SLO revision is a LAST resort — be honest, not aspirational.
- Who has authority to invoke / waive freezes.

### Alerting (Multi-Window, Multi-Burn-Rate)
Replace static thresholds with burn-rate alerts:
- **Fast burn** (page): 14.4× burn over 1h — budget exhausted in 2 days.
- **Slow burn** (ticket): 6× burn over 6h — budget exhausted in ~5 days.
- Multi-window prevents flapping; multi-burn-rate catches both spikes
  and slow regressions.
- See Google SRE Workbook chapter on alerting.

### Implementation
- SLO config in IaC (e.g., Cloud Monitoring SLO objects via Terraform).
- Dashboards: error budget remaining (gauge), burn rate (timeseries),
  recent incidents.
- Quarterly SLO review with stakeholders.

### Anti-patterns
- One SLO per metric per service — alert fatigue.
- Setting SLO target = current performance — you've optimized for the past.
- Hiding error budget data from product / business teams.
- "100% available" — dishonest and removes incentive for reliability work.

### Verification
- SLO config committed.
- Burn-rate alerts firing on synthetic injection test.
- Error budget dashboard visible in team standup.
- Policy doc with named owners.

### Model Tier
Default: Opus (high-leverage decision; affects on-call load and roadmap).
