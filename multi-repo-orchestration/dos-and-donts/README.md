# Dos and Don'ts

Guidance for anyone (human or agent) authoring prompts, agent rules, or content that ends up in agent context for a repo in the family. Universal rules first; per-repo specifics second.

---

## Files in this directory

| File | Scope |
|---|---|
| `universal.md` | Apply to every repo in the family |
| `per-repo-software-engineering-hio-agent-framework.md` | Operational hub specifics |
| `per-repo-software-engineer-core-structure.md` | Generic framework specifics |
| `per-repo-thought-org-with-human-ai-hybrid.md` | Methodology specifics |
| `per-repo-thoughtexperiments.md` | Resonant Cognition content specifics, including child-safety |

---

## How rules combine

- Universal rules are the floor; per-repo rules can be **stricter**, never more permissive
- Conflicts resolve in favor of the stricter rule
- A rule that blocks an action wins over a rule that permits it

---

## How to read a rules file

Every rules file uses the same shape:

- **Do** -- imperative, falsifiable, with rationale in one line
- **Don't** -- imperative, falsifiable, with rationale in one line
- **Edge cases** -- when the rule does not apply or has a documented exception
- **Examples** -- short concrete examples of the rule applied

If a rule is not falsifiable (no one can tell whether it was followed), rewrite it before merging.
