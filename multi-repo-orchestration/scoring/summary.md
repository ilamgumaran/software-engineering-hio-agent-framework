# Scoring Summary

Comparative agentic and security scores across the HIO repo family. Updated when any scorecard is updated. Layered upstream-to-downstream.

---

## At a glance (post-realignment baseline)

| # | Layer | Repo | Agentic | Security | Strongest | Weakest |
|---|---|---|---|---|---|---|
| 1 | Cognition foundation | `thoughtexperiments` | L2 | L2 | A3 (concept ownership) | A4, B3 |
| 2 | Generalized HIO framework | `thought-org-with-human-ai-hybrid` | L2 | L2 | A3 | A4, B3 |
| 3 | Engineering org applied | `software-engineer-core-structure` | L3 | L3 | A3, B1 | A4, B3 |
| 4 | Day-to-day agentic toolkit | `software-engineering-hio-agent-framework` | L4 | L3 | A1, A3, A4 | B3 |

Levels are floor-of-mean across the five dimensions per axis. See per-repo scorecards for evidence.

---

## Reading the table

- **Agentic** -- mean of A1-A5 floored. L1 means an agent walking in cold cannot orient; L5 means the repo actively drives agent behavior.
- **Security** -- mean of B1-B5 floored. L1-L2 means agents should not act autonomously here; L4-L5 means policy is enforced by tooling.
- **Strongest / Weakest** -- the dimensions that pull the mean up or down most.

---

## Patterns observed (post-realignment)

1. **Scores rise as you move downstream** -- expected, since each downstream layer is more concrete and has more agent-relevant detail. The cognition foundation is content-shaped; the day-to-day toolkit is agent-shaped.
2. **Concept ownership is strong throughout** (A3 = L4 in three of four repos) -- the realignment made ownership explicit at every layer.
3. **Prompt injection awareness is the consistent weak point** (B3 = L2 in three of four repos) -- the family has no red-team practice yet.
4. **The toolkit leads on agentic** (L4) and the cognition repo trails (L2) -- this is correct; an agent walking into the toolkit should find more orientation than an agent walking into a cognition-source content repo.

---

## Quarterly targets

Proposed targets after the first quarterly cycle. SME approval required.

| Repo | Agentic target | Security target | Key actions |
|---|---|---|---|
| `thoughtexperiments` | L3 | L3 | Add `skills/story-recommender.md` with safety preconditions; CONTRIBUTING.md with child-safety reviewer requirement |
| `thought-org-with-human-ai-hybrid` | L3 | L3 | Add `prompts/` or `skills/` HIO classifier; CONTRIBUTING.md prompt-injection guidance |
| `software-engineer-core-structure` | L4 | L4 | Add prompt injection notes; skills system for forks; example instantiated `org/` |
| `software-engineering-hio-agent-framework` | L5 | L4 | CI validation for `AGENTS.md`; inventory new sensitive surfaces |

---

## Next review

Proposed: 2026-08-10 (one quarter from this baseline). Owner: SME framework owner (TBD via `governance/sme-update-workflow.md`).
