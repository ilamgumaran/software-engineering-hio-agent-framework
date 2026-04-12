# Implementation Guide

## Overview

This guide maps the 26-week HIO transformation into concrete implementation steps. Each phase builds on the previous, with verification gates that must pass before advancing. The transformation runs in parallel with ongoing delivery -- expect a 10-15% throughput dip in Phase 1 that recovers by Phase 2.

See `transformation/` for operational detail on each phase. This document focuses on **what to implement and how to verify it**.

---

## Phase 0: Seed (Weeks 1-3)

### What to Implement

| Step | Description | Owner |
|------|-------------|-------|
| Measurement infrastructure | Deploy DORA metric collection, fulfillment surveys, AI utilization tracking | Metrics Monitor agent + designated engineer |
| Baseline capture | Record all 9 metric categories at current state | Metrics Monitor agent |
| AI tool provisioning | Configure Claude Code, GitHub Copilot, Gemini Enterprise, Glean access for pioneers | Infrastructure lead |
| Cognitive profiling | Each pioneer completes their cognitive function profile | All pioneers |
| Pioneer selection | Identify 5-6 volunteers for the first cognitive unit | Leadership + volunteers |
| Agent configuration | Set up Analysis Partner and Code Co-Creator for the first unit | Infrastructure lead |

### How to Implement

1. Start with `org/measurement-baseline.md` -- fill in every metric you can measure today
2. Deploy the Metrics Monitor agent connected to Git, CI/CD, and observability systems
3. Run the first fulfillment survey (anonymous, 5 questions, takes 3 minutes)
4. Workshop cognitive profiles using `org/cognitive-profiles.md` as the template
5. Configure agent guardrails per `org/policies.md`

### Verification

- [ ] Baseline document completed with values for all 3 metric layers
- [ ] At least one DORA metric collecting automatically
- [ ] Fulfillment survey completed by all pioneers
- [ ] Each pioneer has a cognitive profile on file
- [ ] AI tools accessible and passing security review

See `plan/phases/phase-0-seed.md` for the strategic summary and `transformation/phase-0-seed.md` for full operational detail.

---

## Phase 1: First Unit (Weeks 4-10)

### What to Implement

| Step | Description | Owner |
|------|-------------|-------|
| First cognitive unit launch | Form the unit, assign outcome, begin harmonized sprints | Unit lead + pioneers |
| Full agent deployment | All 6 agents operational for the first unit | Infrastructure lead |
| Harmonized sprint cadence | Replace scrum ceremonies with HIO workflow | Unit lead |
| Emergence logging | Begin capturing emergence events | Documentation & Knowledge agent |
| Working agreements | Workshop and document unit agreements | Entire first unit |
| Comparison board | Set up side-by-side metric view (first unit vs. legacy teams) | Metrics Monitor agent |

### How to Implement

1. Select the first cognitive unit based on pioneer interest and organizational need -- **Experiment Velocity** is recommended as the first unit because its fast feedback loops make emergence visible quickly
2. Define the unit's outcome in one sentence (e.g., "Ship validated experiments to production within 48 hours")
3. Run the first harmonized sprint using `workflows/` cadences
4. Configure all 6 agents with unit-specific context from `config/`
5. Workshop working agreements using `org/working-agreements.md`

### Verification

- [ ] First unit operational with defined outcome
- [ ] All 6 agents deployed and used at least once
- [ ] At least 2 harmonized sprints completed
- [ ] Emergence log contains at least 1 entry
- [ ] Working agreements documented and signed
- [ ] Comparison board showing data for first unit vs. legacy

See `plan/phases/phase-1-first-unit.md` for the strategic summary and `transformation/phase-1-first-unit.md` for full operational detail.

---

## Phase 2: Prove and Expand (Weeks 11-18)

### What to Implement

| Step | Description | Owner |
|------|-------------|-------|
| Second and third units | Form 2 additional cognitive units from willing volunteers | Leadership + volunteers |
| HIO coach training | Train 2-3 coaches to support unit formation and sprint facilitation | Growth Catalyst function holders |
| Cross-unit patterns | Establish knowledge sharing between units | Documentation & Knowledge agent |
| Metric maturity | All 9 metric categories collecting automatically | Metrics Monitor agent |
| Agent sophistication | Move agents from L2 (Directed Assistant) to L3 (Proactive Collaborator) | All units |
| Legacy team transition planning | Begin planning conversion of remaining legacy teams | Leadership |

### How to Implement

1. Use evidence from Phase 1 to recruit the next wave -- share the comparison board results
2. Let new units self-select their outcome focus from the remaining cognitive unit types
3. Train coaches using `transformation/hio-coach-guide.md`
4. Establish a weekly cross-unit sync (30 minutes, pattern sharing only)
5. Review and update `org/policies.md` based on Phase 1 learnings

### Verification

- [ ] 3 cognitive units operational (15-18 people)
- [ ] At least 2 trained HIO coaches
- [ ] Cross-unit knowledge sharing happening weekly
- [ ] All 9 metric categories reporting automatically
- [ ] Agent utilization at L3 for at least 2 units
- [ ] Comparison board shows measurable improvement over legacy baseline

See `plan/phases/phase-2-prove-expand.md` and `transformation/phase-2-prove-expand.md`.

---

## Phase 3: Full Orchestration (Weeks 19-26)

### What to Implement

| Step | Description | Owner |
|------|-------------|-------|
| Remaining units | Convert final legacy teams into cognitive units 4 and 5 | Leadership + coaches |
| Self-optimizing workflows | Units adjust their own sprint cadence based on metrics | Each unit |
| Full metric dashboard | Organization-wide 9-category dashboard live | Metrics Monitor agent |
| Agent maturity L4 | Agents operating as collaborative partners across all units | All units |
| Organizational learning | Capture the full transformation narrative | Documentation & Knowledge agent |
| Sustainability model | Establish ongoing rhythms that persist beyond the 26 weeks | Leadership + coaches |

### How to Implement

1. Final unit formation -- by now, evidence should make conversion compelling rather than forced
2. Enable units to modify their sprint length, ceremony structure, and agent configurations
3. Deploy the organization-wide dashboard rolling up all unit metrics
4. Conduct a full transformation retrospective at Week 26
5. Document the sustainability model in `transformation/` for ongoing reference

### Verification

- [ ] All 5 cognitive units operational (~30 people)
- [ ] DORA metrics at Elite or High tier
- [ ] Fulfillment score above 8.0 average
- [ ] Agent utilization at L4 across all units
- [ ] Emergence events averaging 2+ per unit per sprint
- [ ] Sustainability rhythms documented and practiced

See `plan/phases/phase-3-full-orchestration.md` and `transformation/phase-3-full-orchestration.md`.

---

## Phase Gate Protocol

Each phase transition requires a gate review:

| Gate | Approvers | Key Question |
|------|-----------|-------------|
| Phase 0 to 1 | Engineering Leadership | Is the measurement infrastructure reliable? |
| Phase 1 to 2 | Engineering Leadership + First Unit | Has the first unit demonstrated measurable improvement? |
| Phase 2 to 3 | Engineering Leadership + Coaches | Are coaches ready to support full-org conversion? |
| Phase 3 Exit | Full Organization | Is the new operating model self-sustaining? |

**Gate failure protocol:** If a gate fails, extend the current phase by 2 weeks and address the gap. Do not compress future phases to compensate.
