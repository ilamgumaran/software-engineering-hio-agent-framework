# Skills

Reusable agent skills for cross-repo work. Each skill is a self-contained markdown file an agent can invoke (or a human can read) to perform a recurring multi-repo operation.

---

## Skill index

| Skill | Purpose | Primary actor |
|---|---|---|
| `repo-cartographer.md` | Map a repo's structure, propose or validate its `AGENTS.md` | II with OI review |
| `cross-repo-tracer.md` | Follow trace links between repos, normalize vocabulary, plan coordinated changes | II with OI review |
| `hio-classifier.md` | Classify a task as OI / II / Interactive using the matrix | II |
| `agentic-scorer.md` | Run the scoring rubric against a repo and produce a draft scorecard | II with OI review |

---

## Skill format

Every skill file uses this shape:

1. **Identity** -- one paragraph; the skill's reason to exist
2. **Inputs** -- exact arguments and where they come from
3. **Steps** -- numbered procedure the agent follows
4. **Outputs** -- exact artifacts produced and where they go
5. **Stop conditions** -- when to halt and escalate
6. **Examples** -- one happy-path and one stop-condition example

Skills are imperative; they tell an agent (or human) exactly what to do.

---

## Distinction from prompts

- **Prompts** (`prompts/`) are LLM inputs. They expect a model to interpret them.
- **Skills** (this directory) are procedures. They expect an actor (agent or human) to execute them step by step.

A skill may invoke a prompt as one of its steps. A prompt typically does not invoke a skill.

---

## Adding a new skill

1. Identify a recurring cross-repo operation that does not have a skill yet
2. Write the skill file using the format above
3. Test the skill against at least one real instance
4. Add it to the index above
5. Reference it from the relevant `AGENTS.md` files where applicable
