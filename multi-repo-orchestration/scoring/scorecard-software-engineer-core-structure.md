# Scorecard: software-engineer-core-structure

**Repo:** [`ilamgumaran/software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure)
**Date:** 2026-05-10 baseline
**Reviewer:** Inorganic agent draft, awaiting SME signature
**Next review:** 2026-08-10

---

## Summary

| Axis | Level | Reason |
|---|---|---|
| Agentic Readiness | **L3** | Strong concept ownership, mature plan structure, but no `AGENTS.md` and prompts are regen-only |
| Security | **L3** | Strong policies template; not yet operationalized in this repo's own workflow |

---

## Detailed scoring

| Dim | Level | Evidence |
|---|---|---|
| A1. Agent orientation | L2 | `CUSTOMIZATION.md` and README mention agents; no `AGENTS.md` until this change adds one |
| A2. Cross-repo traceability | L2 | README is silent on family relationships; this change adds them |
| A3. Concept ownership | L4 | 9 roles, domain extension system clearly owned and structured |
| A4. Prompts and skills | L3 | `prompts/` directory exists for regeneration; no skills system |
| A5. Tool/contract clarity | L3 | `tools/` per-tool guides; no schemas |
| B1. Security boundary docs | L4 | `CUSTOMIZATION.md` includes a comprehensive policies template (data, code, workflow, quality, escalation) |
| B2. Sensitive surface inventory | L3 | Template exists; not instantiated in this repo's own `org/` because the repo is a template |
| B3. Prompt injection awareness | L2 | Not addressed |
| B4. Secrets and credentials | L4 | Public, no secrets; `.gitignore` covers common paths |
| B5. Change reversibility | L3 | Implied via policies template; no enforcement |

---

## Strongest dimensions

- **A3 Concept ownership** at L4 -- the 9 roles are crisply defined and reused by the operational hub repo.
- **B1 Security boundary docs** at L4 -- the policies template in `CUSTOMIZATION.md` is one of the most thorough in the family.
- **B4 Secrets** at L4.

## Weakest dimensions

- **A1 Agent orientation** at L2 -- no `AGENTS.md`. This change addresses it.
- **A2 Cross-repo traceability** at L2 -- README does not mention sibling repos.
- **B3 Prompt injection** at L2 -- not addressed; relevant if forks pull org-content into prompts.

---

## Improvement plan

| Priority | Action | Lifts |
|---|---|---|
| 1 | Land `AGENTS.md` (this change) | A1 -> L4, A2 -> L4 |
| 2 | Add prompt injection guidance to the policies template | B3 -> L4 |
| 3 | Add a skills-system pattern (similar to operational hub) for forks to adopt | A4 -> L4 |
| 4 | Publish JSON schemas for role definitions | A5 -> L4 |
| 5 | Add an example instantiation (org/) showing the policies template filled out | B2 -> L4 |

---

## Sign-off

- [ ] SME framework owner: ___
- [ ] Security reviewer: ___
- [ ] Date signed: ___
