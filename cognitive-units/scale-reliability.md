# Cognitive Unit: Scale & Reliability

## Purpose

Ensure the platform handles anything thrown at it — maintaining availability, recovering fast from failures, and providing the stable foundation every other unit depends on.

---

## Outcome Focus

- **Maintain 99.9%+ platform availability** — the non-negotiable enterprise baseline (Platform Outcomes)
- **Reduce MTTR below 30 minutes** — fast recovery matters more than preventing every incident (DORA)
- **Eliminate cascading failures** — a failure in one subsystem must not bring down others (Code Health)
- **Keep change failure rate below 5%** — changes to production should be safe by default (DORA)

---

## Success Metrics

| Metric | Category | Target | Measurement Frequency |
|---|---|---|---|
| Mean Time to Recovery (MTTR) | DORA | <30 minutes | Per incident |
| Change Failure Rate | DORA | <5% of deployments cause incidents | Weekly |
| Platform Availability | Platform Outcomes | 99.9%+ uptime | Daily |
| Defect Escape Rate | Code Health | <2% of defects reach production | Monthly |
| Build Duration | Code Health | <10 minutes for full pipeline | Weekly |
| Deployment Frequency | DORA | No degradation from reliability work | Weekly |
| Incident Response Satisfaction | SPACE/DX | >80% responder satisfaction | Monthly |

---

## Composition

### Human Members

- **Recommended size:** 5-6 humans
- **Essential functions:** [Quality Guardian](../cognitive-functions/quality-guardian.md), [Solution Architect](../cognitive-functions/solution-architect.md), [Builder](../cognitive-functions/builder.md)
- **Beneficial functions:** [Problem Framer](../cognitive-functions/problem-framer.md), [Pattern Integrator](../cognitive-functions/pattern-integrator.md), [Stakeholder Harmonizer](../cognitive-functions/stakeholder-harmonizer.md)

### AI Agents

| Agent | Priority | What It Does for This Unit |
|---|---|---|
| [Quality Analyst](../agents/quality-analyst.md) | Primary | Monitors test coverage, identifies reliability gaps, validates failure scenarios |
| [Code Co-Creator](../agents/code-co-creator.md) | High | Implements resilience patterns, generates chaos tests, reviews infrastructure code |
| [Metrics Monitor](../agents/metrics-monitor.md) | High | Tracks availability and incident metrics, surfaces trends before they become outages |

---

## Working Agreements

1. **No fixed roles for tasks** — collectively decide who (human or AI) takes each function per sprint
2. **Incidents are learning opportunities, not blame events** — every postmortem produces a systemic improvement
3. **Reliability work is not separate from feature work** — reliability is built into every change, not bolted on after
4. **AI outputs are starting points, not final answers** — automated alerts and analyses get human judgment applied
5. **Thinking time is work time** — time spent on failure mode analysis counts as delivery
6. **Runbooks are living documents** — update them during every incident, not after
7. **Chaos is a practice, not an event** — regular failure injection is part of the sprint rhythm

---

## Typical Workflows

### Incident Response and Learning

1. [Metrics Monitor](../agents/metrics-monitor.md) detects anomaly and alerts the unit
2. [Quality Guardian](../cognitive-functions/quality-guardian.md) leads triage, determines severity and blast radius
3. [Builder](../cognitive-functions/builder.md) + [Code Co-Creator](../agents/code-co-creator.md) implement the fix
4. [Solution Architect](../cognitive-functions/solution-architect.md) identifies the systemic cause for postmortem
5. Unit converts findings into resilience improvements for the next sprint

### Resilience Improvement Cycle

1. [Quality Analyst](../agents/quality-analyst.md) analyzes recent incidents for common failure patterns
2. [Pattern Integrator](../cognitive-functions/pattern-integrator.md) connects patterns across subsystems
3. [Builder](../cognitive-functions/builder.md) + [Code Co-Creator](../agents/code-co-creator.md) implement circuit breakers, retries, or isolation improvements
4. [Quality Guardian](../cognitive-functions/quality-guardian.md) validates through chaos testing

---

## Cross-Unit Dependencies

| Depends On | For What | Frequency |
|---|---|---|
| [Developer Experience](developer-experience.md) | Observability tooling and developer-friendly incident dashboards | Per sprint |
| [Intelligence Layer](intelligence-layer.md) | AI-assisted anomaly detection capabilities | Quarterly |
| [Frontier](frontier.md) | Early warning on emerging infrastructure patterns | Monthly |

| Depended On By | For What | Frequency |
|---|---|---|
| [Experiment Velocity](experiment-velocity.md) | Infrastructure guarantees for experiment workloads | Ongoing |
| [Developer Experience](developer-experience.md) | Reliable platform for self-service tooling | Ongoing |
| [Intelligence Layer](intelligence-layer.md) | Compute infrastructure for AI workloads | Per sprint |
| [Frontier](frontier.md) | Stable sandbox environments for exploration | Per sprint |

---

### Organization Extension Point

> **YOUR_ORG:** Adjust availability targets and MTTR goals to match your SLA commitments. The principle — fast recovery over perfect prevention — applies universally, but the specific numbers depend on your enterprise contracts.
