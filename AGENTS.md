# AGENTS

The operational hub of the HIO repo family. Hosts the cross-repo orchestration framework at `multi-repo-orchestration/`.

## Family

This repo is part of the HIO repo family. The central spec is at [`multi-repo-orchestration/`](multi-repo-orchestration/).

| Repo | Relationship |
|---|---|
| [`thought-org-with-human-ai-hybrid`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid) | Upstream methodology -- HIO principles, organic/inorganic intelligence, the 4 HIO Tests |
| [`software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure) | Upstream generic framework -- 9 roles, domain extension system |
| [`thoughtexperiments`](https://github.com/ilamgumaran/thoughtexperiments) | Sibling -- Resonant Cognition Framework content; governed by this repo's multi-repo spec |

## Purpose and scope

This repo operationalizes HIO methodology for engineering organizations. It is also the host of the cross-repo orchestration framework that governs the entire family.

**In scope:** 10 cognitive functions, 6 AI agent types, 5 cognitive units, 9 metric categories, the 26-week transformation, multi-repo orchestration spec, agent skills and prompts, governance.

**Out of scope:** HIO methodology principles (upstream), generic agent role definitions (upstream), domain content like stories (sibling repo).

## Key concepts owned here

- The 10 cognitive functions: Builder, Problem Framer, Pattern Integrator, Resonance Sensor, Quality Guardian, Growth Catalyst, Solution Architect, Stakeholder Harmonizer, Fresh-Eyes Observer, Learner
- The 6 AI agent types: Analysis Partner, Code Co-Creator, Architecture Explorer, Quality Analyst, Metrics Monitor, Documentation & Knowledge
- The 5 cognitive units: Experiment Velocity, Scale & Reliability, Developer Experience, Intelligence Layer, Frontier
- The 9 metric categories across Current / Outcome / HIO layers
- The multi-repo orchestration framework -- spec, scoring, dos/don'ts, HIO routing, skills, prompts, governance

Concepts not owned here are reused with attribution; see `multi-repo-orchestration/repo-registry.md`.

## How to make changes

- Branch from `main` using a descriptive feature branch name
- Follow the existing markdown style: pure markdown, no YAML frontmatter, tables with 3+ rows
- Cross-link to upstream repos when introducing concepts they own
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
- Land changes in `multi-repo-orchestration/` that require a coordinated sibling change without opening the sibling PR first
- Treat `multi-repo-orchestration/` as a sandbox -- it is sensitive surface

Full list: [`multi-repo-orchestration/dos-and-donts/per-repo-software-engineering-hio-agent-framework.md`](multi-repo-orchestration/dos-and-donts/per-repo-software-engineering-hio-agent-framework.md).

## HIO routing

| Task signal | Route | Why |
|---|---|---|
| Typo fix in non-canonical doc | II | Reversible, mechanical |
| Edit `multi-repo-orchestration/` files | OI | Cascades to entire family |
| Edit `cognitive-functions/` definitions | OI | Identity-level change; vocabulary owned upstream |
| Edit `agents/` definitions | Interactive | Affects HIO operational identity |
| Edit `prompts/` regeneration prompts (substantive) | Interactive | Affects downstream forks |
| Add new agent type via extension | Interactive | Use existing process in `agents/README.md` |
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

For org-wide rules, see [`multi-repo-orchestration/governance/security-and-safety.md`](multi-repo-orchestration/governance/security-and-safety.md).

## Trace links

| Need | Look at |
|---|---|
| HIO methodology and principles | [`thought-org-with-human-ai-hybrid`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid) |
| Generic agent role model (predecessor framework) | [`software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure) |
| Domain content (Resonant Cognition stories) | [`thoughtexperiments`](https://github.com/ilamgumaran/thoughtexperiments) |
| Multi-repo orchestration -- registry, spec, scoring | [`multi-repo-orchestration/`](multi-repo-orchestration/) |
| Per-tool guides (Claude Code, Copilot, Gemini, Glean) | [`tools/`](tools/) |
| Worked examples | [`examples/`](examples/) |

## Spec version

Spec: AGENTS-SPEC-v1
