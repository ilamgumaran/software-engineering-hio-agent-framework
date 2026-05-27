# Operational Health Metrics

Operational metrics that complement DORA (delivery) and SPACE-DX (experience) with concrete, measurable signals for volume, availability, errors, tickets, testability, enhancement velocity, and merge acceptance. These are the metrics leadership watches daily and that agents use to gauge the health of the system they're building.

## Relationship to Existing Metrics

| Existing Category | What It Covers | What This File Adds |
|-------------------|---------------|---------------------|
| `dora.md` | Deployment speed & reliability | Nothing — DORA is complete |
| `code-health.md` | Structural quality (rework, debt) | Test reliability, build success, agent success |
| `space-dx.md` | Developer experience (focus, friction) | Review turnaround, merge acceptance |
| `ai-utilization.md` | Agent adoption depth | Agent implementation success rate |
| `current-legacy.md` | Sprint velocity, backlog | Ticket health, volume |

This file defines metrics that fall between the existing categories or aggregate across them.

---

## Volume & Throughput

### Specs Completed per Sprint
- **Definition**: Number of feature specs moved to IMPLEMENTED status during the sprint
- **Target**: Increasing or stable quarter over quarter
- **Collection**: Count from `tracking/use-cases/` spec tables
- **Cadence**: Sprint

### Merge Rate
- **Definition**: Number of PRs merged to default branch per week
- **Target**: Context-dependent (higher is better if quality gates hold)
- **Collection**: Git analytics (merged PRs per week)
- **Cadence**: Weekly

### Lines Changed per Spec
- **Definition**: Net lines added/removed per implemented spec (code + tests)
- **Target**: Decreasing (smaller, focused changes are better)
- **Collection**: Git diff stats per spec-linked PR
- **Cadence**: Per PR

### Agent vs Human Implementation Ratio
- **Definition**: Percentage of specs implemented primarily by agents vs humans
- **Target**: Increasing agent share as repo maturity grows
- **Collection**: PR author analysis
- **Cadence**: Sprint

---

## Availability & Reliability

### Service Availability
- **Definition**: Percentage of time the service/library is operational (for libraries: builds and tests pass on main)
- **Target**: >99.5% for services; >99.9% for library builds
- **Collection**: CI pipeline pass rate on main branch
- **Cadence**: Daily (automated)

### Error Rate
- **Definition**: Errors per 1,000 operations (for libraries: test failures per 1,000 test runs; for services: HTTP 5xx per 1,000 requests)
- **Target**: <1 per 1,000
- **Collection**: CI logs, service monitoring
- **Cadence**: Daily (automated)

### Build Success Rate
- **Definition**: Percentage of CI builds that pass on first attempt
- **Target**: >95%
- **Collection**: CI pipeline analytics
- **Cadence**: Weekly

### Build Duration
- **Definition**: Wall-clock time from commit push to all CI checks complete
- **Target**: <5 minutes for unit tests; <15 minutes for full pipeline
- **Collection**: CI timestamps
- **Cadence**: Weekly (track trend)

---

## Testability

### Test Coverage (New Code)
- **Definition**: Line coverage percentage for code added in the current sprint
- **Target**: >80% for new code
- **Collection**: Coverage tool (JaCoCo, llvm-cov, etc.)
- **Cadence**: Per PR, aggregated weekly

### Test Reliability (Flakiness)
- **Definition**: Percentage of test runs where a test fails non-deterministically
- **Target**: <2% flaky rate
- **Collection**: CI test result analysis (same commit, different outcomes)
- **Cadence**: Weekly

### Test Suite Duration
- **Definition**: Time to run the full unit test suite
- **Target**: <30 seconds for unit tests; <5 minutes for integration
- **Collection**: Test runner output
- **Cadence**: Weekly (track trend)

### Agent Test-First Compliance
- **Definition**: Percentage of agent-authored PRs where test files were committed before implementation files (TDD compliance)
- **Target**: 100%
- **Collection**: Git commit history analysis within PR
- **Cadence**: Per PR

---

## Enhancement Velocity

### Spec-to-Merge Time
- **Definition**: Calendar time from spec status READY to PR merged
- **Target**: <3 days for small specs; <7 days for large specs
- **Collection**: Spec status timestamps + PR merge timestamps
- **Cadence**: Per spec, aggregated sprint

### Agent Implementation Success Rate
- **Definition**: Percentage of specs where the agent's first PR passes all tests and meets acceptance criteria without rework
- **Target**: >70% (improving with CLAUDE.md refinements)
- **Collection**: PR review history (approved on first review vs needed changes)
- **Cadence**: Sprint

