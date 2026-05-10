# Proposed New Repos

Repos recommended to round out the family. Each proposal is a draft for SME review; nothing here is created automatically.

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

## Proposal 1: `hio-evals`

### Gap

Agents in the family act on documents and code, but the family has no shared evaluation harness for agent outputs (correctness of generated AGENTS.md, scorecards, classifications, recommendations). Without evals, scoring drifts and improvements are unmeasurable.

### Why existing repos cannot absorb

- `software-engineering-hio-agent-framework` already hosts the framework; eval harnesses are runtime-shaped (test code, fixtures, telemetry) and would distort the doc-shape of that repo
- `software-engineer-core-structure` is intentionally domain-agnostic; HIO-specific evals would couple it to HIO
- `thought-org-with-human-ai-hybrid` is methodology, not engineering
- `thoughtexperiments` is content, not infrastructure

### What it owns

- Eval datasets for the four core agent skills (cartographer, tracer, classifier, scorer)
- A runtime harness that can replay tasks against any agent runtime and measure pass rates
- Quarterly leaderboard of agent performance

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

- 1-2 weeks OI to scaffold; 4-6 weeks to populate the four core skill eval sets to a baseline coverage
- Dependencies: secure runtime sandbox (Docker, Kubernetes job, or equivalent)

### Risks

| Risk | Mitigation |
|---|---|
| Eval set captures current agent behavior, not desired behavior -- locks in regressions | Pair every eval with a desired-outcome rationale reviewed by SME |
| Harness runtime requires secrets -- security blast radius | Sandbox the harness; no secret access from agent code paths |
| Evals become overhead nobody runs | Wire to PR CI as a quarterly gate (not per-PR; would be too slow) |

---

## Proposal 2: `agent-spec-registry`

### Gap

The family currently catalogues itself in markdown (`repo-registry.md`). As the family grows past ~20 repos, machine-readable registries become necessary for tools (link validators, scorecard runners, MCP servers) to operate at scale.

### Why existing repos cannot absorb

The current markdown catalog is human-shaped and authoritative; a parallel YAML or JSON catalog would create a maintenance fork. A separate repo solves this by making the machine-readable form the source of truth and generating the markdown view.

### What it owns

- A YAML or JSON registry of repos: identity, layer, owners, sensitivity tier, trace links
- A schema for the registry
- Generators that emit the human-readable `repo-registry.md` from the structured source
- An MCP server (optional) that exposes the registry to any agent runtime

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
- 2-3 weeks for MCP server (optional, deferred)

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
