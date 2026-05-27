# Metrics Framework

The HIO metrics framework operates across three layers. Each layer serves a distinct purpose, and together they provide a complete picture of transformation health.

Measurement begins Day 1 of the transformation. Do not wait for perfect instrumentation -- start capturing what you can and refine as you go.

---

## The Three-Layer Model

**Layer 1: Current** -- What you track today. Do not stop. These provide continuity and stakeholder confidence during transformation.

**Layer 2: Outcome** -- What the platform actually achieves. DORA, developer experience, platform adoption, code quality, and innovation capacity. These prove value.

**Layer 3: HIO** -- How humans and AI harmonize. Human fulfillment, AI utilization, and the emergence of new collaborative patterns. These drive the transformation and differentiate HIO from conventional approaches.

---

## The 10 Categories

| Category | Layer | What It Measures | File |
|---|---|---|---|
| Current/Legacy | Layer 1 (Current) | Velocity, throughput, backlog health | [current-legacy.md](current-legacy.md) |
| DORA | Layer 2 (Outcome) | Deployment performance and reliability | [dora.md](dora.md) |
| Operational Health | Layer 2 (Outcome) | Volume, availability, errors, tickets, testability, merge acceptance | [operational-health.md](operational-health.md) |
| SPACE/DX | Layer 2 (Outcome) | Developer experience and focus | [space-dx.md](space-dx.md) |
| Platform Outcomes | Layer 2 (Outcome) | Platform adoption and business impact | [platform-outcomes.md](platform-outcomes.md) |
| Code Health | Layer 2 (Outcome) | Code quality and maintenance burden | [code-health.md](code-health.md) |
| Innovation | Layer 2 (Outcome) | Exploration capacity and idea throughput | [innovation.md](innovation.md) |
| Human Fulfillment | Layer 3 (HIO) | Wellbeing, growth, and purpose alignment | [human-fulfillment.md](human-fulfillment.md) |
| AI Utilization | Layer 3 (HIO) | Depth and effectiveness of AI agent use | [ai-utilization.md](ai-utilization.md) |
| Harmonization | Layer 3 (HIO) | Human-AI collaboration and emergence | [harmonization.md](harmonization.md) |

## Traceability to Objectives

Metrics alone don't drive decisions. They must connect to objectives:

```
tracking/objectives/ → defines WHY we measure
tracking/use-cases/  → defines WHAT we're building
tracking/decisions/  → records WHAT we chose and WHY
metrics/             → measures HOW WELL it's going
```

See [tracking/README.md](../tracking/README.md) for the full traceability system.

---

## How Metrics Connect

The three layers form a reinforcing loop:

- **Layer 1 (Current)** validates stability. If sprint velocity or backlog health degrades during transformation, something is wrong. These are the guardrails.
- **Layer 2 (Outcome)** proves value. Improving DORA metrics, developer experience, and platform adoption demonstrates that the transformation is producing tangible results.
- **Layer 3 (HIO)** drives the transformation. Human fulfillment and AI utilization feed into better outcomes. Harmonization -- the emergence of new collaborative patterns -- is the leading indicator that the model is working.

The flow: HIO metrics improve first (people engage differently with AI), which drives Outcome metrics (better code, faster delivery, happier developers), which sustains Current metrics (velocity holds or improves while the org transforms).

When layers conflict -- for example, AI utilization is up but developer experience is down -- investigate the friction. The metrics are telling you something important about the human-AI interaction pattern.

---

## Measurement Cadence

| Cadence | What | Template |
|---|---|---|
| Daily | DORA automated capture (deployment frequency, lead time) | -- |
| Weekly | Harmony Pulse across all three layers | [weekly-harmony-pulse.md](weekly-harmony-pulse.md) |
| Monthly | Deep Dive with trend analysis across all 9 categories | [monthly-deep-dive.md](monthly-deep-dive.md) |
| Quarterly | Evolution Review with full structural assessment | [quarterly-evolution.md](quarterly-evolution.md) |
| Phase gate | Comparison Board against exit criteria | [../transformation/](../transformation/) |

The Metrics Monitor agent (see [../agents/metrics-monitor.md](../agents/metrics-monitor.md)) automates collection and anomaly detection. Human interpretation remains essential -- the agent surfaces data, people make meaning.

---

## Baseline Capture

Run the [baseline-survey.md](baseline-survey.md) during Phase 0 (Weeks 1-2) to establish starting points for all three layers. Combine survey data with automated tool analysis (CI/CD logs, calendar data, code repository metrics) for a complete baseline.

Without a baseline, you cannot demonstrate progress. Without demonstrating progress, you cannot sustain transformation.

---

## Anti-Patterns

- **Measuring to judge instead of learn.** Metrics exist to surface patterns and guide decisions, not to evaluate individuals or rank teams.
- **Optimizing one layer at the expense of others.** Pushing DORA metrics while ignoring human fulfillment creates burnout. Focusing on fulfillment while ignoring delivery creates organizational risk.
- **Using metrics to compare teams instead of tracking unit progress.** Each cognitive unit has different starting points and contexts. Compare a unit to its own baseline, not to other units.
- **Letting metrics replace conversation.** Numbers identify where to look. Conversations reveal what is actually happening. The weekly Harmony Pulse is a conversation template, not just a data collection form.
- **Chasing metric perfection early.** Imperfect measurement that starts on Day 1 beats perfect measurement that starts on Day 60.

---

## Organization Extension Point

> **YOUR_ORG:** Start by mapping your existing metrics to Layer 1. Identify which Layer 2 metrics you already capture (even partially). Layer 3 will be new for most organizations -- begin with the baseline survey and build from there. Your specific Layer 1 metrics will differ from the defaults in [current-legacy.md](current-legacy.md); replace them with what you actually track today.
