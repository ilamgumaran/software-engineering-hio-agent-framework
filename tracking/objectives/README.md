# Objectives & Key Results — Tracking

This directory defines organizational objectives and the metrics that measure progress toward them. Objectives connect the "why" (business goals) to the "what" (use cases and specs) and the "how well" (metrics).

## Objective Hierarchy

```
Organization Goals
  └── Engineering Objectives (this directory)
        ├── Key Results (measurable targets)
        │     └── Metrics (from metrics/ directory)
        └── Use Cases (from tracking/use-cases/)
              └── Specs (from specs/)
                    └── Implementation (code)
```

## Objective Format

Each objective is a markdown file in `tracking/objectives/`:

```markdown
# OBJ-NNN: [Objective Title]

## Status: [ACTIVE | ACHIEVED | PAUSED | RETIRED]
## Owner: [Human name]
## Timeframe: [Q1 2026 | H1 2026 | Ongoing]

## Description
[What we're trying to achieve and why it matters]

## Key Results

| KR | Target | Current | Metric Source | Status |
|----|--------|---------|---------------|--------|
| KR1: [description] | [target value] | [current value] | [metrics/file.md → metric name] | [On Track / At Risk / Behind] |
| KR2: [description] | [target value] | [current value] | [metrics/file.md → metric name] | [status] |

## Linked Use Cases
| Use Case | Status |
|----------|--------|
| UC-NNN: [name] | [status] |

## Linked Decisions
| Decision | Impact |
|----------|--------|
| DR-NNN: [name] | [how it serves this objective] |

## Review Cadence
[Weekly / Biweekly / Monthly / Quarterly]

## History
| Date | Event |
|------|-------|
| YYYY-MM-DD | Objective created |
| YYYY-MM-DD | KR1 current value updated to X |
```

---

## Standard Engineering Objectives

The following objectives are recommended for any engineering organization adopting agentic development. Each maps to specific metrics from the `metrics/` directory.

### Delivery Performance (DORA)

| Objective | Key Results | Metric Source |
|-----------|------------|---------------|
| Increase deployment frequency | Deploy to production N times per week | `metrics/dora.md` → Deployment Frequency |
| Reduce lead time for changes | Spec-to-merge in <N days | `metrics/dora.md` → Lead Time |
| Minimize change failure rate | <N% of deployments cause incidents | `metrics/dora.md` → Change Failure Rate |
| Reduce recovery time | MTTR <N hours | `metrics/dora.md` → Mean Time to Recovery |

### Volume & Throughput

| Objective | Key Results | Metric Source |
|-----------|------------|---------------|
| Increase spec throughput | Complete N specs per sprint | `metrics/operational-health.md` → Specs Completed |
| Maintain merge velocity | Merge N PRs per week with <N hours review time | `metrics/operational-health.md` → Merge Rate |
| Scale agent utilization | N% of specs implemented by agents | `metrics/ai-utilization.md` → AI Usage Depth |

### Availability & Reliability

| Objective | Key Results | Metric Source |
|-----------|------------|---------------|
| Maintain service availability | >N% uptime | `metrics/operational-health.md` → Service Availability |
| Reduce error rate | <N errors per 1000 requests | `metrics/operational-health.md` → Error Rate |
| Improve build reliability | <N% build failures | `metrics/operational-health.md` → Build Success Rate |

### Quality & Testability

| Objective | Key Results | Metric Source |
|-----------|------------|---------------|
| Increase test coverage | >N% line coverage for new code | `metrics/operational-health.md` → Test Coverage |
| Reduce test flakiness | <N% flaky test rate | `metrics/operational-health.md` → Test Reliability |
| Ease of testing | Agent can run full test suite in <N minutes | `metrics/operational-health.md` → Test Suite Duration |
| Reduce defect escape rate | <N% of defects found in production | `metrics/code-health.md` → Defect Escape Rate |

### Developer & Agent Experience

| Objective | Key Results | Metric Source |
|-----------|------------|---------------|
| Ease of enhancement | Agent implements spec in <N attempts | `metrics/operational-health.md` → Agent Success Rate |
| Ease of merge acceptance | PR review turnaround <N hours | `metrics/operational-health.md` → Review Turnaround |
| Reduce friction | <N friction events per developer per week | `metrics/space-dx.md` → Friction Events |

### Ticket & Issue Health

| Objective | Key Results | Metric Source |
|-----------|------------|---------------|
| Reduce open ticket age | Average ticket age <N days | `metrics/operational-health.md` → Ticket Age |
| Improve ticket resolution | N% of tickets resolved within SLA | `metrics/operational-health.md` → Ticket Resolution Rate |
| Reduce bug backlog | Open bug count decreasing quarter over quarter | `metrics/operational-health.md` → Bug Backlog Trend |

---

## Traceability Matrix

```
OBJ-001: Reduce lead time
  ├── KR: Spec-to-merge <3 days
  │     └── Metric: metrics/dora.md → Lead Time
  ├── UC-003: BM25 Scoring
  │     ├── Spec: specs/features/003-bm25-scorer.md
  │     └── PR: #15
  └── DR-001: Adopt spec-driven TDD
        └── Rationale: Eliminates ambiguity → faster implementation
```

This traceability ensures that every line of code can be traced back through spec → use case → objective → business goal. When an objective is reviewed, you can see exactly which use cases serve it, which specs implement those use cases, and whether the metrics are trending in the right direction.
