# Weekly Harmony Pulse

Template for the weekly pulse check across all three metric layers. Used by the Metrics Monitor agent (see [../agents/metrics-monitor.md](../agents/metrics-monitor.md)) to prepare data and by the cognitive unit to facilitate a 30-minute weekly conversation.

This is a conversation template, not just a data collection form. The numbers surface where to look. The conversation reveals what is actually happening.

---

## Pulse Metadata

- **Week:** [Week number in transformation, e.g., Week 7 of 26]
- **Unit:** [Cognitive unit name]
- **Date:** [Date]
- **Facilitator:** [Name -- rotate weekly]
- **Participants:** [Names or count]

---

## Section 1: Delivery Health

### DORA Snapshot

| Metric | This Week | Last Week | Trend | Notes |
|---|---|---|---|---|
| Deployment Frequency | [value] | [value] | [up/down/stable] | [context] |
| Lead Time for Changes | [value] | [value] | [up/down/stable] | [context] |
| Change Failure Rate | [value] | [value] | [up/down/stable] | [context] |
| MTTR | [value] | [value] | [up/down/stable] | [context] |

### Current/Legacy Check

| Metric | This Sprint | Last Sprint | On Track? |
|---|---|---|---|
| Stories Completed | [value] | [value] | [yes/no] |
| Sprint Velocity | [value] | [value] | [yes/no] |
| Priority Alignment | [%] | [%] | [yes/no] |

### Blockers

- [Blocker 1: description, owner, expected resolution]
- [Blocker 2: description, owner, expected resolution]

---

## Section 2: Harmonization Check

### Emergence Events This Week

- [Describe any emergence events -- moments where human-AI collaboration produced unexpected value. If none, write "None this week" and note why.]

### Collaboration Patterns

- Cross-function contributions this week: [describe instances of people contributing outside their primary cognitive function]
- Notable human-AI workflow patterns: [describe any effective or ineffective collaboration patterns observed]

### Workflow Experiments

| Experiment | What Was Tried | Outcome | Keep/Modify/Drop |
|---|---|---|---|
| [name] | [description] | [result] | [decision] |

---

## Section 3: Fulfillment Signals

### Quick Pulse (Anonymous, 1-10)

Capture these via anonymous quick poll before or during the session:

- Average energy level this week: [1-10]
- Average intellectual challenge this week: [1-10]
- Average sense of progress this week: [1-10]

### Growth Observations

- Who expanded their bandwidth this week? [names and what they tried -- only share with consent]
- Function rotations this week: [who moved into which cognitive function]

### Red Flags

- [ ] Burnout signals observed (sustained low energy, withdrawal, cynicism)
- [ ] Psychological safety concern (reluctance to speak up, risk avoidance)
- [ ] Fulfillment dip (disengagement, loss of purpose connection)
- [ ] Other: [describe]

If any red flag is checked, escalate to the unit lead for follow-up conversation within 48 hours.

---

## Section 4: AI Health

### Agent Utilization

- Most-used agents this week: [list]
- Average sophistication level this week: [L1-L5]
- Sophistication trend: [up/down/stable vs. last week]

### Novel Uses

- [Describe any creative or unexpected uses of AI agents this week]

### AI Friction

- [Describe any points where AI agents hindered rather than helped -- miscalibrated suggestions, workflow disruptions, trust breakdowns]

---

## Section 5: Actions

### What to Adjust Next Week

| Action | Owner | Why |
|---|---|---|
| [action 1] | [name] | [rationale from pulse data] |
| [action 2] | [name] | [rationale from pulse data] |
| [action 3] | [name] | [rationale from pulse data] |

### Carry-Forward Items

- [Items from last week that remain unresolved]

### Signals for Monthly Deep Dive

- [Patterns or concerns that need deeper analysis in the monthly review]

---

## Facilitation Notes

- Keep the session to 30 minutes. If a topic needs more time, schedule a follow-up rather than extending.
- The anonymous quick pulse should be captured before the meeting starts (async poll). Do not ask people to report fulfillment numbers verbally -- it defeats anonymity.
- Rotate the facilitator role weekly. This builds shared ownership and develops facilitation skills across the unit.
- The Metrics Monitor agent prepares Section 1 data automatically. The facilitator prepares Sections 2-5 from team input.
- Document the pulse in a shared location accessible to the unit. The monthly deep dive draws from weekly pulses.

---

## Organization Extension Point

> **YOUR_ORG:** Adjust the DORA and Current/Legacy metrics in Section 1 to match what you actually track. Add any org-specific health signals (e.g., on-call burden, incident count, customer escalations) to Section 1. The facilitation format (synchronous meeting, async document, Slack thread) should match your team's collaboration patterns.
