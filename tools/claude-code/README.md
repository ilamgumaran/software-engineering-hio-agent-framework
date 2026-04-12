# Claude Code -- HIO Tool Guide

## What It Does

Claude Code is an AI coding assistant that operates directly in your terminal. It reads your codebase, writes code, runs commands, and manages multi-step workflows. Within HIO, it serves as the **primary orchestration engine** -- hosting agent definitions, executing workflows, and switching between agent types based on context.

---

## Role in HIO

Claude Code is the backbone of the AI agent layer. It implements all 6 agent types defined in `agents/` and switches between them based on the task at hand. When configured with `CLAUDE.md`, it operates as a full HIO agent partner rather than a generic coding assistant.

| Agent Type | Claude Code Capability |
|---|---|
| **Analysis Partner** | Codebase analysis, pattern detection, dependency mapping, risk surfacing |
| **Code Co-Creator** | Implementation from specs, test generation, refactoring, migration |
| **Architecture Explorer** | Multi-option design generation, tradeoff analysis, constraint evaluation |
| **Quality Analyst** | Code review, security scanning, performance analysis, tech debt assessment |
| **Metrics Monitor** | Metric computation, trend analysis, anomaly detection, report generation |
| **Documentation & Knowledge** | Doc authoring, decision logging, knowledge synthesis, onboarding materials |

---

## Key Capabilities for HIO

- **Multi-agent switching** -- Activates different agent types within a single session based on `CLAUDE.md` configuration
- **MCP integrations** -- Connects to external tools (databases, APIs, monitoring) for real-time data access
- **Memory system** -- Maintains context across sessions via `CLAUDE.md` and project files
- **Workflow execution** -- Runs multi-step HIO workflows (sprint kickoff, harmony checks, reviews)
- **Codebase awareness** -- Reads and understands the full project structure for informed decisions

---

## HIO-Specific Configuration

1. **Place `CLAUDE.md` at the repo root.** This file configures Claude Code as an HIO agent with awareness of cognitive functions, agent types, and organizational context.
2. **Reference `org/profile.md`** in your CLAUDE.md so the agent understands your team's purpose and constraints.
3. **Reference `org/policies.md`** to enforce AI usage policies and security boundaries.

---

## Setup Guide

1. **Install Claude Code** following the official documentation
2. **Copy `CLAUDE.md`** from this framework to your project root
3. **Customize `CLAUDE.md`** with your org context from `org/profile.md`
4. **Configure MCP integrations** for your monitoring, database, and API tools
5. **Test agent switching** by asking Claude Code to operate as each of the 6 agent types

---

## Limitations and Best Practices

- **Decision Spectrum** -- Claude Code should decide on reversible changes, recommend on semi-reversible ones, and only analyze irreversible ones. Configure this expectation in `CLAUDE.md`.
- **Context window** -- For very large codebases, direct Claude Code to specific directories rather than asking it to analyze everything at once.
- **Verification** -- Always review generated code, especially for security-sensitive or irreversible operations.
- **Complementary tools** -- Claude Code works alongside GitHub Copilot (IDE-level), Gemini Enterprise (large-context), and Glean (knowledge search). See the other tool guides in `tools/`.

---

## Related Files

- Agent configuration: `CLAUDE.md`
- Agent definitions: `agents/`
- HIO workflows for Claude Code: `tools/claude-code/workflows.md`
- AI usage policies: `org/policies.md`
