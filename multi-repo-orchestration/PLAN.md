# Plan and Design

This document captures the plan, design rationale, and decision log behind the multi-repo orchestration framework. SMEs editing this framework should read this first to understand why it is shaped the way it is.

---

## Goal

Make every repo in the HIO family **agent-ready** and **cross-traceable** so that:

- Any coding agent walking into a single repo can locate context in the related repos
- SMEs can maintain agent guidance once and propagate it to hundreds of repos
- Security and HIO collaboration rules are explicit, scored, and enforceable
- New repos joining the family get the same scaffolding for free

---

## Design constraints

| Constraint | Implication |
|---|---|
| Cannot bloat individual repos | Per-repo footprint is a single `AGENTS.md` plus optional spec links |
| Must work with multiple agent runtimes | Spec is markdown only, no runtime-specific syntax |
| Must scale to hundreds of repos | Scorecards and dos/don'ts are templated; SME updates are batchable |
| Must respect HIO philosophy | Organic and inorganic intelligence are partners, not substitutes |
| Cannot create false security | Security scoring is honest about gaps; nothing here is a substitute for review |

---

## Key design decisions

### Decision 1: Central spec lives in `software-engineering-hio-agent-framework`

All three candidates were considered:

| Candidate | Pros | Cons |
|---|---|---|
| `thought-org-with-human-ai-hybrid` | Philosophical home of HIO | Strategic, not operational; would force operational content into a strategic repo |
| `software-engineer-core-structure` | Generic agent framework, domain-agnostic | Less integrated with HIO concepts; cross-repo work needs HIO vocabulary |
| `software-engineering-hio-agent-framework` | Operational hub; already imports both upstream concepts; has agents/, prompts/, tools/ scaffolding | Risk of further bloat |

**Chosen:** `software-engineering-hio-agent-framework` because it is the operational hub that already imports HIO concepts and has the agent vocabulary in place.

### Decision 2: Per-repo footprint is a single `AGENTS.md`

`AGENTS.md` is becoming a community convention for agent-readable repo specs. One file at root, links to this central directory, no nested directory in every sibling repo. Keeps each repo lean.

### Decision 3: Scoring uses two orthogonal dimensions

Agentic readiness and security are scored separately. A repo can score high on one and low on the other; conflating them hides risk. The scoring rubric uses a five-level scale (L1-L5) consistent with the existing `reference/agent-engineering-7-skills.md` readiness assessment.

### Decision 4: HIO collaboration is task-typed, not file-typed

A single file can have OI / II / Interactive zones simultaneously depending on the type of edit. We classify by **task signal** (refactor, bug fix, security review, content authoring, etc.) not by file extension. This avoids brittle path-based rules.

### Decision 5: Skills, prompts, and tools are siblings, not children

Following the parent repo's existing convention, this directory has its own `skills/`, `prompts/`, and `tools/` for multi-repo concerns. They do not extend or override the parent's intra-repo equivalents.

---

## Layering

```
+------------------------------------------+
|  thought-org-with-human-ai-hybrid        |  Strategic / philosophical
|  HIO methodology, principles, examples   |
+------------------------------------------+
              ^ informs
+------------------------------------------+
|  software-engineer-core-structure        |  Generic agent framework
|  9 roles, domains, plan, phases          |
+------------------------------------------+
              ^ extends
+------------------------------------------+
|  software-engineering-hio-agent-framework|  Operational HIO framework
|  10 functions, 6 agents, 5 units, etc.   |
|                                          |
|  multi-repo-orchestration/  <-- THIS     |  Cross-repo layer
+------------------------------------------+
              ^ applies-to
+------------------------------------------+
|  thoughtexperiments                      |  Domain content (Resonant Cognition)
|  Stories, applications, Tamil version    |
+------------------------------------------+
```

The cross-repo layer wraps the operational repo and addresses the other three plus any future siblings.

---

## Roll-out sequence

| Step | Action | Owner |
|---|---|---|
| 1 | Create `multi-repo-orchestration/` central spec (this work) | Inorganic agent + SME review |
| 2 | Add `AGENTS.md` to the three sibling repos | Inorganic agent + SME review |
| 3 | First scoring pass; record baseline | Inorganic agent (II) |
| 4 | SME review of scoring and dos/don'ts | Organic intelligence (OI) |
| 5 | Quarterly re-scoring | Inorganic agent + SME sign-off |
| 6 | Onboard new repos via `governance/sme-update-workflow.md` | SMEs |

---

## What was deliberately deferred

| Deferred | Why | When to revisit |
|---|---|---|
| Machine-readable scorecards (YAML/JSON) | Markdown is the lingua franca for current agents | When automated dashboards are needed |
| MCP server exposing repo registry | Not all agent runtimes use MCP | When MCP becomes universal in the org |
| Automatic re-scoring in CI | Requires per-repo CI investment | After 3+ scoring passes establish stability |
| Cross-repo PR coordinator agent | Higher-trust automation, needs eval harness | After eval harness exists |

---

## Open questions for SMEs

1. Should `AGENTS.md` be the canonical filename, or should we use `.agents/repo-spec.md` to allow richer per-repo agent config alongside?
2. Quarterly re-scoring -- who owns the calendar? Platform team, framework owner, or rotating?
3. When a sibling repo's `AGENTS.md` drifts from the central spec, who reconciles?
4. How do we want to version the spec itself when it changes? Semver, dates, or generation numbers?

These are intentionally left for human deliberation. See `governance/sme-update-workflow.md` for the discussion forum.
