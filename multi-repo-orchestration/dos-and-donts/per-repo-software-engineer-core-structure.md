# Dos and Don'ts: software-engineer-core-structure

Applies on top of `universal.md`. Repo-specific rules can tighten; never relax.

---

## Why this repo is different

This repo is the **HIO-Based Engineering Org Setup** -- the structural template for setting up an engineering organization on HIO principles. It is HIO-coupled by design. The role taxonomy, goals, effectiveness measures, and transformation plan here apply HIO to the specific case of engineering orgs.

Forks live downstream and depend on stable role names and goals templates. Treat changes as breaking changes for downstream consumers unless proven otherwise.

---

## Authoring inside the framework

**Do:**
- Anchor every addition to one or more of the **4 HIO Core Principles** ([upstream methodology](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid))
- Keep the 9 roles stable: Architect, Developer, Tester, UX Expert, Product Manager, Project Manager, Program Manager, Data Scientist, Customer Persona
- Cross-link upstream to `thought-org-with-human-ai-hybrid` for HIO principles, and downstream to `software-engineering-hio-agent-framework` for day-to-day agent operations
- When adding examples, prefer the relevancy domain (the reference implementation) so forks see consistent patterns
- Update `CUSTOMIZATION.md` when adding new extension points
- Keep `org/` template entries un-instantiated -- the templates are meant to be filled by forks, not by this repo

**Don't:**
- Rename or remove a role without a deprecation period announced in `PLAN.md`
- Pre-commit a filled `org/profile.md` -- the file is a template; instantiation belongs in forks
- Add **day-to-day agent operation content** -- 6 agent types, sprint ceremonies, agent skills, multi-repo orchestration internals belong downstream in `software-engineering-hio-agent-framework`
- Redefine HIO principles or vocabulary; cite upstream
- Treat HIO as optional in this repo -- HIO coupling is the point of this repo's existence

---

## Cross-repo coupling

**Do:**
- Cite upstream when invoking HIO principles (do not redefine)
- Note in the PR description if a change will require a downstream toolkit update
- When goals or effectiveness measures evolve, signal the change to consumers (forks and the downstream toolkit)

**Don't:**
- Create a hard runtime dependency from this repo to any downstream fork
- Move agent-runtime details (per-tool MCP configs, agent skill implementations) into this repo -- those belong in the toolkit downstream

---

## Examples

- **Adding a 10th role:** requires `PLAN.md` proposal, SME approval, and a reference example in the relevancy domain. Roles are HIO-aligned; the addition must justify its purpose against the 4 Core Principles.
- **Updating an effectiveness measure:** Interactive routing; signal to forks that they should re-baseline.
- **Tightening a role description:** ensure the change is backward-compatible for existing forks; otherwise version the role.
- **Modifying transformation phases:** Interactive; practitioners depend on this for in-flight transformations.
- **Adding agent runtime configuration here:** *do not* -- belongs downstream.
