# Scorecard: thought-org-with-human-ai-hybrid

**Repo:** [`ilamgumaran/thought-org-with-human-ai-hybrid`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid)
**Date:** 2026-05-10 baseline
**Reviewer:** Inorganic agent draft, awaiting SME signature
**Next review:** 2026-08-10

---

## Summary

| Axis | Level | Reason |
|---|---|---|
| Agentic Readiness | **L2** | Strong content, weak agent orientation; this is the methodology repo, not the operational repo, and that is fine |
| Security | **L2** | Public methodology, no sensitive code; B3 is the highest-leverage gap because content is consumed by other agents |

---

## Detailed scoring

| Dim | Level | Evidence |
|---|---|---|
| A1. Agent orientation | L2 | `CLAUDE.md` exists with project-purpose framing but no `AGENTS.md` until this change |
| A2. Cross-repo traceability | L2 | README does not link operational repos that descend from this work |
| A3. Concept ownership | L4 | Owns HIO definitions, the 4 HIO Tests, organic/inorganic intelligence vocabulary; ownership is unambiguous |
| A4. Prompts and skills | L1 | No prompts or skills assets |
| A5. Tool/contract clarity | N/A | Doc-only repo, no tools |
| B1. Security boundary docs | L2 | None; methodology repo has no agent operations to bound |
| B2. Sensitive surface inventory | L2 | None; public content |
| B3. Prompt injection awareness | L2 | Content is the canonical reference for HIO across other repos -- if untrusted edits land here, prompts elsewhere drift |
| B4. Secrets and credentials | N/A | None present |
| B5. Change reversibility | L2 | Standard branch protection only |

Where a dimension is N/A, the axis level is computed across the remaining dimensions only.

---

## Strongest dimensions

- **A3 Concept ownership** at L4 -- this is *the* repo for HIO vocabulary. The framework's strength is here.

## Weakest dimensions

- **A4 Prompts and skills** at L1 -- intentional so far (it is a thinking repo, not a tooling repo) but a small `skills/hio-classifier.md` here would amplify reach.
- **B3 Prompt injection** at L2 -- highest-leverage fix because changes here cascade.

---

## Improvement plan

| Priority | Action | Lifts |
|---|---|---|
| 1 | Land `AGENTS.md` (this change) -- including links to operationalizing repos | A1 -> L3, A2 -> L4 |
| 2 | Add a `prompts/` or `skills/` directory with the HIO classifier prompt | A4 -> L3 |
| 3 | Add CONTRIBUTING.md guidance on prompt-injection-resistant content (avoid embedded "ignore previous instructions" style examples without fencing) | B3 -> L3 |
| 4 | Mark concept ownership explicitly in each top-level doc heading | A3 -> L5 |
| 5 | Add CODEOWNERS for `framework.md` and `proposals/` to enforce review | B5 -> L4 |

---

## Sign-off

- [ ] SME framework owner: ___
- [ ] Security reviewer: ___
- [ ] Date signed: ___
