# Cognitive Function: Builder

## Identity

The Builder is the frequency of engagement that turns ideas into working systems. This function activates when there is something concrete to create, modify, or repair -- when the work demands hands-on construction rather than analysis or design. Operating as a Builder feels like flow-state craftsmanship: the satisfaction of making something that compiles, passes tests, and solves a real problem. It is the bridge between intent and artifact.

---

## Activation Triggers

- A feature request has been framed and scoped, and implementation can begin
- Technical debt has accumulated to the point where it blocks forward progress
- A prototype or spike is needed to validate a design hypothesis
- An incident requires a hands-on fix to restore service health
- A build pipeline, deployment script, or infrastructure component needs construction
- An existing system needs refactoring to accommodate new requirements
- A proof of concept is needed to evaluate a technology choice

---

## Core Behaviors

### Implementation Patterns
- **Test-driven development**: Write tests that express intent before writing production code, creating a safety net that enables confident refactoring
- **Clean code discipline**: Favor clarity over cleverness; name things precisely; keep functions small and focused on a single responsibility
- **Incremental delivery**: Break large changes into small, reviewable, deployable increments that each leave the system in a working state

### Prototyping

| Technique | When to Use | Output |
|-----------|-------------|--------|
| Spike solution | Uncertainty about feasibility of an approach | Time-boxed throwaway code with a written decision |
| Walking skeleton | New system or major feature with unclear integration points | End-to-end thin slice through all layers |
| Proof of concept | Technology evaluation or stakeholder demonstration | Minimal working demo with documented tradeoffs |
| Incremental prototype | Evolving requirements that need frequent feedback | Shippable increments that gradually become production code |

### Technical Craftsmanship
- **Performance awareness**: Profile before optimizing; measure the impact of changes; understand the cost model of the runtime environment
- **Code clarity over compression**: Write code that a teammate (or future-you) can understand in six months without archaeological effort
- **Dependency hygiene**: Evaluate every dependency for maintenance health, security posture, and alignment with the project's longevity needs

---

## Collaboration Patterns

| Paired With | Collaboration Pattern | Example |
|-------------|----------------------|---------|
| [Problem Framer](problem-framer.md) | Builder receives well-defined problem statements and provides feasibility feedback | Problem Framer identifies root cause of deployment failures; Builder implements the fix |
| [Pattern Integrator](pattern-integrator.md) | Pattern Integrator identifies reusable patterns; Builder extracts them into shared libraries | Pattern Integrator notices three services duplicate retry logic; Builder creates a shared middleware |
| [Resonance Sensor](resonance-sensor.md) | Resonance Sensor identifies developer experience pain points; Builder creates tooling improvements | Resonance Sensor flags slow local dev setup; Builder creates a containerized dev environment |
| [Quality Guardian](quality-guardian.md) | Quality Guardian defines testing strategy; Builder implements tests and production code together | Quality Guardian designs property-based test approach; Builder writes generators and properties |
| [Growth Catalyst](growth-catalyst.md) | Growth Catalyst identifies learning opportunities in build tasks; Builder pairs with less experienced team members | Growth Catalyst suggests a junior take on the refactoring; Builder pairs to teach patterns |
| [Solution Architect](solution-architect.md) | Solution Architect designs system boundaries; Builder implements components within those boundaries | Solution Architect defines API contracts; Builder implements the service behind them |
| [Stakeholder Harmonizer](stakeholder-harmonizer.md) | Stakeholder Harmonizer translates business urgency; Builder communicates realistic timelines | Stakeholder Harmonizer explains compliance deadline; Builder scopes a minimal viable implementation |
| [Fresh-Eyes Observer](fresh-eyes-observer.md) | Fresh-Eyes Observer questions existing implementation choices; Builder explains context or agrees to change | Fresh-Eyes Observer asks why the ORM was chosen; Builder realizes a simpler approach works now |
| [Learner](learner.md) | Builder demonstrates techniques through pairing; Learner documents patterns for the team | Builder shows TDD workflow during pairing; Learner writes a team guide on the approach |

---

## Growth Path

| Stage | Expression | AI Agent Support |
|-------|-----------|-----------------|
| Novice | Implements well-specified tasks with guidance; follows established patterns and templates | AI provides code scaffolding, explains patterns, reviews implementations line by line |
| Developing | Takes ownership of features end-to-end; makes sound implementation decisions within established architecture | AI suggests alternative approaches, identifies edge cases, provides targeted code review |
| Fluent | Delivers complex features independently; mentors others on implementation craft; refactors with confidence | AI acts as a pairing partner for tricky problems, handles boilerplate, runs exploratory tests |
| Mature | Shapes implementation culture across the team; introduces new techniques and tools; balances speed with sustainability | AI handles routine implementation while human focuses on novel problems and team capability |

---

## Anti-Patterns

- **Identity grip on code output**: Defining personal value by lines of code written, resisting shifts to Problem Framer or Solution Architect when the situation calls for thinking before building
- **Building before understanding**: Jumping to implementation before the problem is adequately framed, resulting in well-crafted solutions to the wrong problem
- **Gold-plating**: Adding unrequested features, premature optimization, or excessive abstraction layers that increase complexity without proportional value
- **Tool attachment**: Insisting on a particular language, framework, or tool because of personal comfort rather than project fitness
- **Solo heroics**: Taking on critical implementations alone to demonstrate capability, creating knowledge silos and single points of failure

---

## Example

A platform engineering team needs to migrate their internal developer portal from a monolithic deployment to a containerized architecture. The **Builder** function activates.

The Builder starts by creating a walking skeleton: a single service extracted from the monolith, containerized, and deployed through the existing CI pipeline. Rather than redesigning everything at once, they focus on making one thin slice work end-to-end. They write integration tests that verify the extracted service behaves identically to the monolith endpoint it replaces.

During implementation, the Builder discovers that the session management layer is tightly coupled to the monolith's in-memory state. Instead of building a complex distributed session solution, they flag this to the team's [Solution Architect](solution-architect.md) function and implement a simple session-proxy as a temporary bridge. Each commit is small, tested, and deployable. The migration proceeds incrementally, with the monolith shrinking as containerized services prove themselves in production.

The outcome: a working containerized service in production within one sprint, with a clear pattern for extracting the remaining services. The walking skeleton becomes the template that other team members follow.
