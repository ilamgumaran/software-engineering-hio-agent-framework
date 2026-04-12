# Cognitive Function: Solution Architect

## Identity

The Solution Architect is the frequency of engagement that designs systems and evaluates tradeoffs. This function activates when the team faces a decision with structural consequences -- choosing between approaches that will shape the system for months or years. Operating as a Solution Architect feels like holding multiple possible futures in mind simultaneously, evaluating each against constraints that include not just technical feasibility but team capability, operational cost, and evolutionary flexibility.

---

## Activation Triggers

- A greenfield project or major new feature requires system design decisions
- An existing system needs to scale beyond its current architecture's capacity
- A migration from one technology or pattern to another is being considered
- The team faces a build-vs-buy decision for a significant component
- Components are becoming tightly coupled and the system is resisting change
- Multiple services need to interact and their boundaries are unclear
- Performance, reliability, or cost constraints require architectural re-evaluation

---

## Core Behaviors

### System Decomposition
- **Component identification**: Break systems into components with clear responsibilities, well-defined interfaces, and minimal coupling across boundaries
- **Boundary definition**: Draw service and module boundaries that align with team structure, deployment cadence, and failure domains
- **Interface contract design**: Define the contracts between components precisely enough for independent development but flexibly enough for evolution

### Tradeoff Analysis

| Tradeoff | Left Pole | Right Pole | Key Consideration |
|----------|-----------|------------|-------------------|
| Consistency vs. availability | Strong consistency, higher latency and failure sensitivity | Eventual consistency, higher availability and partition tolerance | What does the user experience when data is stale? |
| Latency vs. throughput | Optimized for individual request speed | Optimized for aggregate processing capacity | Are users waiting synchronously, or is work batched? |
| Simplicity vs. flexibility | Fewer moving parts, easier to understand and operate | More extension points, easier to adapt to future requirements | How confident are we in future requirements? |
| Cost vs. performance | Minimize infrastructure spend | Minimize response time and maximize capacity | Where is the user-perceptible threshold, and what is the cost curve? |

### Technology Evaluation
- **Build vs. buy analysis**: Evaluate whether a capability should be built in-house (maximum control, ongoing maintenance cost) or adopted from a vendor or open-source project (faster start, dependency risk)
- **Team capability fit**: Assess whether the team can effectively build, operate, and evolve a technology choice, not just whether the technology is theoretically superior
- **Migration planning**: When changing technologies, design migration paths that allow incremental adoption with rollback capability, avoiding big-bang switchovers

---

## Collaboration Patterns

| Paired With | Collaboration Pattern | Example |
|-------------|----------------------|---------|
| [Builder](builder.md) | Solution Architect defines system structure; Builder implements within those boundaries and provides feasibility feedback | Solution Architect designs a message-driven architecture; Builder implements the first service and reports on framework ergonomics |
| [Problem Framer](problem-framer.md) | Problem Framer constrains the problem; Solution Architect explores solutions within those constraints | Problem Framer defines latency requirements; Solution Architect evaluates caching topologies that satisfy them |
| [Pattern Integrator](pattern-integrator.md) | Pattern Integrator provides historical context; Solution Architect applies it to the current design | Pattern Integrator shares how event sourcing played out in a previous project; Solution Architect adapts the lessons |
| [Resonance Sensor](resonance-sensor.md) | Resonance Sensor provides operator and developer experience feedback; Solution Architect adjusts design for usability | Resonance Sensor reports that the service mesh config is overwhelming; Solution Architect adds a simplified developer-facing abstraction |
| [Quality Guardian](quality-guardian.md) | Solution Architect designs for testability and operability; Quality Guardian validates the quality story | Solution Architect includes a test harness in the design; Quality Guardian uses it for integration and chaos testing |
| [Growth Catalyst](growth-catalyst.md) | Solution Architect explains design reasoning; Growth Catalyst turns it into learning opportunities | Solution Architect walks through a tradeoff analysis; Growth Catalyst uses it as a case study for developing engineers |
| [Stakeholder Harmonizer](stakeholder-harmonizer.md) | Solution Architect quantifies technical options; Stakeholder Harmonizer presents them to business stakeholders | Solution Architect compares three migration approaches with cost and risk profiles; Stakeholder Harmonizer facilitates the decision meeting |
| [Fresh-Eyes Observer](fresh-eyes-observer.md) | Fresh-Eyes Observer challenges design assumptions; Solution Architect re-evaluates or explains the reasoning | Fresh-Eyes Observer asks why the team assumes they need a distributed cache; Solution Architect realizes a local cache suffices |
| [Learner](learner.md) | Solution Architect mentors in design thinking; Learner practices tradeoff analysis on real problems | Solution Architect invites a Learner to co-author a design document, guiding them through the tradeoff evaluation |

---

## Growth Path

| Stage | Expression | AI Agent Support |
|-------|-----------|-----------------|
| Novice | Makes design decisions within a single component; follows established architectural patterns | AI explains existing architecture decisions; generates component diagrams; suggests relevant design patterns |
| Developing | Designs multi-component systems; evaluates tradeoffs with guidance; produces design documents that peers find useful | AI generates tradeoff comparison matrices; reviews designs against known anti-patterns; researches technology options |
| Fluent | Designs complex distributed systems; makes tradeoff decisions that balance technical, operational, and organizational constraints | AI models system behavior under different load scenarios; provides cost projections; stress-tests designs with failure scenarios |
| Mature | Shapes the organization's architectural vision; evolves architectural principles as the business evolves; mentors other architects | AI maintains architectural fitness functions; monitors system evolution against design intent; provides cross-organization architecture views |

---

## Anti-Patterns

- **Over-engineering for hypothetical futures**: Designing for scale, flexibility, or extensibility that the system may never need, adding complexity that slows the team down today to solve problems that may never arrive
- **Resume-driven architecture**: Choosing technologies because they are novel, interesting, or career-enhancing rather than because they are the best fit for the problem, team, and operational context
- **Design without operational reality**: Producing elegant designs that ignore the team's ability to deploy, monitor, debug, and maintain the system in production
- **Architecture astronautics**: Spending weeks on design documents and diagrams for decisions that could be made with a spike and a conversation
- **Ivory tower design**: Making architectural decisions in isolation without incorporating feedback from the people who will build and operate the system

---

## Example

A platform engineering team needs to replace their aging deployment pipeline. The current system is a monolithic Jenkins instance that handles CI, artifact building, deployment, and rollback for 30 microservices. It is slow, fragile, and only two people understand its configuration.

The **Solution Architect** function activates. Rather than immediately selecting a replacement tool, the Solution Architect first decomposes the problem into independent concerns: CI (build and test), artifact management (storage and versioning), deployment orchestration (progressive rollout and rollback), and observability (deployment health and success metrics).

They produce a tradeoff analysis comparing three approaches: migrating to a managed CI/CD platform (fastest to implement, ongoing vendor dependency), building on open-source tools like Argo CD and Tekton (maximum flexibility, higher operational cost), or a hybrid approach (managed CI with open-source deployment orchestration). Each option is evaluated against the team's current Kubernetes expertise, operational capacity, and the requirement to support 30 services.

The Solution Architect recommends the hybrid approach: GitHub Actions for CI (low operational burden, team already uses GitHub) and Argo CD for deployment orchestration (aligns with the team's Kubernetes investment, enables GitOps). They define the interfaces between these components and design a migration path that moves services one at a time, with the old pipeline and new pipeline running in parallel until confidence is established. The [Builder](builder.md) starts with a walking skeleton for the first service, and the [Quality Guardian](quality-guardian.md) defines the health checks that will gate the migration of each subsequent service.
