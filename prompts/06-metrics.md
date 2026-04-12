# Metrics Prompt: Generate metrics/ (14 files)

## Objective

Generate the README, 9 metric category files, and 4 measurement template files. The metrics system uses a three-layer model that bridges existing engineering metrics with HIO-specific measurements.

## Three-Layer Model

| Layer | Purpose | Categories |
|-------|---------|------------|
| Layer 1: Current | Bridge from existing metrics | Current/Legacy |
| Layer 2: Outcome | Industry-standard outcome measurement | DORA, SPACE/DX, Platform Outcomes, Code Health, Innovation |
| Layer 3: HIO | Framework-specific value measurement | Human Fulfillment, AI Utilization, Harmonization |

## Measurement Cadence

| Cadence | What | Template |
|---------|------|----------|
| Weekly | Pulse survey (5 questions), DORA snapshot | weekly-pulse.md |
| Monthly | Full metric review, trend analysis | monthly-deep-dive.md |
| Quarterly | Evolution assessment, phase evaluation | quarterly-evolution.md |
| Baseline | Initial capture before Phase 0 | baseline-survey.md |

## The 9 Metric Categories

| Category | KPI Count | Key Focus |
|----------|----------|-----------|
| DORA | 4 | Deployment frequency, lead time, MTTR, change failure rate |
| SPACE/DX | 5-6 | Satisfaction, performance, activity, communication, efficiency |
| Platform Outcomes | 5-6 | Adoption, self-service rate, time-to-production |
| Code Health | 4-5 | Test coverage, complexity, dependency freshness, tech debt |
| Innovation | 4-5 | Experiment count, learning cycle time, idea-to-prototype |
| Human Fulfillment | 5-6 | Flow state frequency, function alignment, growth satisfaction |
| AI Utilization | 4-5 | Agent invocation rate, suggestion acceptance, time saved |
| Harmonization | 4-5 | Human-AI collaboration quality, emergence events, unit cohesion |
| Current/Legacy | 4-5 | Existing velocity, burndown, capacity metrics for bridge period |

## Files to Generate

### README.md
Include: three-layer model explanation, cadence table, guidance on metric evolution across transformation phases, and connections between layers. 70-90 lines.

### 9 Category Files

Each file follows this template:

```markdown
# [Category Name]

## Purpose
Why this category exists and what it measures.

## KPIs
| KPI | Formula | Target | Cadence |
4-7 rows with specific, measurable indicators.

## Baseline Capture
How to establish initial measurements for this category.

## Interpretation Guide
How to read these numbers -- what good looks like, warning signs, context.

## Connections
How this category relates to other metric categories.

### Organization Extension Point
> Add organization-specific KPIs and adjust targets.
```

### 4 Template Files

- **baseline-survey.md**: 25 questions across all 9 categories, mix of Likert scale and numeric. Include scoring guide. 120-150 lines.
- **weekly-pulse.md**: 5-question pulse survey plus DORA snapshot format. Quick to complete. 80-100 lines.
- **monthly-deep-dive.md**: Full analysis template covering all 3 layers, trend charts placeholders, action items. 100-130 lines.
- **quarterly-evolution.md**: Phase assessment against transformation goals, metric evolution tracking, next-phase readiness. 100-130 lines.

## Formatting Rules

- KPI tables must include Formula, Target, and Cadence columns
- Baseline Survey must have exactly 25 questions, numbered
- Weekly Pulse must have exactly 5 questions
- 60-80 lines for category files, 80-150 for templates
- No YAML frontmatter
- Cross-reference transformation phases: `[Phase](../transformation/file.md)`
- Cross-reference cognitive units: `[Unit](../cognitive-units/file.md)`
