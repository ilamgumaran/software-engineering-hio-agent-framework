# Cognitive Functions Prompt: Generate cognitive-functions/ (11 files)

## Objective

Generate the README and all 10 cognitive function definition files. These are the atomic building blocks of the HIO framework -- composable capabilities that humans carry and AI agents combine.

## The Composition Model

Cognitive functions are not job titles. Each person carries 2-4 primary functions and can activate others situationally. AI agents compose 3 functions into a unified capability. Include this model in the README with both mapping tables.

## Function-to-Agent Mapping (Canonical)

| Function | Primary Agent | Secondary Agent(s) |
|----------|--------------|---------------------|
| Builder | Code Co-Creator | -- |
| Problem Framer | Analysis Partner | Architecture Explorer, Metrics Monitor |
| Pattern Integrator | Documentation & Knowledge | Analysis Partner, Code Co-Creator, Architecture Explorer, Metrics Monitor |
| Resonance Sensor | Analysis Partner | Quality Analyst |
| Quality Guardian | Quality Analyst | Code Co-Creator, Metrics Monitor |
| Growth Catalyst | Documentation & Knowledge | -- |
| Solution Architect | Architecture Explorer | -- |
| Stakeholder Harmonizer | -- (human-only) | -- |
| Fresh-Eyes Observer | Quality Analyst | -- |
| Learner | Documentation & Knowledge | -- |

## Function-to-Human-Strength Mapping

| Function | Typical Background |
|----------|--------------------|
| Builder | Senior/Staff engineers, prolific coders |
| Problem Framer | Product-minded engineers, tech leads |
| Pattern Integrator | Architects, senior ICs who read widely |
| Resonance Sensor | UX engineers, empathetic tech leads |
| Quality Guardian | QA backgrounds, security-minded engineers |
| Growth Catalyst | Mentors, tech leads, engineering managers |
| Solution Architect | System designers, principal engineers |
| Stakeholder Harmonizer | Engineering managers, TPMs |
| Fresh-Eyes Observer | Recent hires, rotational engineers |
| Learner | Junior engineers, career switchers, curious seniors |

## Files to Generate

### README.md
Include: composition model explanation, both mapping tables above, how functions combine in practice, guidance on function discovery for team members. 60-80 lines.

### 10 Function Files

Each file follows this template structure:

```markdown
# [Function Name]

## Identity
One paragraph defining the function's essence and why it matters.

## Activation Triggers
5-7 bullet points describing situations that activate this function.

## Core Behaviors

### [Behavior Category 1]
Table with 3+ rows showing specific behaviors.

### [Behavior Category 2]
Table with 3+ rows.

### [Behavior Category 3]
Table with 3+ rows.

## Collaboration Patterns
9-row table mapping interaction with every other function.

## Growth Path
4-stage table: Novice, Practitioner, Expert, Master with descriptions.

## Anti-Patterns
5+ bullet points of what this function looks like when misapplied.

## Example
A platform engineering scenario showing this function in action.

### Organization Extension Point
> Adapt triggers, behaviors, and examples to your domain.
```

## Content Guidance per Function

- **Builder**: Focus on code creation velocity, prototype building, system construction. Anti-patterns include coding without design and gold-plating.
- **Problem Framer**: Focus on problem decomposition, root cause analysis, constraint identification. Anti-patterns include solution-first thinking.
- **Pattern Integrator**: Focus on cross-domain synthesis, trend detection, knowledge connection. Anti-patterns include false pattern matching.
- **Resonance Sensor**: Focus on team dynamics, user empathy, communication clarity. Anti-patterns include conflict avoidance and over-accommodation.
- **Quality Guardian**: Focus on correctness, reliability, security, testing strategy. Anti-patterns include quality theater and blocking progress.
- **Growth Catalyst**: Focus on mentoring, skill development, psychological safety. Anti-patterns include rescuing and creating dependency.
- **Solution Architect**: Focus on system design, tradeoff analysis, technical vision. Anti-patterns include ivory tower architecture.
- **Stakeholder Harmonizer**: Focus on alignment, negotiation, priority balancing. Anti-patterns include people-pleasing and false consensus.
- **Fresh-Eyes Observer**: Focus on questioning assumptions, beginner's mind, spotting gaps. Anti-patterns include contrarianism for its own sake.
- **Learner**: Focus on knowledge absorption, skill expansion, curiosity. Anti-patterns include learning without applying and tutorial addiction.

## Formatting Rules

- 80-90 lines per function file
- All tables must have 3+ data rows
- Collaboration Patterns table must reference all 9 other functions
- Growth Path must have exactly 4 stages
- No YAML frontmatter
- Cross-reference agents using relative paths: `[Agent Name](../agents/file.md)`
