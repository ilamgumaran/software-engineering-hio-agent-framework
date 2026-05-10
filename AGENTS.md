# AGENTS

The **HIO Agentic Workflow Toolkit** -- the day-to-day toolkit used inside an HIO-aligned engineering org. Hosts the cross-repo orchestration framework at `multi-repo-orchestration/`.

## Family

This repo is part of the HIO repo family. The central spec is at [`multi-repo-orchestration/`](multi-repo-orchestration/).

| Repo | Relationship |
|---|---|
| [`thoughtexperiments`](https://github.com/ilamgumaran/thoughtexperiments) | Three layers upstream -- Resonant Cognition Framework, the cognition foundation |
| [`thought-org-with-human-ai-hybrid`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid) | Two layers upstream -- the generalized HIO methodology |
| [`software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure) | Direct upstream -- HIO-Based Engineering Org Setup; this toolkit operates inside an org set up using that template |

## Purpose and scope

This repo carries the **day-to-day agentic workflow toolkit** for an HIO-aligned engineering organization, and hosts the cross-repo orchestration framework that governs the family.

**In scope:** 6 AI agent types, agent skills, harmonized sprint ceremonies, per-runtime tool guides, multi-repo orchestration spec / scoring / dos and don'ts / governance, agent skills and prompts, the multi-repo agent skills.

**Operational definitions kept here** (as runtime references for agents): the 10 cognitive functions, 5 cognitive units, 9 metric categories. The *org-level* application of these (goals, effectiveness measures, transformation plan) is upstream in `software-engineer-core-structure`.

**Out of scope:** HIO methodology principles (upstream methodology repo), engineering-org setup and goals (upstream engg-org repo), domain content like cognition stories (upstream cognition foundation repo).

## Key concepts owned here

- The 6 AI agent types: Analysis Partner, Code Co-Creator, Architecture Explorer, Quality Analyst, Metrics Monitor, Documentation & Knowledge
- Harmonized sprint ceremonies (Sprint Kickoff, Daily Harmony Check, Deep Work + Collaboration, Sprint Outcome Review, Harmonization Retrospective, Exploration Time)
- Agent skills (`skills/`) and prompts (`prompts/`) at the day-to-day level
- Per-runtime tool guides (Claude Code, GitHub Copilot, Gemini Enterprise, Glean)
- The multi-repo orchestration framework -- spec, scoring, dos/don'ts, HIO routing, skills, prompts, governance
- Operational definitions of cognitive functions / units / metrics (the org-level application is upstream)

Concepts not owned here are reused with attribution; see `multi-repo-orchestration/repo-registry.md`.

## How to make changes

- Branch from `main` using a descriptive feature branch name
- Keep markdown style: pure markdown, no YAML frontmatter, tables with 3+ rows
- Cross-link upstream when introducing concepts those repos own (HIO principles -> methodology repo; org goals -> engg-org repo; cognition theory -> cognition repo)
- Update `DIRECTORY_GUIDE.md` when adding or removing top-level files
- Run the HIO classifier before committing: see [`multi-repo-orchestration/skills/hio-classifier.md`](multi-repo-orchestration/skills/hio-classifier.md)

## Dos and don'ts

**Do:**
- Use canonical names exactly (cognitive functions, agent types, units, metrics)
- Add new agents/units/metrics via the existing extension points
- Cross-link upstream when introducing imported concepts
- Land spec changes in `multi-repo-orchestration/` here first, then propagate

**Don't:**
- Rename canonical concepts without an upstream change in the methodology repo
- Add **org-setup content** here (role definitions, org-level goals, transformation phases at the org level) -- those belong in `software-engineer-core-structure`
- Land changes in `multi-repo-orchestration/` that require a coordinated sibling change without opening the sibling PR first
- Treat `multi-repo-orchestration/` as a sandbox -- it is sensitive surface

Full list: [`per-repo-software-engineering-hio-agent-framework.md`](multi-repo-orchestration/dos-and-donts/per-repo-software-engineering-hio-agent-framework.md).

## HIO routing

| Task signal | Route | Why |
|---|---|---|
| Typo fix in non-canonical doc | II | Reversible, mechanical |
| Edit `multi-repo-orchestration/` files | OI | Cascades to entire family |
| Edit `cognitive-functions/` definitions | OI | Identity-level change; org-level meaning owned upstream |
| Edit `agents/` definitions | Interactive | Affects HIO operational identity |
| Edit `prompts/` regeneration prompts (substantive) | Interactive | Affects downstream forks |
| Add new agent type via extension | Interactive | Use existing process in `agents/README.md` |
| Move org-setup content downstream-to-here | OI | Conceptual layering change |
| Spec version bump | OI | Family-wide cascade |

Full table and overrides: [`multi-repo-orchestration/hio-collaboration/per-repo-routing.md`](multi-repo-orchestration/hio-collaboration/per-repo-routing.md).

## Security boundaries

**An agent may:**
- Read and modify framework documents in feature branches
- Run scorers, classifiers, link validators (read-only tools)
- Open PRs and comment on issues

**An agent must not:**
- Push to `main`
- Modify `multi-repo-orchestration/` without explicit per-task authorization
- Bump the spec version
- Modify `CLAUDE.md` or `org/policies.md` without OI review
- Move org-setup content into this repo

For org-wide rules, see [`multi-repo-orchestration/governance/security-and-safety.md`](multi-repo-orchestration/governance/security-and-safety.md).

## Trace links

| Need | Look at |
|---|---|
| Cognition foundation (3 layers upstream) | [`thoughtexperiments`](https://github.com/ilamgumaran/thoughtexperiments) |
| HIO methodology (2 layers upstream) | [`thought-org-with-human-ai-hybrid`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid) |
| Engineering org setup, goals, effectiveness measures (direct upstream) | [`software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure) |
| Multi-repo orchestration -- registry, spec, scoring | [`multi-repo-orchestration/`](multi-repo-orchestration/) |
| Per-tool guides (Claude Code, Copilot, Gemini, Glean) | [`tools/`](tools/) |
| Worked examples | [`examples/`](examples/) |
| 6 agent types | [`agents/`](agents/) |
| Sprint ceremonies | [`workflows/`](workflows/) |

## Spec version

Spec: AGENTS-SPEC-v1
