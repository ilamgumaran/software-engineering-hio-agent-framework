# Cognitive Unit: Developer Experience

## Purpose

Make the platform a joy to build on, driving adoption by reducing friction for every team that depends on platform capabilities.

---

## Outcome Focus

- **Achieve >70% self-service rate** — most platform interactions should not require a support ticket (Platform Outcomes)
- **Reduce time-to-first-deploy for new teams below 1 day** — onboarding should feel effortless (Platform Outcomes)
- **Achieve downstream team NPS improvement of 15+ points** — the people using the platform should measurably like it more (Platform Outcomes)
- **Improve DX Score quarter over quarter** — developer satisfaction with platform tooling keeps rising (SPACE/DX)

---

## Success Metrics

| Metric | Category | Target | Measurement Frequency |
|---|---|---|---|
| Self-Service Rate | Platform Outcomes | >70% of interactions without human intervention | Monthly |
| Time to First Deploy | Platform Outcomes | <1 day for new teams | Per onboarding |
| Downstream NPS | Platform Outcomes | 15+ point improvement from baseline | Quarterly |
| DX Score | SPACE/DX | Quarter-over-quarter improvement | Quarterly |
| Code Review Turnaround | SPACE/DX | <4 hours average | Weekly |
| Documentation Coverage | Code Health | >90% of platform APIs documented | Monthly |
| Support Ticket Volume | Platform Outcomes | Decreasing trend | Monthly |
| Onboarding Completion Rate | Platform Outcomes | >95% of new teams deploy within target | Monthly |

---

## Composition

### Human Members

- **Recommended size:** 4-5 humans
- **Essential functions:** [Resonance Sensor](../cognitive-functions/resonance-sensor.md), [Builder](../cognitive-functions/builder.md), [Growth Catalyst](../cognitive-functions/growth-catalyst.md)
- **Beneficial functions:** [Fresh-Eyes Observer](../cognitive-functions/fresh-eyes-observer.md), [Stakeholder Harmonizer](../cognitive-functions/stakeholder-harmonizer.md), [Problem Framer](../cognitive-functions/problem-framer.md)

### AI Agents

| Agent | Priority | What It Does for This Unit |
|---|---|---|
| [Documentation & Knowledge](../agents/documentation-knowledge.md) | Primary | Generates and maintains API docs, tutorials, and onboarding guides |
| [Code Co-Creator](../agents/code-co-creator.md) | High | Builds SDKs, CLI tools, and developer-facing platform interfaces |
| [Analysis Partner](../agents/analysis-partner.md) | Medium | Analyzes support patterns to identify recurring friction points |

---

## Working Agreements

1. **No fixed roles for tasks** — collectively decide who (human or AI) takes each function per sprint
2. **Use the platform as a downstream team would** — dogfooding is mandatory, not optional
3. **Every support ticket is a design failure** — if someone had to ask, the self-service path was not clear enough
4. **AI outputs are starting points, not final answers** — generated documentation gets human review for accuracy and tone
5. **Thinking time is work time** — user research and empathy mapping count as delivery
6. **Measure experience, not just functionality** — a working feature that is hard to discover has not shipped
7. **Fresh eyes are a superpower** — actively seek feedback from people unfamiliar with the platform

---

## Typical Workflows

### Developer Friction Reduction

1. [Analysis Partner](../agents/analysis-partner.md) mines support tickets and Slack questions for recurring themes
2. [Resonance Sensor](../cognitive-functions/resonance-sensor.md) validates findings through direct conversation with downstream teams
3. [Problem Framer](../cognitive-functions/problem-framer.md) scopes the highest-impact friction point
4. [Builder](../cognitive-functions/builder.md) + [Code Co-Creator](../agents/code-co-creator.md) build the improvement
5. [Documentation & Knowledge](../agents/documentation-knowledge.md) updates guides and API references

### New Team Onboarding Optimization

1. [Fresh-Eyes Observer](../cognitive-functions/fresh-eyes-observer.md) walks through the onboarding flow from scratch
2. [Growth Catalyst](../cognitive-functions/growth-catalyst.md) identifies where new teams get stuck or slow down
3. [Builder](../cognitive-functions/builder.md) + [Code Co-Creator](../agents/code-co-creator.md) streamline the onboarding path
4. Measure time-to-first-deploy before and after changes

---

## Cross-Unit Dependencies

| Depends On | For What | Frequency |
|---|---|---|
| [Experiment Velocity](experiment-velocity.md) | API contracts and experiment platform interfaces | Per sprint |
| [Scale & Reliability](scale-reliability.md) | Reliable platform underneath self-service tooling | Ongoing |
| [Intelligence Layer](intelligence-layer.md) | AI-powered documentation and developer assistance | Quarterly |

| Depended On By | For What | Frequency |
|---|---|---|
| [Experiment Velocity](experiment-velocity.md) | Self-service tooling and SDK quality | Per sprint |
| [Scale & Reliability](scale-reliability.md) | Observability tooling and developer-friendly dashboards | Per sprint |
| [Intelligence Layer](intelligence-layer.md) | Developer experience for AI tool integration | Per sprint |
| [Frontier](frontier.md) | Documentation patterns for prototype handoff | Monthly |

---

### Organization Extension Point

> **YOUR_ORG:** Customize the NPS targets and self-service metrics to reflect your platform's current maturity. Early-stage platforms may set lower initial targets with steeper improvement curves.
