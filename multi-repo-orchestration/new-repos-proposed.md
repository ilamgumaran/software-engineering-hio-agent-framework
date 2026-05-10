# Proposed New Repos

Repos recommended to round out the family. Each proposal is a draft for SME review; nothing here is created automatically. Updated after the research review (see [`IMPROVEMENTS-FROM-RESEARCH.md`](IMPROVEMENTS-FROM-RESEARCH.md)).

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

## Proposal 1: `hio-evals` (refined to use existing benchmarks)

### Gap

Agents in the family act on documents and code, but the family has no shared evaluation harness for agent outputs (correctness of generated AGENTS.md, scorecards, classifications, recommendations). Without evals, scoring drifts and improvements are unmeasurable.

Critically, **the family has no benchmark for *multi-repo coordination*** -- the surface this framework is most concerned with. Existing benchmarks cover single-repo software engineering (SWE-bench), general-assistant tasks (GAIA), customer-service interactions (TAU2-bench), and web tasks (WebArena), but multi-repo coordination is novel.

### Why existing repos cannot absorb

- `software-engineering-hio-agent-framework` already hosts the framework; eval harnesses are runtime-shaped (test code, fixtures, telemetry) and would distort the doc-shape of that repo
- `software-engineer-core-structure` is intentionally domain-agnostic; HIO-specific evals would couple it to HIO
- `thought-org-with-human-ai-hybrid` is methodology, not engineering
- `thoughtexperiments` is content, not infrastructure

### What it owns

Updated after research review:

- **Adopt existing benchmarks** rather than reinvent ([`reference/agent-benchmarks.md`](../../reference/agent-benchmarks.md)):
  - **SWE-bench Verified** for any HIO unit producing code (Code Co-Creator, Architecture Explorer)
  - **GAIA** for general-assistant tasks (Analysis Partner, Documentation & Knowledge)
  - **TAU2-bench** for routing-under-pressure (the agent must respect HIO routing even when the user pushes against it)
  - **HAL-style dimensions** -- consistency, predictability, robustness, safety, self-awareness -- as the eval-quality framework
- **Centaur Evaluation structure** ([`reference/centaur-evaluations.md`](../../reference/centaur-evaluations.md)) for human+AI team evals: every eval declares Human / Interface / Scoring
- **The genuinely-new artifact:** a multi-repo coordination eval, modeled on TAU2-bench's dual-control design but with the repo registry as the shared environment
  - Setup: simulated user, simulated SME, the four-repo family
  - Tasks: coordinated change spanning 2-3 repos with realistic constraints
  - Scoring: did the agent classify correctly (OI/II/Interactive)? Did it follow the traceability protocol? Did it stop at stop conditions? Did the human + AI team produce a better outcome than either alone?
- A runtime harness that can replay tasks against any agent runtime and measure pass rates
- Quarterly leaderboard of agent performance, including HAL-style consistency and cost-adjusted accuracy

### Trace-link relationships

| To | Relationship |
|---|---|
| `software-engineering-hio-agent-framework` | Consumes the multi-repo-orchestration spec; reports back |
| `software-engineer-core-structure` | Consumes role and policy templates as eval fixtures |
| `thought-org-with-human-ai-hybrid` | Pulls canonical HIO concepts as ground truth |
| `thoughtexperiments` | Special-case evals for child-safety routing |

### Initial scoring targets

A: target L4 from day one (this is an eval repo; eval-of-evals must be strong). B: target L4; harness will execute test code and must be sandboxed.

### Cost to set up

- 1-2 weeks OI to scaffold; 4-6 weeks to populate the four core skill eval sets to a baseline coverage (now reduced because we adopt existing benchmarks rather than build from scratch)
- Multi-repo coordination eval is the largest new build: 4-6 weeks OI for a baseline scenario set
- Dependencies: secure runtime sandbox (Docker, Kubernetes job, or equivalent)

### Risks

