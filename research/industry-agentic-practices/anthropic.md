# Anthropic — Agentic Development Practices

## Agent Tooling

- **Claude Code CLI**: Terminal-based coding agent using Claude models
- **Claude Agent SDK**: Python/TypeScript SDK for building custom agents
- **Model Context Protocol (MCP)**: Open protocol for agent-tool communication (contributed to AAIF)

## Repository Configuration

### CLAUDE.md (Repo Root)
Primary instruction file. Loaded automatically when Claude Code enters a directory. Supports hierarchical overrides — subdirectory CLAUDE.md files add to or override parent instructions.

Best practices (from Anthropic docs):
- Keep under 200 lines
- Structure: build commands, code standards, negative rules
- Use `IMPORTANT` or `YOU MUST` sparingly for critical rules
- Be specific and falsifiable ("use Python 3.12 type hints" not "write good code")

### .claude/ Directory
```
.claude/
  settings.json        — permission allowlists/denylists, MCP servers
  settings.local.json  — user-specific overrides (gitignored)
  commands/            — custom slash commands as markdown
  skills/              — reusable skill definitions (SKILL.md)
  agents/              — custom subagent definitions (YAML)
  hooks/               — event-triggered shell commands
  rules/               — additional instruction files
```

### Permission Model
`settings.json` defines three tiers:
- `allow` — auto-approved tool calls
- `ask` — require user confirmation
- `deny` — always blocked (deny wins over allow)

### Security Approach
- 89% reduction in successful injection via constitutional AI training
- Typed message blocks separate user content from system instructions
- `<untrusted_external_data>` fencing for content from external sources
- OAuth 2.1 for MCP server authentication (added 2026)
- Agents refuse instructions found inside fenced content

## Sources
- Claude Code docs: https://code.claude.com/docs/en/best-practices
- Agent SDK: https://github.com/anthropics/claude-agent-sdk-python
- MCP spec: https://modelcontextprotocol.io
- Skills repo: https://github.com/anthropics/skills
