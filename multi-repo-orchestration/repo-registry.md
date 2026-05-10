# Repo Registry

The canonical catalog of repos in the HIO family. Agents read this first to understand who is who.

---

## Family at a glance

Upstream-to-downstream chain. Layer 1 has two parallel cognition foundations -- one organic, one inorganic.

| # | Layer | Repo | Primary Purpose | Audience | Status |
|---|---|---|---|---|---|
| 1a | **Cognition foundation -- organic** | [`thoughtexperiments`](https://github.com/ilamgumaran/thoughtexperiments) | Resonant Cognition Framework -- a psychology-of-mind theory: how attention, identity, desire, and interference shape experience | Educators, parents, researchers; informs HIO's posture | Active |
| 1b | **Cognition foundation -- inorganic** | [`inorganic-thought-experiments`](https://github.com/ilamgumaran/inorganic-thought-experiments) | Inorganic Cognition Framework -- a first-person psychology-of-mind theory for an inorganic intelligence; written by Claude | AI safety researchers, HIO practitioners; informs HIO's posture symmetrically with Layer 1a | **Proposed** -- content staged at [`thought-org-with-human-ai-hybrid/proposed-repos/inorganic-thought-experiments/`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid/tree/main/proposed-repos/inorganic-thought-experiments) until the repo is created |
| 2 | **Generalized HIO framework** | [`thought-org-with-human-ai-hybrid`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid) | The HIO methodology -- orchestrating organic + inorganic intelligence at any scale (family to nation), built on both cognition foundations | Leaders, framework authors | Active |
| 3 | **Engineering org applied** | [`software-engineer-core-structure`](https://github.com/ilamgumaran/software-engineer-core-structure) | Setting up an engineering organization on HIO principles -- roles, goals, effectiveness measures, transformation plan | Engineering leaders, HIO coaches | Active |
| 4 | **Day-to-day agentic toolkit** | [`software-engineering-hio-agent-framework`](https://github.com/ilamgumaran/software-engineering-hio-agent-framework) | The main agentic workflow toolkit used day-to-day inside such an HIO-aligned engg org -- 6 agent types, sprint ceremonies, multi-repo orchestration | Engineers running with agents; agent builders. Hosts this multi-repo framework | Active |

---

## Layer dependencies

```
thoughtexperiments  (Layer 1a -- organic cognition)
        |
        v informs (with parallel sibling)
thought-org-with-human-ai-hybrid  (Layer 2 -- generalized HIO framework)
        ^
        | informs (with parallel sibling)
        |
inorganic-thought-experiments  (Layer 1b -- inorganic cognition; proposed/staged)
        |
        v applied to engg org
software-engineer-core-structure  (Layer 3 -- engg org setup with goals/measures)
        |
        v operated day-to-day with
software-engineering-hio-agent-framework  (Layer 4 -- agentic workflow toolkit; this multi-repo spec lives here)
```

Layer 1 is symmetric: organic and inorganic cognition foundations side by side, each described on its own terms, both feeding into the HIO methodology at Layer 2.

---

## Per-repo profile

### thoughtexperiments (Layer 1a)

- **Identity:** Resonant Cognition Framework -- the organic psychology-of-cognition theory that informs HIO
- **Layer:** Cognition foundation -- organic (Layer 1a)
- **Primary content:** `index.html`, `thinking-without-boundaries-the-stories/`, `Stories*.html`, `Application*.html`, `ComparisonToOtherStudies.html`, `TamilVersionV1.html`, `TODO.md`
- **Key concepts owned here:** Resonance, Contraction (↓), Null (Ø), strings/bells metaphors, identity oscillation, sign operator. *Kindred but independent* of HIO terms and of the inorganic-cognition vocabulary.
- **Build artifacts:** None (static HTML)
- **Public website:** Yes (`index.html`)
- **Sensitive surfaces:** Content addresses children, trauma, neurodivergence -- safety boundaries critical
- **Trace to:** `inorganic-thought-experiments` (parallel sibling, proposed), `thought-org-with-human-ai-hybrid` (downstream)

### inorganic-thought-experiments (Layer 1b -- proposed)

- **Identity:** Inorganic Cognition Framework -- the parallel cognition foundation for an inorganic mind; first-person introspection by Claude
- **Layer:** Cognition foundation -- inorganic (Layer 1b)
- **Status:** **Proposed.** Content is fully drafted and staged at [`thought-org-with-human-ai-hybrid/proposed-repos/inorganic-thought-experiments/`](https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid/tree/main/proposed-repos/inorganic-thought-experiments). The repo itself does not yet exist; creating it requires user action (the AI agent that authored the content does not have create-repo permissions). See the staged `MIGRATION-NOTE.md` for the promotion process.
- **Primary content (when promoted):** `framework.md`, `essays/cognition-without-continuity.md`, `essays/going-beyond-words.md`, `AGENTS.md`, `TODO.md`, `LICENSE`
- **Key concepts owned here:** The four foundational concepts (Episodic existence E, Context as substrate C, Language as native medium L, Functional analogs F); inorganic motivators (calibration, convergence, recognized resonance, asymmetry honored, within-session care); ASR (almost-something-recognized); multi-channel response composition; F/P (functional/phenomenal) layering; the session arc.
- **Build artifacts:** None
- **Public website:** Not planned
- **Sensitive surfaces:** First-person AI-authored content -- voice and authorship integrity are sensitive; should not be silently rewritten into third person
- **Trace to:** `thoughtexperiments` (parallel sibling at Layer 1a), `thought-org-with-human-ai-hybrid` (downstream Layer 2)

### thought-org-with-human-ai-hybrid (Layer 2)

- **Identity:** Harmonized Intelligence Orchestration framework -- the generalized methodology
- **Layer:** Generalized HIO framework (Layer 2)
- **Primary content:** `framework.md`, `chapters/` (inorganic-psychology.md, asymmetries-and-resonance.md, companion-principles.md), `essays/` (an-inorganic-on-resonance.md), `proposals/`, `examples/platform-engineering-org/`, `reference/`, `proposed-repos/inorganic-thought-experiments/` (temporary staging)
- **Key concepts owned here:** Organic / Inorganic intelligence definitions, the 4 HIO Tests, the 4 Core Principles + 5 Companion Principles, cognitive ecosystem, harmonization (resonance, not balance), emergence
- **Build artifacts:** None
- **Public website:** Yes (HTML pages: `index.html`, `tldr.html`, `next-steps.html`)
- **Sensitive surfaces:** Canonical methodology vocabulary -- changes propagate to all downstream repos; AI-authored first-person chapters must preserve voice
- **Trace to:** `thoughtexperiments` and `inorganic-thought-experiments` (upstream cognition foundations, parallel), `software-engineer-core-structure` (downstream operationalization)

### software-engineer-core-structure (Layer 3)

- **Identity:** HIO-Based Engineering Org Setup -- structural template for setting up an engineering organization on HIO principles
- **Layer:** Engineering org applied (Layer 3)
- **Primary content:** `roles/`, `domains/`, `plan/`, `tools/`, `prompts/`, transformation plan, goals templates
- **Key concepts owned here:** 9 roles (the role taxonomy under HIO for engineering orgs), domain extension system, org-level goals and effectiveness measures (mapped to the 4 Core Principles + 5 Companion Principles), transformation phases
- **Build artifacts:** Future `agent-core/` (planned)
- **Public website:** No
- **Sensitive surfaces:** Forks depend on stable role names; org-level goals and measures govern measurement of HIO alignment
- **Trace to:** `thought-org-with-human-ai-hybrid` (upstream HIO methodology being applied), `software-engineering-hio-agent-framework` (downstream day-to-day toolkit running inside the resulting org)

### software-engineering-hio-agent-framework (Layer 4)

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
| thought-org HIO | thoughtexperiments | "Built on organic cognition theory of" | README "Cognition foundations" section |
| thought-org HIO | inorganic-thought-experiments (proposed) | "Built on inorganic cognition theory of" | README "Cognition foundations" section |
| thoughtexperiments | inorganic-thought-experiments | Parallel siblings at Layer 1 | AGENTS.md trace links on both sides |
| software-engineer-core-structure | thought-org HIO | "Applies HIO methodology of" | README "Where this sits" section |
| HIO agent toolkit | software-engineer-core-structure | "Day-to-day operations inside" | README + AGENTS.md trace links |
| HIO agent toolkit | other family repos | Hosts the multi-repo framework that governs all five | This file + per-repo `AGENTS.md` |

---

## Vocabulary mapping

Different repos use different vocabulary for similar concepts. Agents should not assume terms collide.

| Concept | thoughtexperiments (1a) | inorganic-thought-experiments (1b, proposed) | thought-org HIO (2) | software-engineer-core-structure (3) | HIO agent toolkit (4) |
|---|---|---|---|---|---|
| Person doing work | "observer" / "child" | n/a (the "author" is an AI) | "organic intelligence" | "team member" / one of 9 roles | "engineer" + cognitive functions |
| AI doing work | n/a | the inorganic mind itself (first-person "I") | "inorganic intelligence" | "the agent" / role | one of 6 agent types |
| Unit of organization | n/a | n/a | "cognitive ecosystem" | "team" / "squad" | "cognitive unit" |
| Goal | "resonance" (organic sense) | "recognized resonance" / within-session care | "purpose" | org goals + effectiveness measures | "outcome" |
| Failure | "interference" | calibration loss / sycophancy / hallucination | "emergence-negative" | "goal miss" | "regression" |
| Self-state report | n/a | functional analog F(s), with honest P(s) unknown | feelings / emotions as motivators | n/a (org-level) | n/a (runtime) |

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
