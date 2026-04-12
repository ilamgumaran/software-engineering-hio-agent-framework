# Transformation Prompt: Generate transformation/ (8 files)

## Objective

Generate the README and 7 supporting files that guide the 26-week transformation from traditional scrum to full HIO orchestration. The transformation is criteria-driven, not calendar-driven -- phases advance when exit criteria are met, not when weeks elapse.

## 4-Phase Overview

| Phase | Name | Weeks | Key Activity | End State |
|-------|------|-------|-------------|-----------|
| 0 | Seed | 1-3 | Baseline capture, pioneer selection, alignment | Ready to form first unit |
| 1 | First Cognitive Unit | 4-10 | Form unit, run 3 harmonized sprints, measure | One unit operating in HIO mode |
| 2 | Prove & Expand | 11-18 | Data-driven scaling, 2 more units, coach training | 3 units operating, coaches trained |
| 3 | Full Orchestration | 19-26 | All 30 people in units, full measurement, optimization | Organization in steady-state HIO |

## End-State Targets

- All team members mapped to cognitive functions
- All 5 cognitive units formed and operating
- All 6 AI agents deployed and integrated
- Full three-layer metrics operational
- Harmonized Sprint cadence established across all units
- HIO coaches embedded in each unit

## Files to Generate

### README.md
Include: 4-phase overview table, text-based timeline visualization, exit-criteria philosophy explanation, and links to all phase files. 70-90 lines.

### 4 Phase Files

Each phase file follows this structure:

```markdown
# Phase [N]: [Name] (Weeks X-Y)

## Objective
What this phase achieves.

## Week-by-Week Activities
### Week X: [Focus]
Detailed activities for the week.
(repeat for each week)

## Key Deliverables
Bullet list of concrete outputs.

## Exit Criteria
- [ ] Criterion 1 (measurable)
- [ ] Criterion 2 (measurable)
(5-8 checkbox items)

## Risks
Phase-specific risks with mitigation references.

### Organization Extension Point
> Adjust timeline and criteria to your organization's pace.
```

Content guidance per phase:
- **Phase 0 Seed**: Capture baselines across all 9 metric categories, select 5-7 pioneers, run HIO orientation workshops, identify first cognitive unit focus area. Exit criteria include baseline captured, pioneers committed, first unit scope defined.
- **Phase 1 First Unit**: Form Experiment Velocity (or chosen unit), assign cognitive functions, deploy 3 agents, run 3 harmonized sprints. Exit criteria include 3 sprints completed, metrics show improvement or parity, team reports positive fulfillment.
- **Phase 2 Prove & Expand**: Analyze Phase 1 data, form Scale & Reliability and Developer Experience units, train 3 HIO coaches, expand metrics to all 3 units. Exit criteria include 3 units operating, coaches certified, cross-unit workflows functioning.
- **Phase 3 Full Orchestration**: Form Intelligence Layer and Frontier units, deploy all 6 agents, full three-layer metrics, optimize based on 18+ weeks of data. Exit criteria include all 30 people in units, all agents deployed, steady-state metrics established.

### risk-management.md
Cover 6 risk categories with likelihood, impact, mitigation strategy, and early warning indicators:
1. Adoption resistance (people reject the model)
2. AI trust deficit (people do not trust agent outputs)
3. Metric gaming (optimizing numbers over outcomes)
4. Cognitive overload (too much change too fast)
5. Leadership misalignment (executives expect different outcomes)
6. Technical integration failure (agents do not connect to tooling)
80-100 lines.

### hio-coach-guide.md
Define the HIO Coach role: skills required, daily activities, coaching patterns, certification criteria, relationship to cognitive functions. Coaches are not managers -- they are Growth Catalyst function carriers who facilitate unit health. 80-100 lines.

### emergence-detection.md
Define what emergence looks like, how to detect it, capture methods, and amplification strategies. Include emergence pattern catalog (5+ patterns), capture workflow, and examples from platform engineering. 80-100 lines.

## Formatting Rules

- Exit criteria must use checkbox syntax: `- [ ] Criterion`
- Week-by-week activities must use H3 headings per week
- Risk tables must include Likelihood, Impact, and Mitigation columns
- 80-130 lines per file
- No YAML frontmatter
- Cross-reference metrics: `[Category](../metrics/file.md)`
- Cross-reference workflows: `[Workflow](../workflows/file.md)`
