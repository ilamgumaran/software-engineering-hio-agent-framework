# HIO Agent Framework for Platform Engineering

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A comprehensive, open-source framework for transforming engineering organizations using **Harmonized Intelligence Orchestration (HIO)**. Built on the [HIO methodology](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid), this framework provides everything needed to shift from traditional role-based engineering to a model where humans and AI agents collaborate as cognitive partners — organized around outcomes, measured by fulfillment alongside delivery, and designed to produce emergence that neither humans nor AI can achieve alone.

**This repo is both the framework and the transformation playbook.** Fork it, customize `org/` for your team, and execute the 26-week accelerated transformation (Option 2).

---

## Why HIO

Traditional engineering organizations treat AI as a productivity tool — autocomplete, code suggestions, maybe some test generation. HIO treats AI as a **cognitive partner**. The difference matters:

| Traditional Engineering Org | HIO Engineering Org |
|---|---|
| Fixed roles (Backend Engineer, QA, PM) | 10 composable cognitive functions anyone can hold |
| AI as a tool (autocomplete, copilot) | 6 AI agent types as team members in every unit |
| Teams organized by technology or component | 5 cognitive units organized by platform outcome |
| Scrum ceremonies (standup, sprint review) | Harmonized sprints (emergence, fulfillment, deep work) |
| Velocity and story points | 9-category metrics across 3 layers |
| Job titles define identity | Cognitive functions evolve with growth |
| Burnout invisible until too late | Fulfillment measured and addressed every sprint |

The result: an organization where human creativity and AI capability **harmonize** to produce outcomes, insights, and innovations that neither could achieve independently — what HIO calls **emergence**.

---

## Framework Components

### The 10 Cognitive Functions

HIO replaces fixed job titles with composable **cognitive functions** — frequencies of engagement that any person can hold and develop. Each engineer holds 2-3 primary functions and actively grows into new ones. See [`cognitive-functions/`](cognitive-functions/README.md) for the full composition model.

| Function | Essence |
|---|---|
| **Builder** | Code creation, system construction, making things work |
| **Problem Framer** | Defining what to solve, why it matters, and what success looks like |
| **Pattern Integrator** | Seeing connections across domains, synthesizing knowledge |
| **Resonance Sensor** | Reading human dynamics, UX intuition, empathy for users and teammates |
| **Quality Guardian** | Ensuring correctness, reliability, security across all dimensions |
| **Growth Catalyst** | Mentoring, coaching, building capability in others |
| **Solution Architect** | Designing systems, evaluating tradeoffs, navigating constraints |
| **Stakeholder Harmonizer** | Aligning diverse interests toward shared outcomes |
| **Fresh-Eyes Observer** | Questioning assumptions, seeing what familiarity hides |
| **Learner** | Absorbing new knowledge, expanding bandwidth, teaching by learning |

**How roles map to functions:**

| Old Role | New Cognitive Functions |
|---|---|
| Senior Backend Engineer | Solution Architect + Builder + Pattern Integrator |
| Frontend Engineer | Builder + Resonance Sensor |
| QA Engineer | Quality Guardian + Problem Framer |
| Product Manager | Problem Framer + Growth Catalyst + Stakeholder Harmonizer |
| Junior Engineer | Builder + Learner + Fresh-Eyes Observer |
| Tech Lead | Solution Architect + Growth Catalyst + Pattern Integrator |
| Engineering Manager | Stakeholder Harmonizer + Growth Catalyst + Resonance Sensor |

---

### The 6 AI Agents

Each AI agent composes cognitive functions, just like humans. They are **team members**, not tools. See [`agents/`](agents/README.md) for full definitions and combination patterns.

| Agent | What It Does | Functions Composed |
|---|---|---|
| **Analysis Partner** | Pre-analyzes problems: data, patterns, prior art, risk | Problem Framer + Pattern Integrator + Resonance Sensor |
| **Code Co-Creator** | Full implementations from specs, tests, refactoring at scale | Builder + Quality Guardian + Pattern Integrator |
| **Architecture Explorer** | Generates and evaluates multiple architecture options with tradeoffs | Solution Architect + Pattern Integrator + Problem Framer |
| **Quality Analyst** | Continuous proactive monitoring: quality, performance, security | Quality Guardian + Resonance Sensor + Fresh-Eyes Observer |
| **Metrics Monitor** | Tracks all metrics, surfaces trends, flags anomalies | Pattern Integrator + Quality Guardian + Problem Framer |
| **Documentation & Knowledge** | Living docs, decision capture, searchable institutional knowledge | Pattern Integrator + Learner + Growth Catalyst |

---

### The 5 Cognitive Units

