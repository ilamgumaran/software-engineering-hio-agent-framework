# Scoring Summary

Comparative agentic and security scores across the HIO repo family. Updated when any scorecard is updated.

---

## At a glance (baseline, this transformation)

| Repo | Agentic | Security | Strongest | Weakest |
|---|---|---|---|---|
| `software-engineering-hio-agent-framework` | L4 | L3 | A1, A3, A4 | B3, B4 |
| `software-engineer-core-structure` | L3 | L3 | A3, B1 | A1, A4 |
| `thought-org-with-human-ai-hybrid` | L2 | L2 | A3 | A1, A2, B3 |
| `thoughtexperiments` | L1 | L2 | --- | A1, A2, A3, B3 |

Levels are floor-of-mean across the five dimensions per axis. See per-repo scorecards for evidence.

---

## Reading the table

- **Agentic** -- mean of A1-A5 floored. L1 means an agent walking in cold cannot orient; L5 means the repo actively drives agent behavior.
- **Security** -- mean of B1-B5 floored. L1-L2 means agents should not act autonomously here; L4-L5 means policy is enforced by tooling.
- **Strongest / Weakest** -- the dimensions that pull the mean up or down most.

---

## Patterns observed

1. **The operational hub leads** -- `software-engineering-hio-agent-framework` is furthest along on agentic readiness because the framework's own subject is agents.
2. **The strategic repo is content-shaped, not agent-shaped** -- `thought-org-with-human-ai-hybrid` scores low on A1/A2 not from neglect, but because it is a methodology document. Adding an `AGENTS.md` per the spec lifts it without distorting its purpose.
3. **Domain content has the steepest curve** -- `thoughtexperiments` is at L1 agentic because there is no orientation file at all. The fix is small in effort but large in score change.
4. **Security floors at L2-L3** -- no repo is below L2 on security because all are MIT, public, and contain no secrets, but none reach L4+ because protections are not yet enforced by tooling.

---

## Quarterly targets

Proposed targets after the first quarterly cycle. SME approval required.

| Repo | Agentic target | Security target | Key actions |
|---|---|---|---|
| `software-engineering-hio-agent-framework` | L5 | L4 | Add CI validation for `AGENTS.md` (A1->L5), inventory sensitive surfaces (B2->L4) |
| `software-engineer-core-structure` | L4 | L4 | Add `AGENTS.md` (A1->L4), add prompt injection notes (B3->L4) |
| `thought-org-with-human-ai-hybrid` | L3 | L3 | Add `AGENTS.md` (A1->L3), explicit concept ownership labels (A3->L4) |
| `thoughtexperiments` | L3 | L3 | Add `AGENTS.md` (A1, A2, A3 all to L3), prompt injection guarding for HTML content (B3->L3) |

---

## Next review

Proposed: 2026-08-10 (one quarter from this baseline). Owner: SME framework owner (TBD via `governance/sme-update-workflow.md`).
