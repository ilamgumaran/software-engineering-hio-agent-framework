# HIO Collaboration

Which tasks should organic intelligence (OI = humans) handle, which inorganic intelligence (II = agents) can take autonomously, and where interactive collaboration is the right fit. The mechanism that makes the HIO principles operational at the task level.

---

## Files in this directory

| File | Purpose |
|---|---|
| `matrix.md` | Master classification matrix -- task signal -> OI / II / Interactive |
| `per-repo-routing.md` | Per-repo overrides and rationale |

---

## Three modes

| Mode | Who acts | When to use |
|---|---|---|
| **OI -- Organic Intelligence** | Humans only; agents may produce drafts but do not commit | Irreversible, security-sensitive, ethically loaded, ambiguous-by-design, child-safety adjacent |
| **II -- Inorganic Intelligence** | Agents act autonomously; humans review at PR time | Reversible, well-specified, mechanical, high-volume |
| **Interactive Collaboration** | Tight loop; agent drafts, human reacts, both iterate | Semi-reversible, novel, depends on judgment, requires translation across repos |

---

## How modes are determined

1. Start from the task signal (refactor, bug fix, content authoring, security review, etc.)
2. Check `matrix.md` for the default routing
3. Check the per-repo override in `per-repo-routing.md`
4. The most restrictive mode wins (OI > Interactive > II)
5. If two repos disagree, escalate to SMEs

---

## Why this matters

HIO insists humans and AI are partners, not substitutes. The cost of getting this wrong is not just "the AI made a mistake" -- it is the loss of trust that makes future collaboration possible. The matrix encodes the routing once, so each session does not re-litigate it.
