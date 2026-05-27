# Amazon — Agentic Development Practices

## Agent Tooling

- **Amazon Q Developer**: AI coding assistant with autonomous agent mode (`/dev`)
- **Kiro**: Spec-driven agentic IDE (successor to Q Developer IDE plugins, EOL April 2027)
- **Bedrock AgentCore**: Managed agent infrastructure on AWS
- **Strands Agent SDK**: Open-source agent SDK underlying AgentCore

## Repository Configuration

### Amazon Q Developer
```
.amazonq/
  rules/*.md     — markdown rules with YAML frontmatter for file-path scoping
```

Rules files use glob patterns to scope instructions:
```yaml
---
applyTo: "src/**/*.java"
---
Use Java 21 features. Follow Google Java Style Guide.
```

### Kiro — Spec-Driven Development
Kiro generates three structured artifacts before writing code:
- **`requirements.md`** — user stories with EARS-notation acceptance criteria
- **`design.md`** — architecture decisions and component design
- **`tasks.md`** — implementation checklist with dependencies

Also uses **steering files** (Markdown) for persistent project context: conventions, architecture decisions, security rules. Specs are the source-of-truth; code is treated as a build artifact.

### Bedrock AgentCore
- Agents defined with instructions, action groups (API schemas), and knowledge bases
- Multi-agent collaboration with supervisor/child patterns
- Supports MCP and A2A protocols
- Pre-built skills for Claude Code, Kiro, Codex, Cursor
- Code Interpreter service (sandboxed Python/JS/TS)

## Security Approach
- **Bedrock Guardrails**: Configurable content filters, denied topics, PII detection, contextual grounding checks
- **Amazon Inspector**: Scanning agent-generated code for vulnerabilities
- Q Developer agents run locally; no external data transmission beyond API calls
- Profile-based agent isolation constrains access per agent
- Automated security scanning with remediation suggestions
- IAM-based identity and access management for all agent operations

## Sources
- Q Developer: https://aws.amazon.com/q/developer/features/
- Q Developer EOL announcement: https://aws.amazon.com/blogs/devops/amazon-q-developer-end-of-support-announcement/
- Kiro: https://kiro.dev/blog/introducing-kiro/
- Kiro specs: https://kiro.dev/docs/specs/
- Bedrock AgentCore: https://aws.amazon.com/blogs/aws/introducing-amazon-bedrock-agentcore-securely-deploy-and-operate-ai-agents-at-any-scale/
- Security posture: https://aws.amazon.com/blogs/security/five-ways-to-use-kiro-and-amazon-q-to-strengthen-your-security-posture/
