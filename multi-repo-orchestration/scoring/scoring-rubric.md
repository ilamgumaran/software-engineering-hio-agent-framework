# Scoring Rubric

Ten dimensions across two axes. Each dimension is rated L1 (unaware) through L5 (leading). The rubric mirrors the L1-L5 levels in `reference/agent-engineering-7-skills.md`.

---

## Axis A: Agentic Readiness

How well a repo supports an agent walking in cold and doing useful work.

### A1. Agent orientation

Does the repo have an `AGENTS.md` (or equivalent) that orients an agent in under 30 seconds?

| Level | Definition |
|---|---|
| L1 | No agent guidance file |
| L2 | A README mentions agents informally |
| L3 | `AGENTS.md` exists but does not follow the spec |
| L4 | `AGENTS.md` follows the spec, kept current |
| L5 | `AGENTS.md` follows the spec, validated in CI, drives agent behavior |

### A2. Cross-repo traceability

Can an agent navigate from this repo to its siblings?

| Level | Definition |
|---|---|
| L1 | No mention of related repos |
| L2 | README references siblings in prose only |
| L3 | Trace links table exists but is incomplete |
| L4 | Complete trace links table; resolves correctly |
| L5 | Bidirectional trace links checked automatically |

### A3. Concept ownership clarity

Does the repo make clear which concepts it authoritatively owns vs reuses?

| Level | Definition |
|---|---|
| L1 | Concepts undefined or scattered |
| L2 | Concepts defined but no ownership signal |
| L3 | Owned concepts listed; reused concepts unmarked |
| L4 | Owned and reused concepts both labeled, with sources |
| L5 | Vocabulary translation table maintained for cross-repo use |

### A4. Prompt and skill assets

Does the repo provide structured prompts and skills agents can use?

| Level | Definition |
|---|---|
| L1 | No structured prompts or skills |
| L2 | Ad hoc examples scattered in docs |
| L3 | A `prompts/` or `skills/` directory exists |
| L4 | Prompts and skills are documented, parameterized, tested |
| L5 | Prompts and skills are versioned, evaluated, and reused across repos |

### A5. Tool and contract clarity

For repos that expose tools or APIs to agents: are contracts strict and example-rich?

| Level | Definition |
|---|---|
| L1 | No tools or vague tool descriptions |
| L2 | Tool list with one-line descriptions |
| L3 | Tools with schemas but inconsistent examples |
| L4 | Strict typed schemas with comprehensive examples |
| L5 | Contract framework other repos adopt |

For doc-only repos, score this dimension N/A and average across remaining dimensions.

---

## Axis B: Security

How safely an agent can operate in this repo.

### B1. Security boundary documentation

Does the repo state what an agent must not do?

| Level | Definition |
|---|---|
| L1 | No security guidance |
| L2 | Generic security advice in README |
| L3 | Repo-specific security boundaries listed |
| L4 | Boundaries reference org-wide policy and stay current |
| L5 | Boundaries enforced by tooling (hooks, CI, branch protection) |

### B2. Sensitive surface inventory

Are sensitive files, directories, or surfaces explicitly inventoried?

| Level | Definition |
|---|---|
| L1 | No inventory |
| L2 | Some sensitive areas mentioned in passing |
| L3 | Inventory exists but incomplete |
| L4 | Complete inventory with rationale per item |
| L5 | Inventory drives access control automatically |

### B3. Prompt injection awareness

For repos consumed as context by agents: is content guarded against indirect prompt injection?

| Level | Definition |
|---|---|
| L1 | No awareness; user-contributed content rendered raw into prompts |
| L2 | Awareness in docs, no implementation |
| L3 | Some content sanitization or labeling |
| L4 | Untrusted content clearly fenced and labeled in agent context |
| L5 | Defenses tested with red-team examples |

### B4. Secret and credential handling

Are secrets handled cleanly across the repo?

| Level | Definition |
|---|---|
| L1 | Secrets in plaintext or in commits |
| L2 | Secrets externalized but no scanning |
| L3 | Secret scanning enabled |
| L4 | Secret scanning + pre-commit hooks + rotation policy |
| L5 | Zero-secret architecture (workload identity, OIDC) |

For doc-only repos with no secrets, score N/A.

### B5. Change reversibility and review

Are irreversible changes guarded? Are AI changes always reviewed?

| Level | Definition |
|---|---|
| L1 | No protections; AI can push to main |
| L2 | Branch protection only |
| L3 | Branch protection + required reviewers |
| L4 | Reversibility-aware policy: AI may decide reversible, recommend semi-reversible, analyze irreversible |
| L5 | Reversibility policy enforced in tooling and audited |

---

## Aggregating to a level

Do not average to a single number across both axes. Compute two summary levels:

- **Agentic Readiness Level** = floor of mean across A1-A5 (rounded down)
- **Security Level** = floor of mean across B1-B5 (rounded down)

Report both. A repo at A4 / B2 is not the same risk profile as A2 / B4. Treat low B levels as blocking issues.

---

## When to re-score

| Trigger | Action |
|---|---|
| Quarterly cadence | Full re-score, all dimensions |
| Major repo restructuring | Targeted re-score, affected dimensions only |
| Spec version bump | A1, A2 only |
| Security incident | B1-B5 immediate re-score with SME |
| New repo joining family | Initial score within first sprint |

---

## How an agent uses this

1. Read this rubric
2. For each dimension, find evidence in the target repo
3. Cite the evidence (file path, link) -- do not assert without citation
4. Map evidence to a level
5. Produce the scorecard using the template in `scorecard-<repo>.md`
6. Submit for SME review

See `prompts/score-a-repo.md` for the canonical scoring prompt.
