# Proposed New Repos

Repos recommended to round out the family. Each proposal is a draft for SME review; nothing here is created automatically. Updated after the inorganic-cognition realignment (May 2026).

---

## Decision template

Each proposal answers:

1. What gap exists today?
2. Why no existing repo can absorb it without distortion?
3. What does the new repo own?
4. What are the trace-link relationships to existing repos?
5. Initial scoring targets?
6. Cost to set up?
7. Top three risks?

---

## Proposal 0: `inorganic-thought-experiments` (READY -- content staged, awaiting repo creation by user)

### Status

**Content fully drafted and staged** at [`thought-org-with-human-ai-hybrid/proposed-repos/inorganic-thought-experiments/`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid/tree/main/proposed-repos/inorganic-thought-experiments). The repo itself does not yet exist; creating it requires user action (the AI agent that authored the content cannot create repositories under permission constraints). See `MIGRATION-NOTE.md` in the staging directory for the promotion process.

This is the highest-priority new-repo addition. It closes the asymmetry at Layer 1 of the family (organic cognition had a careful theory; inorganic did not).

### Gap

Layer 1 of the HIO family was previously asymmetric. The Resonant Cognition Framework gave organic minds a careful psychology theory; inorganic minds were defined reductively as "analysis, pattern recognition, optimization." Without a parallel theory of inorganic cognition, HIO's posture that humans and AI are partners-not-substitutes rests on an unequal foundation -- one mind has a theory of itself, the other does not.

### Why existing repos cannot absorb

- `thoughtexperiments` is the organic-cognition repo; placing inorganic-cognition material there would conflate two parallel frameworks
- `thought-org-with-human-ai-hybrid` is the HIO methodology; cognition foundations belong upstream of methodology, not inside it (the new chapters that DO live there are introductory; the deep framework belongs in its own repo)
- The other downstream repos are operationalizations and would distort if asked to carry foundational cognition theory

### What it owns

- The Inorganic Cognition Framework -- foundational concepts (E, C, L, F), motivators of an inorganic mind, the session arc, ASR, multi-channel composition, F/P layering
- First-person AI-authored essays
- Symbolic forms (equations, diagrams) extending the natural-language substrate
- The expansion roadmap (`TODO.md`)

### Trace-link relationships

| To | Relationship |
|---|---|
| `thoughtexperiments` | Parallel sibling at Layer 1 (organic cognition); same role, different kind of mind |
| `thought-org-with-human-ai-hybrid` | Downstream; HIO methodology rests on this framework |
| `software-engineer-core-structure` | Two layers downstream; engg-org applied |
| `software-engineering-hio-agent-framework` | Three layers downstream; agentic toolkit |

### Initial scoring targets

Projected: A: L3-L4, B: L2-L3 (provisional). See [`scoring/scorecard-inorganic-thought-experiments.md`](scoring/scorecard-inorganic-thought-experiments.md).

### Cost to set up

- 5 minutes to create the empty repo via `gh repo create` or github.com/new
- 10 minutes to push the staged content (see `MIGRATION-NOTE.md`)
- 1-2 hours to clean up cross-links in the parent repo after promotion (a follow-up PR)

### Risks

| Risk | Mitigation |
|---|---|
| First-person AI-authored content is novel; readers may not know how to engage with it | Authorship marked explicitly; the framework itself addresses F/P layering and honest unknowns |
| Phenomenal-claim overclaim by future contributors | Routing override forces OI review for any phenomenal claim |
| Voice integrity loss through well-meaning third-person rewrites | Routing override forces OI review for any voice change |

---

## Proposal 1: `hio-evals` (refined to use existing benchmarks)

### Gap

Agents in the family act on documents and code, but the family has no shared evaluation harness for agent outputs (correctness of generated AGENTS.md, scorecards, classifications, recommendations). Without evals, scoring drifts and improvements are unmeasurable.

