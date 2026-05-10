# Scorecard: software-engineer-core-structure

**Repo:** [`ilamgumaran/software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure)
**Layer:** Engineering org applied (Layer 3 of 4) -- HIO-Based Engineering Org Setup
**Date:** 2026-05-10 baseline (revised after hierarchy realignment)
**Reviewer:** Inorganic agent draft, awaiting SME signature
**Next review:** 2026-08-10

---

## Summary

| Axis | Level | Reason |
|---|---|---|
| Agentic Readiness | **L3** (lifted from earlier baseline; README repositioned and AGENTS.md inverted from HIO-agnostic to HIO-coupled in this realignment) | Strong concept ownership for engg-org setup; HIO coupling now explicit; trace links updated |
| Security | **L3** | Strong policies template; not yet operationalized in this repo's own workflow |

---

## Detailed scoring

| Dim | Level | Evidence |
|---|---|---|
| A1. Agent orientation | L4 | `AGENTS.md` follows the spec; conformant to public AGENTS.md baseline |
| A2. Cross-repo traceability | L4 | AGENTS.md trace links present; HIO methodology upstream and toolkit downstream both linked |
| A3. Concept ownership | L4 | 9 roles + transformation plan + goals/measures clearly owned and now explicitly framed as the HIO-applied engg-org template |
| A4. Prompts and skills | L3 | `prompts/` directory exists for regeneration; no skills system |
| A5. Tool/contract clarity | L3 | `tools/` per-tool guides; no schemas |
| B1. Security boundary docs | L4 | `CUSTOMIZATION.md` includes a comprehensive policies template (data, code, workflow, quality, escalation) |
| B2. Sensitive surface inventory | L3 | Template exists; not instantiated in this repo's own `org/` because the repo is a template |
| B3. Prompt injection awareness | L2 | Not addressed |
| B4. Secrets and credentials | L4 | Public, no secrets; `.gitignore` covers common paths |
| B5. Change reversibility | L3 | Implied via policies template; no enforcement |

---

## Strongest dimensions

- **A3 Concept ownership** at L4 -- 9 roles + transformation plan + goals/measures clearly owned, now framed as the HIO-applied engg-org template after the realignment.
- **B1 Security boundary docs** at L4 -- the policies template in `CUSTOMIZATION.md` is one of the most thorough in the family.
- **A2 Cross-repo traceability** at L4 -- updated trace links resolve cleanly upstream and downstream.

## Weakest dimensions

- **B3 Prompt injection** at L2 -- not addressed; relevant if forks pull org-content into prompts.
- **A4 Prompts and skills** at L3 -- could adopt a skills-system pattern from the toolkit.
- **A5 Tool/contract clarity** at L3 -- per-tool guides are prose; no schemas.

---

## Improvement plan

| Priority | Action | Lifts |
|---|---|---|
| 1 | Land repositioning (this change) -- README, AGENTS.md, central registry | A1 -> L4, A2 -> L4, A3 -> L4 |
| 2 | Add prompt injection guidance to the policies template | B3 -> L4 |
| 3 | Add a skills-system pattern (similar to operational hub) for forks to adopt | A4 -> L4 |
| 4 | Publish JSON schemas for role definitions and goals/measures | A5 -> L4 |
| 5 | Add an example instantiation (org/) showing the policies template filled out | B2 -> L4 |

---

## Sign-off

- [ ] SME framework owner: ___
- [ ] Security reviewer: ___
- [ ] Date signed: ___