Cognitive units replace traditional scrum teams. Each is a group of 6-8 people (including AI agents) organized around a **platform outcome**, not a technology. People choose units based on interest and growth goals. Quarterly rotation is encouraged. See [`cognitive-units/`](cognitive-units/README.md).

| Unit | Outcome Focus | Why It Matters |
|---|---|---|
| **Experiment Velocity** | Making experiments faster to launch | The platform's core value proposition |
| **Scale & Reliability** | Platform handles anything thrown at it | Enterprise non-negotiable |
| **Developer Experience** | Making the platform a joy to build on | Adoption driver |
| **Intelligence Layer** | AI-native platform capabilities | Future differentiation |
| **Frontier** | Exploration of next-generation possibilities | The horizon |

---

### The 9 Metric Categories

HIO measures across **three layers** — you don't stop tracking what you already track, you add outcome and harmonization layers on top. See [`metrics/`](metrics/README.md) for all definitions.

| Layer | Category | What It Measures |
|---|---|---|
| **Current** | Current/Legacy | Stories, velocity, backlog health (what you track today) |
| **Outcome** | DORA | Deployment frequency, lead time, change failure rate, MTTR |
| **Outcome** | SPACE/DX | Developer experience, focus time, friction, satisfaction |
| **Outcome** | Platform Outcomes | Time ask-to-experiment, self-service rate, downstream NPS |
| **Outcome** | Code Health | Rework rate, defect escape rate, tech debt ratio |
| **Outcome** | Innovation | Innovation rate, exploration-to-production, ideas generated |
| **HIO** | Human Fulfillment | Purpose alignment, growth trajectory, burnout risk, energy |
| **HIO** | AI Utilization | Task sophistication (L1-L5), time savings, novel applications |
| **HIO** | Harmonization | Emergence rate, cross-function contribution, bandwidth expansion |

---

### Harmonized Sprint Workflows

Replace standard scrum with ceremonies designed for human-AI collaboration. See [`workflows/`](workflows/README.md).

| Ceremony | Replaces | Key Difference |
|---|---|---|
| **Sprint Kickoff** | Sprint Planning | AI pre-analysis before humans engage; outcomes, not story points |
| **Daily Harmony Check** | Daily Standup | Energy flow and shift decisions, not status updates (15 min) |
| **Sprint Outcome Review** | Sprint Review | Outcome demos + emergence showcase + downstream feedback |
| **Harmonization Retrospective** | Sprint Retro | Emergence, identity grip, fulfillment, one experiment |
| **Deep Work + Collaboration** | *(no equivalent)* | 4 hrs/day protected deep work + 2 hrs/day collaboration windows |
| **Exploration Time** | *(no equivalent)* | 3-4 hrs/week for curiosity-driven unknown-outcome work |

---

## The 26-Week Transformation

This framework includes a complete operational guide for a 26-week accelerated HIO transformation (Option 2), based on the [HIO Platform Engineering Org example](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid/tree/main/examples/platform-engineering-org). Exit criteria trump dates — phases extend if criteria aren't met. See [`transformation/`](transformation/README.md).

| Phase | Weeks | Goal | Key Deliverables |
|---|---|---|---|
| **0: Seed** | 1-3 | Baseline, alignment, pioneers | Metrics baseline, pioneer group, AI agent setup |
| **1: First Unit** | 4-10 | First cognitive unit, 3 sprints | Working unit, ceremony adoption, playbook v0.1 |
| **2: Prove & Expand** | 11-18 | Data-driven scaling | 3 units operational, coaches trained, comparison board |
| **3: Full Orchestration** | 19-26 | Full org transformation | All 30 people in units, full metrics, enterprise influence |

**Week 26 Targets:**
- DORA metrics at "High" or "Elite" tier
- Time from ask to experiment reduced 40%+
- Self-service rate > 70%
- Developer focus time at 3+ days/week
- AI task sophistication at Level 3+ average
- 8+ documented emergence events per quarter
- Fulfillment average at 7+/10

---

## Who Is This For

| You are... | Start here |
|---|---|
| A **leader** evaluating HIO for your org | [`PLAN.md`](PLAN.md) then [`plan/00-overview.md`](plan/00-overview.md) |
| An **engineer** joining a transforming team | [`cognitive-functions/README.md`](cognitive-functions/README.md) then [`workflows/README.md`](workflows/README.md) |
| An **HIO coach** facilitating the transformation | [`transformation/README.md`](transformation/README.md) then [`transformation/hio-coach-guide.md`](transformation/hio-coach-guide.md) |
| An **org** adopting the framework for your team | [`CUSTOMIZATION.md`](CUSTOMIZATION.md) then [`org/`](org/) |
| **Anyone** evaluating fit for a specific project type | [`examples/`](examples/) — 4 worked archetypes |
| **Anyone** trying to understand a specific file | [`DIRECTORY_GUIDE.md`](DIRECTORY_GUIDE.md) |

