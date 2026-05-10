# HIO Agentic Workflow Toolkit

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

The **main agentic workflow toolkit** used day-to-day inside an HIO-aligned engineering organization. 6 AI agent types, harmonized sprint ceremonies, agent skills, and the multi-repo orchestration framework that governs the family of repos.

This repo is **downstream** of the engineering-org setup. The org structure -- roles, goals, effectiveness measures, transformation plan -- lives in [`software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure). Read that first if you're setting up an org; come here when you're running with agents inside one.

---

## Where this sits in the family

| # | Layer | Repo | What it is |
|---|---|---|---|
| 1 | Cognition foundation | [`thoughtexperiments`](https://github.com/ilamgumaran/thoughtexperiments) | Resonant Cognition -- a psychology-of-mind theory |
| 2 | Generalized HIO framework | [`thought-org-with-human-ai-hybrid`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid) | Orchestrating organic + inorganic intelligence at any scale |
| 3 | Engineering org applied | [`software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure) | Setting up an engineering organization on HIO principles -- roles, goals, effectiveness measures, transformation plan |
| 4 | **Day-to-day agentic toolkit** (this repo) | `software-engineering-hio-agent-framework` | The 6 agent types, sprint ceremonies, agent skills, and multi-repo orchestration used inside such an org |

---

## What this toolkit gives you

### The 6 AI Agents

Each agent composes 2-3 of the 10 cognitive functions defined upstream. Agents are team members in cognitive units, not standalone tools.

| Agent | What It Does | Functions Composed |
|---|---|---|
| **Analysis Partner** | Pre-analyzes problems: data, patterns, prior art, risk | Problem Framer + Pattern Integrator + Resonance Sensor |
| **Code Co-Creator** | Full implementations from specs, tests, refactoring at scale | Builder + Quality Guardian + Pattern Integrator |
| **Architecture Explorer** | Generates and evaluates multiple architecture options with tradeoffs | Solution Architect + Pattern Integrator + Problem Framer |
| **Quality Analyst** | Continuous proactive monitoring: quality, performance, security | Quality Guardian + Resonance Sensor + Fresh-Eyes Observer |
| **Metrics Monitor** | Tracks all metrics, surfaces trends, flags anomalies | Pattern Integrator + Quality Guardian + Problem Framer |
| **Documentation & Knowledge** | Living docs, decision capture, searchable institutional knowledge | Pattern Integrator + Learner + Growth Catalyst |

See [`agents/`](agents/) for full definitions.

### Harmonized Sprint Ceremonies

The day-to-day rhythm of an HIO-aligned engineering team. Replaces standard scrum.

| Ceremony | Replaces | Key Difference |
|---|---|---|
| **Sprint Kickoff** | Sprint Planning | AI pre-analysis before humans engage; outcomes, not story points |
| **Daily Harmony Check** | Daily Standup | Energy flow and shift decisions, not status updates (15 min) |
| **Sprint Outcome Review** | Sprint Review | Outcome demos + emergence showcase + downstream feedback |
| **Harmonization Retrospective** | Sprint Retro | Emergence, identity grip, fulfillment, one experiment |
| **Deep Work + Collaboration** | *(no equivalent)* | 4 hrs/day protected deep work + 2 hrs/day collaboration windows |
| **Exploration Time** | *(no equivalent)* | 3-4 hrs/week for curiosity-driven unknown-outcome work |

See [`workflows/`](workflows/).

### Agent Skills and Multi-Repo Orchestration

The toolkit also carries the agent skills (`skills/`) and the **multi-repo orchestration framework** at [`multi-repo-orchestration/`](multi-repo-orchestration/) -- the cross-repo agent governance layer that any coding agent uses to navigate the family.

### Per-Tool Guides

[`tools/`](tools/) contains per-runtime guides: Claude Code, GitHub Copilot, Gemini Enterprise, Glean. Each shows how to operate the 6 agent types in that runtime.

---

## What lives where (and where it does NOT live)

This toolkit and the upstream engg-org-setup repo overlap in places. Where they overlap, the canonical home is upstream and this repo references it:

