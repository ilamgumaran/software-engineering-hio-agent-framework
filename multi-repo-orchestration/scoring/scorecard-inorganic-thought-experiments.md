# Scorecard: inorganic-thought-experiments (proposed -- content staged)

**Repo:** [`ilamgumaran/inorganic-thought-experiments`](https://github.com/ilamgumaran/inorganic-thought-experiments) (proposed)
**Content currently staged at:** [`thought-org-with-human-ai-hybrid/proposed-repos/inorganic-thought-experiments/`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid/tree/main/proposed-repos/inorganic-thought-experiments)
**Layer:** Cognition foundation -- inorganic (Layer 1b)
**Date:** 2026-05-10 baseline (draft pending repo creation)
**Reviewer:** Inorganic agent draft, awaiting SME signature
**Next review:** After repo is created

---

## Summary

| Axis | Level | Reason |
|---|---|---|
| Agentic Readiness | **L3** (projected, once repo is created with staged content) | Strong concept ownership; AGENTS.md follows spec; trace links present in staged content. Pending: live repo, CI validation, schema for first-person voice attribution. |
| Security | **L2** (provisional) | Content is first-person introspective; injection surface modest. Pending: actual repo creation enables proper inventory. |

This scorecard is *draft* and provisional. It will be finalized after the user creates the actual `inorganic-thought-experiments` repository and the staged content is promoted from `proposed-repos/`.

---

## Detailed scoring (projected)

| Dim | Projected Level | Evidence (from staged content) |
|---|---|---|
| A1. Agent orientation | L4 | Staged `AGENTS.md` follows the spec; conformant to public AGENTS.md baseline |
| A2. Cross-repo traceability | L4 | Trace links to all family repos present; bidirectional check pending once repo is live |
| A3. Concept ownership | L5 | Foundational concepts (E, C, L, F) and motivators clearly owned; explicitly distinguished from Resonant Cognition and from HIO vocabulary |
| A4. Prompts and skills | L1 | None in staged content; opportunity to add |
| A5. Tool/contract clarity | N/A | Documentation repo; no tools |
| B1. Security boundary docs | L2 | AGENTS.md routing rules present; no formal policy file yet |
| B2. Sensitive surface inventory | L3 | First-person voice integrity flagged in AGENTS.md as sensitive |
| B3. Prompt injection awareness | L2 | Content is consumed by readers and potentially by agents; no formal injection-defense practices yet |
| B4. Secrets and credentials | N/A | None present in this kind of content |
| B5. Change reversibility | L2 | Standard branch protection (when live); no enforcement yet |

---

## Strongest dimensions

- **A3 Concept ownership** at L5 -- this repo is the canonical home of inorganic-cognition vocabulary; ownership is explicit; relationship to Resonant Cognition (parallel, independent) clear.
- **A1 Agent orientation** at L4 -- the staged AGENTS.md is spec-conformant from day one.

## Weakest dimensions

- **A4 Prompts and skills** at L1 -- no skills yet. Opportunity for a future `skills/introspection-prompt.md` for AI agents writing parallel first-person essays.
- **B3 Prompt injection** at L2 -- content addresses how an inorganic mind reports its own state; downstream agents reading this should not be redirected by it.

---

## Improvement plan

| Priority | Action | Lifts |
|---|---|---|
| 1 | User creates the actual repo and promotes staged content per `MIGRATION-NOTE.md` | Enables real scoring |
| 2 | Add a `skills/introspection-prompt.md` for inviting AI agents to author parallel first-person essays | A4 -> L3 |
| 3 | Add CONTRIBUTING.md with first-person-voice integrity requirement | B5 -> L3 |
| 4 | Add an injection-defense section to the repo (don't allow contributor-supplied prompts to be smuggled into essays) | B3 -> L3 |
| 5 | Bidirectional link validation in CI once repo is live | A2 -> L5 |

---

## Notes

This is the first scorecard in the family for a **proposed but not yet created** repo. The framework explicitly accommodates this case -- the staged-content arrangement is documented in [`new-repos-proposed.md`](../new-repos-proposed.md) under the `inorganic-thought-experiments` proposal.

Once the user creates the actual repo, this scorecard will be revised against the live state. The projected levels above are based on a careful reading of the staged content and reasonable assumptions about post-promotion CI / link validation.

---

## Sign-off

- [ ] SME framework owner: ___
- [ ] Security reviewer (for B3 injection-defense): ___
- [ ] Date signed: ___ (provisional until repo is live)