### Rework Cycles
- **Definition**: Number of review-and-revise cycles before a PR is approved
- **Target**: <2 cycles average
- **Collection**: PR review history
- **Cadence**: Per PR, aggregated sprint

### Enhancement Ease Score
- **Definition**: Composite score (1-5) reflecting how easily new features can be added. Factors: spec clarity (A2 from scoring rubric), test infrastructure (A3), build simplicity (A4).
- **Target**: >4.0
- **Collection**: Agent-readiness self-score dimensions A2+A3+A4, averaged
- **Cadence**: Quarterly (with re-scoring)

---

## Merge Acceptance

### PR Review Turnaround
- **Definition**: Time from PR opened to first substantive review
- **Target**: <4 hours during business hours
- **Collection**: GitHub/GitLab PR analytics
- **Cadence**: Per PR, aggregated weekly

### PR Approval Rate
- **Definition**: Percentage of PRs approved without "request changes"
- **Target**: >60% (indicates specs and CLAUDE.md are effective)
- **Collection**: PR review outcomes
- **Cadence**: Sprint

### Merge Queue Time
- **Definition**: Time from PR approved to PR merged
- **Target**: <1 hour
- **Collection**: PR timestamps
- **Cadence**: Per PR, aggregated weekly

### Review Comment Density
- **Definition**: Number of review comments per PR (excluding nits/style)
- **Target**: Decreasing trend (indicates improving agent output quality)
- **Collection**: PR review comments
- **Cadence**: Sprint

---

## Ticket & Issue Health

### Open Ticket Count
- **Definition**: Total open issues/tickets at any point
- **Target**: Stable or decreasing
- **Collection**: Issue tracker
- **Cadence**: Weekly snapshot

### Average Ticket Age
- **Definition**: Mean age (days) of all open tickets
- **Target**: <14 days
- **Collection**: Issue tracker
- **Cadence**: Weekly

### Ticket Resolution Rate
- **Definition**: Percentage of tickets resolved within their SLA or target timeframe
- **Target**: >80%
- **Collection**: Issue tracker (closed within SLA / total closed)
- **Cadence**: Sprint

### Bug Backlog Trend
- **Definition**: Direction of open bug count over time (increasing/stable/decreasing)
- **Target**: Decreasing or stable
- **Collection**: Issue tracker, bugs label
- **Cadence**: Sprint

### Ticket-to-Spec Ratio
- **Definition**: Percentage of bug tickets that result in a spec (vs ad-hoc fixes)
- **Target**: >50% for non-trivial bugs (forces root cause thinking)
- **Collection**: Cross-reference tickets to specs
- **Cadence**: Sprint

---

## Dashboard Summary

For weekly pulse meetings, present these as a single-page dashboard:

```
┌─────────────────────────────────────────────────────┐
│              OPERATIONAL HEALTH PULSE                │
├──────────────┬──────────────┬───────────────────────┤
│ VOLUME       │ AVAILABILITY │ TESTABILITY           │
│ Specs: N/spr │ Build: N%    │ Coverage: N%          │
│ PRs: N/week  │ Errors: N‰   │ Flaky: N%            │
│ Agent%: N%   │ Duration: Nm │ Suite: Ns             │
├──────────────┼──────────────┼───────────────────────┤
│ VELOCITY     │ MERGE        │ TICKETS               │
│ S2M: Nd      │ Review: Nh   │ Open: N               │
│ Success: N%  │ Approval: N% │ Age: Nd               │
│ Rework: N    │ Queue: Nh    │ Resolution: N%        │
└──────────────┴──────────────┴───────────────────────┘
```

## Thresholds and Alerts

| Metric | Green | Yellow | Red |
|--------|-------|--------|-----|
| Build Success Rate | >95% | 90-95% | <90% |
| Error Rate | <1‰ | 1-5‰ | >5‰ |
| Test Flakiness | <2% | 2-5% | >5% |
| Spec-to-Merge Time | <3d | 3-7d | >7d |
| PR Review Turnaround | <4h | 4-8h | >8h |
| Agent Success Rate | >70% | 50-70% | <50% |
| Ticket Resolution | >80% | 60-80% | <60% |
| Average Ticket Age | <14d | 14-30d | >30d |

When a metric enters **Red**, it triggers a root-cause investigation at the next weekly pulse. When it stays Red for 2 consecutive weeks, it becomes a sprint priority.