| Topic | Canonical home |
|---|---|
| HIO principles and methodology | [`thought-org-with-human-ai-hybrid`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid) |
| Cognition theory underlying HIO | [`thoughtexperiments`](https://github.com/ilamgumaran/thoughtexperiments) |
| Engineering-org **setup**, role taxonomy, goals, effectiveness measures, 26-week transformation | [`software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure) |
| Cognitive functions (10), cognitive units (5), metric categories (9) | This repo (operational definitions used by agents) -- but the *org-level* application of these is upstream |
| 6 AI agent types, agent skills, sprint ceremonies, multi-repo orchestration | This repo (canonical) |
| Per-tool runtime guides (Claude Code, Copilot, Gemini, Glean) | This repo (canonical) |

In the previous structure, this repo carried both the org-setup content and the day-to-day agent operations. The hierarchy has been clarified: org-setup belongs upstream; this repo focuses on day-to-day operations. Operational definitions of cognitive functions / units / metrics are kept here because agents reference them at runtime, but their *org-level meaning and goals* are owned upstream.

---

## Who Is This For

| You are... | Start here |
|---|---|
| Setting up the engg org on HIO | Read [`software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure) first; come back when you're ready to run agents |
| An **engineer** in an HIO-aligned org running with agents | [`agents/README.md`](agents/README.md) then [`workflows/README.md`](workflows/README.md) |
| An **HIO coach** | [`transformation/README.md`](transformation/README.md) -- but note: org-level transformation guidance lives upstream |
| A **coding agent** entering this repo | [`AGENTS.md`](AGENTS.md) then [`multi-repo-orchestration/`](multi-repo-orchestration/) |
| **Anyone** trying to understand a specific file | [`DIRECTORY_GUIDE.md`](DIRECTORY_GUIDE.md) |

---

## Quick Start

1. Confirm your engineering org is set up on HIO using [`software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure)
2. Fork this repo into your org's source control
3. Configure AI agents using [`AGENTS.md`](AGENTS.md), [`CLAUDE.md`](CLAUDE.md), and [`tools/`](tools/)
4. Adopt sprint ceremonies starting from [`workflows/sprint-kickoff.md`](workflows/sprint-kickoff.md)
5. Onboard agents to the family via [`multi-repo-orchestration/prompts/repo-onboarding.md`](multi-repo-orchestration/prompts/repo-onboarding.md)

---

## Directory Structure

```
/
+-- agents/                  # 6 AI agent types with composition patterns
+-- cognitive-functions/     # 10 composable frequencies of engagement (operational)
+-- cognitive-units/         # 5 outcome-focused units (operational)
+-- workflows/               # Harmonized sprint ceremonies
+-- metrics/                 # 9-category measurement system (operational)
+-- transformation/          # Transformation execution -- pairs with org-setup repo upstream
+-- examples/                # 4 worked project archetypes
+-- reference/               # External knowledge (incl. AAIF, MCP/A2A, OWASP, Centaur, ...)
+-- multi-repo-orchestration/   # Cross-repo agent framework that governs the family
+-- org/                     # Organization configuration templates
+-- domains/                 # Domain specialization (platform engineering)
+-- templates/               # Jinja2 document generation templates
+-- prompts/                 # Framework regeneration prompts
+-- tools/                   # AI tool capability guides (per runtime)
+-- agent-core/              # Implementation code (future)
+-- docs/                    # Team-facing documentation
+-- config/                  # Runtime configuration
```

See [`DIRECTORY_GUIDE.md`](DIRECTORY_GUIDE.md) for the purpose of every file.

---

## Foundation

This toolkit is built on, in order of upstream-ness:

- **[Resonant Cognition Framework](https://github.com/ilamgumaran/thoughtexperiments)** -- the cognition theory underlying HIO
- **[The HIO Framework](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid)** -- the generalized methodology
- **[HIO-Based Engineering Org Setup](https://github.com/ilamgumaran/software-engineer-core-structure)** -- the org-setup template that this toolkit operates inside

---

## License

MIT -- fork it, customize it, make it yours.
