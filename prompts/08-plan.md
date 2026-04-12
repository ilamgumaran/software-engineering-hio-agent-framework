# Plan Prompt: Generate plan/ (10 files)

## Objective

Generate 6 main plan documents and 4 phase summary files. The plan/ directory provides the strategic layer of the framework -- executive-level documents that explain what the HIO transformation is, how it works, and why it matters.

## 6 Main Plan Documents

| File | Focus | Lines |
|------|-------|-------|
| 00-overview.md | Executive summary of the entire HIO approach | 100-130 |
| 01-architecture.md | System design showing how components connect | 80-120 |
| 02-capability-matrix.md | Skills mapping across functions, agents, and units | 80-110 |
| 03-measurement-framework.md | Metrics strategy across all 4 phases | 80-120 |
| 04-adoption-strategy.md | Change management approach | 80-110 |
| 05-foundational-tools.md | Tooling requirements and integration plan | 80-110 |

### 00-overview.md
Include: executive summary (2-3 paragraphs), the 5 core design principles, the HIO model diagram (text-based showing functions -> agents -> units -> outcomes), 26-week timeline summary, expected outcomes with quantified targets.

### 01-architecture.md
Include: architecture diagram (text-based showing component relationships), component descriptions for each layer (functions, agents, units, workflows, metrics), integration points between components, data flow description showing how information moves through the system.

### 02-capability-matrix.md
Include: function-by-skill matrix table, agent capability coverage table, unit-to-function allocation table, skill gap analysis template, and growth path summary connecting individual development to organizational capability.

### 03-measurement-framework.md
Include: three-layer metric model (referencing metrics/), measurement cadence across transformation phases, baseline-to-target progression table, dashboard design guidance, and metric evolution strategy explaining how Layer 1 metrics phase out as Layer 3 matures.

### 04-adoption-strategy.md
Include: change management philosophy (invitation over mandate), stakeholder mapping template, communication plan across 4 phases, resistance patterns and responses, pioneer program design, and celebration milestones.

### 05-foundational-tools.md
Include: required tooling categories (CI/CD, collaboration, metrics, AI agents), integration architecture, tool selection criteria, Jinja2 template system explanation (referencing templates/), and minimum viable tooling for Phase 0.

## 4 Phase Summary Files (plan/phases/)

| File | Phase | Lines |
|------|-------|-------|
| phase-0.md | Seed (Weeks 1-3) | 40-60 |
| phase-1.md | First Cognitive Unit (Weeks 4-10) | 40-60 |
| phase-2.md | Prove & Expand (Weeks 11-18) | 40-60 |
| phase-3.md | Full Orchestration (Weeks 19-26) | 40-60 |

Each phase summary includes: objective (1-2 sentences), key activities (5-7 bullets), success criteria (3-5 bullets), resource requirements, and references to detailed transformation/ phase files.

These are concise summaries for executive audiences -- the detailed week-by-week plans live in transformation/.

## Formatting Rules

- Architecture diagrams use text-based representation (indented lists or ASCII)
- Capability matrices use tables with 5+ rows
- Phase summaries must cross-reference: `[Detailed Plan](../transformation/phase-N-name.md)`
- No YAML frontmatter
- 80-130 lines for main documents, 40-60 lines for phase summaries
- Cross-reference metrics: `[Metrics](../metrics/README.md)`
- Cross-reference cognitive units: `[Unit](../cognitive-units/file.md)`
