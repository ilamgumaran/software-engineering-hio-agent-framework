# Tracking — Use Cases, Decisions, and Objectives

This directory provides end-to-end traceability from organizational objectives down to individual specs and code changes. It answers:

- **Why** are we building this? → `objectives/`
- **What** are we building? → `use-cases/`
- **What choices** did we make along the way? → `decisions/`
- **How well** is it going? → `../metrics/`

## The Traceability Chain

```
objectives/OBJ-001.md         "Reduce lead time for changes"
    │
    ├── Key Result: Spec-to-merge <3 days
    │       └── Metric: metrics/operational-health.md → Spec-to-Merge Time
    │
    ├── use-cases/UC-003.md    "BM25 Scoring for re-ranking"
    │       ├── specs/features/003-bm25-scorer.md
    │       ├── specs/test-requirements/003-bm25-scorer-tests.md
    │       └── specs/acceptance-criteria/003-bm25-scorer-criteria.md
    │
    └── decisions/DR-001.md    "Use spec-driven TDD"
            └── Rationale: Eliminates ambiguity → faster agent cycles
```

## How to Keep This Updated

### For Humans (Weekly)

During sprint planning or weekly pulse:
1. Review `objectives/` — are key results on track?
2. Review `use-cases/` — are any stuck in IN_PROGRESS too long?
3. Check if new decisions need recording
4. Update key result "current" values from metrics

### For Agents (Per Task)

When implementing a spec:
1. Check if the spec traces to a use case in `use-cases/`
2. After implementation, update the spec's status row in the use case file
3. Reference relevant decisions in commit messages or PR descriptions

### Automation Opportunities

| Task | Can Be Automated |
|------|-----------------|
| Spec status tracking | Yes — derive from git/PR state |
| Key result current values | Yes — pull from CI/metrics tools |
| Use case status rollup | Yes — aggregate from spec statuses |
| Decision review reminders | Yes — calendar triggers |
| Ticket counts and age | Yes — issue tracker API |
| Build/test metrics | Yes — CI pipeline data |

## Cross-References

| Need | Location |
|------|----------|
| DORA metrics (delivery performance) | `metrics/dora.md` |
| Operational health (volume, availability, tickets) | `metrics/operational-health.md` |
| Code health (quality, debt) | `metrics/code-health.md` |
| Developer experience | `metrics/space-dx.md` |
| AI agent utilization | `metrics/ai-utilization.md` |
| Agent-readiness scoring | `research/directory-standards/AGENT_READINESS_SCORING.md` |
| Security scoring | `multi-repo-orchestration/scoring/scoring-rubric.md` |
