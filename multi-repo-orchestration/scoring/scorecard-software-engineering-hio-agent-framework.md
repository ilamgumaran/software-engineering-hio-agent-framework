# Scorecard: software-engineering-hio-agent-framework

**Repo:** [`ilamgumaran/software-engineering-hio-agent-framework`](https://github.com/ilamgumaran/software-engineering-hio-agent-framework)
**Date:** 2026-05-10 baseline
**Reviewer:** Inorganic agent draft, awaiting SME signature
**Next review:** 2026-08-10

---

## Summary

| Axis | Level | Reason |
|---|---|---|
| Agentic Readiness | **L4** | Strong concept clarity, structured prompts and agents, mature directory; missing CI validation for the new `AGENTS.md` spec |
| Security | **L3** | Repo-specific boundaries documented; sensitive surfaces inventoried partially; no tooling enforcement |

---

## Detailed scoring

| Dim | Level | Evidence |
|---|---|---|
| A1. Agent orientation | L4 | `CLAUDE.md` and now `AGENTS.md` (this change) follow the spec; not yet CI-validated |
| A2. Cross-repo traceability | L4 | README references upstream HIO and core-structure repos; this directory adds the registry |
| A3. Concept ownership | L5 | `cognitive-functions/`, `agents/`, `cognitive-units/` clearly own concepts; vocabulary table now exists in `repo-registry.md` |
| A4. Prompts and skills | L5 | `prompts/` (10 numbered) plus this directory's `skills/` and `prompts/`; canonical names enforced |
| A5. Tool/contract clarity | L3 | `tools/` directory has per-tool guides; no machine-readable contracts yet |
| B1. Security boundary docs | L4 | `org/policies.md` template exists; `governance/security-and-safety.md` adds cross-repo policy |
| B2. Sensitive surface inventory | L3 | `CLAUDE.md` and `org/policies.md` covered; this directory's spec adds another sensitive surface that is now inventoried |
| B3. Prompt injection awareness | L2 | Mentioned in `reference/agent-engineering-7-skills.md` (§5) but not implemented in repo handling |
| B4. Secrets and credentials | L4 | Public repo, no secrets; `.gitignore` covers common secret paths |
| B5. Change reversibility | L3 | Decision Spectrum is documented in `CLAUDE.md`; not enforced in tooling |

---

## Strongest dimensions

- **A3 Concept ownership** at L5 -- the repo is the canonical home for cognitive functions, agent types, units, metrics. Ownership is unambiguous.
- **A4 Prompts and skills** at L5 -- the existing 10-prompt regeneration system is mature; this addition extends rather than replaces it.
- **B4 Secrets** at L4 -- nothing sensitive in the repo by design.

## Weakest dimensions

- **B3 Prompt injection** at L2 -- the repo will be referenced as context by many agents; untrusted contributions to docs could affect downstream prompts. No fencing or labeling yet.
- **A5 Tool/contract clarity** at L3 -- per-tool guides are prose; no schemas.
- **B2 Sensitive surfaces** at L3 -- the new `multi-repo-orchestration/` is itself a sensitive surface (changes here propagate to other repos) and should be added to the policy file.

---

## Improvement plan

| Priority | Action | Lifts |
|---|---|---|
| 1 | Add `AGENTS.md` validation to CI -- check sections, links, spec version | A1 -> L5 |
| 2 | Add prompt injection fencing guidance to `governance/security-and-safety.md` and audit doc-ingest workflows | B3 -> L4 |
| 3 | Inventory `multi-repo-orchestration/` as a sensitive surface in `org/policies.md` | B2 -> L4 |
| 4 | Publish JSON schemas for the AGENTS.md spec | A5 -> L4 |
| 5 | Wire Decision Spectrum into branch protection rules (no AI direct push to main) | B5 -> L4 |

---

## Sign-off

- [ ] SME framework owner: ___
- [ ] Security reviewer: ___
- [ ] Date signed: ___