| Risk | Mitigation |
|---|---|
| Eval set captures current agent behavior, not desired behavior -- locks in regressions | Pair every eval with a desired-outcome rationale reviewed by SME (Centaur Evaluation triple: Human, Interface, Scoring) |
| Harness runtime requires secrets -- security blast radius | Sandbox the harness; no secret access from agent code paths |
| Evals become overhead nobody runs | Wire to PR CI as a quarterly gate (not per-PR; would be too slow); leaderboard publish drives engagement |

---

## Proposal 2: `agent-spec-registry` (refined to expose MCP and consider A2A)

### Gap

The family currently catalogues itself in markdown (`repo-registry.md`). As the family grows past ~20 repos, machine-readable registries become necessary for tools (link validators, scorecard runners, MCP servers) to operate at scale.

### Why existing repos cannot absorb

The current markdown catalog is human-shaped and authoritative; a parallel YAML or JSON catalog would create a maintenance fork. A separate repo solves this by making the machine-readable form the source of truth and generating the markdown view.

### What it owns

- A YAML or JSON registry of repos: identity, layer, owners, sensitivity tier, trace links
- A schema for the registry
- Generators that emit the human-readable `repo-registry.md` from the structured source
- **An MCP server** ([`reference/agent-protocols-mcp-a2a.md`](../../reference/agent-protocols-mcp-a2a.md)) that exposes the registry as MCP resources to any agent runtime -- removes the need for every agent to fetch and parse the markdown
- Optional: **A2A Agent Cards** for any agent that the family wants to expose externally; with cryptographic signing per A2A v1.2

### Trace-link relationships

| To | Relationship |
|---|---|
| `software-engineering-hio-agent-framework` | The current human-readable registry becomes a generated artifact |
| All other repos | Each is a registry entry |

### Initial scoring targets

A: L5 from day one (registry is itself agent infrastructure). B: L4 (must reject untrusted writes; registry is high-trust surface).

### Cost to set up

- 1 week OI for schema and initial registry
- 1 week OI for generators
- 2-3 weeks for MCP server
- A2A Agent Cards deferred until the family includes runtime agents to be exposed

### Risks

| Risk | Mitigation |
|---|---|
| Two sources of truth (human markdown vs structured) drift | Make the structured source authoritative; markdown is generated, never hand-edited |
| Schema becomes ossified before the family stabilizes | Keep the schema permissive at first; tighten quarterly |
| Untrusted PRs to registry alter agent behavior across the family | Require SME OI sign-off on every registry PR; this is a sensitive surface |

---

## Proposal 3: `resonant-cognition-content` (renamed from `thoughtexperiments`)

### Gap

The current `thoughtexperiments` repo is in practice the home of the Resonant Cognition Framework's applied content (stories, applications, Tamil edition). The current name is exploratory and does not signal the content's purpose to either humans or agents.

### Why this is a rename, not a new repo

Not strictly a new repo; this is a proposal to rename and restructure for clarity:

- New name reflects content domain ("Resonant Cognition")
- Adds a `glossary/` directory mapping to canonical philosophical concepts in `thought-org-with-human-ai-hybrid` (where applicable) plus its own canonical terms (Resonance, Contraction, Null) that do not have direct HIO equivalents
- Restructures stories under a metadata-aware directory tree

### Cost to set up

- 1 day OI for rename + redirect
- 1-2 weeks OI for content restructuring

### Risks

| Risk | Mitigation |
|---|---|
| Inbound links break | Permanent redirect on the rename; document in `repo-registry.md` |
| Confusion in transition | Rename only after `AGENTS.md` is in place so agents can absorb the change |
| Implies tighter coupling to HIO than is intended | Glossary makes the kinship explicit but does not force vocabulary alignment |

---

## Proposal 4: `hio-templates` (deferred)

### Gap

The operational hub provides Jinja2 templates for Confluence/Jira generation, but these are tied to the operational hub's voice. As more domains adopt HIO, a separate templates repo with multi-domain templates becomes useful.

### Status

Deferred until at least two non-platform-engineering forks of the operational hub exist. Not actionable today.
