# Agentic Transition — Application Layer

This directory contains an opinionated, end-to-end example of how an
org can adopt GitHub Copilot + Claude Code CLI across many repos. It
is deliberately kept under `examples/` so the core HIO framework
(cognitive functions, units, agents, workflows in the repo root) is
not disturbed by application-level material.

## Read in this order

1. `BEST_PRACTICES.md` — the focused plan and best practices: how
   agents stay repo-aware without re-analysis, and how skills /
   prompts / tools / sub-agents are stored, shared, and kept fresh.
2. `transition-playbook.md` — the longer phased rollout (governance,
   metrics, repo tiers, distribution mechanisms).
3. `AGENTS.md`, `.github/copilot-instructions.md`,
   `.github/instructions/` — example org-level multi-agent /
   Copilot instructions and path-scoped rules.
4. `.claude/skills/`, `.claude/rules/`, `.claude/agents/` — example
   reusable Claude Code skills, path-scoped rules, and specialist
   sub-agents.
5. `config/` — example model routing, cost policy, and quality gates.
6. `repo-setup-batch/`, `repo-setup-api/` — per-archetype repo
   templates (CLAUDE.md, AGENTS.md, copilot-instructions, rules).

## How to adopt

Treat this directory as a starter kit you copy *into a separate
org-level repo* (e.g., `hio-framework`) — not as something the core
HIO framework repo enforces. The core framework defines cognitive
structure; this example shows one concrete way to operationalize it
for batch / API engineering teams.
