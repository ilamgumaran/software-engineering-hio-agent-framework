# Tools

Lightweight tool specifications for cross-repo operations. These are tool-agnostic descriptions an agent or CLI can implement; they are not full implementations.

---

## Tool index

| Tool | Purpose | Status |
|---|---|---|
| `repo-scorecard-cli.md` | Run the agentic-scorer skill from a CLI for any repo | Spec only |
| `cross-repo-link-validator.md` | Walk every `AGENTS.md` and verify trace links resolve | Spec only |
| `vocab-translator.md` | Apply the registry translation table to a piece of text | Spec only |

---

## Why specs, not implementations

Different agent runtimes (Claude Code, Copilot, Gemini, custom) implement tools differently. Specs let each runtime supply its own implementation while keeping the contract identical. When an implementation lands, link it from the spec.

See [`reference/multi-agent-frameworks-landscape.md`](../../reference/multi-agent-frameworks-landscape.md) for the framework landscape that motivates this runtime-agnostic posture.

---

## MCP-implementability

These tool specs are deliberately written so that any of them can be implemented as a [Model Context Protocol](../../reference/agent-protocols-mcp-a2a.md) (MCP) server without further translation. The fields each spec captures (name, invocation contract, inputs, outputs, errors, permissions) map cleanly to MCP tool primitives:

| Spec field | MCP primitive |
|---|---|
| Name and purpose | Tool name and description |
| Invocation contract -- arguments | Tool input schema |
| Outputs | Tool output schema |
| Errors | Tool error responses |
| Permissions | Server capability declaration on connect |

When the family adopts an MCP server (e.g., for the proposed `agent-spec-registry`), these specs become the source of truth for the server's tool catalog.

---

## Tool spec format

1. **Name and purpose** -- one line
2. **Invocation contract** -- arguments, types, defaults
3. **Behavior** -- what it does, step by step
4. **Outputs** -- shape of the output
5. **Errors** -- failure modes and stable error codes
6. **Permissions** -- what permissions the implementation must have

Keep tool specs short. If they exceed 60 lines, you are likely describing a skill, not a tool -- move it to `skills/`.

---

## Adding a new tool

1. Write the spec using the format above
2. Add it to the tool index
3. If the tool will be exposed to agents at runtime, also note the OWASP categories it touches (Tool Misuse, Resource Exhaustion, Supply Chain) and the per-task budget defaults
4. SME review for any tool that performs writes
5. When implementing, prefer MCP unless the runtime cannot speak it
