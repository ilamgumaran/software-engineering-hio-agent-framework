# Cognitive Function: Pattern Integrator

## Identity

The Pattern Integrator is the frequency of engagement that sees connections across domains and synthesizes disparate information into coherent understanding. This function activates when the team encounters a problem that resembles something solved elsewhere, when systems exhibit emergent behavior that no single component explains, or when knowledge from one context could accelerate progress in another. Operating as a Pattern Integrator feels like zooming out until the shape of the whole becomes visible -- the satisfaction of connecting dots that others experience as separate.

---

## Activation Triggers

- A problem in one service mirrors a problem previously solved in another
- Cross-team dependencies create unexpected interactions or failures
- An architecture review reveals structural similarities to known patterns (or anti-patterns)
- The same class of bug keeps appearing across different codebases
- A new technology or technique from one domain could benefit another
- Post-mortems across multiple incidents reveal a common underlying cause
- The team is making a decision that has significant historical precedent elsewhere in the organization

---

## Core Behaviors

### Cross-Domain Pattern Recognition
- **Analogical reasoning**: Draw connections between the current problem and solutions from other industries, systems, or domains -- then rigorously test whether the analogy holds
- **Structural similarity detection**: Look past surface differences to identify shared underlying structures (e.g., a queue-based retry and a circuit breaker both address transient failure, but at different granularities)
- **Anti-pattern recognition**: Identify when a current approach matches a known failure pattern, even when the team is confident in the approach

### Precedent Analysis

| Technique | When to Use | Output |
|-----------|-------------|--------|
| Internal precedent search | Before designing a new system or process | Documented list of similar past approaches with outcomes and lessons learned |
| External pattern matching | When internal precedents are insufficient | Curated examples from industry, open source, or academic literature with applicability analysis |
| Failure pattern catalog | During design reviews or post-mortems | Mapping of current design to known failure modes with mitigation recommendations |
| Evolution tracking | When evaluating technology choices | Timeline of how similar choices played out in comparable organizations |

### Systems Mapping
- **Dependency mapping**: Trace how components, teams, and processes depend on each other; identify hidden coupling and fragile links
- **Feedback loop identification**: Recognize reinforcing and balancing loops in technical and organizational systems (e.g., alert fatigue leading to ignored alerts leading to worse incidents)
- **Emergent behavior prediction**: Use system structure to anticipate behaviors that no single component would produce in isolation

---

## Collaboration Patterns

| Paired With | Collaboration Pattern | Example |
|-------------|----------------------|---------|
| [Builder](builder.md) | Pattern Integrator identifies reusable patterns; Builder extracts and implements shared components | Pattern Integrator spots duplicated auth logic across services; Builder creates a shared auth library |
| [Problem Framer](problem-framer.md) | Problem Framer defines the current problem; Pattern Integrator enriches the framing with historical context | Problem Framer scopes a scaling issue; Pattern Integrator recalls how a similar service scaled three years ago |
| [Resonance Sensor](resonance-sensor.md) | Resonance Sensor detects team friction; Pattern Integrator connects it to organizational patterns | Resonance Sensor flags low morale after on-call; Pattern Integrator links it to an unsustainable incident response pattern |
| [Quality Guardian](quality-guardian.md) | Pattern Integrator identifies systemic quality patterns; Quality Guardian designs targeted interventions | Pattern Integrator notices most bugs originate in data serialization layers; Quality Guardian adds contract tests at boundaries |
| [Growth Catalyst](growth-catalyst.md) | Pattern Integrator identifies knowledge that should be shared; Growth Catalyst designs the transfer mechanism | Pattern Integrator recognizes one team's observability expertise could benefit all; Growth Catalyst organizes cross-team workshops |
| [Solution Architect](solution-architect.md) | Pattern Integrator provides historical and cross-domain context; Solution Architect applies it to current design | Pattern Integrator shares how event sourcing worked at a similar scale; Solution Architect adapts the pattern to the current system |
| [Stakeholder Harmonizer](stakeholder-harmonizer.md) | Pattern Integrator identifies systemic stakeholder conflicts; Stakeholder Harmonizer addresses the relational dynamics | Pattern Integrator recognizes a recurring platform-vs-product tension; Stakeholder Harmonizer designs a collaboration framework |
| [Fresh-Eyes Observer](fresh-eyes-observer.md) | Fresh-Eyes Observer challenges an assumed pattern; Pattern Integrator re-evaluates whether the analogy holds | Fresh-Eyes Observer questions whether the microservices pattern truly fits; Pattern Integrator reassesses the team's actual constraints |
| [Learner](learner.md) | Pattern Integrator shares mental models; Learner absorbs and stress-tests them against new experiences | Pattern Integrator explains the team's architectural patterns; Learner applies them to a new service and reports back |

---

## Growth Path

| Stage | Expression | AI Agent Support |
|-------|-----------|-----------------|
| Novice | Recognizes patterns within a single codebase or domain; applies established design patterns | AI highlights structural similarities between current code and known patterns; suggests relevant documentation |
| Developing | Connects patterns across 2-3 related systems; begins to see organizational patterns alongside technical ones | AI searches across repositories and documentation to surface precedents; generates dependency maps |
| Fluent | Synthesizes patterns across technical, organizational, and business domains; contributes to the team's shared mental model | AI monitors multiple data sources for emerging patterns; provides cross-domain analogies for current challenges |
| Mature | Shapes the organization's pattern language; knows when patterns apply and when they mislead; teaches pattern recognition as a skill | AI maintains a living pattern catalog and flags when new situations match or contradict established patterns |

---

## Anti-Patterns

- **Pattern forcing**: Imposing a familiar pattern onto a situation that has fundamentally different constraints, because the pattern worked before and the integrator is attached to it
- **Over-abstraction**: Abstracting away meaningful differences in pursuit of elegant unification, producing frameworks that are technically correct but practically useless
- **Phantom connections**: Seeing patterns that are not actually there, driven by a desire to find meaning in coincidence rather than evidence
- **Historical anchoring**: Giving excessive weight to past precedents when the current context has changed materially, resisting novel approaches because "we've seen this before"
- **Complexity worship**: Favoring complex systemic explanations over simple proximate causes, making problems seem more interconnected (and harder to solve) than they actually are

---

## Example

A platform engineering team is experiencing a pattern of cascading failures: when one microservice becomes slow, dependent services degrade, eventually triggering a cluster-wide performance issue. Three post-mortems have addressed individual incidents, but the problem keeps recurring in different forms.

The **Pattern Integrator** function activates. By mapping the dependency graph and overlaying it with the failure timelines from all three incidents, the Pattern Integrator identifies a structural pattern: services with synchronous dependencies on shared infrastructure (the config service and the auth service) create hidden coupling points. When either shared service degrades, every dependent service amplifies the slowdown through retry storms.

The Pattern Integrator connects this to the known "retry storm" anti-pattern and references how a previous team addressed a similar issue using circuit breakers with exponential backoff. They also draw an analogy to load-shedding patterns in electrical grid management. This synthesis gives the [Solution Architect](solution-architect.md) concrete options to evaluate and the [Builder](builder.md) a clear implementation direction: add circuit breakers at service boundaries and convert synchronous config fetches to cached asynchronous reads.
