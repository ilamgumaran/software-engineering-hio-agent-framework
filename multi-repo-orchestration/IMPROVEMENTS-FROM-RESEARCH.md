# Improvements From Research

This document evaluates the multi-repo orchestration framework after surveying external research on agentic workflows. It is the second-PR companion to `PLAN.md` -- where PLAN explains the design that *was* shipped, this file explains what should change *next* and why, citing external sources.

---

## What was reviewed

| Source family | Detail |
|---|---|
| AGENTS.md as an open standard | `reference/agents-md-and-agentic-ai-foundation.md` |
| MCP and A2A protocols | `reference/agent-protocols-mcp-a2a.md` |
| Anthropic's 5 effective-agent patterns and multi-agent research system | `reference/anthropic-effective-agents-patterns.md` |
| Stanford HAI / Digital Economy Lab Centaur Evaluations | `reference/centaur-evaluations.md` |
| OWASP Top 10 for Agentic Applications 2026 | `reference/owasp-top-10-agentic-applications.md` |
| LangGraph, CrewAI, AutoGen, OpenAI Agents SDK, Google ADK, Anthropic Agent SDK, Magentic-One | `reference/multi-agent-frameworks-landscape.md` |
| SWE-bench, GAIA, TAU-bench, WebArena, HAL Reliability Dashboard | `reference/agent-benchmarks.md` |
| Constitutional AI (Anthropic), Deliberative Alignment (OpenAI), debate-based safety, multi-agent alignment | `reference/agent-alignment-research.md` |

---

## Self-evaluation of the first PR

What the first PR did well:

- Layered architecture (Strategic -> Generic -> Operational -> Domain content) is consistent with the Linux Foundation Agentic AI Foundation's split between methodology, protocols, and applications
- Two-axis scoring (agentic + security) avoids the common pitfall of collapsing safety into a single score
- Cognitive-function vocabulary survives intact -- no terminology was reinvented when external standards were available
- Per-repo `AGENTS.md` files are markdown-only, no frontmatter, compatible with the public AGENTS.md convention without change

Genuine gaps the first PR has, surfaced by the research:

| Gap | Source that surfaced it | Severity |
|---|---|---|
| Spec did not declare compatibility with public AGENTS.md | AAIF / agents.md | Medium -- silent compatibility, but explicit is better |
| Security rubric did not map to OWASP Top 10 for Agentic | OWASP 2026 | High -- industry standard exists; rubric should align |
| `hio-evals` proposal would have reinvented benchmarks | SWE-bench/GAIA/TAU-bench | High -- expensive duplication |
| No mention of Least-Agency principle | OWASP 2026 | Medium -- principle is named in the standard; framework should adopt the name |
| Framework was silent on MCP/A2A even though the central spec implies a registry agents would want to query | MCP, A2A, AAIF | Medium -- becomes acute when family scales |
| Routing matrix lacked academic backing for the human+AI team unit | Centaur Evaluations | Low -- adds rigor; not blocking |
| 6 HIO agent types were not mapped to Anthropic's 5 control-flow patterns | Anthropic Building Effective Agents | Low -- internal clarity |
| Cost-adjusted accuracy and N-run consistency missing from `metrics/ai-utilization.md` | 2026 benchmark trend | Low -- not blocking but production-relevant |
| Shared-constitution framing missing from governance | Constitutional AI, Deliberative Alignment | Low -- conceptual lift, not behavioral change |

---

## Improvements landed in this PR

### A. Spec compatibility with public AGENTS.md

- `multi-repo-orchestration/agent-spec/AGENTS-SPEC-v1.md` updated with a compatibility note (additive sections satisfy public AGENTS.md baseline)
- `multi-repo-orchestration/skills/repo-cartographer.md` validation step now includes a public-AGENTS.md compatibility check

### B. OWASP Top 10 mapping for the security axis

