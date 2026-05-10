# Reference Library

Structured external knowledge that informs how this framework is applied. These references are **not** the framework -- the framework lives in `cognitive-functions/`, `agents/`, `cognitive-units/`, `workflows/`, `metrics/`, `transformation/`, and `multi-repo-orchestration/`. References capture *external lessons* (talks, research, industry case studies, standards) that shape how we adapt the framework to real engineering work.

Each reference is read once, translated into framework concepts, and then linked from the places it informs.

---

## Current References

| File | Source type | Topic | Where it shows up |
|---|---|---|---|
| [agent-engineering-7-skills.md](agent-engineering-7-skills.md) | Talk | 7 technical capabilities for production AI agents (System Design, Tool/Contract, Retrieval, Reliability, Security, Eval/Observability, Product Thinking) | Skills development in `domains/platform-engineering/skills.md`, role transitions in `transformation/`, deep-work tasks in `workflows/` |
| [industry-lessons-2024-2026.md](industry-lessons-2024-2026.md) | Industry case studies | What worked / what failed in real AI transformations (Shopify, Meta, Amazon, Klarna, Goldman, JPMorgan, Duolingo, MS, MIT, McKinsey) | Risk register in `transformation/risk-management.md`, change strategy in `org/policies.md`, principles in `CLAUDE.md` |
| [agents-md-and-agentic-ai-foundation.md](agents-md-and-agentic-ai-foundation.md) | Open standards | The public AGENTS.md convention and the Linux Foundation Agentic AI Foundation (AAIF) | `multi-repo-orchestration/agent-spec/AGENTS-SPEC-v1.md`, scorecard A1 dimension |
| [agent-protocols-mcp-a2a.md](agent-protocols-mcp-a2a.md) | Open protocols | Model Context Protocol (Anthropic) and Agent2Agent (Google) | `multi-repo-orchestration/tools/`, `multi-repo-orchestration/skills/`, future cross-repo MCP server |
| [anthropic-effective-agents-patterns.md](anthropic-effective-agents-patterns.md) | Vendor research | Anthropic's 5 composable agent patterns + multi-agent research system | `agents/README.md`, `cognitive-units/`, future `agent-core/` |
| [centaur-evaluations.md](centaur-evaluations.md) | Academic research (Stanford HAI / Digital Economy Lab) | Centaur Evaluations -- measuring human+AI team performance | `multi-repo-orchestration/hio-collaboration/matrix.md`, `metrics/harmonization.md` |
| [owasp-top-10-agentic-applications.md](owasp-top-10-agentic-applications.md) | Open standard (OWASP GenAI Project) | OWASP Top 10 for Agentic Applications 2026 | `multi-repo-orchestration/scoring/scoring-rubric.md` (B-axis), `multi-repo-orchestration/governance/security-and-safety.md` |
| [multi-agent-frameworks-landscape.md](multi-agent-frameworks-landscape.md) | Vendor / open-source survey | LangGraph, CrewAI, AutoGen, OpenAI Swarm/Agents SDK, Google ADK, Anthropic Agent SDK, Magentic-One | `tools/` per-tool guides, `agents/`, future `agent-core/` |
| [agent-benchmarks.md](agent-benchmarks.md) | Benchmarks | SWE-bench, GAIA, TAU-bench / TAU2-bench, WebArena, HAL Reliability Dashboard | `multi-repo-orchestration/new-repos-proposed.md` (hio-evals), `metrics/ai-utilization.md` |
| [agent-alignment-research.md](agent-alignment-research.md) | Academic / vendor research | Constitutional AI (Anthropic), Deliberative Alignment (OpenAI), debate-based safety | `governance/security-and-safety.md`, `org/policies.md` |

---

## Reference vs. Cognitive Functions vs. Agents

Three distinct concepts; easy to confuse:

| Concept | What it is | Lives in |
|---|---|---|
| **Cognitive Functions** (10) | Frequencies of *engagement* a person or AI can hold (Builder, Problem Framer, Quality Guardian, ...) | `cognitive-functions/` |
| **Agent Types** (6) | AI roles composed from cognitive functions (Analysis Partner, Code Co-Creator, ...) | `agents/` |
| **Agent Engineering Capabilities** (7) | Technical *disciplines* required to build production AI agent systems (System Design, Tool/Contract Design, ...) | `reference/agent-engineering-7-skills.md` |

The 10 cognitive functions describe *how a mind engages with work*. The 7 capabilities describe *what you have to know* to build AI agents that work in production. They are orthogonal. A single human engineer in HIO holds 2-3 cognitive functions and is developing 2-4 of the 7 capabilities at any given time.

References sit alongside all three -- they bring in *external* knowledge that informs how all three are applied.

---

## How to Add a New Reference

1. Save the source content as a standalone markdown file in this directory.
2. Open with a `## Source` block: title, author/source, URL, date extracted, type.
3. Extract the structured insight -- concepts, frameworks, role mapping if relevant.
4. Add an `## HIO Integration Notes` section explaining where in this framework the reference connects.
5. Add a row to the table above with the file name and a one-line description of where it shows up.
6. If the reference contradicts or stretches the existing framework, also propose changes via a PR to the affected files (do not silently update).
