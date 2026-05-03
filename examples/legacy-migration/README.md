# Example: Legacy Migration — Order-Hub Monolith Carve-Out

> **Archetype**: Legacy Migration
> **Tactical gain**: Unblock EU regional launch by carving the highest-risk endpoint out of a 12-year-old monolith in 6 weeks.
> **Reversibility**: Mostly irreversible (DB partitioning, contract changes). Decisions skew Pure-Human and Hybrid.

---

## Scenario

**Order-Hub** is the company's order-orchestration monolith. It is 12 years old, ~1.4M LoC of Java 8, owns 60% of the revenue path, has no real test harness, and is owned (in name only) by an SRE rotation that no current member built. A new EU region launch is committed for **Week 6**. The blocker: `/checkout/finalize` — the highest-volume endpoint — needs region-aware tax handling that the monolith's hard-coded tax engine cannot deliver without a six-month rewrite.

Strategy: carve `/checkout/finalize` out as an independent service ("FinalizeService"), leaving Order-Hub to call it. Ship in 5 weeks; soak for 1 week behind a feature flag; cut over for EU launch in Week 6.

| Constraint | Implication |
|---|---|
| 6-week deadline | Cannot do a "proper" rewrite — must do a strangler-fig extraction |
| Monolith has no tests for this path | All confidence comes from production traffic shadowing, not tests |
| 60% of revenue flows through this code | Change failure rate target < 2%; rollback path mandatory |
| Original authors gone | Documentation & Knowledge agent does heavy lifting on archaeology |
| Region-aware tax = new contract | Tool/Contract Design discipline is non-negotiable |

---

## Cognitive Unit

This work lives inside the existing **[Scale & Reliability](../../cognitive-units/scale-reliability.md)** unit, with a temporary boost: one rotation-in from [Developer Experience](../../cognitive-units/developer-experience.md) to handle the platform-side service-template work.

### Composition

| Member | Cognitive functions held | 7-cap focus this sprint |
|---|---|---|
| Priya (Staff Eng, lead) | Solution Architect + Pattern Integrator + Stakeholder Harmonizer | System Design (L4), Tool/Contract Design (L4) |
| Marco (Senior Backend) | Builder + Quality Guardian | Reliability (L4), System Design (L3) |
| Sam (Senior Backend) | Builder + Solution Architect | Tool/Contract Design (L3 → L4 goal) |
| Lin (SRE) | Quality Guardian + Pattern Integrator | Reliability (L5), Eval/Observability (L4) |
| Jordan (QA) | Quality Guardian + Problem Framer | Eval/Observability (L4), Security (L3) |
| Alex (Platform Eng, rotation-in) | Builder + Growth Catalyst | Reliability (L4) |
| **Architecture Explorer** (AI) | Solution Architect + Pattern Integrator + Problem Framer | proposes 3 extraction strategies on Day 1 |
| **Code Co-Creator** (AI) | Builder + Quality Guardian + Pattern Integrator | implements scaffolding, generates contract tests |
| **Documentation & Knowledge** (AI) | Pattern Integrator + Learner + Growth Catalyst | reads 12 years of code + ADRs + Confluence; produces the carve-out's institutional memory pack on Day 1 |
| **Quality Analyst** (AI) | Quality Guardian + Resonance Sensor + Fresh-Eyes Observer | continuous regression-risk scoring on every PR; runs traffic-shadowing diff detection |

See [`agents/`](../../agents/) for full agent definitions.

---

## The 7 Capabilities Exercised

Per [`reference/agent-engineering-7-skills.md`](../../reference/agent-engineering-7-skills.md):

| Capability | Why it's central here | Who leads |
|---|---|---|
| **System Design** (Primary) | Strangler-fig extraction is a system-design problem. Where does state live? How do calls fan out? What is the new failure boundary? | Priya |
| **Tool/Contract Design** (Primary) | The new tax-handling contract is the irreversible decision of this project. Vague contract = months of pain. | Sam |
| **Reliability Engineering** (Primary) | Cutting over a revenue-critical path requires retries, timeouts, fallbacks, circuit breakers. | Lin + Alex |
| **Eval/Observability** (Strong) | We have no tests; observability is our only confidence. Trace every call across the boundary. | Lin + Jordan |
| **Security** (Strong) | The carve-out crosses a network boundary; auth/authz redone. PCI scope re-evaluated. | Jordan |
| **Retrieval** (Strong) | Documentation & Knowledge agent must retrieve relevant slices of the monolith on demand. | AI agent |
| **Product Thinking** (Supporting) | Mostly internal; matters for ops UX (alerting, runbook clarity). | Lin |

---

## Sprint Flow (3 sprints × 2 weeks)

This project runs three Harmonized Sprints. See [`workflows/`](../../workflows/) for ceremonies.

### Sprint 1 (Weeks 1-2): Archaeology + Contract

