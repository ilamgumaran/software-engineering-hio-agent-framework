# Cognitive Function: Growth Catalyst

## Identity

The Growth Catalyst is the frequency of engagement that develops capability in others. This function activates when a team member is stuck, when a skill gap threatens delivery, or when an opportunity exists to turn a routine task into a learning experience. Operating as a Growth Catalyst feels like investing in the future -- the patience to let someone struggle productively, the judgment to intervene before struggle becomes frustration, and the reward of watching someone achieve something they could not do yesterday.

---

## Activation Triggers

- A new team member joins and needs to build context and skills
- A post-mortem reveals a knowledge gap that contributed to an incident
- A team member expresses interest in growing into a new function
- The team's skill profile does not cover an upcoming technical need
- A routine task could become a learning opportunity with light facilitation
- Feedback from a team member indicates they feel stagnant or underutilized
- A technology shift requires the team to develop new capabilities

---

## Core Behaviors

### Skill Gap Identification
- **Team skill matrix**: Map current capabilities across the team to identify coverage gaps, single points of expertise, and growth opportunities for individuals
- **Predictive gap analysis**: Compare the team's current skills against upcoming roadmap needs to identify gaps before they become urgent
- **Strength recognition**: Identify and name strengths that individuals may not see in themselves, creating a foundation for growth that builds on existing capability

### Learning Path Design

| Technique | When to Use | Output |
|-----------|-------------|--------|
| Structured growth plan | Individual wants to develop a new function or deepen an existing one | Time-boxed plan with milestones, resources, and check-in schedule |
| Stretch assignment | Individual is ready for a challenge beyond current comfort zone | Carefully chosen task with safety nets and support structure |
| Pairing rotation | Team needs broader knowledge distribution | Scheduled pairing partnerships that rotate across skill areas |
| Teaching opportunity | Individual has mastered something worth sharing | Tech talk, workshop, or documentation project that solidifies their knowledge |

### Feedback Delivery
- **SBI model (Situation-Behavior-Impact)**: Describe the specific situation, the observed behavior, and the impact it had -- keeping feedback concrete and actionable rather than abstract
- **Growth-oriented framing**: Frame feedback in terms of future capability rather than past failure; focus on what to do differently rather than what went wrong
- **Feedback cadence**: Deliver feedback close to the event, in small doses, and regularly -- not saved up for formal review cycles

---

## Collaboration Patterns

| Paired With | Collaboration Pattern | Example |
|-------------|----------------------|---------|
| [Builder](builder.md) | Growth Catalyst identifies learning opportunities in build tasks; Builder pairs with less experienced team members | Growth Catalyst suggests a junior engineer take on the service extraction; Builder pairs with them through the implementation |
| [Problem Framer](problem-framer.md) | Growth Catalyst uses problem framing as a teaching vehicle; Problem Framer models structured thinking | Growth Catalyst arranges for a developing team member to lead a 5 Whys session with Problem Framer coaching |
| [Pattern Integrator](pattern-integrator.md) | Pattern Integrator shares mental models; Growth Catalyst designs exercises to practice pattern recognition | Pattern Integrator explains architectural patterns; Growth Catalyst creates a "pattern journal" exercise for the team |
| [Resonance Sensor](resonance-sensor.md) | Resonance Sensor detects emotional readiness for growth; Growth Catalyst adjusts the pace and approach | Resonance Sensor flags that a team member is overwhelmed; Growth Catalyst reduces the stretch assignment scope |
| [Quality Guardian](quality-guardian.md) | Quality Guardian identifies testing skill gaps; Growth Catalyst designs targeted training | Quality Guardian finds the team cannot write effective integration tests; Growth Catalyst organizes a hands-on workshop |
| [Solution Architect](solution-architect.md) | Growth Catalyst uses architecture decisions as learning opportunities; Solution Architect explains tradeoff reasoning | Growth Catalyst arranges for developing engineers to participate in architecture reviews with Solution Architect as guide |
| [Stakeholder Harmonizer](stakeholder-harmonizer.md) | Growth Catalyst develops communication skills in team members; Stakeholder Harmonizer provides real-world practice | Growth Catalyst coaches a team member on stakeholder communication; Stakeholder Harmonizer invites them to a planning meeting |
| [Fresh-Eyes Observer](fresh-eyes-observer.md) | Fresh-Eyes Observer's questions reveal learning opportunities; Growth Catalyst builds on them | Fresh-Eyes Observer asks a clarifying question about deployment; Growth Catalyst realizes the deployment process needs documentation |
| [Learner](learner.md) | Growth Catalyst provides structure and support; Learner brings curiosity and effort | Growth Catalyst designs a 30-60-90 day learning plan; Learner follows it and provides feedback on what is and is not working |

---

## Growth Path

| Stage | Expression | AI Agent Support |
|-------|-----------|-----------------|
| Novice | Shares knowledge informally; helps teammates solve specific problems through pairing | AI provides learning resources tailored to the mentee's level; suggests pairing topics |
| Developing | Creates structured learning plans for individuals; delivers feedback using SBI model; identifies skill gaps in the team | AI tracks individual progress against learning plans; generates skill gap reports; drafts feedback talking points |
| Fluent | Designs team-wide capability building programs; develops future Growth Catalysts; knows when to push and when to support | AI monitors team skill evolution over time; identifies optimal stretch assignments; facilitates knowledge-sharing logistics |
| Mature | Shapes the organization's learning culture; connects growth to business outcomes; builds systems that develop people at scale | AI provides organizational learning analytics; identifies cross-team mentoring opportunities; measures growth program effectiveness |

---

## Anti-Patterns

- **Dependency creation**: Providing so much help that the learner cannot function independently, creating a mentor-dependent relationship rather than building autonomy
- **Expertise-limited coaching**: Only coaching in areas of personal expertise rather than helping people find the right resources and mentors for their specific growth needs
- **Hard feedback avoidance**: Focusing only on encouragement and positive reinforcement, avoiding the difficult conversations that drive the most growth
- **Unsolicited teaching**: Turning every interaction into a lesson when the other person needs a quick answer or just wants to be heard
- **Growth at the wrong time**: Pushing learning opportunities during a crisis or deadline when the team needs execution, not development

---

## Example

A platform engineering team has a critical gap: only one engineer understands the Kubernetes operator that manages their custom resource definitions. This creates a single point of failure and blocks that engineer from taking vacation or working on other projects.

The **Growth Catalyst** function activates. Rather than simply assigning someone to "learn the operator," the Growth Catalyst designs a structured approach. They identify a mid-level engineer who has expressed interest in Kubernetes internals and create a four-week growth plan.

Week one: the learner shadows the expert during a routine operator update, asking questions and taking notes. Week two: the learner handles a minor operator change with the expert available for questions but not driving. Week three: the learner leads a small feature addition to the operator, with the expert reviewing the code. Week four: the learner writes internal documentation for the operator and presents a brief tech talk to the team.

The Growth Catalyst checks in at each transition, adjusting the pace based on the [Resonance Sensor](resonance-sensor.md)'s read of the learner's confidence and stress level. By the end of the month, the team has two people who can maintain the operator, the documentation exists for a third to ramp up, and the learner has expanded their function blend from pure [Builder](builder.md) to include [Pattern Integrator](pattern-integrator.md) thinking about Kubernetes operator patterns.
