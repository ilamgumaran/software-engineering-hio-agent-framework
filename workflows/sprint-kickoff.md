# Workflow: Sprint Kickoff

## Trigger

Start of each 2-week harmonized sprint. AI agents complete pre-analysis asynchronously before the meeting. The full cognitive unit meets for approximately 2 hours and 10 minutes across five phases.

---

## Participants

| Role | Human Functions | AI Agents |
|------|----------------|-----------|
| Facilitator | [Stakeholder Harmonizer](../cognitive-functions/stakeholder-harmonizer.md) | -- |
| Pre-analyst | -- | [Analysis Partner](../agents/analysis-partner.md), [Metrics Monitor](../agents/metrics-monitor.md) |
| Quality input | -- | [Quality Analyst](../agents/quality-analyst.md) |
| Context provider | -- | [Documentation & Knowledge](../agents/documentation-knowledge.md) |
| Full unit | All members (all cognitive functions) | All unit agents |

---

## Steps

### Phase 1: AI Pre-Analysis (Async, Before Meeting)

This phase runs 24-48 hours before the kickoff meeting. All outputs are shared in a pre-read document for the unit.

1. **[Metrics Monitor](../agents/metrics-monitor.md)**: Generate current metrics snapshot covering DORA metrics, platform outcomes, and code health for this cognitive unit. Include trend lines from the previous 2-3 sprints.
2. **[Analysis Partner](../agents/analysis-partner.md)**: Analyze the problem space for upcoming work including data patterns, prior art, risk factors, and cross-team dependencies. Flag any problems that may benefit from exploration time.
3. **[Quality Analyst](../agents/quality-analyst.md)**: Surface proactive quality findings from the previous sprint including test coverage gaps, technical debt trends, and incident patterns. Recommend areas where quality investment would have the highest leverage.
4. **[Documentation & Knowledge](../agents/documentation-knowledge.md)**: Compile relevant context from related ADRs, previous sprint learnings, stakeholder feedback, and emergence log entries from exploration time.

### Phase 2: Problem Framing (Full Unit, 60 minutes)

5. **All members**: Review AI pre-analysis outputs together as a starting point
6. **[Problem Framer](../cognitive-functions/problem-framer.md) functions**: Reframe through the human lens. What did AI miss? What feels wrong? What is the real problem beneath the surface?
7. **[Resonance Sensor](../cognitive-functions/resonance-sensor.md) functions**: Read energy in the room. What excites people? What feels like a slog? Where is natural momentum?
8. **[Fresh-Eyes Observer](../cognitive-functions/fresh-eyes-observer.md) functions**: Challenge assumptions. Are we solving the right problem? What are we taking for granted?

### Phase 3: Outcome Definition (30 minutes)

Outcomes are defined using the format: "By the end of this sprint, [measurable change] will be true."

9. **[Stakeholder Harmonizer](../cognitive-functions/stakeholder-harmonizer.md) functions**: Define success in outcome terms, not story points. What will be different at the end of this sprint? Ensure outcomes align with downstream team needs.
10. **All members**: Agree on 2-3 sprint outcomes (not a backlog of stories). Each outcome has clear success criteria and a definition of "achieved" versus "partially achieved."
11. **[Metrics Monitor](../agents/metrics-monitor.md)**: Confirm how each outcome will be measured, establish baselines, and set up any new tracking needed

### Phase 4: Workflow Design (30 minutes)

For each outcome, the unit designs how humans and AI agents will collaborate.

12. **All members**: For each outcome, design the human-AI collaboration workflow. Which agents support which work streams? What does the [Deep Work and Collaboration](deep-work-collaboration.md) rhythm look like for this outcome?
13. **[Builder](../cognitive-functions/builder.md)/[Solution Architect](../cognitive-functions/solution-architect.md) functions**: Claim work streams based on interest and growth opportunity, not assignment. No one is assigned work. Members volunteer for what energizes them.
14. **All members**: Assign AI agents to work streams with clear collaboration patterns. Define what each agent will do asynchronously versus in collaboration windows.
15. **[Quality Guardian](../cognitive-functions/quality-guardian.md) functions**: Identify quality checkpoints for each outcome. Where should the [Quality Analyst](../agents/quality-analyst.md) focus attention?

### Phase 5: Fulfillment Check (10 minutes)

16. **Each person**: Rate excitement and stretch on a 1-10 scale. "Am I energized? Am I growing?"
17. **Facilitator**: If anyone scores below 7/10 fulfillment, pause and adjust assignments until energy improves. This is not optional. Low fulfillment at kickoff predicts poor outcomes.
18. **[Documentation & Knowledge](../agents/documentation-knowledge.md)**: Capture sprint commitments, workflow designs, and fulfillment baselines. Publish the sprint plan to the unit's shared space.

---

## Timing Summary

| Phase | Duration | Who |
|-------|----------|-----|
| Phase 1: AI Pre-Analysis | Async (24-48 hrs before) | AI agents only |
| Phase 2: Problem Framing | 60 minutes | Full unit |
| Phase 3: Outcome Definition | 30 minutes | Full unit |
| Phase 4: Workflow Design | 30 minutes | Full unit |
| Phase 5: Fulfillment Check | 10 minutes | Full unit |

---

## Inputs

- Previous sprint outcome review results
- [Metrics Monitor](../agents/metrics-monitor.md)'s latest metrics snapshot
- [Analysis Partner](../agents/analysis-partner.md)'s problem space analysis
- Backlog of problems to solve (not user stories)
- Stakeholder feedback and priorities

## Outputs

- 2-3 defined sprint outcomes with measurable success criteria
- Human-AI workflow assignments per outcome
- Fulfillment baseline for this sprint (individual scores)
- Documented collaboration patterns for each work stream
- Pre-read document archived for reference during [Sprint Outcome Review](sprint-outcome-review.md)

---

## Anti-Patterns

- **Story point estimation.** Falling back to pointing stories instead of defining outcomes. If someone asks "how many points?", redirect to outcomes.
- **Skipping AI pre-analysis.** Starting the meeting from scratch instead of building on AI preparation. The pre-read exists so humans can think deeper, not start over.
- **Assigning work.** Telling people what to do instead of having members claim work based on interest and growth.
- **Ignoring low fulfillment.** Pushing past low energy signals instead of adjusting. A score below 7 is a blocker, not a footnote.
- **AI as final word.** Treating pre-analysis outputs as conclusions rather than starting points for human judgment.
- **Too many outcomes.** Committing to more than 3 outcomes dilutes focus and invites scope creep.
- **Rushing Phase 2.** Problem framing is where the real value lives. Never compress it to save time.

---

### Organization Extension Point

> **YOUR_ORG:** Adjust time allocations for each phase based on unit size. Add domain-specific pre-analysis steps (e.g., compliance review, security scan) to Phase 1.
