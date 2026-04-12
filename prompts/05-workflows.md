# Workflows Prompt: Generate workflows/ (7 files)

## Objective

Generate the README and 6 workflow definition files. Workflows define the ceremonies and collaboration patterns of the Harmonized Sprint, replacing traditional scrum ceremonies with human-AI collaborative rituals.

## The Harmonized Sprint Model

A Harmonized Sprint is a 2-week cycle with these ceremonies replacing scrum equivalents:

| Scrum Ceremony | HIO Equivalent | Key Difference |
|---------------|----------------|----------------|
| Sprint Planning | Sprint Kickoff | Outcome-focused, AI-assisted pattern analysis |
| Daily Standup | Daily Harmonization | Function-based check-in, AI synthesis |
| Backlog Refinement | Async Collaboration | Continuous AI-assisted refinement |
| -- (no equivalent) | Emergence Capture | Novel pattern detection and amplification |
| Sprint Review | Sprint Review | Outcome demonstration with metric overlay |
| Sprint Retrospective | Retrospective | Human fulfillment focus, AI trend analysis |

## The 6 Workflows

| Workflow | Timing | Duration |
|----------|--------|----------|
| Sprint Kickoff | Day 1 of sprint | 90 minutes |
| Daily Harmonization | Every working day | 15 minutes |
| Async Collaboration | Continuous | Ongoing |
| Emergence Capture | As patterns detected | 30 minutes |
| Sprint Review | Last day of sprint | 60 minutes |
| Retrospective | Last day of sprint | 60 minutes |

## Files to Generate

### README.md
Include: Harmonized Sprint model overview, the scrum comparison table above, sprint timeline visual (text-based), and guidance on adapting ceremony frequency. 60-80 lines.

### 6 Workflow Files

Each file follows this template structure:

```markdown
# [Workflow Name]

## Trigger
What initiates this workflow.

## Participants
| Role | Who |
3+ rows mapping cognitive functions and agents to participation.

## Steps
Numbered steps with bold actor labels:
1. **Analysis Partner**: Synthesize context from previous sprint data
2. **Problem Framer (human)**: Frame the outcome hypothesis
3. **Metrics Monitor**: Present relevant baseline metrics

## Inputs
Bullet list of required inputs.

## Outputs
Bullet list of produced artifacts.

## Anti-Patterns
5+ things that indicate this workflow is being misused.

### Organization Extension Point
> Adapt timing, participants, and steps to your team cadence.
```

## Content Guidance per Workflow

- **Sprint Kickoff**: 5 phases (Context Setting, Outcome Framing, Work Shaping, Commitment, Launch). Most complex workflow at 100+ lines. Analysis Partner opens with pattern synthesis, humans frame outcomes, Architecture Explorer maps dependencies.
- **Daily Harmonization**: Brief function-based check-in. Each person shares which function they are activating today. Metrics Monitor provides overnight data synthesis. 15 minutes max.
- **Async Collaboration**: Defines how humans and AI agents collaborate between ceremonies. Code Co-Creator pairs on implementation, Documentation & Knowledge maintains context, Quality Analyst runs continuous review.
- **Emergence Capture**: Triggered when novel patterns are detected. Analysis Partner flags emergence, team discusses amplification. Creates emergence tickets for tracking.
- **Sprint Review**: Outcome demonstration, not feature demo. Metrics Monitor presents metric deltas. Each unit shows outcomes against their focus area. Stakeholders provide resonance feedback.
- **Retrospective**: Human fulfillment focus alongside process improvement. Metrics Monitor shows SPACE/DX and Human Fulfillment trends. Growth Catalyst facilitates psychological safety discussion.

## Formatting Rules

- Every step must have a bold actor label: `**Agent or Function Name**`
- Steps must be numbered, not bulleted
- Participants table must identify both humans (by function) and AI agents
- Sprint Kickoff must be 100+ lines; others 70-100 lines
- No YAML frontmatter
- Cross-reference metrics: `[Category](../metrics/file.md)`
- Cross-reference agents: `[Agent](../agents/file.md)`
