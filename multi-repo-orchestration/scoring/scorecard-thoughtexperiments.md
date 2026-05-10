# Scorecard: thoughtexperiments

**Repo:** [`ilamgumaran/thoughtexperiments`](https://github.com/ilamgumaran/thoughtexperiments)
**Layer:** Cognition foundation (Layer 1 of 4) -- upstream of HIO
**Date:** 2026-05-10 baseline (revised after hierarchy realignment)
**Reviewer:** Inorganic agent draft, awaiting SME signature
**Next review:** 2026-08-10

---

## Summary

| Axis | Level | Reason |
|---|---|---|
| Agentic Readiness | **L2** (was L1; lifted by README and AGENTS.md added in this realignment) | Now has an orientation README + spec-conformant AGENTS.md; vocabulary clearly owned and distinguished from HIO; trace links present |
| Security | **L2** | Public content; sensitive subject matter (children, trauma) raises stakes for B3 |

---

## Detailed scoring

| Dim | Level | Evidence |
|---|---|---|
| A1. Agent orientation | L4 | `AGENTS.md` follows the spec; conformant to public AGENTS.md baseline |
| A2. Cross-repo traceability | L3 | AGENTS.md Trace links present; bidirectional check pending CI |
| A3. Concept ownership | L4 | Resonant Cognition vocabulary clearly owned; explicitly distinguished from HIO terms; README and AGENTS.md both state independence |
| A4. Prompts and skills | L1 | None |
| A5. Tool/contract clarity | N/A | Static HTML, no tools |
| B1. Security boundary docs | L2 | None beyond AGENTS.md routing |
| B2. Sensitive surface inventory | L3 | `TODO.md` flags trauma/neurodivergence as edge cases that need safety boundaries -- partial inventory |
| B3. Prompt injection awareness | L2 | Content is consumed by readers and potentially by agents recommending stories; no fencing of untrusted contributions yet |
| B4. Secrets and credentials | N/A | None |
| B5. Change reversibility | L2 | Standard branch protection only; published content addresses children |

---

## Strongest dimensions

- **A3 Concept ownership** at L4 -- this repo is the canonical home of Resonant Cognition vocabulary; ownership is clear; relationship to HIO (kindred, independent, upstream) is explicit.
- **B2 Sensitive surface inventory** at L3 -- `TODO.md` already names edge cases (trauma, neurodivergence, age ranges) that require care.

## Weakest dimensions

- **A4 Prompts and skills** at L1 -- no prompts or skills assets yet. A small `skills/story-recommender.md` with safety preconditions would lift this.
- **B3 Prompt injection** at L2 -- content addresses children; an agent that pulls a story into a prompt should be especially defended.
- **B1 Security boundary docs** at L2 -- AGENTS.md establishes routing but no formal boundary policy beyond it yet.

---

## Improvement plan

| Priority | Action | Lifts |
|---|---|---|
| 1 | Land README and AGENTS.md per the realignment (this change) | A1 -> L4, A2 -> L3, A3 -> L4 |
| 2 | Build a glossary mapping Resonance / Contraction / Null to canonical definitions; cross-link to `thought-org-with-human-ai-hybrid` | A3 -> L5 |
| 3 | Add CONTRIBUTING.md with explicit child-safety review requirement (any change touching stories requires SME OI sign-off) | B5 -> L4 |
| 4 | Move story content to a structured directory with metadata (age range, themes, safety flags) | B2 -> L4 |
| 5 | Add a `skills/story-recommender.md` skill that an agent uses when recommending content, with safety preconditions | A4 -> L3, B3 -> L3 |

---

## Sign-off

- [ ] SME framework owner: ___
- [ ] Content safety reviewer (organic intelligence required): ___
- [ ] Date signed: ___
