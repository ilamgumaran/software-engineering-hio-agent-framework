# Platform Engineering Evaluation

Domain-specific evaluation methodology using the HIO three-layer approach. Each layer builds on the previous, moving from operational metrics to outcomes to emergent human-AI value.

---

## Three-Layer Evaluation Model

### Layer 1: Current State (Operational)

Metrics that capture day-to-day platform engineering operations. These are the starting point, not the goal.

| Metric | How to Measure | Frequency | Baseline Target |
|--------|---------------|-----------|----------------|
| Sprint velocity | Story points completed per sprint | Per sprint | Stable trend |
| Deployment count | Platform service deployments per week | Weekly | 10+ per week |
| Incidents per week | P1-P3 incidents involving platform services | Weekly | Fewer than 3 |
| Ticket volume | Infrastructure requests requiring manual intervention | Weekly | Declining trend |
| Pipeline success rate | CI/CD pipeline pass rate across all downstream teams | Daily | >95% |
| Mean time to provision | Time from resource request to resource available | Per request | <15 minutes |

### Layer 2: Outcome (Impact)

Metrics that measure whether platform engineering delivers its intended value. These are what leadership cares about.

| Metric | How to Measure | Frequency | Target |
|--------|---------------|-----------|--------|
| DORA: Deployment Frequency | Downstream team deployments per day | Weekly | Multiple per day |
| DORA: Lead Time for Changes | Commit to production for downstream teams | Weekly | <1 hour |
| DORA: Change Failure Rate | Percentage of deployments causing incidents | Weekly | <5% |
| DORA: Mean Time to Recovery | Time from incident detection to resolution | Per incident | <1 hour |
| Self-Service Rate | Percentage of infrastructure actions completed without tickets | Monthly | >70% |
| Time-to-First-Deploy | Time for a new team to deploy their first service | Per onboarding | <4 hours |
| Downstream Developer NPS | Net Promoter Score from platform users | Quarterly | >40 |
| Golden Path Adoption | Percentage of teams using recommended workflows | Monthly | >80% |
| Platform Availability | Uptime of core platform services | Monthly | >99.9% |

### Layer 3: HIO (Emergence)

Metrics that capture the unique value created by harmonized human-AI collaboration. These are what makes HIO different.

| Metric | How to Measure | Frequency | Indicator |
|--------|---------------|-----------|-----------|
| Fulfillment in platform work | Survey: "I find meaning in building platform capabilities" (1-10) | Per sprint | Average >7 |
| Emergence events | Count of outcomes that exceeded individual capability | Per sprint | 2+ per sprint |
| AI collaboration sophistication | Level of AI agent usage (1: lookup, 5: co-creation) | Per sprint | Trending toward 4+ |
| Cross-function contributions | Instances of people operating outside their primary function | Per sprint | 3+ per sprint |
| Workflow experiment rate | New workflow patterns tried per sprint | Per sprint | 1+ per sprint |

---

## Evaluation Suite Format

Platform health checks are defined as structured evaluation suites:

```yaml
evaluation:
  name: "Platform Health Check"
  unit: "Scale & Reliability"
  frequency: "weekly"
  layers:
    current:
      - metric: "pipeline_success_rate"
        source: "ci_dashboard"
        threshold: 0.95
        alert: "below"
      - metric: "mean_time_to_provision"
        source: "platform_api_logs"
        threshold_minutes: 15
        alert: "above"
    outcome:
      - metric: "self_service_rate"
        source: "ticket_system + platform_api"
        threshold: 0.70
        alert: "below"
      - metric: "downstream_deploy_frequency"
        source: "deployment_tracker"
        threshold_daily: 1
        alert: "below"
    hio:
      - metric: "fulfillment_score"
        source: "sprint_survey"
        threshold: 7
        alert: "below"
      - metric: "emergence_events"
        source: "retrospective_log"
        threshold: 2
        alert: "below"
```

---

## Testing Methodology

Platform capabilities are validated through four testing approaches:

| Approach | What It Tests | When to Use |
|----------|--------------|-------------|
| Contract Testing | API compatibility between platform and downstream services | Every PR that changes an API |
| Integration Testing | End-to-end platform workflows (provision, deploy, observe) | Nightly and pre-release |
| Chaos Testing | Platform resilience under failure conditions | Weekly in staging, monthly in production |
| Adoption Testing | Whether downstream teams can complete golden paths unassisted | Per capability launch |

---

## Organization Extension Point

> **YOUR_ORG:** Customize thresholds in each layer to match your platform maturity. Early-stage platforms should set lower targets for self-service rate and golden path adoption. Adjust DORA targets based on your deployment model (monolith vs microservices).

---

*Reference: [metrics/](../../metrics/) | [workflows.md](workflows.md)*
