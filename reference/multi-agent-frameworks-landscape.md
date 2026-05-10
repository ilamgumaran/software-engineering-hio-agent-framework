# Multi-Agent Frameworks Landscape (2026)

## Source

| Field | Value |
|---|---|
| **Type** | Vendor and open-source survey |
| **Date extracted** | May 2026 |
| **Surveys cited** | gurusup.com (`/blog/best-multi-agent-frameworks-2026`), turing.com (`/resources/ai-agent-frameworks`), datacamp.com (`/tutorial/crewai-vs-langgraph-vs-autogen`), bswen docs (`/blog/2026-04-29-agent-framework-production-comparison`) |

---

## Frameworks compared

| Framework | Vendor | Orchestration model | State management | Model agnostic | Production-ready? |
|---|---|---|---|---|---|
| **LangGraph** | LangChain | Directed graph with conditional edges, time-travel checkpointing | Built-in checkpoints | Yes | Yes -- recommended for reliability |
| **CrewAI** | crewAIInc (open source) | Role-based crews; sequential or hierarchical processes | Sequential task output passing | Yes | Production for many uses; lowest learning curve |
| **AutoGen / AG2** | Microsoft Research | Conversational GroupChat among agents | In-memory conversation history | Yes | Production capable; foundation for Magentic-One |
| **Magentic-One** | Microsoft Research (built on AutoGen) | Orchestrator + 4 worker agents (FileSurfer, WebSurfer, Coder, Computer Terminal) | Orchestrator-managed working memory | Yes | Research / advanced production |
| **OpenAI Swarm** | OpenAI | Lightweight handoff-based | Minimal | OpenAI-only | Explicitly *not* for production |
| **OpenAI Agents SDK** | OpenAI | Production replacement for Swarm; handoffs + guardrails | Provided | OpenAI primary | Yes |
| **Google ADK 1.0** | Google | Agent Development Kit; native A2A and MCP | Provided | Yes | Yes -- positioned as 2026 multi-agent standard |
| **Anthropic Agent SDK** | Anthropic | Released alongside Claude 4.6; thin orchestration over Claude Code | Provided | Claude-only | Yes |
| **Semantic Kernel / Microsoft Agent Framework** | Microsoft | Enterprise; Magentic orchestration available | Provided | Yes | Yes |
| **LlamaIndex Agents** | LlamaIndex | Workflow-style; native A2A | Provided | Yes | Production for retrieval-heavy uses |

---

## Notable architectural patterns

### Orchestrator-workers (Magentic-One)

One lead agent (Orchestrator) plans, maintains structured working memory, dispatches to specialist worker agents (FileSurfer, WebSurfer, Coder, Computer Terminal), restarts on stalls, determines completion. Achieved competitive performance to state-of-the-art on GAIA, AssistantBench, and WebArena -- without modifying core agent capabilities or how they collaborate.

Reference paper: [arxiv.org/abs/2411.04468](https://arxiv.org/abs/2411.04468)

### Graph-with-checkpoints (LangGraph)

Directed graph defines flow; conditional edges decide branching; checkpoints at every node permit time-travel debugging and resume. Best fit when reliability dominates over rapid prototyping.

### Role-based crews (CrewAI)

Declarative roles (Researcher, Writer, Critic). Process types (sequential, hierarchical) decide how roles interact. Lowest learning curve -- ~20 lines to start.

### Conversational GroupChat (AutoGen)

Agents converse turn-by-turn; a manager agent decides who speaks next. Particularly suited to debate, critique, and tool-use loops.

---

## How HIO maps onto these frameworks

The HIO operational hub specifies *what* the agents are (6 types composing 10 cognitive functions) and *how humans and agents collaborate* (Decision Spectrum, OI/II/Interactive routing, Harmonized Sprints). It is intentionally agnostic about *which framework* implements the agents.

Likely fit:

| HIO use case | Recommended framework family |
|---|---|
| Single repo, code-first work | Anthropic Agent SDK + Claude Code |
| Multi-step reasoning with reproducible flows | LangGraph |
| Role-based team simulation | CrewAI |
| Tool-heavy enterprise integration | Microsoft Agent Framework / Semantic Kernel |
| Cross-org agent interop | Google ADK with A2A |
| Generalist task automation | Magentic-One |

---

## What this means for the multi-repo orchestration framework

The `multi-repo-orchestration/` framework deliberately:

- Keeps tool specs as **markdown** rather than tying to one framework's tool API
- Defines skills as **procedures** (`skills/`) rather than executable code, so each runtime can implement
- Uses MCP-compatible vocabulary in tool specs so the same skill can be implemented as an MCP server in any compliant runtime

This is by design: forks and external orgs choose their framework; this layer stays portable.

---

## Where this reference shows up

| Place | How it's used |
|---|---|
| `tools/` per-tool guides | Cross-link to corresponding framework guides |
| `multi-repo-orchestration/tools/README.md` | Note the runtime-agnostic posture |
| Future `agent-core/` | Framework selection ADR will cite this |
