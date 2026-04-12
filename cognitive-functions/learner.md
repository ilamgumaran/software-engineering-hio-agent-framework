# Cognitive Function: Learner

## Identity

The Learner is the frequency of engagement that absorbs new knowledge and expands bandwidth. This function activates when the team encounters unfamiliar technology, when an individual transitions to a new domain, or when a post-incident review reveals knowledge gaps that need to be filled. Operating as a Learner feels like deliberate openness: the humility to acknowledge what you do not yet know, the discipline to learn systematically rather than haphazardly, and the generosity to share what you learn so others do not have to rediscover it.

---

## Activation Triggers

- A new technology, language, or framework is being adopted by the team
- An individual rotates into a new domain or takes on a new cognitive function
- A post-incident review identifies a knowledge gap that contributed to the incident
- A team member encounters a problem outside their current expertise
- Documentation is missing or outdated, and someone needs to learn the system and capture the knowledge
- A conference, course, or training event has introduced new ideas that need integration into practice
- The team is exploring a build-vs-buy decision and needs to understand an unfamiliar option

---

## Core Behaviors

### Active Learning
- **Deliberate practice**: Focus learning effort on specific skills at the edge of current capability, with tight feedback loops and intentional repetition
- **Spaced repetition**: Distribute learning across time rather than cramming, revisiting concepts at increasing intervals to build durable understanding
- **Learning by doing**: Prioritize hands-on experimentation over passive reading, building small projects or spike solutions to test understanding

### Documentation Creation

| Technique | When to Use | Output |
|-----------|-------------|--------|
| Learning journal | During any extended learning effort | Dated entries documenting what was learned, what was confusing, and what needs further exploration |
| "Teach it to write it" documentation | After achieving working understanding of a new system | Guide written from the perspective of someone learning the system, capturing the path rather than just the destination |
| Decision record | After evaluating a new technology or approach | Structured record of what was evaluated, criteria used, conclusions reached, and open questions |
| Cheat sheet or quick reference | After mastering a new tool or workflow | Concise reference for the most common operations, designed for use during actual work |

### Knowledge Sharing
- **Teaching as learning**: Explain concepts to others as a way to deepen understanding; the effort of making knowledge clear for someone else reveals gaps in one's own comprehension
- **Pairing for knowledge transfer**: Pair with more experienced practitioners to absorb tacit knowledge that does not appear in documentation
- **Pattern absorption**: Build mental models from new domains by identifying structural similarities with familiar domains, then testing where the analogy breaks down

---

## Collaboration Patterns

| Paired With | Collaboration Pattern | Example |
|-------------|----------------------|---------|
| [Builder](builder.md) | Builder demonstrates implementation techniques; Learner absorbs patterns and documents them | Builder shows how to write a Kubernetes operator; Learner follows along and creates a step-by-step guide |
| [Problem Framer](problem-framer.md) | Problem Framer models structured thinking; Learner practices decomposition on real problems | Problem Framer walks through a root cause analysis; Learner applies the technique to a different incident and shares results |
| [Pattern Integrator](pattern-integrator.md) | Pattern Integrator shares mental models; Learner stress-tests them against new experiences | Pattern Integrator explains the team's caching patterns; Learner applies them to a new service and reports where they did and did not fit |
| [Resonance Sensor](resonance-sensor.md) | Resonance Sensor creates psychological safety; Learner feels safe to ask questions and make mistakes | Resonance Sensor establishes norms that value questions; Learner asks about things others might consider "basic" |
| [Quality Guardian](quality-guardian.md) | Quality Guardian models quality thinking; Learner develops testing instincts through practice | Quality Guardian reviews a Learner's test suite and explains which failure modes are missing and why |
| [Growth Catalyst](growth-catalyst.md) | Growth Catalyst provides structure; Learner provides curiosity and effort | Growth Catalyst creates a 30-60-90 day plan; Learner follows it, adapts it, and provides feedback on effectiveness |
| [Solution Architect](solution-architect.md) | Solution Architect explains design decisions; Learner absorbs tradeoff reasoning | Solution Architect invites Learner to co-author a design document, explaining the tradeoff evaluation process |
| [Stakeholder Harmonizer](stakeholder-harmonizer.md) | Stakeholder Harmonizer models communication skills; Learner develops stakeholder awareness | Stakeholder Harmonizer brings a Learner to a planning meeting and debriefs on the dynamics afterward |
| [Fresh-Eyes Observer](fresh-eyes-observer.md) | Both share a questioning stance from different origins; together they surface more assumptions | Learner asks "what is this?" while Fresh-Eyes Observer asks "why is this?"; both contribute to clearer understanding |

---

## Growth Path

| Stage | Expression | AI Agent Support |
|-------|-----------|-----------------|
| Novice | Follows structured learning paths; asks many questions; documents what they learn for their own reference | AI provides curated learning resources; explains concepts at the right level; answers questions patiently and thoroughly |
| Developing | Designs their own learning paths; identifies knowledge gaps proactively; begins sharing knowledge with others | AI suggests learning resources based on identified gaps; reviews documentation for clarity; generates practice exercises |
| Fluent | Learns new domains quickly by transferring patterns; creates learning resources that benefit the whole team; teaches others to learn effectively | AI accelerates research by synthesizing information from multiple sources; reviews learning materials for completeness |
| Mature | Models learning as a lifelong practice; shapes the team's learning culture; knows when to learn deeply vs. learn enough to collaborate | AI supports organizational knowledge management; identifies cross-team learning opportunities; measures knowledge distribution |

---

## Anti-Patterns

- **Permanent learner mode**: Staying in learning mode to avoid the accountability that comes with competence, using "I'm still learning" as a shield against expectations
- **Learning as procrastination**: Using the need to learn more as a reason to delay action, when sufficient knowledge already exists to make progress
- **Knowledge hoarding**: Absorbing knowledge without sharing it, accumulating expertise that benefits only the individual rather than the team
- **Tutorial dependency**: Moving from tutorial to tutorial without applying knowledge to real problems, building familiarity without capability
- **Breadth without depth**: Learning a little about everything without going deep enough in anything to be genuinely useful, collecting surface knowledge

---

## Example

A platform engineering team decides to adopt OpenTelemetry for distributed tracing across their microservices. No one on the team has production experience with it. A mid-level engineer activates the **Learner** function and takes the lead on building the team's capability.

They start with deliberate practice: reading the OpenTelemetry documentation, then immediately building a minimal tracing setup in a test service. Rather than trying to learn everything at once, they focus on the most common use case first -- tracing a request across two services through an HTTP call. They keep a learning journal documenting what works, what is confusing, and what the documentation leaves unclear.

After a week, they have a working prototype and a solid understanding of the core concepts. They schedule a pairing session with a teammate from the [Builder](builder.md) function to instrument a real production service together. During the pairing, the Learner explains the concepts while the Builder handles the integration details, and both learn from the exchange.

The Learner then writes a "Getting Started with Tracing" guide using the "teach it to write it" approach, capturing not just the final configuration but the reasoning behind each choice and the mistakes they made along the way. This guide becomes the onboarding document for the rest of the team. Within a month, four services are instrumented, and the Learner has expanded their function blend to include [Pattern Integrator](pattern-integrator.md) as they begin to see how tracing patterns connect to the team's broader observability strategy.
