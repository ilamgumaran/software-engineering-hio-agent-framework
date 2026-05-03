# Reference Library

Structured external knowledge that informs how this framework is applied. These references are **not** the framework — the framework lives in `cognitive-functions/`, `agents/`, `cognitive-units/`, `workflows/`, `metrics/`, and `transformation/`. References capture *external lessons* (talks, research, industry case studies) that shape how we adapt the framework to real engineering work.

Each reference is read once, translated into framework concepts, and then linked from the places it informs.

---

## Current References

| File | Source | Topic | Where it shows up |
|---|---|---|---|
| [agent-engineering-7-skills.md](agent-engineering-7-skills.md) | Talk: *Transitioning to an AI-Centric Engineering Org* | 7 technical capabilities for production AI agents (System Design, Tool/Contract, Retrieval, Reliability, Security, Eval/Observability, Product Thinking) | Skills development in `domains/platform-engineering/skills.md`, role transitions in `transformation/`, deep-work tasks in `workflows/` |
| [industry-lessons-2024-2026.md](industry-lessons-2024-2026.md) | Public reporting on Shopify, Meta, Amazon, Klarna, Goldman Sachs, JPMorgan, Duolingo, Microsoft, MIT, McKinsey | What worked / what failed in real AI transformations | Risk register in `transformation/risk-management.md`, change strategy in `org/policies.md`, principles in `CLAUDE.md` |

---

## Reference vs. Cognitive Functions vs. Agents

Three distinct concepts; easy to confuse:

| Concept | What it is | Lives in |
|---|---|---|
| **Cognitive Functions** (10) | Frequencies of *engagement* a person or AI can hold (Builder, Problem Framer, Quality Guardian, ...) | `cognitive-functions/` |
| **Agent Types** (6) | AI roles composed from cognitive functions (Analysis Partner, Code Co-Creator, ...) | `agents/` |
| **Agent Engineering Capabilities** (7) | Technical *disciplines* required to build production AI agent systems (System Design, Tool/Contract Design, ...) | `reference/agent-engineering-7-skills.md` |

The 10 cognitive functions describe *how a mind engages with work*. The 7 capabilities describe *what you have to know* to build AI agents that work in production. They are orthogonal. A single human engineer in HIO holds 2-3 cognitive functions and is developing 2-4 of the 7 capabilities at any given time.

---

## How to Add a New Reference

1. Save the source content as a standalone markdown file in this directory.
2. Open with a `## Source` block: title, author/source, URL, date extracted, type.
3. Extract the structured insight — concepts, frameworks, role mapping if relevant.
4. Add an `## HIO Integration Notes` section explaining where in this framework the reference connects.
5. Add a row to the table above with the file name and a one-line description of where it shows up.
