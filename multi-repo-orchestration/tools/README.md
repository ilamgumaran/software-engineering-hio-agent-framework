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

---

## Tool spec format

1. **Name and purpose** -- one line
2. **Invocation contract** -- arguments, types, defaults
3. **Behavior** -- what it does, step by step
4. **Outputs** -- shape of the output
5. **Errors** -- failure modes and stable error codes
6. **Permissions** -- what permissions the implementation must have

Keep tool specs short. If they exceed 60 lines, you are likely describing a skill, not a tool -- move it to `skills/`.
