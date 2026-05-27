# Use Case & Spec Lifecycle Tracking

This directory tracks the lifecycle of every use case and specification across the HIO repo family. It provides traceability from business objective → use case → spec → implementation → validation.

## Why Track Use Cases Separately from Specs?

Specs describe **what** to build. Use cases describe **why** it matters and **who** benefits. A single use case may spawn multiple specs. Tracking at both levels prevents:
- Specs that exist without business justification
- Use cases that were agreed upon but never spec'd
- Completed specs that were never validated against the original use case
- Scope drift where specs evolve away from the use case they serve

## Use Case Lifecycle

```
PROPOSED → ACCEPTED → SPEC'D → IN_PROGRESS → IMPLEMENTED → VALIDATED → RETIRED
    ↑                                              │
    └──────────── REVISION ◄───────────────────────┘
```

| Status | Meaning | Who Transitions |
|--------|---------|-----------------|
| **PROPOSED** | Someone identified a need | Any team member |
| **ACCEPTED** | Aligned to an objective; prioritized | Human (OI) |
| **SPEC'D** | Feature spec(s) written | Human (OI) |
| **IN_PROGRESS** | Agent or human is implementing | Automatic (when branch created) |
| **IMPLEMENTED** | All specs under this use case pass tests | Agent reports |
| **VALIDATED** | Human verified against original use case intent | Human (OI) |
| **RETIRED** | Use case superseded or no longer relevant | Human (OI) |
| **REVISION** | Requirements changed; cycle restarts | Human (OI) |

## Use Case Registry Format

Each use case is a markdown file in `tracking/use-cases/`:

```markdown
# UC-NNN: [Use Case Name]

## Status: [PROPOSED | ACCEPTED | SPEC'D | IN_PROGRESS | IMPLEMENTED | VALIDATED | RETIRED]

## Objective Alignment
Links to: [objective ID from tracking/objectives/]

## Description
[What the user/system needs to do and why]

## Beneficiaries
- [Who benefits and how]

## Specs
| Spec | Status | PR |
|------|--------|----|
| specs/features/NNN-feature.md | IMPLEMENTED | #42 |
| specs/features/NNN-feature.md | READY | — |

## Decisions
- [DR-NNN: decision title](../decisions/DR-NNN.md) — [one-line summary]

## Success Criteria
- [Measurable outcome 1]
- [Measurable outcome 2]

## History
| Date | Event | By |
|------|-------|----|
| YYYY-MM-DD | Proposed | [name] |
| YYYY-MM-DD | Accepted | [name] |
```

## Keeping Use Cases Updated

### Triggers for Update

| Event | Update Required |
|-------|----------------|
| New spec written | Add to use case's Specs table |
| Spec status changes | Update spec row in use case |
| PR merged for a spec | Add PR link to spec row |
| Decision made affecting use case | Add to Decisions section |
| All specs implemented | Move use case to IMPLEMENTED |
| Human validates | Move to VALIDATED |
| Requirements change | Move to REVISION, update description |
| Use case no longer needed | Move to RETIRED with rationale |

### Agent Responsibilities

Agents SHOULD:
- Check if their current spec belongs to a use case before implementing
- Update the spec status row when they complete implementation
- Flag if a spec they're implementing doesn't trace to any use case

Agents MUST NOT:
- Create, modify, or retire use cases (human-only)
- Change the objective alignment (human-only)
- Move a use case to VALIDATED (human-only)

### Human Responsibilities

- Review use case registry weekly during sprint planning
- Validate completed use cases (not just specs)
- Retire obsolete use cases rather than leaving them stale
- Ensure every new spec traces to a use case
