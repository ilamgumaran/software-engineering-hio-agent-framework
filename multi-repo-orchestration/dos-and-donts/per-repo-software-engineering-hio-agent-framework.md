# Dos and Don'ts: software-engineering-hio-agent-framework

Applies on top of `universal.md`. Repo-specific rules can tighten; never relax.

---

## Why this repo is different

This is the **day-to-day agentic toolkit** for an HIO-aligned engineering organization, and the host of the multi-repo orchestration framework. Changes here can affect agent behavior in every other repo via the multi-repo framework. Apply caution proportional to blast radius.

This repo is downstream of `software-engineer-core-structure` (engineering-org setup). Org-level concerns belong upstream; agent-runtime and day-to-day operation concerns belong here.

---

## Authoring inside the framework

**Do:**
- Use the canonical names exactly: 10 cognitive functions, 6 AI agents, 5 cognitive units, 9 metric categories
- Add new agents, units, or metrics via the existing extension points (see `agents/README.md`, `cognitive-units/README.md`)
- Cross-link upstream when introducing concepts (`thoughtexperiments` for cognition theory, `thought-org-with-human-ai-hybrid` for HIO methodology, `software-engineer-core-structure` for org-level role taxonomy and goals)
- Update `DIRECTORY_GUIDE.md` when you add or remove top-level files
- Bump `agent-spec/AGENTS-SPEC-v1.md` version on incompatible changes; coordinate with sibling repos before merging

**Don't:**
- Rename canonical concepts (cognitive functions, agent types) without an upstream change in `thought-org-with-human-ai-hybrid` (or `software-engineer-core-structure` for role taxonomy)
- Land a change in `multi-repo-orchestration/` that requires a coordinated change in a sibling repo without opening that sibling's PR first
- Modify the regeneration prompts (`prompts/00-master.md` etc.) without re-validating against the existing structure
- Add **org-setup content** here (org-level role definitions, the org-level transformation plan, goals templates) -- those belong upstream in `software-engineer-core-structure`
- Treat `multi-repo-orchestration/` as a sandbox -- this directory is sensitive surface

---

## Working with `AGENTS.md` spec

**Do:**
- Land spec changes here first, then propagate to sibling repos in the same change set
- Add a CHANGELOG line for any spec change in `agent-spec/AGENTS-SPEC-v1.md`
- Maintain compatibility with the public AGENTS.md convention (AAIF baseline)

**Don't:**
- Branch the spec per repo; a single canonical spec applies to the whole family
- Allow drift between this directory's `AGENTS.md` patterns and what sibling repos actually use
- Allow the spec to drift incompatibly from the public AGENTS.md convention

---

## Examples

- Adding a new agent type: edit `agents/README.md`, add `agents/<name>.md`, update `CLAUDE.md` agent type list, update operational scorecards if needed. Do not touch sibling repos for this.
- Changing the spec from v1 to v2: open coordinated PRs in all four repos, do not merge until all four are reviewed.
- Renaming a cognitive function: do not. If unavoidable, raise an issue in `thought-org-with-human-ai-hybrid` (methodology) and `software-engineer-core-structure` (org-level usage) first.
- Adding the org-level transformation plan: *do not* -- belongs upstream in `software-engineer-core-structure`.
