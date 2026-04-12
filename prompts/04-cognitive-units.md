# Cognitive Units Prompt: Generate cognitive-units/ (7 files)

## Objective

Generate the README, 5 unit definition files, and a blank template. Cognitive units replace traditional scrum teams. Each unit is organized around an outcome, not a backlog, and includes both humans and AI agents.

## The 5 Cognitive Units

| Unit | Outcome Focus | Typical Size |
|------|---------------|-------------|
| Experiment Velocity | Making experiments faster to launch and cheaper to run | 5-7 humans + 3 agents |
| Scale & Reliability | Platform handles anything thrown at it with minimal toil | 5-7 humans + 3 agents |
| Developer Experience | Making the platform a joy to build on | 5-7 humans + 3 agents |
| Intelligence Layer | AI-native platform capabilities that learn and adapt | 4-6 humans + 3 agents |
| Frontier | Exploration of next-generation possibilities | 3-5 humans + 2 agents |

## Cross-Unit Dependencies

| Unit | Depends On | Provides To |
|------|-----------|------------|
| Experiment Velocity | Developer Experience (tooling), Scale & Reliability (infra) | Intelligence Layer (experiment data) |
| Scale & Reliability | Intelligence Layer (anomaly detection) | All units (reliable platform) |
| Developer Experience | Scale & Reliability (stable foundation) | Experiment Velocity (fast workflows) |
| Intelligence Layer | Scale & Reliability (compute), Experiment Velocity (data) | All units (AI capabilities) |
| Frontier | Intelligence Layer (AI capabilities) | All units (future patterns) |

## Files to Generate

### README.md
Include: unit model explanation, comparison table (Traditional Team vs Cognitive Unit with 5+ rows), formation guide (how to create a new unit), and the cross-unit dependencies table above. 70-90 lines.

### 5 Unit Files

Each file follows this template structure:

```markdown
# [Unit Name]

## Purpose
Why this unit exists and what outcome it drives.

## Outcome Focus
The primary measure of this unit's success.

## Success Metrics
| Metric | Target | Cadence |
5-7 rows of KPIs specific to this unit.

## Composition

### Human Functions
Which cognitive functions this unit needs and how many.

### AI Agents
Which agents support this unit and their roles.

## Working Agreements
5-7 bullet points defining how the unit operates.

## Typical Workflows
3-4 common workflow patterns referencing workflows/.

## Cross-Unit Dependencies
What this unit needs from and provides to other units.

### Organization Extension Point
> Adjust composition, metrics, and agreements to your context.
```

### _template.md
A blank version of the unit file structure with [placeholder] markers for creating new units.

## Content Guidance per Unit

- **Experiment Velocity**: Optimizes for cycle time from hypothesis to validated learning. Needs strong Builder and Problem Framer functions. Primary agents: Code Co-Creator, Analysis Partner, Metrics Monitor.
- **Scale & Reliability**: Optimizes for uptime, latency, and incident recovery. Needs strong Quality Guardian and Solution Architect functions. Primary agents: Architecture Explorer, Quality Analyst, Metrics Monitor.
- **Developer Experience**: Optimizes for developer satisfaction and onboarding speed. Needs strong Resonance Sensor and Builder functions. Primary agents: Code Co-Creator, Quality Analyst, Documentation & Knowledge.
- **Intelligence Layer**: Optimizes for AI capability maturity and model effectiveness. Needs strong Pattern Integrator and Builder functions. Primary agents: Analysis Partner, Code Co-Creator, Architecture Explorer.
- **Frontier**: Optimizes for novel discoveries and prototype validation. Needs strong Fresh-Eyes Observer and Learner functions. Primary agents: Analysis Partner, Architecture Explorer.

## Formatting Rules

- 80-100 lines per unit file
- Success Metrics table must have 5-7 rows
- Working Agreements must have 5-7 items
- No YAML frontmatter
- Cross-reference workflows: `[Workflow](../workflows/file.md)`
- Cross-reference agents: `[Agent](../agents/file.md)`
