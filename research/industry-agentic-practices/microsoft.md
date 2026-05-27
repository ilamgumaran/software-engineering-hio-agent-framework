# Microsoft / GitHub — Agentic Development Practices

## Agent Tooling

- **GitHub Copilot (Agent Mode)**: IDE and cloud-based coding agent
- **Copilot Coding Agent**: Cloud agent that opens PRs autonomously, monitored via repo Agents tab
- **Squad**: Multi-agent teams (lead, frontend, backend, tester) inside a single repo
- **Microsoft Agent Framework**: Unified framework merging AutoGen + Semantic Kernel (1.0 GA Q1 2026)

## Repository Configuration

### Instruction File Hierarchy
```
.github/
  copilot-instructions.md                 — project-wide instructions (all Copilot requests)
  instructions/*.instructions.md          — path-specific instructions (YAML frontmatter scoping)
  agents/<name>.agent.md                  — custom agent profiles (YAML + Markdown, max 30K chars)
  skills/<skill-name>/SKILL.md            — reusable capability packages

AGENTS.md                                — root-level orientation file (AAIF standard)
```

### Path-Specific Instructions
Microsoft uses YAML frontmatter to scope rules to file patterns:
```yaml
---
applyTo: "src/**/*.ts"
---
Use strict TypeScript. Prefer functional patterns.
```

### Custom Agent Profiles
`.github/agents/<name>.agent.md` defines:
- Agent name and expertise description
- Available tools and MCP servers
- Behavioral instructions
- Maximum 30K characters per profile

### Permission Model
- Cloud agent runs in sandboxed environments
- Branch protection and required reviewers enforced
- Copilot Studio has built-in cross-prompt injection (XPIA) and user prompt injection (UPIA) blocking

## Microsoft Agent Framework (formerly AutoGen)
AutoGen is now in maintenance mode. Key evolution:
- Implicit group-chat management replaced by explicit **graph-based Workflows**
- Typed nodes, edges, and human-in-the-loop pause/resume
- Middleware architecture: inject content safety filters, logging, compliance checks into the agent loop

## Security Approach
- **Copilot Studio**: Real-time XPIA and UPIA blocking
- **Agent 365** (GA May 2026): Runtime threat detection for injection and model theft, alerts via Microsoft Sentinel
- **Entra Internet Access** (GA March 2026): Network-level injection blocking
- Notable CVEs: CVE-2026-21520 (Copilot Studio indirect injection), CVE-2025-32711 (EchoLeak zero-click in M365 Copilot)
- Published research: "When prompts become shells: RCE vulnerabilities in AI agent frameworks" (May 2026)

## Sources
- VS Code custom instructions: https://code.visualstudio.com/docs/copilot/customization/custom-instructions
- Copilot AGENTS.md support: https://github.blog/changelog/2025-08-28-copilot-coding-agent-now-supports-agents-md-custom-instructions/
- Custom agents: https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/create-custom-agents
- Squad: https://github.blog/ai-and-ml/github-copilot/how-squad-runs-coordinated-ai-agents-inside-your-repository/
- Microsoft Agent Framework: https://azure.microsoft.com/en-us/blog/introducing-microsoft-agent-framework/
- AI agent security blog: https://www.microsoft.com/en-us/security/blog/2026/05/07/prompts-become-shells-rce-vulnerabilities-ai-agent-frameworks/
