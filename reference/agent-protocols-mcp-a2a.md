# Agent Protocols: Model Context Protocol (MCP) and Agent2Agent (A2A)

## Sources

### Model Context Protocol (MCP)

| Field | Value |
|---|---|
| **Title** | Model Context Protocol |
| **Type** | Open protocol (JSON-RPC 2.0) |
| **Primary URL** | https://modelcontextprotocol.io |
| **Spec URL** | https://modelcontextprotocol.io/specification/2025-11-25 |
| **Origin** | Anthropic, November 2024 |
| **Stewardship** | Linux Foundation -- Agentic AI Foundation (AAIF), donated December 2025 |
| **Wikipedia** | https://en.wikipedia.org/wiki/Model_Context_Protocol |
| **Anthropic announcement** | https://www.anthropic.com/news/model-context-protocol |
| **Date extracted** | May 2026 |

### Agent2Agent (A2A)

| Field | Value |
|---|---|
| **Title** | Agent2Agent Protocol |
| **Type** | Open protocol |
| **Primary URL** | https://a2a-protocol.org |
| **Repository** | https://github.com/a2aproject/A2A |
| **Origin** | Google with 50+ partners, April 2025 |
| **Stewardship** | Linux Foundation -- Agentic AI Foundation (AAIF), contributed June 2025 |
| **Google announcement** | https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/ |
| **Date extracted** | May 2026 |

---

## What MCP does

MCP standardizes how an AI agent connects to **tools and data sources**. Mechanically, JSON-RPC 2.0 over stdio (locally spawned servers) or HTTP/SSE (remote servers). Three primitives a server exposes:

- **Tools** -- callable operations the agent can invoke
- **Resources** -- readable content the agent can fetch
- **Prompts** -- pre-defined prompt templates the agent can render

Clients and servers run a capability-negotiation handshake on connect. By March 2026, MCP had surpassed 97 million monthly SDK downloads, 81,000+ GitHub stars, and was supported by Anthropic, OpenAI, Google, Microsoft, and AWS.

## What A2A does

A2A standardizes how AI agents communicate **with each other** across organizational and platform boundaries. Core capabilities:

- **Capability discovery** via signed Agent Cards (JSON, cryptographically signed for domain verification as of v1.2)
- **Multi-modality** including audio and video streaming
- **Asynchronous tasks** via push notifications to client-supplied secure webhooks
- **150+ supporting organizations** as of April 2026 (Google, Microsoft, AWS, Salesforce, SAP, ServiceNow, Workday, IBM, ...)

Native A2A support is built into Google ADK, LangGraph, CrewAI, LlamaIndex Agents, Semantic Kernel, and AutoGen.

## How they compose

- **MCP** = agent <-> tools / data
- **A2A** = agent <-> agent

They are intentionally complementary. An A2A-discoverable agent typically uses MCP internally to access tools.

---

## HIO Integration Notes

### MCP

The operational hub already references MCP setup in `tools/claude-code/README.md`. The multi-repo orchestration framework intentionally specifies tools (`multi-repo-orchestration/tools/`) as **runtime-agnostic markdown specs**, not MCP servers, because not every consumer runs an MCP-capable client.

A proposed evolution path:

1. **Today:** Tools are markdown specs; any runtime can implement
2. **Next:** Implement `repo-scorecard-cli`, `cross-repo-link-validator`, `vocab-translator` as MCP servers; expose to Claude Code, Cursor, Codex, etc. without per-runtime ports
3. **Later:** Expose the entire `multi-repo-orchestration/repo-registry.md` as an MCP resource so any agent can fetch the registry without parsing markdown

This lifts dimension **A5 (Tool/contract clarity)** in the scoring rubric and reduces per-runtime integration work.

### A2A

A2A becomes relevant if:

- The HIO family grows to include agent-runtime repos (e.g., the proposed `hio-evals` runs evaluator agents)
- An external organization adopts a fork and wants its agents to interop with the family's agents
- The proposed `agent-spec-registry` (in `new-repos-proposed.md`) chooses to expose Agent Cards for each repo in the family

For pure documentation repos (the current state), A2A is over-engineering. We track the protocol as a future-fit option.

---

## Where this reference shows up

| Place | How it's used |
|---|---|
| `multi-repo-orchestration/tools/README.md` | Note that tool specs are MCP-implementable |
| `multi-repo-orchestration/new-repos-proposed.md` | `hio-evals` and `agent-spec-registry` proposals updated to call out MCP/A2A surface |
| `tools/claude-code/README.md` | MCP integration guidance (already present, now cited) |
| `governance/security-and-safety.md` | A2A signed-agent-card requirements when an agent in the family acts on behalf of an external agent |
