# Repo Registry

The canonical catalog of repos in the HIO family. Agents read this first to understand who is who.

---

## Family at a glance

| Repo | Layer | Primary Purpose | Audience | Status |
|---|---|---|---|---|
| [`thought-org-with-human-ai-hybrid`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid) | Strategic | HIO methodology, philosophy, principles, transformation playbooks | Leaders, framework authors | Active |
| [`software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure) | Generic framework | 9-role engineering agent framework, domain-agnostic | Engineering leads, agent builders | Active |
| [`software-engineering-hio-agent-framework`](https://github.com/ilamgumaran/software-engineering-hio-agent-framework) | Operational | HIO operationalized: 10 functions, 6 agents, 5 units, 26-week transformation | Engineering orgs adopting HIO | Active, primary host of this framework |
| [`thoughtexperiments`](https://github.com/ilamgumaran/thoughtexperiments) | Domain content | Resonant Cognition Framework: stories, applications, Tamil edition | Educators, researchers, parents | Active |

---

## Layer dependencies

```
thought-org-with-human-ai-hybrid    (strategic, free-standing)
          |
          v informs
software-engineer-core-structure    (generic, free-standing)
          |
          v extends
software-engineering-hio-agent-framework  (operational hub)
          |
          v applies-to / governs
thoughtexperiments + future repos
```

The operational hub is where this multi-repo orchestration framework lives.

---

## Per-repo profile

### thought-org-with-human-ai-hybrid

- **Identity:** Harmonized Intelligence Orchestration framework -- the philosophical and strategic source
- **Primary content:** `framework.md`, `proposals/`, `examples/platform-engineering-org/`, `reference/`
- **Key concepts owned here:** Organic / Inorganic intelligence definitions, the 4 HIO Tests, cognitive ecosystem, emergence
- **Build artifacts:** None (it's a documentation repo)
- **Public website:** Yes (HTML pages: `index.html`, `tldr.html`, `next-steps.html`)
- **Sensitive surfaces:** None (public, MIT)
- **Trace to:** `software-engineering-hio-agent-framework` (operationalization)

### software-engineer-core-structure

- **Identity:** Multi-Role Software Engineering Agent Framework -- generic, forkable
- **Primary content:** `roles/`, `domains/`, `plan/`, `tools/`, `prompts/`
- **Key concepts owned here:** 9 fixed roles, domain extension system, 7-phase implementation
- **Build artifacts:** Future `agent-core/` (planned)
- **Public website:** No
- **Sensitive surfaces:** Reference implementation guidance for AI tools and policies
- **Trace to:** `software-engineering-hio-agent-framework` (HIO superset), domain-specific forks

### software-engineering-hio-agent-framework

- **Identity:** HIO operationalized for platform engineering; hosts this multi-repo framework
- **Primary content:** `cognitive-functions/`, `agents/`, `cognitive-units/`, `workflows/`, `metrics/`, `transformation/`, `multi-repo-orchestration/` (this dir)
- **Key concepts owned here:** 10 cognitive functions, 6 AI agent types, 5 cognitive units, 9 metric categories, 26-week transformation
- **Build artifacts:** Future `agent-core/`, `docs/`, `config/`
- **Public website:** No
- **Sensitive surfaces:** AI agent configuration (`CLAUDE.md`), policies (`org/policies.md`), this multi-repo spec
- **Trace to:** `thought-org-with-human-ai-hybrid` (upstream methodology), `software-engineer-core-structure` (upstream generic framework)

### thoughtexperiments

- **Identity:** Resonant Cognition Framework -- applied content for children and adults
- **Primary content:** HTML applications and stories, `TODO.md` roadmap, `thinking-without-boundaries-the-stories/`
- **Key concepts owned here:** Resonance, contraction (↓), Null (Ø), strings/bells metaphors, identity oscillation
- **Build artifacts:** None (static HTML)
- **Public website:** Yes (`index.html`)
- **Sensitive surfaces:** Content addresses children, trauma, neurodivergence -- safety boundaries critical
- **Trace to:** `thought-org-with-human-ai-hybrid` (philosophical kinship), no direct dependency

---

## Cross-repo relationships

| From | To | Relationship | Where this is encoded |
|---|---|---|---|
| HIO agent framework | thought-org HIO | "Built on" -- methodology source | README.md "Foundation" section |
| HIO agent framework | core structure | "Built on" -- generic predecessor | README.md "Also built on" |
| HIO agent framework | thoughtexperiments | Governs (via this multi-repo framework) | This file + `AGENTS.md` in target |
| thought-org HIO | examples/platform-engineering-org | "Operationalized by" | README "How this was made" |
| core structure | (any domain fork) | "Forked-by" pattern | CUSTOMIZATION.md scaling section |
| thoughtexperiments | thought-org HIO | Conceptual kinship (independent) | Not encoded yet -- proposal in `new-repos-proposed.md` |

---

## Vocabulary mapping

Different repos use different vocabulary for similar concepts. Agents should not assume terms collide.

| Concept | thought-org HIO | core structure | HIO agent framework | thoughtexperiments |
|---|---|---|---|---|
| Person doing work | "organic intelligence" | "team member" | "engineer" + cognitive functions | "observer" / "child" |
| AI doing work | "inorganic intelligence" | "the agent" / role | one of 6 agent types | n/a (content-only) |
| Unit of organization | "cognitive ecosystem" | "team" | "cognitive unit" | n/a |
| Goal | "purpose" | "task" / "requirement" | "outcome" | "resonance" |
| Failure | n/a | "bug" / "defect" | "regression" / "emergence-negative" | "interference" |

When working across repos, translate explicitly. See `agent-spec/traceability-protocol.md` step 3.

---

## Adding a new repo to the family

1. Open an issue in `software-engineering-hio-agent-framework` titled `Family addition: <repo name>`
2. Provide the per-repo profile fields above
3. Run the meta-prompt in `PROMPT.md` to scaffold the new repo's `AGENTS.md`
4. Score the new repo using `skills/agentic-scorer.md`
5. Add a row here, in `scoring/summary.md`, and in `hio-collaboration/per-repo-routing.md`
6. SME approval required before merging

See `governance/sme-update-workflow.md` for the full process.
