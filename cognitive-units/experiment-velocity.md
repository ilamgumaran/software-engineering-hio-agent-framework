# Cognitive Unit: Experiment Velocity

## Purpose

Reduce the time and effort required to go from an experiment idea to a running experiment, making fast experimentation the platform's core value proposition.

---

## Outcome Focus

- **Reduce time-from-ask-to-experiment by 40%+** — measured end-to-end from request submission to live experiment (Platform Outcomes)
- **Increase self-service experiment launch rate** — more teams launching experiments without platform team intervention (Platform Outcomes)
- **Reduce experiment setup failures** — fewer failed or misconfigured experiment launches (Code Health)
- **Accelerate deployment pipeline for experiment code** — faster path from code to production for experiment-related changes (DORA)

---

## Success Metrics

| Metric | Category | Target | Measurement Frequency |
|---|---|---|---|
| Time Ask-to-Experiment | Platform Outcomes | 40% reduction from baseline | Weekly |
| Self-Service Rate | Platform Outcomes | >60% of experiments launched without intervention | Monthly |
| Deployment Frequency | DORA | Multiple deploys per day for experiment services | Weekly |
| Lead Time for Changes | DORA | <4 hours from commit to production | Weekly |
| Innovation Rate | Innovation | 3+ new experiment capabilities per quarter | Quarterly |
| Experiment Setup Failure Rate | Code Health | <5% of launches fail due to configuration | Weekly |
| New vs Maintenance Ratio | Innovation | >40% time on new capabilities | Monthly |

---

## Composition

### Human Members

- **Recommended size:** 4-6 humans
- **Essential functions:** [Builder](../cognitive-functions/builder.md), [Problem Framer](../cognitive-functions/problem-framer.md), [Solution Architect](../cognitive-functions/solution-architect.md)
- **Beneficial functions:** [Growth Catalyst](../cognitive-functions/growth-catalyst.md), [Resonance Sensor](../cognitive-functions/resonance-sensor.md), [Stakeholder Harmonizer](../cognitive-functions/stakeholder-harmonizer.md)

### AI Agents

| Agent | Priority | What It Does for This Unit |
|---|---|---|
| [Code Co-Creator](../agents/code-co-creator.md) | Primary | Accelerates experiment infrastructure code, generates boilerplate, reviews PRs |
| [Architecture Explorer](../agents/architecture-explorer.md) | High | Evaluates experiment platform design options, identifies scalability risks |
| [Analysis Partner](../agents/analysis-partner.md) | Medium | Analyzes experiment launch patterns to find bottlenecks and optimization opportunities |

---

## Working Agreements

1. **No fixed roles for tasks** — collectively decide who (human or AI) takes each function per sprint
2. **Prototype before designing** — build a rough working version before investing in architecture documents
3. **Thinking time is work time** — dedicated time for problem framing counts as delivery
4. **AI outputs are starting points, not final answers** — all AI-generated code and designs get human review
5. **Measure from the experimenter's perspective** — if the person launching the experiment does not feel it got faster, the metric does not matter
6. **Ship small, ship often** — prefer incremental improvements to large releases
7. **Document experiment patterns as they emerge** — successful patterns become self-service templates

---

## Typical Workflows

### New Experiment Type Onboarding

1. [Problem Framer](../cognitive-functions/problem-framer.md) interviews requesting team to understand experiment requirements
2. [Architecture Explorer](../agents/architecture-explorer.md) analyzes existing patterns for reusable components
3. [Builder](../cognitive-functions/builder.md) + [Code Co-Creator](../agents/code-co-creator.md) implement experiment template
4. [Solution Architect](../cognitive-functions/solution-architect.md) reviews for platform consistency
5. Requesting team validates with a real experiment launch

### Experiment Pipeline Optimization

1. [Analysis Partner](../agents/analysis-partner.md) identifies slowest stages in the current pipeline
2. [Problem Framer](../cognitive-functions/problem-framer.md) scopes which bottleneck to address this sprint
3. [Builder](../cognitive-functions/builder.md) + [Code Co-Creator](../agents/code-co-creator.md) implement the improvement
4. Measure time-to-experiment before and after the change

---

## Cross-Unit Dependencies

| Depends On | For What | Frequency |
|---|---|---|
| [Scale & Reliability](scale-reliability.md) | Infrastructure guarantees for experiment workloads | Ongoing |
| [Developer Experience](developer-experience.md) | Self-service tooling and SDK quality | Per sprint |
| [Intelligence Layer](intelligence-layer.md) | AI-powered experiment analysis capabilities | Quarterly |

| Depended On By | For What | Frequency |
|---|---|---|
| [Developer Experience](developer-experience.md) | API contracts and experiment platform interfaces | Per sprint |
| [Frontier](frontier.md) | Proven experiment patterns to explore extensions for | Monthly |
| [Intelligence Layer](intelligence-layer.md) | Experiment data pipelines for AI model training | Quarterly |

---

### Organization Extension Point

> **YOUR_ORG:** Customize the experiment types and pipeline stages to match your platform's experimentation model. The outcomes remain the same — speed and self-service — but the specifics depend on what "experiment" means in your context.
