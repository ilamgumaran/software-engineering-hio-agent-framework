# Example: New Platform Building — PromptOps Internal Platform MVP

> **Archetype**: New Platform / Greenfield
> **Tactical gain**: End ungoverned agent sprawl in 8 weeks. The company has 12 production AI agents running across teams, none with shared tracing, evals, or governance. Ship MVP "agent registry + tracing + eval gateway" so every new agent gets observability and governance for free.
> **Reversibility**: Mostly reversible. Decisions skew Pure-AI and Hybrid early; Pure-Human as the platform takes shape and external consumers commit.

---

## Scenario

The company has 12 AI agents in production across 6 teams (customer-support agent, billing-reconciliation agent, code-review agent, sales-research agent, etc.). Each was built independently. Each has its own tracing approach (or none), its own eval discipline (or none), its own deployment pipeline. Every team is reinventing the same five things, and no one can answer the CFO's question: *"What is the cost-per-task across our agent portfolio, and what is the failure rate?"*

Mandate from the CTO: **build a thin internal platform — PromptOps — that gives the next agent built (and the existing 12) a default-good way to be observable, evaluated, and governed.** MVP in 8 weeks. Three pilot agent teams have signed up. Anything more ambitious than MVP is out of scope.

| Constraint | Implication |
|---|---|
| 8-week MVP deadline | "MVP" is enforced — registry + tracing + eval gateway, nothing else |
| Three pilot teams already lined up | Real users from Week 4; their feedback drives Sprint 3-4 priorities |
| Built by a brand-new cognitive unit | Unit-formation overhead is real (per [`cognitive-units/README.md`](../../cognitive-units/README.md)) |
| Greenfield = many reversible decisions | Move fast on internals; lock the *contracts* with pilot teams |
| Industry warning: 95% of AI pilots fail to reach production (MIT 2026) | Build the eval harness *before* the platform itself |

See [`reference/industry-lessons-2024-2026.md`](../../reference/industry-lessons-2024-2026.md) for the lessons applied here.

---

## Cognitive Unit

A **new** cognitive unit is formed: **AI Platform** (a sibling to the existing [Intelligence Layer](../../cognitive-units/intelligence-layer.md), which uses AI capabilities, while AI Platform *enables* them). Modeled from [`cognitive-units/_template.md`](../../cognitive-units/_template.md).

### Outcome statement

> *Any team in the company can deploy, trace, and evaluate an AI agent the same week they decide to build one.*

### Composition

| Member | Cognitive functions | 7-cap focus |
|---|---|---|
| Naomi (Principal Eng, lead) | Solution Architect + Pattern Integrator + Stakeholder Harmonizer | System Design (L5), Eval/Observability (L4) |
| Yusuf (Senior Backend) | Builder + Solution Architect | Tool/Contract Design (L4), Reliability (L4) |
| Mei (Backend, +ML interest) | Builder + Learner | Retrieval (L3 → L4 goal), System Design (L3) |
| Theo (SRE) | Quality Guardian + Pattern Integrator | Reliability (L5), Eval/Observability (L4) |
| Riya (QA → Eval Engineer transition) | Quality Guardian + Problem Framer + Fresh-Eyes Observer | Eval/Observability (L3 → L5 goal), Security (L3) |
| Devon (Frontend) | Builder + Resonance Sensor + Growth Catalyst | Product Thinking (L4), Tool/Contract (L3) |
| Pat (PM) | Problem Framer + Stakeholder Harmonizer + Growth Catalyst | Product Thinking (L4) |
| **Architecture Explorer** (AI) | Solution Architect + Pattern Integrator + Problem Framer | proposes 3 platform shapes Day 1; reasons about tradeoffs continuously |
| **Code Co-Creator** (AI) | Builder + Quality Guardian + Pattern Integrator | scaffolds the registry, tracing collector, eval runner |
| **Documentation & Knowledge** (AI) | Pattern Integrator + Learner + Growth Catalyst | maintains living docs from Day 1; produces self-service onboarding by Week 6 |
| **Analysis Partner** (AI) | Problem Framer + Pattern Integrator + Resonance Sensor | reads the 12 existing agents to extract real patterns and pain |
| **Quality Analyst** (AI) | Quality Guardian + Resonance Sensor + Fresh-Eyes Observer | continuous PR review, security scanning, drift detection |

Note the unit has **5 AI agents** — appropriate when the unit is *building AI agent infrastructure*. The dogfooding is intentional: the platform's first user is the unit itself.

---

## The 7 Capabilities — All Seven, with Priority

This project is unusual in exercising every one of the 7 agent engineering capabilities at meaningful depth. See [`reference/agent-engineering-7-skills.md`](../../reference/agent-engineering-7-skills.md).

