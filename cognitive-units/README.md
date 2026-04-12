# Cognitive Units

## What Is a Cognitive Unit

A **cognitive unit** is a group of 6-8 people (including AI agents) organized around a platform outcome, not a technology. It replaces traditional scrum teams. Members hold **cognitive functions** rather than job titles. Units execute **Harmonized Sprints** as their primary delivery rhythm.

Each unit is a self-contained problem-solving organism. It has the collective intelligence to frame problems, build solutions, ensure quality, and sense whether stakeholders are actually served — all without waiting on external approvals or handoffs.

---

## Why Units Instead of Teams

| Dimension | Traditional Team | Cognitive Unit |
|---|---|---|
| **Organizing principle** | Technical component or service | Platform outcome |
| **Membership** | Fixed by manager assignment | Chosen by interest and growth goals |
| **Measurement** | Velocity, story points | Outcome metrics across 9 categories |
| **Ceremonies** | Standup, retro, planning | Harmonized Sprint rituals with resonance checks |
| **AI integration** | Tools used by individuals | AI agents as full unit members with defined roles |
| **Growth model** | Promotion ladder | Quarterly rotation across units, function expansion |
| **Identity** | "I'm on the payments team" | "I hold Builder and Pattern Integrator in Experiment Velocity" |

---

## The 5 Platform Engineering Units

| Unit | Outcome Focus | Key Metrics | Typical Size |
|---|---|---|---|
| [Experiment Velocity](experiment-velocity.md) | Making experiments faster to launch | Time Ask-to-Experiment, Deployment Frequency | 6-8 |
| [Scale & Reliability](scale-reliability.md) | Platform handles anything thrown at it | MTTR, Platform Availability | 6-8 |
| [Developer Experience](developer-experience.md) | Making the platform a joy to build on | Self-Service Rate, DX Score | 6-7 |
| [Intelligence Layer](intelligence-layer.md) | AI-native platform capabilities | AI Task Sophistication, Novel Applications | 6-7 |
| [Frontier](frontier.md) | Exploration of next-generation possibilities | Exploration-to-Production, Emergence Rate | 6-7 |

---

## Unit Composition

Each cognitive unit contains:

- **4-6 humans** with diverse cognitive function coverage
- **2-4 AI agents** (minimum: [Code Co-Creator](../agents/code-co-creator.md) + one other)
- At least one person holding the [Stakeholder Harmonizer](../cognitive-functions/stakeholder-harmonizer.md) function
- **Function coverage goal:** all 10 cognitive functions represented across members (a single person may hold 2-3 functions)

No unit should duplicate another unit's exact composition. Diversity of perspective is the point.

---

## Cross-Unit Coordination

Units are autonomous but not isolated. Coordination happens through:

- **Shared metrics dashboard** — all 9 metric categories visible to every unit
- **Dependency tracking** — each unit file documents what it depends on and who depends on it
- **Program-level sync** — a lightweight weekly sync where one representative per unit surfaces blockers and opportunities
- **Rotation overlap** — people who recently rotated carry context between units naturally

---

## Quarterly Rotation

**Why rotate:** Growth comes from seeing problems from multiple angles. A [Builder](../cognitive-functions/builder.md) who has worked in Scale & Reliability brings reliability instincts to Experiment Velocity.

**How to rotate:** At the end of each quarter, anyone can express interest in joining a different unit. Units negotiate composition to maintain function coverage. No one is forced to move.

**What stays stable:** The unit's purpose, outcome focus, and working agreements persist across rotations. Institutional memory lives in documentation and AI agent context.

**What changes:** The humans in the unit, and consequently the specific energy and perspective the unit brings to its outcome.

---

## Creating a New Unit

Use [_template.md](_template.md) as a starting point. Follow these five steps:

1. **Define the outcome** — What platform result does this unit exist to achieve? If you cannot state it in one sentence, it is not focused enough.
2. **Select success metrics** — Draw from the 9 metric categories. Choose 6-8 metrics that directly measure the outcome.
3. **Determine composition** — Identify essential cognitive functions and which AI agents the unit needs most.
4. **Document dependencies** — Map what you need from other units and what they will need from you.
5. **Establish working agreements** — The unit's first act is agreeing on how it will work together.

---

### Organization Extension Point

> **YOUR_ORG:** Define your units based on your platform's value proposition. Five units work well for a ~30-person org. Smaller orgs may start with 2-3 units; larger orgs may need 6-8. The principle holds: organize around outcomes, not technologies.
