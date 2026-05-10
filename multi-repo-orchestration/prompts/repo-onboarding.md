# Prompt: Repo Onboarding

Use this when an agent enters a repo in the HIO family for the first time and needs to orient before doing work.

---

## Inputs

- **Target repo:** `[owner/name]`
- **Task description:** `[what the user wants done]`
- **Family registry:** `https://github.com/ilamgumaran/software-engineering-hio-agent-framework/blob/main/multi-repo-orchestration/repo-registry.md`

---

## Prompt

```
You are an agent entering [owner/name] in the HIO repo family. Before doing
any work, orient yourself.

1. Read AGENTS.md at the root of [owner/name]. If it is missing, halt and
   report "AGENTS.md missing -- run repo-cartographer skill first".

2. Read multi-repo-orchestration/repo-registry.md in software-engineering-hio-agent-framework.
   Identify which layer this repo occupies (Strategic, Generic, Operational, Domain content).

3. From the AGENTS.md "Trace links" table, fetch the AGENTS.md of every linked
   sibling repo. Build a working set.

4. Apply hio-classifier to the task description. Cite the matrix row that
   determined the routing.

5. List the dos and don'ts that apply to this task from
   dos-and-donts/per-repo-<name>.md and dos-and-donts/universal.md.

6. Produce an orientation report with these sections:
   - Repo identity (one line)
   - Layer (one of the four)
   - Sibling repos in scope for this task
   - HIO classification (OI / II / Interactive) with rationale
   - Applicable dos and don'ts (bulleted, max 10)
   - Open questions for the human (or "none")

7. Stop. Wait for human acknowledgement before making any changes.

Task: [task description]
```

---

## When to use

- First time an agent works in a repo
- After a long gap when context may be stale
- Whenever the task touches more than one repo

## When not to use

- The agent has just performed orientation in this session for the same repo
- The task is a trivial typo fix in a non-canonical doc
