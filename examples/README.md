# HIO Worked Examples

Four concrete project archetypes that show how the HIO Agent Framework is applied — using **only the agents, cognitive functions, units, workflows, and metrics already in this repo**. Each example specifies the team, the cognitive unit, which agent types are deployed, which of the 10 cognitive functions are activated, which of the 7 agent engineering capabilities are exercised, the sprint-by-sprint flow, the decision spectrum, the metrics watched, and the short-term tactical business gain.

These are not aspirational. They are designed so a team that has just stood up the framework can run any of them this quarter, with the tools they have today.

---

## The Four Archetypes

| Project | Risk profile | Reversibility | Time horizon | Tactical gain |
|---|---|---|---|---|
| [Legacy Migration](legacy-migration/) — Order-Hub monolith carve-out | High | Mostly irreversible | 6 weeks | Unblock EU regional launch |
| [New Platform](new-platform/) — PromptOps internal platform MVP | Medium | Mostly reversible | 8 weeks | End ungoverned agent sprawl |
| [Experimental](experimental/) — AI-augmented code review pilot | Low (if killed cleanly) | Fully reversible | 12 weeks (time-boxed) | Save 120 senior eng hrs/mo if it works |
| [Business-Critical](business-critical/) — PCI-DSS audit remediation strike | Very High | Irreversible (compliance) | 21 days | Protect $8M revenue exposure |

Pick the archetype that most resembles your real work, then adapt. Each example has its own `README.md` plus supporting files that are linked back to the framework's core docs (`agents/`, `cognitive-functions/`, `cognitive-units/`, `workflows/`, `metrics/`).

---

## What Every Example Covers

| Section | Why it's in every example |
|---|---|
| **Scenario** | A specific, realistic situation with stakes, deadline, and constraints |
| **Team composition** | Humans + AI agents, mapped to cognitive functions and the 7 capabilities |
| **Cognitive unit form** | Which of the 5 units this lives in (or whether a temporary unit is formed) |
| **Sprint flow** | Week-by-week work, with which ceremonies are emphasized |
| **Agent type deployment** | Which of the 6 AI agents are active, and on what tasks |
| **Decision spectrum in practice** | Specific examples of pure-human, hybrid, and pure-AI decisions |
| **Metrics watched** | Which of the 9 metric categories are primary; specific targets |
| **Risks** | Project-specific risks and the framework mechanism that mitigates each |
| **Emergence opportunities** | Where unexpected human-AI insights are likely to appear |
| **Tactical gain** | The short-term business value the project must deliver |
| **What you can reuse** | Templates and patterns to lift into your own project |

---

## How to Choose an Archetype

Use this decision tree:

1. **Is there a 14-30 day deadline with significant business consequences?** → [Business-Critical](business-critical/)
2. **Is the work mostly inside an existing system that is older than 5 years?** → [Legacy Migration](legacy-migration/)
3. **Is the work greenfield, building something the company has never had?** → [New Platform](new-platform/)
4. **Is the work a hypothesis to test, with kill criteria and an unknown outcome?** → [Experimental](experimental/)

Most real engineering work blends archetypes. A common combination: business-critical pressure on top of a legacy migration. When that happens, run the more constrained archetype's playbook (business-critical) and pull tools from the other (legacy migration).

---

## Reading Order

If you are evaluating the framework, read [Business-Critical](business-critical/) first — it shows the framework producing tactical value in 21 days using only what is already in place.

If you are setting up your first cognitive unit, read [New Platform](new-platform/) — it shows a unit forming from scratch.

If you are inheriting a difficult system, read [Legacy Migration](legacy-migration/).

If you have a research-flavored question, read [Experimental](experimental/).
