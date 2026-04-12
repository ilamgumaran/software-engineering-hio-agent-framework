# Metrics: Platform Outcomes

## Purpose

Platform-specific business outcomes that demonstrate the platform engineering organization is delivering value to its consumers. These metrics answer the question stakeholders actually care about: is the platform making downstream teams more effective?

Platform Outcomes sit in Layer 2 (Outcome) and are often the most persuasive metrics for leadership and cross-org stakeholders.

---

## KPIs

| KPI | What It Measures | How to Capture | Target Direction | Frequency |
|---|---|---|---|---|
| Time Ask-to-Experiment | Days from feature request to live experiment | Request tracker timestamps (Jira, Linear, etc.) | Lower (40%+ reduction) | Per request |
| Self-Service Rate | % of downstream team actions completed without platform team help | Support ticket analysis + self-service portal logs | Higher (>70%) | Monthly |
| Time to First Deploy | Hours for a new team to deploy their first service on the platform | Onboarding tracking from first access to first production deploy | Lower (trending down) | Per onboarding |
| Platform Adoption Rate | % of eligible teams actively using the platform | Usage telemetry from platform services | Higher (trending up) | Monthly |
| Experiment Success Rate | % of experiments producing actionable results (whether positive or negative) | Experiment tracking system | Higher (>60%) | Monthly |
| Downstream Team NPS | Net Promoter Score from platform consumers | Quarterly NPS survey of downstream engineering teams | Higher (15+ point improvement) | Quarterly |

---

## Baseline Capture

To establish your Platform Outcomes baseline:

1. Audit the last quarter of feature requests. Measure elapsed time from request to first production experiment for each.
2. Categorize the last month of support tickets: which could have been self-service vs. which required platform team involvement?
3. Review the last 3 team onboardings. How long did each take from first access to first deploy?
4. Count eligible teams and active users of platform services.
5. Run a baseline NPS survey with downstream teams (include in [baseline-survey.md](baseline-survey.md) or run separately).

---

## Targets (Option 2 Accelerated Plan)

These targets align with the 26-week transformation timeline:

| KPI | Baseline | Week 13 Target | Week 26 Target |
|---|---|---|---|
| Time Ask-to-Experiment | Measured in Phase 0 | 20% reduction | 40%+ reduction |
| Self-Service Rate | Measured in Phase 0 | 50% | 70%+ |
| Time to First Deploy | Measured in Phase 0 | 30% reduction | 50%+ reduction |
| Platform Adoption Rate | Current state | 10% increase | 20%+ increase |
| Downstream Team NPS | Measured in Phase 0 | +8 points | +15 points |

---

## Interpretation Guide

- **Time Ask-to-Experiment** is the single most visible metric for platform value. If feature requests still take weeks to reach experiment stage by Week 13, the cognitive unit structure or workflow design needs adjustment. See [../workflows/](../workflows/).
- **Self-Service Rate** below 50% means the platform is still a bottleneck rather than an enabler. Investigate whether the gap is tooling (missing self-service capabilities), documentation (people do not know how), or trust (people are afraid to self-serve).
- **Time to First Deploy** captures the new-team experience. If this is high, the platform has an onboarding problem that will cap adoption.
- **Downstream Team NPS** is a lagging indicator. It will not move quickly. Look for directional improvement, not dramatic jumps.
- **Experiment Success Rate** measures experiment design quality, not just outcomes. An experiment that conclusively shows an idea does not work is still a success.

---

## Connection to Other Categories

**Feeds:**
- Current/Legacy -- platform adoption drives the throughput numbers leadership watches
- Innovation -- faster ask-to-experiment cycles enable more exploration
- Human Fulfillment -- seeing platform impact on downstream teams drives purpose alignment

**Fed by:**
- DORA -- reliable deployments are a prerequisite for platform trust
- Code Health -- clean, well-tested platform code reduces onboarding friction
- AI Utilization -- AI agents handling routine platform support increases self-service rate
- Harmonization -- cross-function collaboration produces better platform features

---

## Organization Extension Point

> **YOUR_ORG:** Replace or supplement these KPIs with the platform outcomes your leadership already tracks. If your org uses internal developer portals (Backstage, Port, Cortex), pull adoption and self-service data from those systems. The downstream NPS survey should be customized to your specific platform services and consumer team relationships.
