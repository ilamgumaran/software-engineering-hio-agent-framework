# HIO Agent Framework: Overview

## Vision

An AI-native platform engineering organization where humans and AI agents collaborate as cognitive partners, organized around outcomes instead of roles, measured by fulfillment alongside delivery.

The Harmonized Intelligence Orchestration (HIO) framework replaces the traditional role-based engineering org with a composable system of **cognitive functions**, **AI agents**, and **outcome-oriented cognitive units** -- transforming a ~30-person platform engineering team over 26 weeks.

---

## Problem Statement

| Problem | Impact | HIO Solution |
|---------|--------|--------------|
| Output-not-outcome metrics | Teams optimize for velocity instead of value | Outcome-focused cognitive units |
| AI-as-tool-not-partner | AI used for autocomplete, not collaboration | 6 integrated AI agent types |
| Role identity silos | "I'm a backend engineer" limits contribution | Composable cognitive functions |
| No fulfillment measurement | Burnout invisible until too late | Human fulfillment metrics |
| No emergence zone | Human-AI collaboration doesn't produce novel value | Harmonized sprint model |
| No DORA metrics | Engineering performance unmeasured | 9-category metrics framework |

---

## Solution Architecture

The HIO framework composes five interconnected layers:

1. **10 Cognitive Functions** -- portable human capabilities that replace fixed roles
2. **6 AI Agents** -- specialized AI partners that amplify cognitive functions
3. **5 Cognitive Units** -- outcome-oriented teams that replace traditional squads
4. **Harmonized Sprints** -- a cadence model that creates space for emergence
5. **9-Category Metrics** -- measurement that values fulfillment alongside delivery

These layers deploy across a **4-phase, 26-week transformation** from seed to full orchestration. See `plan/03-implementation-guide.md` for the phase-by-phase rollout and `transformation/` for operational detail.

---

## The 6 AI Agents

| Agent | Purpose | Functions Composed |
|-------|---------|-------------------|
| **Analysis Partner** | Investigate problems, surface patterns, sense organizational resonance | Problem Framer + Pattern Integrator + Resonance Sensor |
| **Code Co-Creator** | Collaborative code authoring with quality and pattern awareness | Builder + Quality Guardian + Pattern Integrator |
| **Architecture Explorer** | Evaluate design options, map system boundaries, frame trade-offs | Solution Architect + Pattern Integrator + Problem Framer |
| **Quality Analyst** | Assess quality from multiple angles, observe with fresh eyes | Quality Guardian + Resonance Sensor + Fresh-Eyes Observer |
| **Metrics Monitor** | Track patterns across 9 metric categories, flag anomalies | Pattern Integrator + Quality Guardian + Problem Framer |
| **Documentation & Knowledge** | Capture decisions, synthesize knowledge, accelerate learning | Pattern Integrator + Learner + Growth Catalyst |

See `agents/` for detailed agent configurations and `plan/01-capabilities.md` for the full capability matrix.

---

## The 10 Cognitive Functions

| Function | Essence |
|----------|---------|
| **Builder** | Translates intent into working systems -- code, infrastructure, pipelines |
| **Problem Framer** | Shapes ambiguous situations into solvable problems |
| **Pattern Integrator** | Connects signals across domains to reveal systemic insight |
| **Resonance Sensor** | Detects emotional and organizational currents that data misses |
| **Quality Guardian** | Holds the standard for correctness, reliability, and craft |
| **Growth Catalyst** | Creates conditions for people and systems to develop |
| **Solution Architect** | Designs structures that balance constraints with possibility |
| **Stakeholder Harmonizer** | Aligns diverse interests without flattening them |
| **Fresh-Eyes Observer** | Sees what familiarity obscures -- questions the unquestioned |
| **Learner** | Extracts transferable knowledge from experience |

See `cognitive-functions/` for full function definitions.

---

## Goals

| Goal | Metric | Target (Week 26) |
|------|--------|-------------------|
| Deployment frequency | DORA | Daily per cognitive unit |
| Lead time for changes | DORA | < 1 day |
| Change failure rate | DORA | < 5% |
| Mean time to recovery | DORA | < 1 hour |
| Developer satisfaction | SPACE/DX | > 4.2 / 5.0 |
| Human fulfillment score | Human Fulfillment | > 8.0 / 10.0 |
| AI agent adoption | AI Utilization | L4 (Collaborative Partner) across all units |
| Platform reliability | Platform Outcomes | 99.9% availability |
| Emergence events logged | Harmonization | > 2 per unit per sprint |
| Innovation allocation | Innovation | 20% of sprint capacity |

---

## Constraints

- **Org size:** ~30 people, organized into 5 cognitive units of ~6 each
- **Timeline:** 26 weeks from seed to full orchestration
- **Delivery continuity:** Must maintain delivery during transformation (15% throughput dip acceptable)
- **Security:** All AI tools must pass organizational security review before deployment
- **Adoption model:** Must be invitational, not forced -- volunteers first, evidence second

---

## Stakeholders

| Stakeholder | Interest | Engagement |
|-------------|----------|------------|
| **Engineering Leadership** | ROI, velocity, retention | Weekly metrics reviews, phase gate approvals |
| **Engineering Team** | Meaningful work, skill growth, autonomy | Voluntary participation, cognitive profiling, retrospectives |
| **Downstream Teams** | Platform reliability, API stability | SLA dashboards, feedback loops |
| **Security** | Data protection, AI guardrails, compliance | Tool approval process, policy co-creation |
| **HR / People Ops** | Role definitions, career paths, wellbeing | Cognitive function career framework, fulfillment data |

---

## Tool Strategy

| Tool | Role in HIO | Primary Agents |
|------|-------------|---------------|
| **Claude Code** | Orchestration layer, agent execution, MCP integrations | All agents |
| **GitHub Copilot** | IDE-level code generation and suggestion | Code Co-Creator |
| **Gemini Enterprise** | Large-context analysis, document reasoning | Analysis Partner, Architecture Explorer |
| **Glean** | Enterprise knowledge search and retrieval | Documentation & Knowledge, Analysis Partner |

See `plan/05-foundational-tools.md` for the full 8-layer infrastructure toolchain and `org/infrastructure.md` for organization-specific tool configuration.