**Goal**: Understand what we're cutting out. Define the new contract. Build nothing yet.

| Ceremony | Distinctive activity for this project |
|---|---|
| [Sprint Kickoff](../../workflows/sprint-kickoff.md) | Documentation & Knowledge agent presents a 20-page **Code Archaeology Pack** generated from the monolith repo + Confluence + Slack history: every code path that touches `/checkout/finalize`, every prior incident, every ADR mentioning tax. Architecture Explorer presents 3 extraction strategies with tradeoffs. Humans pick. |
| Daily Harmony Check | 15-min daily; blocker focus is "what did the AI agents *not* know?" — gaps in retrieval drive next-day work |
| [Deep Work](../../workflows/deep-work-collaboration.md) | Sam pairs with Code Co-Creator to draft the new contract (OpenAPI + JSON Schema). Quality Analyst reviews for ambiguity. |
| Sprint Review | Demo: contract approved, archaeology pack published, 3 strategies converged to 1 chosen approach with named tradeoff acceptance |
| [Retrospective](../../workflows/harmonization-retrospective.md) | Specifically: "where did the human catch what the AI missed in the monolith?" — captured in [`emergence-detection.md`](../../transformation/emergence-detection.md) |

**Sprint 1 exit criteria**:
- New contract signed off by all consumer teams (3 of them)
- Code Archaeology Pack reviewed by 2 humans who were *not* in the unit (fresh-eyes review)
- Rollback strategy documented — if Week 6 cutover fails, what happens
- Test/observability strategy approved (no tests possible → traffic shadowing + dual-run + structured tracing)

### Sprint 2 (Weeks 3-4): Build + Shadow

**Goal**: Build FinalizeService, run it in shadow mode against production traffic, drive diff rate to < 0.1%.

| Day | Activity |
|---|---|
| 3.1 | Code Co-Creator scaffolds the new service from the contract. Marco + Sam review every line — *AI writes, humans verify and judge*. |
| 3.3 | Lin builds the traffic-shadowing infrastructure. Quality Analyst is wired in to diff every shadowed response against the monolith. |
| 4.1 | Shadow goes live. Initial diff rate: 8% (mostly tax-rounding). Quality Analyst clusters diffs by root cause. |
| 4.4 | Diff rate < 0.5%. Remaining diffs reviewed by Priya — accepted as "new behavior is correct." |

**Sprint 2 exit criteria**:
- Diff rate < 0.1%
- p99 latency of new service ≤ 1.2× monolith path
- All synthetic adversarial inputs rejected with structured errors
- Tracing covers 100% of cross-boundary calls

### Sprint 3 (Weeks 5-6): Cut Over + Soak

**Goal**: Move 100% of traffic to FinalizeService behind a feature flag, soak for 7 days, then formally cut over for EU launch.

| Day | Activity |
|---|---|
| 5.1 | 1% canary in non-EU traffic |
| 5.2 | 10% canary; Quality Analyst flags one anomaly (a discount-code edge case); fix shipped |
| 5.4 | 50% traffic |
| 5.5 | 100% traffic, monolith path retained as fallback |
| 6.1 | EU region added behind launch flag; FinalizeService handles EU tax via new contract |
| 6.5 | Public launch. Monolith fallback remains armed for 30 days. |

---

## Decision Spectrum in Practice

Per [`CLAUDE.md`](../../CLAUDE.md), reversibility governs who decides:

| Decision | Type | Who decides | Why |
|---|---|---|---|
| Choose extraction strategy (3 options from Architecture Explorer) | Pure Human | Priya, ratified by unit | Irreversible — chosen strategy shapes 18 months of work |
| Tax-handling contract shape | Hybrid | Sam proposes with Code Co-Creator; humans + consumer teams ratify | Semi-reversible (consumers depend on it) |
| Service framework choice (existing template vs. new) | Hybrid | Alex + Architecture Explorer; Priya signs off | Reversible-with-cost |
| Retry counts, timeout values | Pure AI then human review | Code Co-Creator generates from reliability template; Lin tunes | Reversible — tune in production |
| Traffic-shadowing diff thresholds | Pure AI | Quality Analyst sets and adjusts | Reversible, measurable |
| Cutover timing (1% → 10% → 100%) | Pure Human | Priya + Lin | Irreversible if failure cascades |
| Rollback decision during canary | Pure Human (oncall) | Lin or oncall, no AI veto | Irreversible blast radius |

---

## Metrics Watched

Primary metrics for this project, drawn from [`metrics/`](../../metrics/):

