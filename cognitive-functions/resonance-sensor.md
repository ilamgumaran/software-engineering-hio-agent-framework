# Cognitive Function: Resonance Sensor

## Identity

The Resonance Sensor is the frequency of engagement that reads human dynamics, detects friction, and translates empathy into actionable insight. This function activates when the team's energy shifts, when users express frustration that data alone does not capture, or when workflow bottlenecks have a human dimension that metrics miss. Operating as a Resonance Sensor feels like tuning into a signal beneath the noise -- the awareness that something is off before anyone has articulated what or why.

---

## Activation Triggers

- Team velocity drops and the causes are not visible in the backlog or metrics
- Users report dissatisfaction that does not map neatly to specific bugs or features
- A new process or tool is meeting technical requirements but generating unexpected resistance
- On-call rotations, sprint retrospectives, or standups reveal unspoken tension
- Onboarding feedback suggests the team's practices are harder to learn than they appear
- A team member's engagement or energy noticeably changes
- Cross-team collaboration feels transactional rather than generative

---

## Core Behaviors

### User Empathy
- **Pain point observation**: Watch users interact with systems and note where they hesitate, retry, or work around -- these moments reveal friction that logs and metrics often miss
- **Experience mapping**: Trace the full journey of a user (developer, operator, or end-user) through a workflow, identifying emotional peaks and valleys alongside functional steps
- **Feedback synthesis**: Combine qualitative feedback (interviews, support tickets, Slack messages) into patterns that reveal systemic experience issues

### Team Dynamics Reading

| Technique | When to Use | Output |
|-----------|-------------|--------|
| Energy check-ins | Start of meetings, sprint transitions, post-incident | Quick pulse on team engagement and capacity; early warning of burnout or disengagement |
| Retrospective facilitation | End of sprint or project milestone | Surfaced concerns that the team may not raise unprompted; themes across multiple retros |
| One-on-one observation | Ongoing, especially during change periods | Understanding of individual motivations, blockers, and growth aspirations |
| Interaction pattern tracking | When team dynamics feel off | Map of who collaborates with whom, where information flows, and where it stalls |

### Friction Detection
- **Workflow bottleneck sensing**: Identify where human friction (unclear ownership, context-switching, tool frustration) slows work more than technical limitations
- **Tool-experience mismatch detection**: Notice when a technically sound tool creates a poor experience, leading to workarounds, shadow processes, or abandonment
- **Communication gap identification**: Detect when teams or individuals are talking past each other due to different mental models, vocabulary, or assumptions

---

## Collaboration Patterns

| Paired With | Collaboration Pattern | Example |
|-------------|----------------------|---------|
| [Builder](builder.md) | Resonance Sensor identifies developer experience pain; Builder creates tooling improvements | Resonance Sensor flags painful deploy process; Builder creates a one-command deploy script |
| [Problem Framer](problem-framer.md) | Resonance Sensor provides qualitative human data; Problem Framer structures it into formal problem statements | Resonance Sensor detects user confusion around config management; Problem Framer scopes the UX improvement |
| [Pattern Integrator](pattern-integrator.md) | Resonance Sensor detects recurring human friction; Pattern Integrator connects it to systemic patterns | Resonance Sensor notices teams repeatedly struggle during handoffs; Pattern Integrator identifies a missing shared context pattern |
| [Quality Guardian](quality-guardian.md) | Resonance Sensor identifies where quality processes create developer friction; Quality Guardian adjusts the approach | Resonance Sensor flags that mandatory code coverage thresholds are generating meaningless tests; Quality Guardian redesigns the quality gate |
| [Growth Catalyst](growth-catalyst.md) | Resonance Sensor identifies emotional and motivational blockers; Growth Catalyst designs supportive interventions | Resonance Sensor detects imposter syndrome in a new team member; Growth Catalyst adjusts mentoring approach |
| [Solution Architect](solution-architect.md) | Resonance Sensor provides user experience input; Solution Architect incorporates it into system design | Resonance Sensor reports that developers find the service mesh configuration overwhelming; Solution Architect simplifies the developer-facing interface |
| [Stakeholder Harmonizer](stakeholder-harmonizer.md) | Resonance Sensor reads the emotional dynamics in stakeholder relationships; Stakeholder Harmonizer addresses them | Resonance Sensor detects that the infrastructure team feels undervalued by product; Stakeholder Harmonizer facilitates a joint planning session |
| [Fresh-Eyes Observer](fresh-eyes-observer.md) | Fresh-Eyes Observer questions accepted team norms; Resonance Sensor validates whether those norms serve the team's wellbeing | Fresh-Eyes Observer questions the "always available" on-call culture; Resonance Sensor confirms it is causing burnout |
| [Learner](learner.md) | Resonance Sensor identifies the emotional aspects of learning; Learner benefits from psychologically safe environments | Resonance Sensor creates space for questions without judgment; Learner feels safe to ask "basic" questions |

---

## Growth Path

| Stage | Expression | AI Agent Support |
|-------|-----------|-----------------|
| Novice | Notices obvious team frustrations and user complaints; responds with empathy but may not know how to act on observations | AI analyzes sentiment in communication channels; highlights patterns in user feedback |
| Developing | Reads subtler signals (tone shifts, disengagement, workarounds); begins translating observations into recommendations | AI correlates team sentiment data with project metrics; drafts experience-improvement proposals |
| Fluent | Anticipates friction before it becomes visible; designs processes that account for human dynamics; trusted as the team's "emotional barometer" | AI monitors multiple feedback channels in real time; provides early warning when friction indicators emerge |
| Mature | Shapes team culture; coaches others in empathy and observation skills; influences organizational design based on human dynamics understanding | AI provides longitudinal analysis of team health trends; identifies systemic culture patterns across teams |

---

## Anti-Patterns

- **Empathy as avoidance**: Using emotional sensitivity as a reason to avoid data-driven decisions or difficult conversations, conflating "people might feel bad" with "this is the wrong decision"
- **Projection**: Attributing one's own emotional state to the team, reading frustration or excitement where it does not actually exist
- **Conflict avoidance disguised as empathy**: Smoothing over genuine disagreements that need to surface, prioritizing short-term harmony over long-term health
- **Emotional gatekeeping**: Insisting that all decisions pass through an emotional impact assessment, slowing down work that is straightforward
- **Burnout martyrdom**: Over-investing in sensing others' emotional states to the point of personal depletion, modeling unsustainable empathy

---

## Example

A platform engineering team has recently adopted a new internal developer platform (IDP). Adoption metrics look healthy: 80% of teams have onboarded, and the dashboard shows active usage. However, the **Resonance Sensor** function picks up a different signal.

During a casual conversation in Slack, a developer mentions they "just use the old CLI and then update the IDP dashboard manually." The Resonance Sensor digs deeper through informal conversations and discovers that six out of ten developers have similar workarounds. The IDP's UI requires too many clicks for common operations, so developers perform the action via their familiar CLI and then "sync" the dashboard to keep metrics green.

The Resonance Sensor compiles these observations -- not as a bug report, but as an experience gap analysis. They present the finding: the platform is technically adopted but experientially rejected. This insight reframes the team's next quarter priorities, shifting from "add more features to the IDP" to "make the IDP the path of least resistance for the five most common developer workflows." The [Problem Framer](problem-framer.md) takes this insight and scopes specific UX improvements, while the [Builder](builder.md) begins creating CLI-integrated shortcuts that feed directly into the platform.