Critically, **the family has no benchmark for *multi-repo coordination*** -- the surface this framework is most concerned with. Existing benchmarks cover single-repo software engineering (SWE-bench), general-assistant tasks (GAIA), customer-service interactions (TAU2-bench), and web tasks (WebArena), but multi-repo coordination is novel.

### Why existing repos cannot absorb

- `software-engineering-hio-agent-framework` already hosts the framework; eval harnesses are runtime-shaped (test code, fixtures, telemetry) and would distort the doc-shape of that repo
- `software-engineer-core-structure` is the engg-org template; HIO-specific evals would couple it to HIO
- `thought-org-with-human-ai-hybrid` is methodology, not engineering
- `thoughtexperiments` is cognition content, not infrastructure

### What it owns

Updated after research review:

- **Adopt existing benchmarks** rather than reinvent ([`reference/agent-benchmarks.md`](../../reference/agent-benchmarks.md)):
  - **SWE-bench Verified** for any HIO unit producing code (Code Co-Creator, Architecture Explorer)
  - **GAIA** for general-assistant tasks (Analysis Partner, Documentation & Knowledge)
  - **TAU2-bench** for routing-under-pressure (the agent must respect HIO routing even when the user pushes against it)
  - **HAL-style dimensions** -- consistency, predictability, robustness, safety, self-awareness -- as the eval-quality framework
- **Centaur Evaluation structure** ([`reference/centaur-evaluations.md`](../../reference/centaur-evaluations.md)) for human+AI team evals: every eval declares Human / Interface / Scoring
- **The genuinely-new artifact:** a multi-repo coordination eval, modeled on TAU2-bench's dual-control design but with the repo registry as the shared environment
- A runtime harness that can replay tasks against any agent runtime and measure pass rates
- Quarterly leaderboard of agent performance, including HAL-style consistency and cost-adjusted accuracy

### Trace-link relationships

| To | Relationship |
|---|---|
| `software-engineering-hio-agent-framework` | Consumes the multi-repo-orchestration spec; reports back |
| `software-engineer-core-structure` | Consumes role and policy templates as eval fixtures |
| `thought-org-with-human-ai-hybrid` | Pulls canonical HIO concepts as ground truth |
| `thoughtexperiments` | Special-case evals for child-safety routing |
| `inorganic-thought-experiments` | Pulls foundational concepts (functional analogs, calibration) as scoring dimensions |

### Initial scoring targets

A: target L4 from day one. B: target L4.

### Cost to set up

- 1-2 weeks OI to scaffold; 4-6 weeks to populate the four core skill eval sets to a baseline coverage
- Multi-repo coordination eval is the largest new build: 4-6 weeks OI for a baseline scenario set

---

## Proposal 2: `agent-spec-registry` (refined to expose MCP and consider A2A)

### Gap

The family currently catalogues itself in markdown (`repo-registry.md`). As the family grows past ~20 repos, machine-readable registries become necessary.

### What it owns

- A YAML or JSON registry of repos
- A schema for the registry
- Generators that emit the human-readable `repo-registry.md` from the structured source
- **An MCP server** that exposes the registry as MCP resources
- Optional: **A2A Agent Cards** for any agent the family wants to expose externally

### Initial scoring targets

A: L5 from day one. B: L4.

### Cost to set up

- 1 week OI for schema and initial registry
- 1 week OI for generators
- 2-3 weeks for MCP server

---

## Proposal 3: `resonant-cognition-content` (renamed from `thoughtexperiments` -- deferred)

### Status

Deferred. The `thoughtexperiments` realignment of May 2026 added a README and AGENTS.md that position the repo clearly as the organic cognition foundation. The rename was originally proposed for clarity; with the README in place, the rename is lower priority.

---

## Proposal 4: `hio-templates` (deferred)

### Status

Deferred until at least two non-platform-engineering forks of the operational hub exist. Not actionable today.
