# GitHub Copilot -- HIO Tool Guide

## What It Does

GitHub Copilot provides AI-powered code suggestions directly in your IDE. It offers inline completions, chat-based code generation, and context-aware suggestions as you type. Within HIO, it supports the **Builder** cognitive function during deep work blocks.

---

## Role in HIO

Copilot is the **IDE-level coding assistant** -- it operates at the keystroke level during implementation work. It is **not** a replacement for the Code Co-Creator agent (Claude Code). The two tools are complementary:

| Capability | GitHub Copilot | Claude Code (Code Co-Creator) |
|---|---|---|
| Inline code completion | Primary | Not applicable |
| Small edits and snippets | Primary | Capable |
| Multi-file implementation | Limited | Primary |
| Architecture decisions | Not applicable | Primary |
| Workflow orchestration | Not applicable | Primary |
| Sprint ceremony support | Not applicable | Primary |

---

## Best For

- **Inline suggestions** during coding -- autocomplete functions, variables, and patterns
- **Code completion** for boilerplate, repetitive patterns, and standard implementations
- **Small edits** -- quick fixes, renames, and localized refactoring
- **Test scaffolding** -- generating test stubs from function signatures
- **Documentation comments** -- inline docstrings and code comments

---

## HIO Integration

- Works alongside Claude Code during **Deep Work Collaboration** blocks (`workflows/deep-work-collaboration.md`)
- Supports the **Builder** cognitive function (`cognitive-functions/builder.md`) with rapid implementation assistance
- Feeds into **Quality Analyst** reviews -- Copilot-generated code should still pass agent-assisted code review
- Complements rather than replaces the multi-agent workflow

---

## Setup and Configuration

1. **Install the GitHub Copilot extension** in your IDE (VS Code, JetBrains, Neovim)
2. **Authenticate** with your organization's GitHub account
3. **Configure suggestion behavior** -- enable or disable auto-suggestions per language
4. **Review organizational policies** in `org/policies.md` for AI-generated code guidelines
5. **Brief your team** that Copilot handles inline work; Claude Code handles orchestration

---

## Limitations

- No awareness of HIO framework concepts (cognitive functions, agent types, workflows)
- Limited to the current file and nearby open files for context
- Cannot execute commands, run tests, or perform multi-step workflows
- Generated code requires the same review standards as human-written code

---

## Related Files

- Deep work workflow: `workflows/deep-work-collaboration.md`
- Builder function: `cognitive-functions/builder.md`
- Copilot workflows: `tools/github-copilot/workflows.md`
- AI policies: `org/policies.md`
