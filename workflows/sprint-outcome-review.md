# Workflow: Sprint Outcome Review

## Trigger

End of each 2-week harmonized sprint (Friday, Week 2). Precedes the [Harmonization Retrospective](harmonization-retrospective.md).

---

## Participants

| Role | Human Functions | AI Agents |
|------|----------------|-----------|
| Facilitator | [Stakeholder Harmonizer](../cognitive-functions/stakeholder-harmonizer.md) | -- |
| Metrics presenter | -- | [Metrics Monitor](../agents/metrics-monitor.md) |
| Full unit | All members | All unit agents |
| Stakeholders | Downstream teams, customers (optional) | -- |

---

## Steps

### Phase 1: Metrics Comparison (15 minutes)

1. **[Metrics Monitor](../agents/metrics-monitor.md)**: Present full metrics comparison for the sprint. Baseline values at kickoff versus current state. Include DORA metrics, platform outcomes, code health, and any custom outcome metrics defined during kickoff.
2. **[Quality Analyst](../agents/quality-analyst.md)**: Present quality trends across the sprint including test coverage changes, defect rates, and technical debt movement.
3. **All members**: Discuss what the numbers reveal. Where did metrics move as expected? Where did they surprise us?

### Phase 2: Outcome Demonstrations (20 minutes)

4. **Outcome owners**: For each of the 2-3 sprint outcomes, demonstrate the OUTCOME achieved, not the features built. Frame each demo as: "We committed to [outcome]. Here is evidence that [outcome] was achieved."
5. **[Analysis Partner](../agents/analysis-partner.md)**: Provide data-backed assessment of each outcome against the success criteria defined at kickoff.
6. **Stakeholders**: Share reactions. Did the outcomes solve the problems they were meant to solve?

### Phase 3: Emergence Showcase (15 minutes)

7. **All members**: Highlight moments where human-AI collaboration produced unexpected value. What emerged that nobody planned for?
8. **[Architecture Explorer](../agents/architecture-explorer.md)**: Surface architectural insights or patterns that emerged from the sprint's work.
9. **[Documentation & Knowledge](../agents/documentation-knowledge.md)**: Present entries from the sprint's emergence log. Connect emergence events to broader patterns across sprints.

### Phase 4: Downstream Feedback (10 minutes)

10. **Stakeholders/downstream teams**: Share how the sprint's outcomes affected their work. What landed well? What needs adjustment?
11. **[Resonance Sensor](../cognitive-functions/resonance-sensor.md) functions**: Read the energy of the feedback. What resonates? What causes tension?
12. **[Documentation & Knowledge](../agents/documentation-knowledge.md)**: Capture all feedback, emergence events, and outcome assessments for the retrospective and future sprints.

---

## Inputs

- Sprint kickoff outcomes and success criteria
- [Metrics Monitor](../agents/metrics-monitor.md) baseline and current metrics
- Sprint emergence log
- Stakeholder and downstream team feedback

## Outputs

- Outcome achievement assessment (achieved, partially achieved, not achieved) with evidence
- Documented emergence events and unexpected value
- Stakeholder feedback summary
- Metrics delta report (baseline to current)

---

## Anti-Patterns

- **Counting stories completed.** The review is about outcomes achieved, not volume of work done.
- **Skipping the emergence showcase.** Emergence is where the deepest value lives. Never cut it for time.
- **No downstream feedback.** Without external perspective, the review becomes self-congratulatory.
- **Feature demos instead of outcome demos.** Show what changed, not what was built.
- **Blaming AI for missed outcomes.** AI agents are tools. Missed outcomes are signals about the workflow, not the agent.
- **Ignoring partial achievements.** Partial outcomes still contain learnings. Explore them instead of writing them off.

---

### Organization Extension Point

> **YOUR_ORG:** Add stakeholder-specific review segments for compliance, security, or business metrics relevant to your domain.
