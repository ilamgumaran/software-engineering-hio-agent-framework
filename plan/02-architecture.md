# Architecture

## High-Level Architecture

```
Human Input (Cognitive Unit Members)
    |
    v
Task Router + Agent Selector
    |
    v
+------------------------------------------------------+
| Agent Executors                                       |
| +------------+ +------------+ +--------------------+ |
| | Analysis   | | Code Co-   | | Architecture       | |
| | Partner    | | Creator    | | Explorer           | |
| +------------+ +------------+ +--------------------+ |
| +------------+ +------------+ +--------------------+ |
| | Quality    | | Metrics    | | Documentation &    | |
| | Analyst    | | Monitor    | | Knowledge          | |
| +------------+ +------------+ +--------------------+ |
+------------------------------------------------------+
    |
    v
Integration Layer (Git, Jira, Confluence, CI/CD, Data)
    |
    v
External Systems
```

Each layer communicates through structured message passing. The **Task Router** interprets human intent, the **Agent Executors** perform cognitive work, and the **Integration Layer** connects to organizational tooling via MCP (Model Context Protocol) servers.

---

## Task Router Logic

The Task Router receives human input and determines which agent(s) to engage. Routing decisions are based on **intent signals** extracted from the input:

| Intent Signal | Primary Agent | Supporting Agent(s) |
|--------------|---------------|---------------------|
| "investigate", "why", "what caused" | Analysis Partner | Quality Analyst |
| "build", "implement", "create code" | Code Co-Creator | Architecture Explorer |
| "design", "architect", "how should we" | Architecture Explorer | Analysis Partner |
| "test", "quality", "review", "secure" | Quality Analyst | Code Co-Creator |
| "measure", "track", "how are we doing" | Metrics Monitor | Analysis Partner |
| "document", "capture", "share knowledge" | Documentation & Knowledge | Analysis Partner |
| "incident", "broken", "down" | Analysis Partner + Quality Analyst | Metrics Monitor |

When input matches multiple signals, the router selects a **primary agent** and one or more **supporting agents** that execute in coordination.

---

## Agent Selection

```
function selectAgents(input, context):
    signals = extractIntentSignals(input)
    unitContext = getCognitiveUnitContext(context.unit)

    primary = matchPrimaryAgent(signals)
    supporting = matchSupportingAgents(signals, primary)

    if context.isEmergenceZone:
        supporting.add(DocumentationKnowledge)  // always capture emergence

    if unitContext.recentFulfillmentDip:
        supporting.add(MetricsMonitor)  // monitor human state

    return AgentTeam(primary, supporting, unitContext)
```

The selection process considers not just the immediate task but the **cognitive unit's current state** -- including recent fulfillment scores, active sprint goals, and emergence zone status.

---

## Multi-Agent Coordination

When multiple agents work on the same task, they coordinate through a **shared context window**:

1. **Primary agent** receives the full task context and produces an initial response
2. **Supporting agents** receive the primary agent's output plus their specialized lens
3. **Reconciliation** merges outputs, flagging contradictions for human resolution
4. **Human checkpoint** -- the cognitive unit member reviews, adjusts, and approves

```
Primary Agent Output
    |
    +---> Supporting Agent A ---> Reconciliation ---> Human Checkpoint
    |                                  ^
    +---> Supporting Agent B ----------+
```

**Conflict resolution:** When agents disagree (e.g., Code Co-Creator optimizes for speed but Quality Analyst flags risk), both perspectives are presented to the human with the relevant cognitive function. The framework never auto-resolves agent conflicts.

---

## Cognitive Unit Integration

Each of the 5 cognitive units has a dedicated agent configuration:

| Cognitive Unit | Primary Agents | Configuration Focus |
|---------------|----------------|-------------------|
| **Experiment Velocity** | Code Co-Creator, Architecture Explorer | Fast iteration, low ceremony, emergence-friendly |
| **Scale & Reliability** | Quality Analyst, Metrics Monitor | Reliability gates, performance budgets, SLO tracking |
| **Developer Experience** | Analysis Partner, Documentation & Knowledge | Feedback synthesis, tooling optimization, onboarding |
| **Intelligence Layer** | Analysis Partner, Architecture Explorer | AI integration patterns, data pipeline design |
| **Frontier** | Architecture Explorer, Code Co-Creator | Exploration, prototyping, fresh-eyes emphasis |

Unit-specific configurations are stored in `config/` and referenced by `org/infrastructure.md`.

---

## Emergence Zone

The **emergence zone** is the architectural region where human-AI collaboration produces value that neither could produce alone. It exists at three handoff points:

1. **Problem reframing** -- AI surfaces data, human reframes the question in a way AI wouldn't
2. **Pattern connection** -- AI detects patterns, human connects them to organizational context AI lacks
3. **Quality judgment** -- AI flags concerns, human applies craft judgment about what matters

Emergence events are detected when outputs at these handoff points diverge significantly from the AI's initial trajectory. The **Documentation & Knowledge** agent automatically captures emergence events for organizational learning.

---

## Data Flow

```
Cognitive Unit Activity
    |
    +--> Code Changes -----> Git ---------> DORA Metrics ------+
    |                                                           |
    +--> Sprint Events ----> Jira --------> Platform Outcomes --+
    |                                                           |
    +--> Decisions ---------> Confluence --> Knowledge Base -----+--> Metrics
    |                                                           |   Monitor
    +--> Conversations -----> Slack -------> SPACE/DX Data -----+
    |                                                           |
    +--> Fulfillment Data --> Surveys -----> Human Fulfillment -+
    |                                                           |
    +--> Agent Interactions > Agent Logs --> AI Utilization -----+
    |
    +--> Emergence Events --> Emergence Log -> Harmonization Metrics
```

All data flows converge in the **Metrics Monitor**, which tracks the 9 metric categories defined in `metrics/`. Dashboards are generated per cognitive unit and rolled up to the organizational level.

---

## Security Boundaries

| Boundary | Policy |
|----------|--------|
| **Agent data access** | Agents access only repositories and systems their cognitive unit owns |
| **PII handling** | Fulfillment data is anonymized before agent processing |
| **Code execution** | Agents suggest code; humans approve execution in production paths |
| **External system access** | All MCP integrations require security review per `org/policies.md` |
| **Knowledge boundaries** | Agents do not share context across cognitive units without explicit routing |

See `org/policies.md` for organization-specific security configuration and `config/` for MCP server definitions.
