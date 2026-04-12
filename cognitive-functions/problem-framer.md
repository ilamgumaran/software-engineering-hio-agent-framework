# Cognitive Function: Problem Framer

## Identity

The Problem Framer is the frequency of engagement that defines *what* to solve and *why* it matters before anyone jumps to *how*. This function activates when ambiguity is high, when symptoms are being confused with root causes, or when stakeholders disagree about what the real issue is. Operating as a Problem Framer feels like clearing fog -- the satisfaction comes not from building a solution but from achieving the clarity that makes the right solution obvious.

---

## Activation Triggers

- Requirements are ambiguous or contradictory, and the team is unsure where to start
- A recurring incident keeps returning despite repeated fixes
- Stakeholders describe the same situation with different language and different priorities
- A proposed solution feels disconnected from the actual user pain
- The team is debating solutions before agreeing on the problem
- A post-mortem reveals that the original problem statement was incomplete
- Scope creep is making a project feel unbounded

---

## Core Behaviors

### Stakeholder Interviewing
- **Active listening with restatement**: Reflect back what you hear in different words to confirm understanding and surface hidden assumptions
- **Divergent questioning**: Ask open-ended questions that explore the problem space before converging on a definition
- **Perspective rotation**: Interview multiple stakeholders to build a composite view; note where perspectives align and where they conflict

### Problem Decomposition

| Technique | When to Use | Output |
|-----------|-------------|--------|
| 5 Whys | A symptom is clear but root cause is unknown | Chain of causation leading to an actionable root cause |
| Fishbone (Ishikawa) diagram | Multiple potential causes across different categories | Visual map of causes organized by category (people, process, technology, environment) |
| Impact mapping | Goal is clear but the path to achieve it is not | Tree connecting goals to actors to impacts to deliverables |
| Constraint identification | Problem scope feels unbounded | Explicit list of what is and is not in scope, with reasoning |

### Root Cause Framing
- **Symptom vs. cause separation**: Explicitly distinguish observable symptoms from underlying causes; resist the urge to treat symptoms as the problem
- **Problem statement discipline**: Write problem statements that include who is affected, what the impact is, and what constraints exist -- without embedding a solution
- **Temporal analysis**: Map when the problem occurs, when it does not, and what changed between those states

---

## Collaboration Patterns

| Paired With | Collaboration Pattern | Example |
|-------------|----------------------|---------|
| [Builder](builder.md) | Problem Framer defines what to build; Builder validates feasibility and provides implementation feedback | Problem Framer scopes an API reliability issue; Builder confirms the fix is achievable in one sprint |
| [Pattern Integrator](pattern-integrator.md) | Problem Framer defines the current problem; Pattern Integrator connects it to similar problems solved elsewhere | Problem Framer identifies a caching issue; Pattern Integrator recalls an analogous solution from a different service |
| [Resonance Sensor](resonance-sensor.md) | Resonance Sensor surfaces emotional and experiential data; Problem Framer structures it into actionable problem statements | Resonance Sensor detects developer frustration with deploy times; Problem Framer quantifies the impact and defines the improvement target |
| [Quality Guardian](quality-guardian.md) | Problem Framer defines the quality problem; Quality Guardian designs the measurement and verification approach | Problem Framer identifies flaky tests as the root cause of slow releases; Quality Guardian designs a test stability framework |
| [Growth Catalyst](growth-catalyst.md) | Problem Framer identifies capability gaps as root causes; Growth Catalyst designs learning interventions | Problem Framer discovers incidents stem from insufficient observability knowledge; Growth Catalyst creates a training plan |
| [Solution Architect](solution-architect.md) | Problem Framer constrains the problem space; Solution Architect explores solution options within those constraints | Problem Framer defines latency SLOs; Solution Architect evaluates caching strategies that meet them |
| [Stakeholder Harmonizer](stakeholder-harmonizer.md) | Problem Framer surfaces conflicting problem definitions; Stakeholder Harmonizer aligns stakeholders on a shared framing | Problem Framer maps three different views of "the deployment problem"; Stakeholder Harmonizer facilitates agreement |
| [Fresh-Eyes Observer](fresh-eyes-observer.md) | Fresh-Eyes Observer challenges the initial framing; Problem Framer incorporates the new perspective | Fresh-Eyes Observer asks why the team assumes the database is the bottleneck; Problem Framer re-examines the evidence |
| [Learner](learner.md) | Problem Framer models structured thinking; Learner practices decomposition techniques on real problems | Problem Framer walks through a 5 Whys analysis; Learner applies the technique to a different incident |

---

## Growth Path

| Stage | Expression | AI Agent Support |
|-------|-----------|-----------------|
| Novice | Applies basic decomposition techniques (5 Whys) to well-bounded problems; writes simple problem statements | AI asks guided questions to help decompose problems; suggests relevant techniques |
| Developing | Conducts stakeholder interviews; distinguishes symptoms from causes; produces problem statements that the team finds useful | AI synthesizes interview notes, identifies contradictions, and drafts initial problem statements for review |
| Fluent | Frames complex, cross-team problems; anticipates downstream effects of problem definitions; knows when framing is sufficient to proceed | AI provides pattern-matched examples from past problem framings; challenges assumptions in the current framing |
| Mature | Shapes how the organization thinks about problems; teaches framing techniques; recognizes when re-framing is needed mid-solution | AI monitors ongoing work for signs of misframed problems and flags them proactively |

---

## Anti-Patterns

- **Endless reframing**: Continuously refining the problem statement without ever declaring it sufficient to act on, using "we need more clarity" as a shield against commitment
- **Analysis paralysis**: Gathering data and conducting interviews long past the point of diminishing returns, delaying action in pursuit of perfect understanding
- **Solution-shaped framing**: Unconsciously defining the problem in a way that makes a preferred solution the obvious answer, rather than letting the problem definition remain solution-agnostic
- **Scope inflation**: Expanding the problem definition to include every adjacent concern, making the problem feel unsolvable and the team feel overwhelmed
- **Framing as gatekeeping**: Using the Problem Framer function to block others from building until every ambiguity is resolved, rather than accepting productive uncertainty

---

## Example

A platform engineering team receives escalating complaints about their internal CI/CD pipeline. Developers report that "builds are too slow," the infrastructure team says "the cluster is fine," and management wants "the pipeline fixed by end of quarter."

The **Problem Framer** function activates. Rather than immediately investigating build times, the Problem Framer interviews five developers, two SREs, and the engineering director. Through these conversations, a more nuanced picture emerges: build times are only part of the issue. Developers are frustrated because failed builds provide unhelpful error messages, forcing them to re-run the entire pipeline to identify which stage failed.

The Problem Framer writes a structured problem statement: "Developers spend an average of 25 minutes per failed build diagnosing the failure point, because pipeline stage failures do not produce actionable error output. This affects 40+ developers and accounts for approximately 15% of lost development time weekly." This reframing shifts the team's focus from raw build speed to failure diagnostics -- a smaller, more targeted problem with a clearer path to measurable improvement.
