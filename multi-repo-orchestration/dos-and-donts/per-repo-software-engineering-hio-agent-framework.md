# Dos and Don'ts: software-engineering-hio-agent-framework

Applies on top of `universal.md`. Repo-specific rules can tighten; never relax.

---

## Why this repo is different

This is the operational hub. Changes here can affect agent behavior in every other repo via the multi-repo orchestration framework. Apply caution proportional to blast radius.

---

## Authoring inside the framework

**Do:**
- Use the canonical names exactly: 10 cognitive functions, 6 AI agents, 5 cognitive units, 9 metric categories
- Add new agents, units, or metrics via the existing extension points (see `agents/README.md`, `cognitive-units/README.md`)
- Cross-link to upstream when introducing concepts (`thought-org-with-human-ai-hybrid` for HIO methodology, `software-engineer-core-structure` for the 9-role model)
- Update `DIRECTORY_GUIDE.md` when you add or remove top-level files
- Bump `agent-spec/AGENTS-SPEC-v1.md` version on incompatible changes; coordinate with sibling repos before merging

**Don't:**
- Rename canonical concepts (cognitive functions, agent types) without an upstream change in `thought-org-with-human-ai-hybrid`
- Land a change in `multi-repo-orchestration/` that requires a coordinated change in a sibling repo without opening that sibling's PR first
- Modify the regeneration prompts (`prompts/00-master.md` etc.) without re-validating against the existing structure
- Treat `multi-repo-orchestration/` as a sandbox -- this directory is sensitive surface

---

## Working with `AGENTS.md` spec

**Do:**
- Land spec changes here first, then propagate to sibling repos in the same change set
- Add a CHANGELOG line for any spec change in `agent-spec/AGENTS-SPEC-v1.md`

**Don't:**
- Branch the spec per repo; a single canonical spec applies to the whole family
- Allow drift between this directory's `AGENTS.md` patterns and what sibling repos actually use

---

## Examples

- Adding a new agent type: edit `agents/README.md`, add `agents/<name>.md`, update `CLAUDE.md` agent type list, update operational scorecards if needed. Do not touch sibling repos for this.
- Changing the spec from v1 to v2: open coordinated PRs in all four repos, do not merge until all four are reviewed.
- Renaming a cognitive function: do not. If unavoidable, raise an issue in `thought-org-with-human-ai-hybrid` first.
