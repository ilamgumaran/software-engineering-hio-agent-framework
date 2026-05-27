# OpenAI — Agentic Development Practices

## Agent Tooling

- **Codex**: Cloud-based autonomous coding agent (GA May 2025), runs in sandboxed containers
- **Agents SDK**: Python/TypeScript SDK (replaced Swarm, deprecated Oct 2024)
- **AGENTS.md**: Open standard contributed to AAIF (Linux Foundation)

## Repository Configuration

### AGENTS.md (Repo Root)
- Plain markdown, no schema, no frontmatter
- Agent walks directory tree from root to CWD, loading nearest file
- Monorepos use per-package files (OpenAI's own repo has 88)
- Best practice: keep root under 300 lines
- Describe only what agents cannot discover themselves

### setup.sh
Environment setup script executed when Codex spins up a container for the repo.

### No Config Directory
OpenAI does not use a `.openai/` or similar config directory. All context is in AGENTS.md and repo-level files (README.md, CONTRIBUTING.md).

### Permission Model
Codex runs in sandboxed environments:
- No persistent state between sessions
- Network access restricted (internet disabled by default)
- AGENTS.md treated as trusted content (repo-owner authored)
- Issue/PR content treated as untrusted

## Agents SDK Architecture
Core primitives:
- **Agents**: instructions + model + tools
- **Handoffs**: typed agent-to-agent transfer of control
- **Guardrails**: input/output validators that can halt execution
- **Tracing**: built-in observability for debugging

Agent loop: model → tool calls → results → model, until final output.

## Security Approach
- Layered defense: narrow inputs, constrain tools, isolate untrusted content
- RL-powered red teaming at scale
- Safety Bug Bounty (March 2026, Bugcrowd) targeting injection, exfiltration, harmful autonomy
- Containment through sandboxing rather than prompt-level defenses alone

## Adoption (May 2026)
AGENTS.md natively supported by: Codex, Cursor, Windsurf, Kilo Code, Factory, Builder.io, GitHub Copilot

## Sources
- AGENTS.md spec: https://agents.md/
- OpenAI developer guide: https://developers.openai.com/codex/guides/agents-md
- GitHub repo: https://github.com/agentsmd/agents.md
- Prompt injection defense: https://openai.com/index/designing-agents-to-resist-prompt-injection/
