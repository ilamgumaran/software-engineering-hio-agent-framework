# Model Routing Policy

## Task-to-Model Mapping

| Task Type                  | Model        | Rationale                          |
|----------------------------|--------------|------------------------------------|
| Linting, formatting fixes  | Haiku 4.5    | Low complexity, high volume        |
| Unit test generation       | Sonnet 4.6   | Needs code understanding           |
| Feature implementation     | Sonnet 4.6   | Standard complexity                |
| Batch job design/refactor  | Opus 4.6     | High blast radius, needs reasoning |
| API contract changes       | Opus 4.6     | Cross-service impact               |
| Security review            | Opus 4.6     | Cannot afford false negatives      |
| Documentation generation   | Sonnet 4.6   | Good quality, lower cost           |
| Commit message generation  | Haiku 4.5    | Simple summarization               |
| Code review (automated)    | Sonnet 4.6   | Balanced cost/quality              |
| Architecture decisions     | Opus 4.6     | Needs deep reasoning               |
| Incident triage            | Opus 4.6     | High stakes, needs full context    |

## Cost Levers (Org Admin Only)

Adjusted centrally. Individual developers do not change these.

- **Default model ceiling:** Sonnet 4.6 for interactive sessions.
- **Escalation trigger:** Agent can request Opus if task involves
  3+ services, database schema changes, or security-sensitive code.
- **Token budget per session:** 200K input / 32K output (Sonnet),
  300K input / 64K output (Opus).
- **Parallel agent limit:** 3 concurrent subagents per developer.
- **Auto-compact threshold:** 80% of context window.

## How Agents Use This

Skills reference this policy by task type. Agents should state which tier
they are operating at when the task is ambiguous.
