# AGENTS.md Specification v1

The contract every repo in the family follows. A single `AGENTS.md` at the repo root, conforming to this spec, is enough to make a repo agent-ready.

---

## Required sections

Every `AGENTS.md` MUST include the following sections in this order. Optional sections MAY be added after.

| Section | Purpose | Length guidance |
|---|---|---|
| `# AGENTS` heading + one-line repo identity | Tell the agent what this repo is | 1 line |
| `## Family` | Link to repo registry and sibling repos | 5-15 lines |
| `## Purpose and scope` | What this repo is for; what it is not for | 5-20 lines |
| `## Key concepts owned here` | Concepts authoritatively defined here | 5-20 lines |
| `## How to make changes` | Branch convention, commit style, PR expectations | 5-15 lines |
| `## Dos and don'ts` | Repo-specific prompt-author guidance | 10-30 lines |
| `## HIO routing` | Which task types are OI / II / Interactive | Table, 5-10 rows |
| `## Security boundaries` | What an agent must never do; sensitive surfaces | 5-15 lines |
| `## Trace links` | Where to look in related repos | Table, 3-8 rows |
| `## Spec version` | Which version of this spec the file follows | 1 line |

---

## Spec versioning

This spec is versioned. Each `AGENTS.md` declares the version it follows in its final line:

```
Spec: AGENTS-SPEC-v1
```

Incompatible changes bump the version. Backward-compatible additions reuse the version with a minor suffix (e.g., `v1.1`).

---

## File location and discoverability

- **Filename:** `AGENTS.md` (uppercase, exact)
- **Location:** Repository root
- **Encoding:** UTF-8, LF line endings
- **Format:** Pure markdown, no frontmatter
- **Discoverability:** Linked from the repo `README.md` near the top, with the line: `> AI agents: see [AGENTS.md](AGENTS.md) before making changes.`

---

## Section format details

### Family

```markdown
## Family

This repo is part of the HIO repo family. The central spec is at
[ilamgumaran/software-engineering-hio-agent-framework/multi-repo-orchestration](https://github.com/ilamgumaran/software-engineering-hio-agent-framework/tree/main/multi-repo-orchestration).

| Repo | Relationship |
|---|---|
| `<repo-1>` | <one-line> |
| `<repo-2>` | <one-line> |
```

### Dos and don'ts

Use two short bullet lists. Maximum five bullets each. Bullets must be imperative and falsifiable -- a reader can tell whether the rule was followed.

```markdown
## Dos and don'ts

**Do:**
- <imperative, falsifiable bullet>

**Don't:**
- <imperative, falsifiable bullet>
```

Link to the per-repo full file in `dos-and-donts/per-repo-<name>.md` for the long version.

### HIO routing

```markdown
## HIO routing

| Task signal | Route | Why |
|---|---|---|
| <task type> | OI / II / Interactive | <one-line rationale> |
```

Minimum five rows. Anything not listed defaults to **Interactive**.

### Security boundaries

Use positive ("agent may") and negative ("agent must not") clauses. Reference the central `governance/security-and-safety.md` rather than restating org-wide rules.

```markdown
## Security boundaries

**An agent may:**
- <action>

**An agent must not:**
- <action>

For org-wide rules, see [security-and-safety](.../governance/security-and-safety.md).
```

### Trace links

```markdown
## Trace links

| Need | Look at |
|---|---|
| <intent> | <repo or path> |
```

Minimum three rows. Each row should answer a real question an agent would have.

---

## Validation checklist for SMEs

Before merging an `AGENTS.md` change, verify:

- [ ] All required sections present and in order
- [ ] Spec version line at the bottom
- [ ] Dos and don'ts are imperative and falsifiable
- [ ] HIO routing has at least five task-signal rows
- [ ] Security boundaries reference central policy, do not restate it
- [ ] Trace links resolve (no 404s)
- [ ] Repo `README.md` has the agent-pointer line near the top

The `skills/repo-cartographer.md` skill performs this check automatically when run by an agent.

---

## What this spec deliberately does not require

- **Code-style rules** -- those live in language-specific config (linters, formatters)
- **CI/CD rules** -- those live in `.github/workflows/` or equivalent
- **Per-file ownership** -- use CODEOWNERS for that
- **Test requirements** -- those belong in repo-specific contributor guides

`AGENTS.md` is for agent orientation, not engineering-org policy.

---

## Reference: minimum viable AGENTS.md

A conformant minimum file is roughly 80 lines. See any of the per-repo `AGENTS.md` files added to sibling repos in the same change as this spec for live examples.
