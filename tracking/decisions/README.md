# Decision Records — Tracking

This directory tracks architectural, technical, and process decisions linked to organizational objectives. It extends the standard ADR (Architecture Decision Record) format with objective alignment and impact tracking.

## Why Track Decisions Centrally?

In agentic development, decisions happen fast. Multiple agents and humans make choices across repos. Without tracking:
- Decisions get lost in PR comments and chat threads
- Conflicting decisions are made in different repos
- The rationale for constraints (like "zero dependencies") is forgotten
- Nobody knows if a decision achieved its intended objective

## Decision Record Format

Each decision is a markdown file in `tracking/decisions/`:

```markdown
# DR-NNN: [Decision Title]

## Status: [PROPOSED | ACCEPTED | SUPERSEDED | DEPRECATED]
## Date: YYYY-MM-DD
## Decider: [Human name — decisions are always human-made]

## Objective Alignment
Links to: [objective ID from tracking/objectives/]
Impact on metrics: [which metrics this decision affects]

## Context
[What situation prompted this decision? What constraints exist?]

## Options Considered

### Option A: [Name]
- Pros: [...]
- Cons: [...]

### Option B: [Name]
- Pros: [...]
- Cons: [...]

## Decision
[Which option was chosen and why]

## Consequences
- [Positive consequence 1]
- [Negative consequence 2]
- [Tradeoff accepted]

## Affected Repos
| Repo | Impact |
|------|--------|
| repo-name | [what changes] |

## Review Schedule
- First review: [date — typically 1 month after]
- Was the intended outcome achieved? [Yes/No/Partial — filled in at review]

## Use Cases Affected
- [UC-NNN: use case name](../use-cases/UC-NNN.md)

## History
| Date | Event |
|------|-------|
| YYYY-MM-DD | Proposed |
| YYYY-MM-DD | Accepted |
| YYYY-MM-DD | First review — [outcome] |
```

## Decision Categories

| Category | Examples | Default Route |
|----------|----------|---------------|
| **Architecture** | Module boundaries, API design, dependency choices | Human (OI) |
| **Technology** | Language version, framework selection, tool adoption | Human (OI) |
| **Process** | TDD enforcement, review requirements, spec format | Human (OI) |
| **Security** | Permission model, secret handling, sandboxing | Human (OI) |
| **Performance** | Latency budgets, resource limits, caching strategy | Interactive |
| **Prioritization** | What to build next, what to defer | Human (OI) |

## Linking Decisions to Objectives

Every decision should trace to at least one objective in `tracking/objectives/`. If a decision doesn't serve an objective, question whether it's needed.

```
Objective: "Reduce lead time for changes"
  └── DR-005: Adopt spec-driven TDD
        └── Impact: Faster agent implementation cycles → shorter lead time
```

## Agent Interaction with Decisions

Agents SHOULD:
- Reference relevant decisions when implementing (e.g., "per DR-001, zero external dependencies")
- Flag when an implementation choice conflicts with a recorded decision

Agents MUST NOT:
- Make or override decisions (all decisions are human-made)
- Ignore a decision that constrains their work
- Treat a SUPERSEDED decision as current
