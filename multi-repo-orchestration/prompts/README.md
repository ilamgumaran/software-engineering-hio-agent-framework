# Prompts

Prompts for cross-repo work. These are LLM inputs -- the assumption is that a model interprets them and produces an artifact.

---

## Prompt index

| Prompt | Purpose |
|---|---|
| `repo-onboarding.md` | An agent picks up an unfamiliar repo in the family |
| `score-a-repo.md` | Re-score a repo against the rubric |
| `classify-task-hio.md` | Classify a task as OI / II / Interactive |
| `propose-new-repo.md` | Propose a new repo with rationale |

---

## How to use

1. Read the prompt and supply the bracketed inputs at the top
2. Pass it to a reasoning-capable agent that has read access to the repo family
3. Review the agent's output before merging

Never auto-apply the agent's output without OI review when the task lands in OI per `hio-collaboration/matrix.md`.

---

## Distinction from existing `prompts/` in the parent repo

The parent repo's `prompts/00-master.md` etc. regenerate the framework's structure. These prompts are different -- they perform multi-repo operations.
