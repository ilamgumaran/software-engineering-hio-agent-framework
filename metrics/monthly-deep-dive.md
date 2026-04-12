# Monthly Deep Dive

Template for the monthly metric analysis across all 9 categories. This is a 60-90 minute session that goes beyond the weekly pulse to examine trends, cross-category connections, and strategic adjustments.

The Metrics Monitor agent (see [../agents/metrics-monitor.md](../agents/metrics-monitor.md)) prepares the data. The cognitive unit interprets the data and decides what to change.

---

## Deep Dive Metadata

- **Month:** [Month and year]
- **Transformation Week Range:** [e.g., Weeks 5-8 of 26]
- **Unit:** [Cognitive unit name]
- **Date:** [Date]
- **Prepared by:** [Name + Metrics Monitor agent]
- **Participants:** [Names]

---

## Section 1: Full Metric Review

### Layer 1: Current

| Metric | Month Start | Month End | Trend | Status |
|---|---|---|---|---|
| Stories Completed | [value] | [value] | [arrow] | [green/yellow/red] |
| Sprint Velocity | [value] | [value] | [arrow] | [green/yellow/red] |
| Backlog Readiness | [%] | [%] | [arrow] | [green/yellow/red] |
| Priority Alignment | [%] | [%] | [arrow] | [green/yellow/red] |
| Merge/Release Rate | [value] | [value] | [arrow] | [green/yellow/red] |

### Layer 2: Outcome

| Metric | Month Start | Month End | Trend | Status |
|---|---|---|---|---|
| Deployment Frequency | [value] | [value] | [arrow] | [green/yellow/red] |
| Lead Time for Changes | [value] | [value] | [arrow] | [green/yellow/red] |
| Change Failure Rate | [%] | [%] | [arrow] | [green/yellow/red] |
| MTTR | [value] | [value] | [arrow] | [green/yellow/red] |
| Focus Time Days | [value] | [value] | [arrow] | [green/yellow/red] |
| DX Friction Events | [value] | [value] | [arrow] | [green/yellow/red] |
| Code Review Turnaround | [value] | [value] | [arrow] | [green/yellow/red] |
| Rework Rate | [%] | [%] | [arrow] | [green/yellow/red] |
| Innovation Rate | [%] | [%] | [arrow] | [green/yellow/red] |
| Self-Service Rate | [%] | [%] | [arrow] | [green/yellow/red] |

### Layer 3: HIO

| Metric | Month Start | Month End | Trend | Status |
|---|---|---|---|---|
| Avg Fulfillment Score | [value] | [value] | [arrow] | [green/yellow/red] |
| Burnout Risk Index | [value] | [value] | [arrow] | [green/yellow/red] |
| AI Sophistication Level | [L1-L5] | [L1-L5] | [arrow] | [green/yellow/red] |
| Emergence Events (MTD) | [count] | -- | -- | [green/yellow/red] |
| Workflow Experiments | [count] | -- | -- | [green/yellow/red] |
| Bandwidth Expansion | [%] | -- | -- | [green/yellow/red] |

---

## Section 2: Trend Analysis

### What Is Improving

- [Metric/pattern 1: what improved, why, and whether the improvement is sustainable]
- [Metric/pattern 2: what improved, why, and whether the improvement is sustainable]

### What Is Declining

- [Metric/pattern 1: what declined, likely cause, and recommended response]
- [Metric/pattern 2: what declined, likely cause, and recommended response]

### What Is Flat (But Shouldn't Be)

- [Metric/pattern that should be moving but is not, and what might be blocking progress]

---

## Section 3: Cross-Category Connections

Examine how changes in one category are affecting others. Document at least two connections:

| Change Observed | Impact on Other Category | Implication |
|---|---|---|
| [e.g., AI utilization depth increased to L3] | [e.g., Lead time for changes decreased 15%] | [e.g., AI code review is reducing review bottleneck] |
| [e.g., Focus time days dropped to 1.5/week] | [e.g., Innovation rate declined, fulfillment dipped] | [e.g., Meeting load from transformation activities is crowding out deep work] |

### Conflicts Between Layers

- [Document any cases where improving one layer seems to hurt another, e.g., pushing AI utilization while fulfillment drops]

---

## Section 4: Playbook Updates

Based on this month's data, what practices should change?

### Add

- [New practice to introduce, rationale from data]

### Remove

- [Practice to stop, rationale from data]

### Modify

- [Practice to adjust, what to change and why]

Playbook changes should be reflected in the relevant workflow documents (see [../workflows/](../workflows/)).

---

## Section 5: Cross-Unit Learning

- What did other cognitive units discover this month that this unit can learn from?
- [Unit A finding: description and applicability]
- [Unit B finding: description and applicability]

- What did this unit discover that other units should know about?
- [Finding 1: description and how to share it]

---

## Section 6: Recommendations

Specific actions for the next month, each tied to data:

| Recommendation | Metric Driver | Owner | Timeline |
|---|---|---|---|
| [action 1] | [which metric or trend prompted this] | [name] | [target date] |
| [action 2] | [which metric or trend prompted this] | [name] | [target date] |
| [action 3] | [which metric or trend prompted this] | [name] | [target date] |

---

## Preparation Checklist

The Metrics Monitor agent prepares:
- [ ] All Layer 1 and Layer 2 quantitative data pulled from automated sources
- [ ] Weekly pulse summaries aggregated for the month
- [ ] Anomalies and outliers flagged

The facilitator prepares:
- [ ] Layer 3 qualitative data compiled from weekly pulses
- [ ] Cross-unit learning inputs gathered
- [ ] Previous month's recommendations reviewed for progress

---

## Organization Extension Point

> **YOUR_ORG:** Adjust the metric rows in Section 1 to match your actual tracked metrics across all three layers. Add any org-specific cross-category connections you want to monitor (e.g., on-call burden vs. innovation rate). The cross-unit learning section requires a mechanism for units to share findings -- establish this channel (shared wiki, monthly all-hands, Slack channel) during Phase 0.
