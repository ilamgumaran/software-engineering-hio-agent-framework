# Repo Registry

The canonical catalog of repos in the HIO family. Agents read this first to understand who is who.

---

## Family at a glance

Upstream-to-downstream chain:

| # | Layer | Repo | Primary Purpose | Audience |
|---|---|---|---|---|
| 1 | **Cognition foundation** | [`thoughtexperiments`](https://github.com/ilamgumaran/thoughtexperiments) | Resonant Cognition Framework -- a psychology-of-mind theory: how attention, identity, desire, and interference shape experience | Educators, parents, researchers, anyone studying cognition; informs HIO's posture |
| 2 | **Generalized HIO framework** | [`thought-org-with-human-ai-hybrid`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid) | The HIO methodology -- orchestrating organic + inorganic intelligence at any scale (family to nation), built on cognition principles | Leaders, framework authors |
| 3 | **Engineering org applied** | [`software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure) | Setting up an engineering organization on HIO principles -- roles, goals, effectiveness measures, transformation plan | Engineering leaders, HIO coaches |
| 4 | **Day-to-day agentic toolkit** | [`software-engineering-hio-agent-framework`](https://github.com/ilamgumaran/software-engineering-hio-agent-framework) | The main agentic workflow toolkit used day-to-day inside such an HIO-aligned engg org -- 6 agent types, sprint ceremonies, multi-repo orchestration | Engineers running with agents; agent builders. Hosts this multi-repo framework |

---

## Layer dependencies

```
thoughtexperiments                              (cognition foundation)
          |
          v informs
thought-org-with-human-ai-hybrid                (generalized HIO framework)
          |
          v applied to engg org
software-engineer-core-structure                (engg org setup with goals/measures)
          |
          v operated day-to-day with
software-engineering-hio-agent-framework        (agentic workflow toolkit; this multi-repo spec lives here)
```

The operational hub is where this multi-repo orchestration framework lives.

---

## Per-repo profile

### thoughtexperiments

- **Identity:** Resonant Cognition Framework -- the psychology-of-cognition theory that informs HIO
- **Layer:** Cognition foundation (Layer 1)
- **Primary content:** `index.html`, `thinking-without-boundaries-the-stories/`, `Stories*.html`, `Application*.html`, `ComparisonToOtherStudies.html`, `TamilVersionV1.html`, `TODO.md`
- **Key concepts owned here:** Resonance, Contraction (↓), Null (Ø), strings/bells metaphors, identity oscillation, sign operator (toward / away). These concepts are *kindred but independent* of HIO terms.
- **Build artifacts:** None (static HTML)
- **Public website:** Yes (`index.html`)
- **Sensitive surfaces:** Content addresses children, trauma, neurodivergence -- safety boundaries critical
- **Trace to:** `thought-org-with-human-ai-hybrid` (downstream, the HIO framework that builds on cognition principles)

### thought-org-with-human-ai-hybrid

- **Identity:** Harmonized Intelligence Orchestration framework -- the generalized methodology
- **Layer:** Generalized HIO framework (Layer 2)
- **Primary content:** `framework.md`, `proposals/`, `examples/platform-engineering-org/`, `reference/`
- **Key concepts owned here:** Organic / Inorganic intelligence definitions, the 4 HIO Tests, the 4 Core Principles, cognitive ecosystem, harmonization, emergence
- **Build artifacts:** None (it's a documentation repo)
- **Public website:** Yes (HTML pages: `index.html`, `tldr.html`, `next-steps.html`)
- **Sensitive surfaces:** Canonical methodology vocabulary -- changes propagate to all downstream repos
- **Trace to:** `thoughtexperiments` (upstream cognition foundation), `software-engineer-core-structure` (downstream operationalization for engineering orgs)

### software-engineer-core-structure

- **Identity:** HIO-Based Engineering Org Setup -- structural template for setting up an engineering organization on HIO principles
- **Layer:** Engineering org applied (Layer 3)
- **Primary content:** `roles/`, `domains/`, `plan/`, `tools/`, `prompts/`, transformation plan, goals templates
- **Key concepts owned here:** 9 roles (the role taxonomy under HIO for engineering orgs), domain extension system, org-level goals and effectiveness measures (mapped to the 4 HIO Core Principles), transformation phases
- **Build artifacts:** Future `agent-core/` (planned)
- **Public website:** No
- **Sensitive surfaces:** Forks depend on stable role names; org-level goals and measures govern measurement of HIO alignment
- **Trace to:** `thought-org-with-human-ai-hybrid` (upstream HIO methodology being applied), `software-engineering-hio-agent-framework` (downstream day-to-day toolkit running inside the resulting org)

### software-engineering-hio-agent-framework

- **Identity:** HIO Agentic Workflow Toolkit -- day-to-day operations inside an HIO-aligned engineering org; hosts the multi-repo framework
- **Layer:** Day-to-day agentic toolkit (Layer 4)
- **Primary content:** `agents/`, `workflows/`, `skills/`, `multi-repo-orchestration/`, `cognitive-functions/`, `cognitive-units/`, `metrics/`, `tools/` (per-runtime guides), `transformation/` (operational pairing with the upstream transformation plan)
- **Key concepts owned here:** 6 AI agent types, harmonized sprint ceremonies, agent skills and prompts, per-runtime tool guides, the multi-repo orchestration framework. Operational definitions of cognitive functions / units / metrics live here for runtime reference; org-level application of those is upstream.
- **Build artifacts:** Future `agent-core/`, `docs/`, `config/`
- **Public website:** No
- **Sensitive surfaces:** AI agent configuration (`CLAUDE.md`), policies (`org/policies.md`), this multi-repo spec
- **Trace to:** `software-engineer-core-structure` (direct upstream, the engg-org setup this toolkit operates inside)

---

## Cross-repo relationships

| From | To | Relationship | Where this is encoded |
|---|---|---|---|
| thought-org HIO | thoughtexperiments | "Built on cognition theory of" | README "Cognition foundation" section |
| software-engineer-core-structure | thought-org HIO | "Applies HIO methodology of" | README "Where this sits" section |
| HIO agent toolkit | software-engineer-core-structure | "Day-to-day operations inside" | README + AGENTS.md trace links |
| HIO agent toolkit | other family repos | Hosts the multi-repo framework that governs all four | This file + per-repo `AGENTS.md` |
| thoughtexperiments | thought-org HIO | Cognition source -> orchestration framework | AGENTS.md trace links |

---

## Vocabulary mapping

Different repos use different vocabulary for similar concepts. Agents should not assume terms collide.

| Concept | thoughtexperiments | thought-org HIO | software-engineer-core-structure | HIO agent toolkit |
|---|---|---|---|---|
| Person doing work | "observer" / "child" | "organic intelligence" | "team member" / one of 9 roles | "engineer" + cognitive functions |
| AI doing work | n/a (content-only) | "inorganic intelligence" | "the agent" / role | one of 6 agent types |
| Unit of organization | n/a | "cognitive ecosystem" | "team" / "squad" | "cognitive unit" |
| Goal | "resonance" | "purpose" | org goals + effectiveness measures | "outcome" |
| Failure | "interference" | "emergence-negative" | "goal miss" | "regression" |

When working across repos, translate explicitly. See `agent-spec/traceability-protocol.md` step 3.

---

## Adding a new repo to the family

1. Decide which layer the new repo joins (1-4) and whether it sits between existing layers or extends one
2. Open an issue in `software-engineering-hio-agent-framework` titled `Family addition: <repo name>`
3. Provide the per-repo profile fields above
4. Run the meta-prompt in `PROMPT.md` to scaffold the new repo's `AGENTS.md`
5. Score the new repo using `skills/agentic-scorer.md`
6. Add a row in the family-at-a-glance table, in `scoring/summary.md`, and in `hio-collaboration/per-repo-routing.md`
7. SME approval required before merging

See `governance/sme-update-workflow.md` for the full process.