| Capability | How it shows up | Lead |
|---|---|---|
| **System Design** (Primary) | Registry, tracing collector, eval gateway as separately-deployable services with clean contracts | Naomi + Yusuf |
| **Tool/Contract Design** (Primary) | The *external* contract — "how an agent integrates with PromptOps" — is the single most consequential design output | Yusuf |
| **Eval/Observability** (Primary — built first, on purpose) | The platform's reason to exist. Built *before* the platform's own features. | Riya + Theo |
| **Retrieval** (Strong) | Tracing data needs to be queryable; eval datasets need versioning | Mei |
| **Reliability** (Strong) | The platform must not become the new bottleneck for 12 production agents | Theo |
| **Security** (Strong) | Centralized agent traces are a juicy target; PII must be scrubbed at ingest | Theo + Riya |
| **Product Thinking** (Strong) | Internal platform UX — if it's not a joy, teams will route around it | Devon + Pat |

---

## Sprint Flow (4 sprints × 2 weeks)

### Sprint 0 (Week 0 — pre-sprint, 3 days)

Per [`workflows/sprint-kickoff.md`](../../workflows/sprint-kickoff.md), but extended for unit formation (this is a brand-new unit). Activities from [`transformation/phase-1-first-unit.md`](../../transformation/phase-1-first-unit.md):

- Working agreements drafted (cross-reference [`org/working-agreements.md`](../../org/working-agreements.md))
- Function map completed — every member knows their primary functions and growth edges
- AI agent setup: each member configures Code Co-Creator, Architecture Explorer, etc. for their work
- Analysis Partner runs an audit of the 12 existing agents (Day 1-3) — surfaces real patterns

### Sprint 1 (Weeks 1-2): Eval Harness First

**Counter-intuitive choice** (driven by the MIT 2026 lesson — see [`reference/industry-lessons-2024-2026.md`](../../reference/industry-lessons-2024-2026.md)): build the *evaluation* and *tracing* infrastructure before the platform features.

**Goal**: Anything we build from Week 3 onward is eval-instrumented from birth.

| Activity | Lead |
|---|---|
| Tracing collector v0 (OpenTelemetry-based) | Theo + Code Co-Creator |
| Eval runner v0 (offline; runs LLM-judge + rule-based evals) | Riya + Code Co-Creator |
| Three reference eval datasets (correctness, safety, latency) for the existing customer-support agent | Riya + Analysis Partner |
| Internal "use it on yourself" — the unit's own work tracked through tracing collector v0 | Whole unit |

**Sprint 1 exit criteria**:
- Tracing collector ingests 100% of unit's own AI agent calls
- Eval runner produces a green/red per dataset
- One pilot team agrees their next sprint will use the eval runner

### Sprint 2 (Weeks 3-4): Registry + First Pilot

**Goal**: Agent registry stands up. First pilot agent (customer-support) is wired in fully.

| Activity | Lead |
|---|---|
| Agent registry service (CRUD; agent metadata; ownership; eval status) | Yusuf + Code Co-Creator |
| Frontend portal (list agents; view trace; view eval status) | Devon + Code Co-Creator |
| Customer-support agent migrated to PromptOps | Pilot team + Mei |
| Threat model for the platform itself | Theo + Quality Analyst |

**Sprint 2 exit criteria**:
- Customer-support agent reports through PromptOps
- p99 tracing collector ingest latency < 100ms
- Threat model accepted by SecEng (one round of pure-human review)

### Sprint 3 (Weeks 5-6): Two More Pilots, Self-Service Path

**Goal**: Self-service path works without unit hand-holding. Two more pilots ship.

| Activity | Lead |
|---|---|
| Self-service onboarding (docs + CLI + sample agent) | Devon + Documentation & Knowledge |
| Eval gateway (block-deploy gate when evals fail) | Riya + Yusuf |
| Pilots 2 & 3: billing-reconciliation, code-review agents migrate | Pilot teams + Mei |
| First on-call rotation for PromptOps platform | Theo |

**Sprint 3 exit criteria**:
- A team that has never seen the unit can onboard their agent in < 1 day (self-service rate signal — see [`metrics/platform-outcomes.md`](../../metrics/platform-outcomes.md))
- Eval gateway has blocked at least one bad deploy (intended behavior)
- All 3 pilots reporting through PromptOps

### Sprint 4 (Weeks 7-8): Hardening + Public Launch

**Goal**: MVP launch to all teams. Existing 12 agents migrated within next quarter (with the platform team supporting, not building).

