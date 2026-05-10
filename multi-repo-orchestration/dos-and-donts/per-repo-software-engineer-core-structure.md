# Dos and Don'ts: software-engineer-core-structure

Applies on top of `universal.md`. Repo-specific rules can tighten; never relax.

---

## Why this repo is different

This repo is intentionally domain-agnostic. It is the generic forkable predecessor to the HIO operational hub. Forks live downstream and depend on its 9-role model staying stable. Treat changes here as breaking changes for downstream consumers unless proven otherwise.

---

## Authoring inside the framework

**Do:**
- Keep the 9 roles stable: Architect, Developer, Tester, UX Expert, Product Manager, Project Manager, Program Manager, Data Scientist, Customer Persona
- When adding examples, prefer the relevancy domain (the reference implementation) so forks see consistent patterns
- Update `CUSTOMIZATION.md` when adding new extension points
- Keep `org/` template entries un-instantiated -- the templates are meant to be filled by forks, not by this repo

**Don't:**
- Rename or remove a role without a deprecation period announced in `PLAN.md`
- Couple this repo to HIO concepts -- HIO is downstream, not upstream
- Pre-commit a filled `org/profile.md` -- the file is a template; instantiation belongs in forks
- Add CI that requires HIO-specific structures (cognitive units, etc.); this repo must remain HIO-agnostic

---

## Cross-repo coupling

**Do:**
- When the operational hub references this repo as upstream, ensure the reference is in `README.md` "Foundation" or equivalent
- Note in the PR description if a change will require a downstream fork update

**Don't:**
- Create a hard dependency from this repo to any downstream fork
- Use HIO vocabulary (cognitive functions, etc.) inside this repo's role definitions

---

## Examples

- Adding a 10th role: requires `PLAN.md` proposal, SME approval, and a reference example in the relevancy domain.
- Updating the policies template in `CUSTOMIZATION.md`: encourage forks to re-evaluate their instantiated `org/policies.md`.
- Tightening a role description: ensure the change is backward-compatible for existing forks; otherwise, version the role.
