# Metrics: SPACE/DX

## Purpose

Developer experience metrics based on the SPACE framework (Satisfaction, Performance, Activity, Communication, Efficiency). These capture how it feels to build software in the org -- the human side of engineering productivity.

SPACE/DX sits in Layer 2 (Outcome) because developer experience is an outcome the platform produces, not just an internal feeling. Poor DX drives attrition, slows delivery, and blocks transformation adoption.

---

## KPIs

| KPI | What It Measures | How to Capture | Target Direction | Frequency |
|---|---|---|---|---|
| Focus Time Days | Days per week with 4+ hours of uninterrupted work | Calendar analysis + self-report | Higher (3+ days/week) | Weekly |
| Context Switching Frequency | Number of context switches per day | Tool telemetry + self-report (interruption log) | Lower (<5/day) | Weekly |
| Friction Events | Developer-reported pain points per week | Friction log (Slack channel, form, or standup capture) | Lower (trending down) | Weekly |
| Developer Experience Score | Comprehensive DX assessment | Quarterly anonymous DX survey (1-100 scale) | Higher (>70) | Quarterly |
| Code Review Turnaround | Hours from PR opened to first substantive review | Git platform analytics (GitHub, GitLab) | Lower (<4 hours) | Weekly |

---

## Baseline Capture

To establish your SPACE/DX baseline:

1. Run an anonymous DX survey covering satisfaction, tooling, friction, and flow. Use the DX section of the [baseline-survey.md](baseline-survey.md).
2. Analyze 4 weeks of calendar data to calculate Focus Time Days (look for meetings, on-call rotations, and interrupt patterns).
3. Pull code review turnaround times from your git platform for the same 4-week window.
4. Establish a friction log -- even a simple Slack channel where people note pain points.

Self-report data is valid. Do not dismiss it because it is subjective. Developer experience is inherently subjective, and subjective data is the right data for subjective phenomena.

---

## SPACE Dimensions Mapping

| SPACE Dimension | KPIs Covered | Notes |
|---|---|---|
| Satisfaction | DX Score, Friction Events | How people feel about their tools and workflows |
| Performance | Code Review Turnaround | Quality and speed of collaborative work |
| Activity | (Captured in DORA and Current/Legacy) | Intentionally not duplicated here |
| Communication | Code Review Turnaround, Context Switching | Quality of collaboration signals |
| Efficiency | Focus Time Days, Context Switching | Ability to do deep work without friction |

---

## Interpretation Guide

- **Focus Time Days** below 2/week is a red flag. Deep work is where engineering value is created. If meetings and interrupts consume more than 3 days per week, address the structural cause before expecting transformation progress.
- **Context Switching** above 8/day indicates workflow or organizational fragmentation. Check for too many Slack channels, unclear ownership boundaries, or on-call burden.
- **Friction Events** matter more as a trend than an absolute number. A team that reports 12 friction events in Week 3 and 6 in Week 10 is improving, even if 6 still feels high.
- **DX Score** below 50 requires intervention. Between 50-70 is the improvement zone. Above 70 is the target.
- **Code Review Turnaround** above 24 hours blocks flow. AI-assisted review (see [../agents/](../agents/)) can reduce this significantly.

---

## Connection to Other Categories

**Feeds:**
- Human Fulfillment -- developer experience directly impacts fulfillment scores
- DORA -- focus time and reduced friction drive faster lead times
- Innovation -- focus time creates space for exploration

**Fed by:**
- AI Utilization -- AI agents reducing toil improves DX scores
- Platform Outcomes -- self-service capabilities reduce friction events
- Code Health -- clean code and fast builds reduce developer frustration

---

## Organization Extension Point

> **YOUR_ORG:** Customize the DX survey to your specific toolchain and workflow pain points. If you already run developer surveys (e.g., through DX, Pluralsight Flow, or internal tools), map those to the KPIs above rather than creating a parallel survey. The friction log format should match your team's communication patterns -- Slack emoji reactions, Google Forms, or standup mentions all work.