| Activity | Lead |
|---|---|
| Reliability hardening (rate limits, circuit breakers, replay) | Theo + Code Co-Creator |
| Cost-per-task dashboard (CFO's question) | Mei + Metrics Monitor |
| Internal launch announcement | Pat + Naomi |
| Sprint Outcome Review with all 12 agent owners | Whole unit |

**Sprint 4 exit criteria** (= MVP done):
- 3 pilots in production reporting through PromptOps
- Cost-per-task visible across pilot agents
- Self-service onboarding < 1 day measured
- Migration guide for the other 9 agents published

---

## Decision Spectrum in Practice

| Decision | Type | Who decides | Why |
|---|---|---|---|
| Platform shape: monolith vs. 3 services vs. extension of existing system | Hybrid | Architecture Explorer proposes 3; Naomi + Yusuf decide | Reversible-with-cost; Naomi's judgment + AI's tradeoff modeling |
| External agent integration contract | Pure Human (after Hybrid drafting) | Yusuf drafts with Code Co-Creator; Naomi + 3 pilot teams ratify | Irreversible once external teams adopt |
| Tracing schema | Pure AI then human review | Code Co-Creator generates from OpenTelemetry standards; Theo tunes | Reversible — versioned schema |
| Eval threshold values per dataset | Pure AI | Riya + Quality Analyst tune from data | Reversible, data-driven |
| Build "agent marketplace" feature in MVP | Pure Human | Naomi: out of scope, full stop | Risk of MVP creep; the answer is no |
| Whether to enforce eval gateway as deploy-blocking | Hybrid | Riya proposes; Naomi + Pat decide; pilot teams consulted | Semi-reversible (changes blast radius of eval failures) |

---

## Metrics Watched

This project is built around [`metrics/platform-outcomes.md`](../../metrics/platform-outcomes.md):

| Metric | Target by Week 8 | Why primary |
|---|---|---|
| **Time: agent ask → first PromptOps trace** | < 1 day | The platform's core value claim |
| **Self-service rate** | > 60% (pilots could complete steps without unit help) | If teams need hand-holding, MVP is not done |
| **Cost-per-task across pilot agents** | Visible (was: invisible) | Answers the CFO question |
| **Eval coverage** | 100% of pilot agents | Eval-first principle holds |
| **AI Task Sophistication** | L4 avg | This unit *is* AI agent engineering — sophistication is high here |
| **Emergence events** | ≥ 4 logged | Greenfield + 5 AI agents = high emergence opportunity |
| **DX Score (pilot teams)** | > 7/10 | Internal-platform UX matters |
| **Fulfillment** | 7+/10 | New unit + ambitious deadline = watch closely |

---

## Risks (Project-Specific)

| Risk | Mitigation |
|---|---|
| MVP creep — pilot teams want a marketplace, scoring, optimization, etc. | Naomi has explicit veto; out-of-scope list maintained publicly; MVP is sacred |
| The unit becomes the bottleneck (3 pilots dependent on a 7-person team) | Self-service path is a Sprint 3 hard requirement, not a stretch |
| Built-it-but-no-one-comes (the 12 existing agent owners ignore the platform) | Pat (Stakeholder Harmonizer) builds adoption coalition Sprints 1-3, *before* launch |
| Evals are wrong — the platform's eval verdict misleads | Multi-method evals (LLM-judge + rule + human spot-check); calibration tracked |
| Centralized traces become a security incident | Threat model in Sprint 2; PII scrubbed at ingest; access controls reviewed |
| Industry pattern: 95% of AI pilots fail to reach production | Eval-first discipline + 3 pilots committed before Week 1 = direct counter |

---

## Emergence Opportunities

- **The 12-agent audit reveals a meta-pattern.** Analysis Partner reading the 12 existing agents finds that 8 of them have implemented variants of the same retrieval-then-validate loop. That pattern becomes a first-class platform primitive that no one designed up front.
- **Eval-first reshapes priorities.** A pilot team realizes their agent has a 22% silent-failure rate that nobody knew about. The unit's eval harness becomes more valuable than the registry — the platform's center of gravity shifts before launch.
- **AI agents in the unit propose architectural moves humans wouldn't.** Architecture Explorer proposes a wildly unusual idempotency pattern. Naomi rejects 80%, but the 20% she keeps reshapes the registry's API.

Log all of these in [`emergence-detection.md`](../../transformation/emergence-detection.md).

---

## What You Can Reuse

| Asset | Notes |
|---|---|
| Eval-first principle | Build the eval harness *before* the platform's own features. This single move counters the 95% pilot-failure pattern. |
| Outcome statement format | One sentence, one outcome, no "and"s. "Any team can deploy, trace, and evaluate..." passes; "Any team can deploy AND scale AND govern AND audit..." fails. |
| Pilot-first path to launch | 3 pilots committed before Week 1; their feedback drives priority each sprint |
| AI-heavy unit composition | Building AI agent infrastructure justifies 5 AI agents in the unit (more than typical) |
| MVP veto authority | A named human can say "no" without negotiation; this is the most underrated governance mechanism |

---

## Tactical Business Gain Summary

| Gain | Value |
|---|---|
| Cost-per-task visible for first time | Answers CFO's question; informs next quarter's AI investment |
| Eval-first becomes the default | All future agents start with an eval harness |
| 12-agent sprawl ends | Migration plan for remaining 9 agents in flight by Week 8 |
| Self-service < 1 day | Removes the AI Platform unit as a bottleneck before it becomes one |
| New cognitive unit operational | Living proof that [`transformation/phase-1-first-unit.md`](../../transformation/phase-1-first-unit.md) works for greenfield |
| Capability development visible | Riya moved L3 → L5 on Eval/Observability; Mei moved L3 → L4 on Retrieval |
