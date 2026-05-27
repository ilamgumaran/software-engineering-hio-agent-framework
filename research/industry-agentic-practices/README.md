# Industry Agentic Development Practices — Comparative Research

## Last Updated: May 2026

This directory consolidates how the six major companies building AI coding agents approach repository structure, agent configuration, security, and development workflows. Use this as the evidence base for the generic agent configuration standard and the agent-readiness scoring mechanism.

## Quick Reference: Agent Instruction Files by Company

| Company | Primary File | Location | Format | Native Agents |
|---------|-------------|----------|--------|---------------|
| **Anthropic** | `CLAUDE.md` | Repo root (+ subdirs) | Markdown | Claude Code |
| **OpenAI** | `AGENTS.md` | Repo root (+ subdirs) | Markdown | Codex |
| **Google** | `GEMINI.md` | Repo root | Markdown | Gemini Code Assist, Jules |
| **Microsoft/GitHub** | `.github/copilot-instructions.md` | `.github/` dir | Markdown + YAML frontmatter | Copilot |
| **Amazon** | `.amazonq/rules/*.md` | `.amazonq/` dir | Markdown + YAML frontmatter | Q Developer, Kiro |
| **Meta** | *(SDK-driven, no standard file)* | N/A | Programmatic | CodeCompose, Confucius |

## Cross-Company Convergence Points

### What Every Company Agrees On

1. **Markdown is the format** — every company uses plain markdown for agent instructions
2. **Repo root is the anchor** — primary instruction file lives at repo root
3. **Agents need project context** — build commands, directory layout, conventions, constraints
4. **Security boundaries are explicit** — what agents cannot do is stated directly
5. **Human approval gates exist** — irreversible or high-risk actions require human sign-off
6. **Sandboxed execution** — agents run in containers or VMs, not on production systems

### Where Companies Diverge

| Concern | Approach A | Approach B |
|---------|-----------|-----------|
| File naming | Unified (`AGENTS.md` — AAIF standard) | Agent-specific (`CLAUDE.md`, `GEMINI.md`) |
| Scoping | Subdirectory files (OpenAI, Anthropic) | YAML frontmatter with glob patterns (Microsoft, Amazon) |
| Permission model | Allowlist in config (Anthropic `.claude/settings.json`) | Implicit from instructions (OpenAI) |
| Multi-agent | Explicit agent profiles (Microsoft `.github/agents/`) | Single file for all agents (OpenAI) |
| Spec-driven development | Amazon Kiro (`requirements.md`, `design.md`, `tasks.md`) | Others: optional/custom |

## Files in This Directory

| File | Content |
|------|---------|
| `anthropic.md` | Anthropic/Claude Code practices |
| `openai.md` | OpenAI/Codex practices |
| `google.md` | Google/Gemini/Jules practices |
| `microsoft.md` | Microsoft/GitHub Copilot practices |
| `amazon.md` | Amazon Q/Kiro/Bedrock practices |
| `meta.md` | Meta/Llama/Confucius practices |
