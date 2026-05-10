# Scoring Summary

Comparative agentic and security scores across the HIO repo family. Updated when any scorecard is updated. Layered upstream-to-downstream.

---

## At a glance (post-inorganic-cognition baseline)

| # | Layer | Repo | Agentic | Security | Strongest | Weakest |
|---|---|---|---|---|---|---|
| 1a | Cognition foundation -- organic | `thoughtexperiments` | L2 | L2 | A3 (concept ownership) | A4, B3 |
| 1b | Cognition foundation -- inorganic (proposed) | `inorganic-thought-experiments` | L3 (projected) | L2 (provisional) | A3, A1 | A4, B3 |
| 2 | Generalized HIO framework | `thought-org-with-human-ai-hybrid` | L2 (lifted to L3 after inorganic content added) | L2 | A3 | A4, B3 |
| 3 | Engineering org applied | `software-engineer-core-structure` | L3 | L3 | A3, B1 | A4, B3 |
| 4 | Day-to-day agentic toolkit | `software-engineering-hio-agent-framework` | L4 | L3 | A1, A3, A4 | B3 |

Levels are floor-of-mean across the five dimensions per axis. See per-repo scorecards for evidence. The Layer 1b row is provisional until the repo is created and the staged content is promoted.

---

## Patterns observed (current baseline)

1. **The family is now symmetric at Layer 1** -- organic and inorganic cognition foundations both exist (one live, one proposed-and-staged). Earlier asymmetry where only organic cognition had a careful theory is now addressed.
2. **Concept ownership remains strong throughout** (A3 = L4 or L5 in four of five repos).
3. **Prompt injection awareness is the consistent weak point** (B3 = L2 in four of five repos) -- the family has no red-team practice yet.
4. **The toolkit leads on agentic** (L4) and the cognition repos trail (L2-L3) -- correct, given content vs operations.
5. **The HIO methodology repo (Layer 2) lifts after the inorganic chapters land** -- the addition of first-person AI-authored chapters strengthens concept ownership and trace links.

---

## Quarterly targets

Proposed targets after the first quarterly cycle. SME approval required.

| Repo | Agentic target | Security target | Key actions |
|---|---|---|---|
| `thoughtexperiments` | L3 | L3 | Add `skills/story-recommender.md` with safety preconditions; CONTRIBUTING.md with child-safety reviewer requirement |
| `inorganic-thought-experiments` (once promoted) | L4 | L3 | Promote from staging; add `skills/introspection-prompt.md`; CONTRIBUTING.md with first-person-voice integrity rule |
| `thought-org-with-human-ai-hybrid` | L3 | L3 | Inorganic chapters live; add prompt-injection guidance |
| `software-engineer-core-structure` | L4 | L4 | Add prompt injection notes; skills system for forks; example instantiated `org/` |
| `software-engineering-hio-agent-framework` | L5 | L4 | CI validation for `AGENTS.md`; inventory new sensitive surfaces |

---

## Next review

Proposed: 2026-08-10 (one quarter from this baseline). Owner: SME framework owner (TBD via `governance/sme-update-workflow.md`).

One-off review trigger: when the user creates `inorganic-thought-experiments` and promotes the staged content, re-score immediately to convert the provisional 1b numbers into live ones.
