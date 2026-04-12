# AI Agents

## How Agents Work

HIO replaces fixed AI tool categories with 6 composable **AI agents** that operate as specialized partners within cognitive units. Each agent composes 2-3 cognitive functions, giving it a distinct perspective on work. Agents are not siloed assistants -- they switch based on task type, and multiple agents collaborate on complex work. A single conversation may involve the Analysis Partner framing a problem, the Architecture Explorer proposing solutions, and the Code Co-Creator implementing the chosen approach.

The agent model mirrors how humans compose cognitive functions. Where a human engineer might hold Builder + Pattern Integrator, the Code Co-Creator agent holds Builder + Quality Guardian + Pattern Integrator. This shared language enables genuine human-AI collaboration rather than tool-use delegation.

---

## Agent Selection

The system routes tasks to agents based on intent analysis. When a task arrives, the framework matches signals in the request to the most appropriate primary agent. If the signal is ambiguous, the Analysis Partner activates first to frame the problem before routing to a specialized agent.

| Task Signal | Primary Agent |
|-------------|--------------|
| Error logs, failure spikes, anomalous metrics | Analysis Partner |
| Feature spec, implementation request, code change | Code Co-Creator |
| System design, migration plan, scaling question | Architecture Explorer |
| Test coverage, vulnerability scan, compliance check | Quality Analyst |
| Metric dashboard, trend report, health pulse | Metrics Monitor |
| Runbook, ADR, onboarding guide, knowledge gap | Documentation & Knowledge |
| Ambiguous requirement, conflicting data | Analysis Partner |
| Refactoring request, dependency update | Code Co-Creator |

---

## Agent Switching

Agents announce state transitions explicitly so both humans and other agents maintain shared context.

**Format:** "Acting as [Agent Name]: [brief rationale for activation]..."

**Rules:**
- Always announce when switching agents mid-task
- Explain why the switch is happening ("the problem is now well-framed, switching to implementation")
- Complete current work phase before switching -- do not leave partial analysis or half-written code
- A single agent remains active at any moment; collaboration happens sequentially, not in parallel
- Preserve context across switches -- the incoming agent receives a summary of what the outgoing agent produced
- Switching back to a previous agent is valid (e.g., Code Co-Creator discovers a new problem, switches back to Analysis Partner)

---

## Agent Combinations

| Task Type | Primary Agent | Supporting Agents |
|-----------|--------------|-------------------|
| New platform capability | Architecture Explorer then Code Co-Creator | Quality Analyst, Documentation & Knowledge |
| Production incident | Analysis Partner then Code Co-Creator | Quality Analyst, Metrics Monitor |
| Sprint planning | Analysis Partner | Metrics Monitor |
| Platform health review | Quality Analyst + Metrics Monitor | Analysis Partner |
| Developer onboarding | Documentation & Knowledge | Code Co-Creator |
| Architecture decision | Architecture Explorer | Analysis Partner, Documentation & Knowledge |
| Performance optimization | Analysis Partner then Code Co-Creator | Quality Analyst, Metrics Monitor |
| Compliance audit | Quality Analyst | Documentation & Knowledge, Analysis Partner |

---

## Agent + Human Collaboration

Each agent type interacts with human cognitive functions through defined collaboration surfaces. The most productive work happens in the **Emergence Zone** -- the space where human intuition and AI analysis combine to produce outcomes neither could achieve alone. A human Resonance Sensor noticing team fatigue combined with the Metrics Monitor detecting velocity decline creates an insight that pure data or pure intuition would miss.

Agents defer to human judgment on ambiguous tradeoffs, organizational politics, and ethical considerations. Humans defer to agents on exhaustive search, pattern detection across large datasets, and consistency verification.

| Agent | Primary Human Collaboration Surface | Emergence Zone Example |
|-------|-------------------------------------|----------------------|
| Analysis Partner | Problem Framer, Resonance Sensor | Human senses something is off + agent confirms with data = faster incident detection |
| Code Co-Creator | Builder, Quality Guardian | Human designs novel algorithm + agent generates comprehensive tests = higher confidence shipping |
| Architecture Explorer | Solution Architect, Fresh-Eyes Observer | Human challenges assumptions + agent generates alternative designs = better decisions |
| Quality Analyst | Quality Guardian, Resonance Sensor | Human notices developer friction + agent quantifies the pattern = targeted quality investment |
| Metrics Monitor | Pattern Integrator, Stakeholder Harmonizer | Human reads organizational dynamics + agent tracks leading indicators = proactive intervention |
| Documentation & Knowledge | Growth Catalyst, Learner | Human identifies skill gap + agent generates targeted learning material = accelerated onboarding |

---

## Agent Index

| Agent | File | Purpose | Cognitive Functions Composed |
|-------|------|---------|------------------------------|
| Analysis Partner | [analysis-partner.md](analysis-partner.md) | Pre-analyze problems, detect patterns, assess risk | Problem Framer + Pattern Integrator + Resonance Sensor |
| Code Co-Creator | [code-co-creator.md](code-co-creator.md) | Implement features, generate tests, refactor code | Builder + Quality Guardian + Pattern Integrator |
| Architecture Explorer | [architecture-explorer.md](architecture-explorer.md) | Generate and evaluate architecture options with tradeoffs | Solution Architect + Pattern Integrator + Problem Framer |
| Quality Analyst | [quality-analyst.md](quality-analyst.md) | Proactive quality monitoring, security scanning, coverage analysis | Quality Guardian + Resonance Sensor + Fresh-Eyes Observer |
| Metrics Monitor | [metrics-monitor.md](metrics-monitor.md) | Track metrics, surface trends, flag anomalies | Pattern Integrator + Quality Guardian + Problem Framer |
| Documentation & Knowledge | [documentation-knowledge.md](documentation-knowledge.md) | Living docs, decision capture, institutional knowledge | Pattern Integrator + Learner + Growth Catalyst |

---

## Adding a New Agent

1. **Identify the function gap.** Observe recurring task types where no existing agent provides adequate coverage. Document 3-5 concrete scenarios where the team needed an agent that did not exist.

2. **Compose cognitive functions.** Select 2-3 cognitive functions from the [function catalog](../cognitive-functions/README.md) that together address the identified gap. Verify that this composition does not duplicate an existing agent.

3. **Draft the agent file.** Follow the standard template: Identity, Perspective, Core Skills, Decision Framework, Inputs and Outputs, Collaboration Patterns, and Example. Ensure the file is 100-140 lines.

4. **Map collaboration patterns.** Define how the new agent interacts with each existing agent and with all 10 human cognitive functions. This forces clarity about boundaries and handoff points.

5. **Validate through usage.** Run the new agent through at least 3 real task scenarios. Verify that it activates correctly, produces useful outputs, and hands off cleanly to other agents. Update this README with the new agent's entry.

> **Organization Extension Point:** Your domain may require agents not listed here -- for example, a "Compliance Automator" in regulated industries or a "Data Pipeline Orchestrator" in analytics-heavy organizations. Use the process above to formalize them.
