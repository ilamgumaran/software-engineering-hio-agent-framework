# Google — Agentic Development Practices

## Agent Tooling

- **Jules**: Async coding agent (GA Aug 2025), runs in isolated VMs, returns PRs. Powered by Gemini 3.1 Pro.
- **Gemini Code Assist (Agent Mode)**: IDE-integrated agent (VS Code, IntelliJ), multi-file edits with MCP support
- **Gemini CLI**: Terminal-based agent using GEMINI.md for context
- **Agent2Agent (A2A)**: Open protocol for agent interoperability (contributed to AAIF/Linux Foundation)

## Repository Configuration

### GEMINI.md (Repo Root)
Project-wide instructions for Gemini-based agents. Equivalent to CLAUDE.md/AGENTS.md.

### .gemini/ Directory
```
.gemini/
  settings.json    — CLI configuration
  agents/          — custom subagent definitions
  skills/          — custom skill definitions (SKILL.md)
```

Also supports:
- `.agents/AGENTS.md` — system instructions loaded on agent startup
- `~/.gemini/agents/` — personal agent definitions

### A2A Protocol
Open protocol for cross-platform agent-to-agent communication:
- **Agent Cards**: JSON discovery documents describing agent capabilities
- Supports sync/async/streaming communication
- Rich data exchange (text, files, structured JSON)
- Complementary to MCP (A2A = agent-to-agent; MCP = agent-to-tool)
- 50+ partners: Atlassian, Salesforce, PayPal, etc.

## Security Approach
- **User Alignment Critic**: Separate Gemini model validating agent actions align with user intent
- **Agent Origin Sets**: Restrict accessible sites/resources per agent
- **Model Armor**: Runtime layer blocking injection, tool poisoning, data leakage
- Google reported 32% increase in prompt injection attempts (Nov 2025 - Feb 2026)
- Known vulnerability in "Antigravity" IDE: insufficient input sanitization enabling code execution (patched)

## Sources
- Jules: https://jules.google/
- Jules Tools CLI: https://developers.googleblog.com/en/meet-jules-tools-a-command-line-companion-for-googles-async-coding-agent/
- Gemini Code Assist: https://developers.google.com/gemini-code-assist/docs/agent-mode
- A2A Protocol: https://a2a-protocol.org/latest/
- Gemini CLI: https://github.com/google-gemini/gemini-cli
- Chrome agentic security: https://security.googleblog.com/2025/12/architecting-security-for-agentic.html
