# Scorecard: thoughtexperiments

**Repo:** [`ilamgumaran/thoughtexperiments`](https://github.com/ilamgumaran/thoughtexperiments)
**Date:** 2026-05-10 baseline
**Reviewer:** Inorganic agent draft, awaiting SME signature
**Next review:** 2026-08-10

---

## Summary

| Axis | Level | Reason |
|---|---|---|
| Agentic Readiness | **L1** | No agent orientation; static HTML content with `TODO.md` roadmap |
| Security | **L2** | Public content; sensitive subject matter (children, trauma) raises stakes for B3 |

---

## Detailed scoring

| Dim | Level | Evidence |
|---|---|---|
| A1. Agent orientation | L1 | No `AGENTS.md`, `CLAUDE.md`, or equivalent until this change |
| A2. Cross-repo traceability | L1 | No mention of `thought-org-with-human-ai-hybrid` despite philosophical kinship |
| A3. Concept ownership | L3 | `TODO.md` lists owned concepts (Resonance, Contraction, Null) but no glossary file |
| A4. Prompts and skills | L1 | None |
| A5. Tool/contract clarity | N/A | Static HTML, no tools |
| B1. Security boundary docs | L2 | None |
| B2. Sensitive surface inventory | L3 | `TODO.md` flags trauma/neurodivergence as edge cases that need safety boundaries -- partial inventory |
| B3. Prompt injection awareness | L2 | Content is consumed by readers and potentially by agents recommending stories; no fencing of untrusted contributions |
| B4. Secrets and credentials | N/A | None |
| B5. Change reversibility | L2 | Standard branch protection only; published content addresses children |

---

## Strongest dimensions

- **B2 Sensitive surface inventory** at L3 -- `TODO.md` already names edge cases (trauma, neurodivergence, age ranges) that require care. This is rare and valuable.

## Weakest dimensions

- **A1 Agent orientation** at L1 -- nothing to orient an agent; this change adds it.
- **A2 Cross-repo traceability** at L1 -- philosophical sibling not linked.
- **B3 Prompt injection** at L2 -- content addresses children; an agent that pulls a story into a prompt should be especially defended.

---

## Improvement plan

| Priority | Action | Lifts |
|---|---|---|
| 1 | Land `AGENTS.md` (this change) -- including child-safety routing rules | A1 -> L3, A2 -> L3 |
| 2 | Build a glossary mapping Resonance / Contraction / Null to canonical definitions; cross-link `thought-org-with-human-ai-hybrid` | A3 -> L4 |
| 3 | Add CONTRIBUTING.md with explicit child-safety review requirement (any change touching stories requires SME OI sign-off) | B5 -> L4 |
| 4 | Move story content to a structured directory with metadata (age range, themes, safety flags) | B2 -> L4 |
| 5 | Add a `skills/story-recommender.md` skill that an agent uses when recommending content, with safety preconditions | A4 -> L3, B3 -> L3 |

---

## Sign-off

- [ ] SME framework owner: ___
- [ ] Content safety reviewer (organic intelligence required): ___
- [ ] Date signed: ___
