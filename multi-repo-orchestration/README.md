# Multi-Repo Orchestration Framework

A cross-repo agent framework for the HIO repo family. Lets any coding agent (or SME) walk into any one of the four sibling repos and trace context, dos and don'ts, scoring, and HIO collaboration boundaries back to a single source of truth -- this directory.

**Home:** This directory is the central spec. The other repos in the family carry a lightweight `AGENTS.md` at root that points here.

---

## Why this exists

The HIO family currently spans four repos with overlapping but distinct purposes. Without a shared spec, every coding agent (Claude Code, Copilot, Gemini, internal SDK agents, future agents) has to re-discover the relationships, the rules, and the safety boundaries each time. SMEs editing one repo cannot easily push the same change across the others.

This framework solves three problems at once:

1. **Discoverability** -- any agent can find the related repos and the role each plays in under 30 seconds
2. **Governance** -- dos and don'ts, security boundaries, and HIO collaboration rules are codified per repo, not folklore
3. **Scaling** -- the same spec format scales to hundreds of repos; SMEs maintain the spec, agents follow it

---

## What's in this directory

| Path | Purpose |
|---|---|
| `README.md` | This file -- entry point and navigation |
| `PLAN.md` | The plan and design that produced this framework |
| `PROMPT.md` | The original user prompt and the meta-prompt for regeneration |
| `repo-registry.md` | Catalog of all repos in the family with cross-links |
| `agent-spec/AGENTS-SPEC-v1.md` | The standardized AGENTS.md format every repo follows |
| `agent-spec/traceability-protocol.md` | How agents follow links between repos safely |
| `scoring/` | Rubric and per-repo scorecards (agentic readiness + security) |
| `dos-and-donts/` | Universal and per-repo prompt-author guidance |
| `hio-collaboration/` | OI / II / Interactive routing matrix per repo |
| `skills/` | Agent skills usable across the family (cartographer, tracer, classifier, scorer) |
| `tools/` | Lightweight tool specs (CLI-style) for cross-repo operations |
| `prompts/` | Prompts for onboarding, scoring, classifying, and proposing |
| `new-repos-proposed.md` | New repos recommended to round out the family |
| `governance/` | SME workflow, change management, security and safety |

---

## How to read this in 10 minutes

1. `repo-registry.md` -- understand the four repos and how they relate
2. `scoring/summary.md` -- comparative agentic + security scores across the family
3. `agent-spec/AGENTS-SPEC-v1.md` -- the contract every repo follows
4. `hio-collaboration/matrix.md` -- when a human reviews vs an agent acts vs they collaborate
5. `governance/sme-update-workflow.md` -- how this stays maintained

---

## How to use this as an agent

If you are an AI agent (Claude Code, Copilot Chat, Gemini, custom SDK agent) entering any repo in the family:

1. Read `AGENTS.md` at the repo root for repo-specific rules
2. Follow the link to this directory (`multi-repo-orchestration/`) for cross-repo context
3. Apply the dos and don'ts in `dos-and-donts/per-repo-<name>.md`
4. Classify your task using `hio-collaboration/matrix.md`
5. Stop and ask a human if your task lands in the **Organic Intelligence** column or any irreversible row

See `agent-spec/traceability-protocol.md` for the full lifecycle.

---

## How to use this as an SME

If you are a subject-matter expert maintaining one or more repos in the family:

1. Update `AGENTS.md` in your repo when scope, ownership, or rules change
2. Bump the spec version in `agent-spec/AGENTS-SPEC-v1.md` if the contract itself changes
3. Re-run `skills/agentic-scorer.md` quarterly and update the scorecard
4. Add new repos via `governance/sme-update-workflow.md`

SMEs are the source of truth. Agents read; SMEs write the rules agents read.

---

## Relationship to existing framework files

This directory does not replace anything in the parent repo. It composes on top of:

| Existing | Role | This directory |
|---|---|---|
| `agents/` | 6 HIO agent type definitions (intra-repo) | Adds inter-repo orchestration layer |
| `cognitive-functions/` | 10 modes of human-AI engagement | Reused unchanged in HIO collaboration matrix |
| `prompts/` | Framework regeneration prompts | Adds prompts specific to multi-repo work |
| `tools/` | Per-tool guides (Claude Code, Copilot, Gemini) | Adds tool-agnostic cross-repo operations |
| `reference/agent-engineering-7-skills.md` | 7 technical capabilities | Used as the security and reliability axis of scoring |

If any existing file conflicts with a rule here, the existing file wins for its scope; this framework wins for cross-repo concerns.

---

## License

MIT, same as the parent repo.
