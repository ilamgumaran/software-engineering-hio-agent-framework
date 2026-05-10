# Cross-Repo Traceability Protocol

How an agent (or human) follows links between repos in the family safely and efficiently. Defines the lifecycle from "new task arrives" to "change merged".

---

## Lifecycle stages

| Stage | Stage owner | Output |
|---|---|---|
| 1. Orient | Agent | Repo identity confirmed, sibling links read |
| 2. Classify | Agent | Task signal mapped to OI / II / Interactive |
| 3. Translate | Agent | Vocabulary normalized across repos |
| 4. Plan | Agent or human (per classification) | Concrete plan with cross-repo touchpoints listed |
| 5. Execute | Agent (II), human (OI), or both (Interactive) | Changes |
| 6. Verify | Agent + human | Changes pass the validation checklist |
| 7. Record | Agent | Trace links added or updated in `AGENTS.md` if scope changed |

---

## Stage 1: Orient

1. Read `AGENTS.md` at the repo root
2. Follow the link to `multi-repo-orchestration/repo-registry.md`
3. Identify upstream and downstream sibling repos for the current repo
4. If the task touches a concept owned by another repo, fetch that repo's `AGENTS.md`

**Stop conditions:**
- `AGENTS.md` missing -> create it from the spec before doing anything else, route the original task to Interactive
- `AGENTS.md` spec version older than current -> warn human, proceed but flag in PR

---

## Stage 2: Classify

Use `hio-collaboration/matrix.md` and the per-repo routing table in `AGENTS.md`. The most restrictive classification wins (Interactive beats II, OI beats Interactive).

| Task signal | Default | Override sources |
|---|---|---|
| Refactor within a single file | II | per-repo override |
| New public API or contract | Interactive | per-repo override -> OI |
| Security-sensitive change | OI | never overridden to II |
| Doc fix, typo, link update | II | per-repo override |
| Cross-repo concept change | OI | requires SME |
| Anything ambiguous | Interactive | n/a |

---

## Stage 3: Translate

If the task spans repos, normalize vocabulary using the table in `repo-registry.md`. Examples:

| Repo says | Normalized concept | Use elsewhere as |
|---|---|---|
| "organic intelligence" | human cognition | "engineer" / "team member" |
| "cognitive unit" | outcome team | "team" / "squad" |
| "emergence" | outcome neither could produce alone | "high-leverage collaboration" |
| "interference" | distortion of perception | "noise" / "distraction" |

Put translations in the PR description so reviewers do not have to re-derive them.

---

## Stage 4: Plan

Produce a plan that lists, in order:

1. Files in this repo to change
2. Sibling repos that need a coordinated change (if any)
3. Trace links that must be updated in `AGENTS.md` files
4. Spec version bumps required (if any)
5. SME review surface (which humans must approve before merge)

If step 2 is non-empty, the task is automatically Interactive.

---

## Stage 5: Execute

For **II tasks**, the agent acts directly and opens a PR.

For **OI tasks**, the agent prepares a draft (analysis, options, risk register) and explicitly does not commit; a human commits.

For **Interactive tasks**, the agent opens a draft PR with a checklist of items requiring human input. The agent does not mark the PR ready-for-review until each checklist item is addressed.

---

## Stage 6: Verify

Mandatory checks regardless of classification:

- [ ] All `AGENTS.md` trace links still resolve
- [ ] No vocabulary drift (translations applied consistently)
- [ ] Security boundaries respected (see `governance/security-and-safety.md`)
- [ ] If a sibling repo was touched, both PRs reference each other

---

## Stage 7: Record

If scope, ownership, or rules changed, update:

1. The repo's `AGENTS.md` (Family, Trace links, or HIO routing tables as relevant)
2. The central `repo-registry.md` if a relationship was added or removed
3. The repo's scorecard if the change affects an agentic-readiness or security score (see `scoring/`)

---

## Failure modes and recovery

| Failure | Symptom | Recovery |
|---|---|---|
| Stale trace link | Link 404s | Fix link, log incident in PR description |
| Conflicting per-repo override | Two repos disagree on classification of the same task | Escalate to SME via `governance/sme-update-workflow.md` |
| Vocabulary collision | Same word means different things across repos | Add row to `repo-registry.md` translation table |
| Spec version drift | Repo's `AGENTS.md` references an older spec | Migrate to current spec; SME approves |
| New concept with no owner repo | Task introduces a concept no repo currently owns | Propose new repo via `new-repos-proposed.md` |

---

## Why this protocol exists

Without it, every agent re-derives cross-repo context every session, drifts on vocabulary, and silently breaks links. This protocol makes the work boring and mechanical -- which is exactly what enables it to scale to hundreds of repos.
