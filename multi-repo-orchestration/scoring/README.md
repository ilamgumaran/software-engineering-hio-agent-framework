# Scoring

Comprehensive scoring of every repo in the family on two orthogonal dimensions: **agentic readiness** and **security**. Honest baseline first; improvement second.

---

## What's here

| File | Purpose |
|---|---|
| `scoring-rubric.md` | The rubric -- 10 dimensions, L1-L5 levels, definitions |
| `summary.md` | Comparative table across all repos in the family |
| `scorecard-thought-org-with-human-ai-hybrid.md` | Per-repo scorecard |
| `scorecard-software-engineer-core-structure.md` | Per-repo scorecard |
| `scorecard-software-engineering-hio-agent-framework.md` | Per-repo scorecard |
| `scorecard-thoughtexperiments.md` | Per-repo scorecard |

---

## How scoring works

1. An agent runs the `skills/agentic-scorer.md` skill against a repo
2. The skill produces a draft scorecard mapped to `scoring-rubric.md`
3. SMEs review and adjust the draft, especially security dimensions
4. The signed scorecard is committed and the `summary.md` table updated
5. Re-score quarterly or when a repo undergoes a major change

---

## Scoring philosophy

- **Honesty over flattery.** A repo with low scores is a roadmap, not a failure.
- **Two axes, never one.** Agentic and security move independently; do not collapse to a single number.
- **L1-L5 mirrors the upstream readiness scale** in `reference/agent-engineering-7-skills.md`. This is intentional.
- **Quarterly review beats one-shot scoring.** Repos drift; scoring tracks drift.
- **Security gaps are findings, not embarrassments.** Surface them, fix them, re-score.

---

## How to read a scorecard

Each scorecard has:

- A summary header with overall agentic and security levels
- A table mapping each rubric dimension to L1-L5 with a one-line evidence cite
- A short "strongest dimensions" and "weakest dimensions" callout
- A prioritized improvement list
- A signature block (who reviewed, when, next review date)

The `summary.md` aggregates only the headers across all repos for at-a-glance comparison.