- `multi-repo-orchestration/scoring/scoring-rubric.md` B-axis level definitions updated with OWASP category cross-references
- `multi-repo-orchestration/governance/security-and-safety.md` updated with OWASP mapping table and explicit Least-Agency principle
- `multi-repo-orchestration/hio-collaboration/matrix.md` adds an Agent-to-Agent communication row (forces Interactive routing pending A2A signed-agent-card adoption)

### C. `hio-evals` refined to use existing benchmarks

- `multi-repo-orchestration/new-repos-proposed.md` refined to incorporate SWE-bench, GAIA, TAU2-bench as building blocks; multi-repo eval is the genuinely-new artifact

### D. MCP / A2A awareness

- `multi-repo-orchestration/tools/README.md` updated to note runtime-agnostic posture and MCP-implementability
- New-repo proposals updated to call out MCP/A2A surface where relevant

### E. Centaur Evaluations citation

- `multi-repo-orchestration/hio-collaboration/matrix.md` cites Centaur Evaluations as the academic foundation
- A future Centaur-style measurement is queued for `metrics/harmonization.md` (not changed in this PR; tracked here)

### F. Anthropic-pattern mapping

- New `reference/anthropic-effective-agents-patterns.md` carries the mapping; `agents/README.md` will get a sidebar in a follow-up if SMEs sign off

### G. Shared-constitution framing

- `multi-repo-orchestration/governance/security-and-safety.md` opens with the framing that the security policy + matrix + AGENTS.md family act as a shared constitution for agents in the family

---

## Improvements deliberately deferred to a third PR (or later)

| Improvement | Why deferred |
|---|---|
| Centaur-style measurement instrument added to `metrics/harmonization.md` | Requires SME design choices about which tasks to use as the measurement set |
| HAL dimensions (consistency, predictability, robustness, safety, self-awareness) added to `metrics/ai-utilization.md` | Requires SME calibration of thresholds |
| Anthropic-pattern sidebar added to `agents/README.md` | The 5 patterns describe control flow; existing 6 agents describe role -- sidebar is helpful but not load-bearing |
| MCP server implementations of the three tool specs | Implementation work, not spec work |
| A2A signed-agent-card adoption when family includes runtime agents | No runtime agents in family yet |
| Re-scoring after these changes land | Quarterly cadence per `governance/sme-update-workflow.md` |

---

## Updated baseline scores after this PR

Projected post-merge scores (will be re-run as a Type A change at the next quarterly cadence):

| Repo | Agentic before | Agentic after | Security before | Security after |
|---|---|---|---|---|
| `software-engineering-hio-agent-framework` | L4 | L4 (no change; further lift requires CI validation) | L3 | L4 (OWASP mapping + Least-Agency) |
| `software-engineer-core-structure` | L3 | L3 | L3 | L3 (framework changes inherited at next instantiation) |
| `thought-org-with-human-ai-hybrid` | L2 | L2 | L2 | L3 (governance reuse) |
| `thoughtexperiments` | L1 | L1 | L2 | L2 (no change; per-repo work needed) |

---

## What the user gets in concrete terms

Before: a self-contained framework, internally consistent, but not aligned to industry standards.

After: the same framework, **explicitly compatible with**:

- The public AGENTS.md convention (any of Codex, Cursor, Windsurf, Kilo, Factory, Builder agents read our files as orientation)
- OWASP Top 10 for Agentic Applications 2026 (security scoring uses the same vocabulary as the industry standard)
- MCP and A2A (the registry can become an MCP resource; agents in the family can become A2A-discoverable)
- Stanford Centaur Evaluations (the routing matrix has academic backing)
- Anthropic's effective-agent patterns and Microsoft's Magentic-One orchestrator-worker model (the agent topology is named, not implicit)
- SWE-bench, GAIA, TAU-bench, WebArena, HAL (the eval proposal uses standard benchmarks plus one new multi-repo eval)

---

## Sign-off

- [ ] SME framework owner: ___
- [ ] Security reviewer: ___
- [ ] Date signed: ___
