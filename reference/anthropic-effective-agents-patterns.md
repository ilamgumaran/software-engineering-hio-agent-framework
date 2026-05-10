# Anthropic's Effective-Agent Patterns

## Source

| Field | Value |
|---|---|
| **Title** | Building Effective Agents |
| **Type** | Engineering blog + white paper |
| **Author** | Anthropic Applied AI team |
| **Primary URL** | https://www.anthropic.com/research/building-effective-agents |
| **Resource hub** | https://resources.anthropic.com/building-effective-ai-agents |
| **Companion: Multi-agent research system** | https://www.anthropic.com/engineering/multi-agent-research-system |
| **Companion: Context engineering** | https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents |
| **Companion: Long-running harnesses** | https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents |
| **Companion: Tool writing** | https://www.anthropic.com/engineering/writing-tools-for-agents |
| **Date extracted** | May 2026 |

---

## Core thesis

Anthropic's most successful customer-facing agent implementations rely on **simple, composable patterns** rather than monolithic frameworks. Five patterns are sufficient for the majority of production agentic workflows:

1. **Prompt chaining** -- decompose a task into sequential LLM calls; each step's output feeds the next
2. **Routing** -- classify inputs and dispatch them to the most appropriate downstream prompt or sub-agent
3. **Parallelization** -- run multiple LLM calls in parallel, either to vote (sectioning) or to gather independent perspectives (voting)
4. **Orchestrator-workers** -- a lead model breaks a task into subtasks and dispatches to specialized worker models
5. **Evaluator-optimizer** -- one LLM proposes a response; another LLM critiques; iterate until quality threshold met

A sixth pattern -- **the autonomous agent** -- emerges when these are composed into a loop with tool use, observation, and termination criteria.

## Multi-agent research system (companion)

Anthropic's internal research-deep-dive system uses an **orchestrator-worker** topology: a lead agent decomposes the research question, dispatches parallel sub-agents, then composes their outputs. The same topology powers Microsoft's Magentic-One and most successful enterprise multi-agent systems.

---

## Mapping to the HIO 6-agent model

The HIO operational hub's 6 agent types (`agents/`) compose cognitive functions; Anthropic's 5 patterns describe the *control flow* in which agents are invoked. They are orthogonal. The same Code Co-Creator agent might be invoked via routing in one task, evaluator-optimizer in another.

| Anthropic pattern | HIO agent types most often involved | Example task |
|---|---|---|
| Prompt chaining | Analysis Partner -> Architecture Explorer -> Code Co-Creator | Spec to working code |
| Routing | Analysis Partner classifies; routes to specialist | Inbound issue triage |
| Parallelization | Multiple Code Co-Creators voting on a refactor; or Architecture Explorer + Quality Analyst running in parallel | High-stakes decisions |
| Orchestrator-workers | Lead = unit's primary agent; workers = specialist agents | Multi-component delivery |
| Evaluator-optimizer | Code Co-Creator proposes; Quality Analyst evaluates; iterate | Test-driven implementation |
| Autonomous agent (loop) | Any agent in a tool-use loop | Long-running incident triage |

## Mapping to the multi-repo orchestration framework

| Pattern | Where it shows up in this framework |
|---|---|
| Routing | `hio-classifier` skill routes tasks to OI / II / Interactive |
| Orchestrator-workers | `cross-repo-tracer` orchestrates per-repo specialist actions |
| Evaluator-optimizer | `agentic-scorer` produces draft; SMEs evaluate; iterate |
| Prompt chaining | `repo-cartographer` chains analysis -> draft -> validation |

---

## Context engineering takeaways

From the companion blog: agent failure modes shift from "wrong words in the prompt" to "wrong configuration of context". For multi-step or multi-context-window agents, the harness (loop, memory, planning surface) matters more than the model. This validates HIO's emphasis on composing well-defined cognitive functions and well-bounded agent types over heroic single prompts.

## Tool writing takeaways

Agents fail when tools are vaguely defined. Anthropic's blog reinforces what `reference/agent-engineering-7-skills.md` (Capability 2: Tool/Contract Design) already states:

- Tool descriptions must be unambiguous to a tool-using agent reading cold
- Examples in tool descriptions are load-bearing, not decorative
- Agents should be able to discover tools' purpose without invoking them

This directly informs scoring rubric dimension **A5 (Tool/contract clarity)**.

---

## Where this reference shows up

| Place | How it's used |
|---|---|
| `agents/README.md` | Patterns added as a sidebar mapping HIO agent types to control flows |
| `multi-repo-orchestration/skills/` | Each skill explicitly maps to one or more patterns |
| `multi-repo-orchestration/scoring/scoring-rubric.md` | A5 leveling references Anthropic's tool-writing guidance |
| `cognitive-units/README.md` | Orchestrator-worker pattern referenced in unit composition |