---

## Worked Examples

Four concrete project archetypes show the framework in action — using only the agents, cognitive functions, units, workflows, and metrics already in this repo. See [`examples/`](examples/).

| Archetype | Tactical gain | Reversibility | Time horizon |
|---|---|---|---|
| [Legacy Migration](examples/legacy-migration/) | Unblock EU regional launch via monolith carve-out | Mostly irreversible | 6 weeks |
| [New Platform](examples/new-platform/) | End ungoverned AI-agent sprawl with PromptOps MVP | Mostly reversible | 8 weeks |
| [Experimental](examples/experimental/) | Save ~120 senior eng hrs/mo if AI-augmented code review proves out | Fully reversible | 12 weeks |
| [Business-Critical](examples/business-critical/) | Protect $8M revenue exposure via 21-day PCI-DSS audit strike | Irreversible | 21 days |

The business-critical example is specifically designed to show the framework producing tactical short-term value **with what you have today** — no procurement, no new hires, no waiting on transformation phases.

---

## Reference Library

External knowledge that informs how the framework is applied. See [`reference/`](reference/).

| Reference | Topic |
|---|---|
| [`agent-engineering-7-skills.md`](reference/agent-engineering-7-skills.md) | The 7 technical capabilities for production AI agents (System Design, Tool/Contract Design, Retrieval, Reliability, Security, Eval/Observability, Product Thinking) — orthogonal to the 10 cognitive functions |
| [`industry-lessons-2024-2026.md`](reference/industry-lessons-2024-2026.md) | What worked and what failed in real AI transformations — Shopify, Meta, Amazon, Klarna, Goldman Sachs, JPMorgan, Duolingo, MIT, McKinsey |

---

## Quick Start

1. **Fork** this repository
2. **Read** [`plan/00-overview.md`](plan/00-overview.md) for the strategic picture
3. **Workshop** a purpose statement with your team (use the 4 HIO tests in [`org/profile.md`](org/profile.md))
4. **Customize** [`org/profile.md`](org/profile.md) with your team's context
5. **Map** your team to cognitive functions using [`org/cognitive-profiles.md`](org/cognitive-profiles.md)
6. **Capture** your baseline with [`metrics/baseline-survey.md`](metrics/baseline-survey.md)
7. **Begin** Phase 0 with [`transformation/phase-0-seed.md`](transformation/phase-0-seed.md)
8. **Configure** AI agents using [`CLAUDE.md`](CLAUDE.md) and [`tools/`](tools/)

---

## Directory Structure

```
/
├── cognitive-functions/     # 10 composable frequencies of engagement
├── agents/                  # 6 AI agent types with composition patterns
├── cognitive-units/         # 5 outcome-focused units (replace scrum teams)
├── workflows/               # Harmonized sprint ceremonies
├── metrics/                 # 9-category measurement system (3 layers)
├── transformation/          # 26-week transformation guide (4 phases)
├── examples/                # 4 worked project archetypes (legacy, new, experimental, business-critical)
├── reference/               # External knowledge (7 capabilities, industry lessons)
├── org/                     # Organization configuration templates
├── plan/                    # Strategic plan documents
├── domains/                 # Domain specialization (platform engineering)
├── templates/               # Jinja2 document generation templates
├── prompts/                 # Framework regeneration prompts
├── tools/                   # AI tool capability guides
├── agent-core/              # Implementation code (future)
├── docs/                    # Team-facing documentation
└── config/                  # Runtime configuration
```

See [`DIRECTORY_GUIDE.md`](DIRECTORY_GUIDE.md) for the purpose of every file.

---

## Foundation

This framework is built on the **[Harmonized Intelligence Orchestration (HIO) Framework](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid)** — a comprehensive methodology for designing organizations where humans and AI work as cognitive partners. The HIO framework provides the theoretical foundation, organizational design principles, and transformation methodology that this repo operationalizes into a concrete, forkable agent system.

If you're new to HIO, start with the [main framework](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid) to understand the philosophy, then return here for the engineering-specific implementation. The [platform engineering org example](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid/tree/main/examples/platform-engineering-org) is the specific transformation plan this framework executes (Option 2 — 26-week accelerated).

**Also built on:**
- **[Multi-Role Software Engineering Agent Framework](https://github.com/ilamgumaran/software-engineer-core-structure)** — The foundational agent architecture (9 roles, domain extension system, workflow patterns) that this framework evolves into the HIO model

---

## License

MIT — fork it, customize it, make it yours.
