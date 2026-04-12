# Metrics: Current/Legacy

## Purpose

Metrics the organization currently tracks. These provide continuity, stakeholder confidence, and a stability baseline during the HIO transformation. Do not stop tracking these -- they are the guardrails that ensure the transformation does not break what already works.

Current/Legacy sits in Layer 1 (Current) because these are the metrics your org already knows and trusts. Leadership reads these. Stakeholders expect them. Removing them during transformation creates unnecessary anxiety.

---

## KPIs

| KPI | What It Measures | How to Capture | Target Direction | Frequency |
|---|---|---|---|---|
| Stories Completed | Number of stories completed per sprint | Sprint tracking tool (Jira, Linear, Shortcut) | Stable or higher | Sprint |
| Sprint Velocity | Story points delivered per sprint | Sprint tracking tool | Stable (not necessarily higher) | Sprint |
| Backlog Readiness | % of stories in the next sprint meeting definition of ready | Backlog grooming records | Higher (>80%) | Sprint |
| Priority Alignment | % of sprint work matching top organizational priorities | Sprint plan vs. priority list comparison | Higher (>85%) | Sprint |
| Merge/Release Rate | PRs merged and releases shipped per sprint | Git platform analytics + release tracking | Stable or higher | Sprint |

---

## Baseline Capture

These metrics should already have a baseline -- they are what you track today. To formalize:

1. Pull the last 6 sprints of velocity data. Calculate the mean and standard deviation.
2. Record current backlog readiness and priority alignment percentages.
3. Pull merge/release rate from git platform analytics for the same period.
4. Document the current definitions (what counts as a "story," how points are assigned, what "ready" means).

The baseline is not just the numbers -- it is also the definitions. During transformation, keeping definitions consistent ensures trend data remains meaningful.

---

## Interpretation Guide

- **Stories Completed** and **Sprint Velocity** should remain stable during transformation. A temporary dip of 10-15% during Phase 1 (Weeks 3-8) is expected as the org restructures into cognitive units. A dip beyond 20% or lasting more than 3 sprints requires intervention.
- **Backlog Readiness** often improves during transformation because cognitive units take more ownership of story refinement. If it drops, the unit structure may be unclear about who owns refinement.
- **Priority Alignment** is the most important Layer 1 metric. The transformation must not cause the org to drift from its delivery commitments. If priority alignment drops, re-examine whether the transformation activities are competing with delivery work rather than enabling it.
- **Merge/Release Rate** is a proxy for flow. A declining merge rate during transformation may indicate that new workflows or review processes are creating bottlenecks.

---

## The Transition Plan

As the transformation matures, Layer 1 metrics gradually become less emphasized while Layer 2 and 3 metrics take prominence:

| Phase | Layer 1 Role | Layer 2 Role | Layer 3 Role |
|---|---|---|---|
| Phase 0-1 (Weeks 1-8) | Primary reporting metrics | Baseline capture | Baseline capture |
| Phase 2 (Weeks 9-13) | Stability guardrails | Growing importance | Early signals |
| Phase 3 (Weeks 14-20) | Background monitoring | Primary reporting metrics | Growing importance |
| Phase 4 (Weeks 21-26) | Background monitoring | Co-primary with Layer 3 | Co-primary with Layer 2 |

Do not retire Layer 1 metrics. Simply shift the reporting emphasis. Stakeholders who rely on these numbers should still receive them. The conversation shifts from "these are our metrics" to "these confirm stability while we focus on deeper outcomes."

---

## Connection to Other Categories

**Feeds:**
- DORA -- merge rate and velocity are leading indicators of deployment frequency
- Innovation -- velocity stability confirms that innovation investment is not eroding delivery
- AI Utilization -- time savings from AI should appear as maintained or improved velocity

**Fed by:**
- Code Health -- low rework and fast builds support consistent throughput
- SPACE/DX -- focus time and low friction enable steady delivery
- Platform Outcomes -- platform improvements reduce the maintenance burden that drags on velocity

---

## Organization Extension Point

> **YOUR_ORG:** Replace these default KPIs with whatever your org actually tracks today. The specific metrics matter less than the principle: keep tracking what leadership already trusts, maintain stability during transformation, and gradually expand the conversation to include Layer 2 and 3 outcomes. If your org tracks cycle time, throughput, or capacity metrics instead of velocity and story points, use those. The framework is metric-agnostic at Layer 1.
