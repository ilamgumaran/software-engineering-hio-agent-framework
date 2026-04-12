# Metrics: DORA

## Purpose

The four key metrics from the DORA (DevOps Research and Assessment) program. These are industry-standard engineering performance indicators validated across thousands of organizations. They measure how effectively an engineering team delivers software and recovers from failures.

DORA metrics sit in Layer 2 (Outcome) because they measure what the platform achieves, not how it is built.

---

## KPIs

| KPI | What It Measures | How to Capture | Target Direction | Frequency |
|---|---|---|---|---|
| Deployment Frequency | How often code deploys to production | CI/CD pipeline logs, deployment event tracking | Higher (daily+) | Daily |
| Lead Time for Changes | Time from first commit to running in production | Git commit timestamps + deployment timestamps | Lower (<1 day) | Per deployment |
| Change Failure Rate | % of deployments causing incidents or rollbacks | Incident tracking system + deployment logs | Lower (<5%) | Weekly aggregate |
| Mean Time to Recovery | Time from failure detection to service restoration | Incident start/end timestamps from alerting and incident management | Lower (<30 min) | Per incident |

---

## Baseline Capture

To establish your DORA baseline:

1. Pull 4 weeks of CI/CD deployment data (all environments, focus on production).
2. Calculate each metric using the definitions above.
3. Classify each metric into the tier table below.
4. Document the results in your Phase 0 baseline report.

Automated capture is strongly preferred. If your CI/CD tooling does not emit these events natively, instrument it during Phase 0. Manual tracking is acceptable as a stopgap but introduces measurement error.

The Metrics Monitor agent (see [../agents/metrics-monitor.md](../agents/metrics-monitor.md)) can be configured to pull DORA data automatically from common CI/CD platforms.

---

## DORA Tier Classification

| Tier | Deploy Frequency | Lead Time | Change Failure Rate | MTTR |
|---|---|---|---|---|
| Elite | Multiple per day | <1 hour | <5% | <1 hour |
| High | Weekly to daily | 1 day to 1 week | 5-10% | <1 day |
| Medium | Monthly to weekly | 1 week to 1 month | 10-15% | <1 week |
| Low | Less than monthly | >1 month | >15% | >1 week |

---

## Interpretation Guide

- **Elite** = world-class delivery performance. Sustain and protect.
- **High** = target state for Week 26 of the transformation. Achievable for a ~30-person platform org with focused effort.
- **Medium** = acceptable during the transformation period. Track trend direction, not absolute value.
- **Low** = requires immediate attention. A Low-tier metric in any category signals a systemic issue that will undermine transformation progress.

Improvement is not always linear. Expect temporary dips during Phase 1-2 as the org restructures into cognitive units and adopts new workflows (see [../workflows/](../workflows/)).

---

## Connection to Other Categories

**Feeds:**
- Platform Outcomes -- deployment reliability directly drives platform adoption and downstream team confidence
- Code Health -- deployment health reflects underlying code quality and test coverage

**Fed by:**
- Code Health -- higher test coverage and lower tech debt reduce change failure rate
- AI Utilization -- AI-assisted code review and generation can reduce lead time for changes
- Current/Legacy -- sprint velocity and merge rate are leading indicators of deployment frequency

---

## Organization Extension Point

> **YOUR_ORG:** If you already track DORA metrics, map your existing definitions and data sources here. Pay attention to how you define "deployment" and "failure" -- inconsistent definitions are the most common source of misleading DORA data. If you use a DORA dashboard tool (Sleuth, LinearB, Swarmia, etc.), document the integration here.
