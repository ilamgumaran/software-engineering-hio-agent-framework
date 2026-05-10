# SME Update Workflow

How subject-matter experts maintain this framework as the family evolves. Without an explicit workflow, drift is inevitable.

---

## Roles

| Role | Responsibility |
|---|---|
| **Framework owner** | Single accountable owner of `multi-repo-orchestration/` and the spec version |
| **Repo SME** | Per-repo expert who owns that repo's `AGENTS.md` and per-repo files |
| **Security reviewer** | OI sign-off on B-axis scoring and security-related changes |
| **Content safety reviewer** | OI sign-off on `thoughtexperiments` content changes |

A single person may hold multiple roles. Every role must have an explicit holder before any change merges.

---

## Cadence

| Activity | Cadence | Owner |
|---|---|---|
| Re-score every repo | Quarterly | Framework owner runs `agentic-scorer`; SMEs review |
| Validate cross-repo links | Monthly (automated) | `cross-repo-link-validator` tool |
| Review per-repo dos/don'ts and routing overrides | Quarterly | Repo SMEs |
| Audit spec version drift | Per spec change | Framework owner |
| Review proposed new repos | As proposed | Framework owner + repo SMEs |

---

## Change types

### Type A: Lightweight (II-eligible)

- Typo fix
- Trace link update where the target moved
- Scorecard refresh after a re-score
- Add a vocabulary translation row

Agent drafts; one SME reviewer; merge.

### Type B: Spec or routing change (Interactive)

- Modify dos/don'ts text
- Add a new HIO routing row
- Add an override in `per-repo-routing.md`
- Update an `AGENTS.md` section beyond Trace links

Agent drafts; framework owner + affected repo SME review; merge.

### Type C: Identity-level change (OI)

- Bump spec version (v1 -> v2)
- Add or remove a repo in the family
- Modify the rubric in `scoring-rubric.md`
- Modify the matrix in `hio-collaboration/matrix.md`

Agent may draft analysis; humans (framework owner + 2 SMEs) commit. No agent commits for Type C.

---

## Workflow steps

1. **Open issue** in `software-engineering-hio-agent-framework` titled `Multi-repo: <change summary>`
2. **Tag change type** (A, B, or C)
3. **Apply HIO classifier** (II, Interactive, OI) and post the routing as a comment
4. **Author drafts** the change (agent for Type A and B drafts; humans for Type C)
5. **PR**, with linked PRs in any sibling repos affected
6. **Review** per the change type
7. **Merge** in coordinated order: spec changes first, sibling repos after
8. **Update summary** in `scoring/summary.md` and `repo-registry.md` if relevant

---

## SME onboarding

When a new SME takes ownership of a repo or role:

1. They read `multi-repo-orchestration/README.md` and `PLAN.md`
2. They run `repo-cartographer.md` against their repo to verify familiarity
3. They sign off on the most recent scorecard for their repo, or open issues for any score they disagree with
4. They commit to the cadence in this file

---

## SME offboarding

1. Outgoing SME identifies replacement
2. Replacement runs onboarding above
3. Outgoing SME transfers any open issues and pending change drafts
4. Update the role table in this file

---

## Disputes and escalation

- Disagreement between two SMEs -> framework owner decides
- Disagreement involving framework owner -> escalate to a third SME for tie-break
- Security-related dispute -> security reviewer's call is final on the security axis
- Content safety dispute (thoughtexperiments) -> content safety reviewer's call is final

---

## Anti-patterns

| Anti-pattern | Symptom | Fix |
|---|---|---|
| Single SME holds every role | Bus factor 1 | Distribute roles within first quarter |
| Reviews routinely under 24h with minor comments only | Likely rubber-stamping | Rotate reviewers; require explicit sign-off on dos/don'ts and security |
| Scorecards never re-run | Drift accumulates silently | Calendar the quarterly re-score; assign explicit owner |
| Per-repo overrides accumulate without review | Erosion of central matrix | Two-quarter review; remove unused overrides |
