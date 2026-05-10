# Original Prompt and Meta-Prompt

This file preserves the user request that produced this framework, and provides a self-contained meta-prompt that can regenerate the framework in a fresh repo or for a different family of repos.

---

## Original user request (verbatim)

> Agents and skills - We are going to explore how to setup agents and skills based on the repo, overall team objectives and needs.
>
> Look at all these repos and develop a framework under the suitable repo with structured prompts instructions skills and tools to understand the needs and enhance each repo with such specs agents and tools so any coding agent looking at the repo can trace to related repo and understand the context to make changes. This will also help SMEs to enhance them in the agent and keep hundreds of repos updated automatically. I want a comprehensive scoring for each repos support for agentic including security. So we should first explain dos and don'ts of such prompts per repo so agents who build them will be knowledgeable and using HIO recommend what organic intelligence can review and what inorganic intelligence should take care and where interactive collaboration is needed. If new repos are needed suggest. Store all the plan design and prompt for this work also in the relevant repo

---

## Distilled requirements

| Requirement | Where it is satisfied |
|---|---|
| Cross-repo traceability for any coding agent | `agent-spec/`, `repo-registry.md`, per-repo `AGENTS.md` |
| SMEs can maintain at scale | `governance/sme-update-workflow.md` |
| Comprehensive scoring including security | `scoring/` |
| Per-repo dos and don'ts of prompts | `dos-and-donts/` |
| HIO routing -- OI vs II vs Interactive | `hio-collaboration/` |
| New repo suggestions | `new-repos-proposed.md` |
| Plan, design, and prompts stored in the repo | `PLAN.md`, `README.md`, this file, `prompts/` |

---

## Meta-prompt for regeneration

Use the following prompt with a reasoning-capable agent that has access to the repo family. Replace the bracketed placeholders for a different family of repos.

```
You are setting up a multi-repo orchestration framework for an [ORG/TEAM]
family of [N] repos: [list repos with one-line descriptions].

Goals:
1. Any coding agent entering any repo can find context in related repos in <30s
2. SMEs can maintain agent rules across all repos with one-place edits
3. Every repo has a security and agentic-readiness score
4. Every repo has explicit dos/don'ts for prompt authors
5. Every repo task is classifiable into Organic Intelligence (human review),
   Inorganic Intelligence (agent autonomous), or Interactive Collaboration
6. New repos are proposed if gaps exist in the family

Deliverables, all stored under multi-repo-orchestration/ in the operational hub repo:
- README.md, PLAN.md, PROMPT.md (this file)
- repo-registry.md cataloging the family
- agent-spec/AGENTS-SPEC-v1.md and traceability-protocol.md
- scoring/ with rubric, per-repo scorecards, summary
- dos-and-donts/ with universal and per-repo guidance
- hio-collaboration/ with master matrix and per-repo routing
- skills/ for cross-repo agent skills
- tools/ and prompts/ for cross-repo operations
- new-repos-proposed.md
- governance/ with SME workflow and security-and-safety policy

In each non-hub repo, add a single AGENTS.md at root that:
- States repo identity, purpose, related repos
- Links back to the central framework
- Lists key dos and don'ts and security boundaries
- Has the HIO routing summary

Follow the existing parent-repo style: pure markdown, no YAML frontmatter,
tables with 3+ rows, Organization Extension Point markers, cross-references.
Reuse the 10 cognitive functions, 6 agent types, and 7 agent-engineering
capabilities already defined in the framework.

Produce all files in a single feature branch named claude/agent-framework-setup-<id>.
```

---

## Companion prompts in this directory

This meta-prompt orchestrates the whole framework. For more focused regeneration tasks, use:

| Prompt | Purpose |
|---|---|
| `prompts/repo-onboarding.md` | An agent picks up an unfamiliar repo in the family |
| `prompts/score-a-repo.md` | Re-score a repo against the rubric |
| `prompts/classify-task-hio.md` | Classify a task as OI / II / Interactive |
| `prompts/propose-new-repo.md` | Propose a new repo with rationale |

---

## When to re-run this prompt

- A new repo joins the family and the registry needs a refresh
- The agent-engineering capabilities reference is updated upstream
- The HIO methodology document materially changes
- Quarterly review surfaces a structural gap

Incremental edits do not require regeneration. Use the focused prompts in `prompts/` instead.