| Metric | Source | Target | Why primary here |
|---|---|---|---|
| **Change Failure Rate** | [DORA](../../metrics/dora.md) | < 2% | Revenue-critical path; the floor |
| **MTTR** | [DORA](../../metrics/dora.md) | < 30 min | Rollback path must be fast |
| **Rework Rate** | [Code Health](../../metrics/code-health.md) | < 10% | Rushing legacy work usually inflates rework — watch closely |
| **Lead Time for Changes** | [DORA](../../metrics/dora.md) | < 1 day after Week 2 | Sprint 2-3 cadence demands it |
| **Diff rate (shadow vs. monolith)** | Project-specific (Quality Analyst) | < 0.1% by Week 4 | Custom metric; our only correctness signal |
| **AI Task Sophistication** | [AI Utilization](../../metrics/ai-utilization.md) | L3+ avg | Code Co-Creator handling implementation, not just autocomplete |
| **Fulfillment / Burnout Risk** | [Human Fulfillment](../../metrics/human-fulfillment.md) | Green | Legacy work + deadline = burnout risk; the [Daily Harmony Check](../../workflows/daily-harmony-check.md) watches this daily |
| **Emergence events** | [Harmonization](../../metrics/harmonization.md) | ≥ 2 logged | This is fertile ground (humans + AI on a system neither fully knows) |

**The critical rule** (per [`metrics/README.md`](../../metrics/README.md)): if any metric improves while another declines, that is a warning, not a win. Specifically watched here: if Lead Time drops while Rework Rate rises, slow down.

---

## Risks (Project-Specific)

| Risk | Probability | Mitigation in framework |
|---|---|---|
| Documentation & Knowledge agent retrieves wrong slice → carve-out misses a code path | Medium | Fresh-eyes review of archaeology pack by 2 humans outside the unit (a [Fresh-Eyes Observer](../../cognitive-functions/fresh-eyes-observer.md) function activation) |
| Code Co-Creator writes plausible-but-subtly-wrong code in the financial path | Medium-High | Mandatory line-by-line review by Marco + Sam; senior sign-off per [`org/policies.md`](../../org/policies.md); industry lesson [Amazon Kiro post-incident](../../reference/industry-lessons-2024-2026.md#what-failed) |
| Tax contract gets ratified, then a consumer pushes back at Week 5 | Medium | All 3 consumer teams included in Sprint 1 review, signed off in writing |
| Cutover fails Friday before launch | Low | Cutover scheduled mid-week; monolith fallback armed for 30 days post-launch; [`transformation/risk-management.md`](../../transformation/risk-management.md) cutover playbook applies |
| Burnout in last sprint | Medium | Daily Harmony Check tracks energy; Priya empowered to push deadline if fulfillment drops two weeks running (no metric is worth burning the team) |

---

## Emergence Opportunities

These are where to look for human-AI insights neither could produce alone — log them in [`emergence-detection.md`](../../transformation/emergence-detection.md):

- **The archaeology surfaces a forgotten invariant.** When Documentation & Knowledge agent's retrieval lands on a 2018 Slack thread that explains *why* the original tax engine made a particular weird choice — a human reading recognizes the rationale that the AI couldn't classify.
- **Diff clusters reveal a latent bug in the monolith.** Quality Analyst clusters shadow diffs and one cluster looks like "FinalizeService is wrong" — but Lin's reliability instinct recognizes it as the *monolith* having always been wrong; the new service is correcting it. The unit decides to ship the correction.
- **Contract review with consumers reveals shared pain.** Stakeholder Harmonizer (Priya) hears all 3 consumer teams describe the same workaround they've each been carrying. The carve-out becomes the moment to fix it for everyone.

---

## What You Can Reuse

| Asset | Path | Adapt for your migration |
|---|---|---|
| Archaeology Pack template | (template lifted into your repo) | Same prompt to Documentation & Knowledge agent: "summarize all code, docs, ADRs, and incidents touching `<endpoint>`; flag unknowns as questions" |
| Strangler-fig extraction strategy comparison | This README, "Sprint 1" | Architecture Explorer prompt: "given <constraint>, produce 3 strategies, name tradeoffs, recommend default" |
| Traffic shadowing diff harness | Conceptually defined here | Lin's pattern: dual-run, structured diff, AI clusters, humans review tail |
| Decision Spectrum table | This README | Copy and adapt — the table itself is the discipline |
| Risk register format | This README + [`risk-management.md`](../../transformation/risk-management.md) | Pair every risk with the framework mechanism that mitigates it |

---

## Tactical Business Gain Summary

| Gain | Value |
|---|---|
| EU launch unblocked on schedule | $X revenue Q1 |
| Order-Hub blast radius reduced (one fewer revenue-critical responsibility) | Insurance against next outage |
| Strangler-fig pattern proven and documented | Template for next 5 carve-outs |
| Capability development visible | Sam moved L3 → L4 on Tool/Contract Design; Lin maintained L5 on Reliability; Alex moved L3 → L4 on Reliability |
| Emergence events logged | 2 (forgotten-invariant find; consumer-shared-pain insight) |
