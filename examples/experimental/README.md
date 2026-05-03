# Example: Experimental Project — AI-Augmented Code Review Pilot

> **Archetype**: Experimental / Time-Boxed Hypothesis
> **Tactical gain**: If the hypothesis holds, save ~120 senior engineering hours/month on code review across the platform org. If it fails, kill cleanly with a published decision memo so the next experiment doesn't repeat the same path.
> **Reversibility**: Fully reversible — that is the point. Decisions skew Pure-AI and Hybrid; humans set the kill criteria up front.

---

## Scenario

A senior engineer notices that ~40% of comments on infra repo PRs are mechanical: "missing test," "this re-implements helper X," "this would benefit from being moved to Y." A Frontier-unit hypothesis emerges:

> **Hypothesis**: An AI agent with full repo + ADR + style-guide context can produce code review comments that senior engineers would *accept* (not merely tolerate) at a rate ≥ 70%, on at least the mechanical 40% of comments. If true, we save ~120 senior eng hours/month and senior engineers reclaim time for architectural review.

The question is genuinely open. We do not know if it will work. The point is to find out — quickly, cheaply, and *with kill criteria defined before we start*.

| Constraint | Implication |
|---|---|
| Time-boxed: 12 weeks | Hard stop. Extension only with new evidence and explicit decision. |
| Kill criteria defined Day 0 | Required before work starts; no moving the goalposts (per [Industry Lessons](../../reference/industry-lessons-2024-2026.md): 95% of AI pilots fail to reach production — most because no one defined what "fail" looks like) |
| 4 humans (small team) | Experiment must be efficient |
| Lives in [Frontier](../../cognitive-units/frontier.md) unit | Frontier exists for exactly this kind of work |
| Outcome may be "kill it" — and that is a success | Cultural framing matters; see [`workflows/exploration-time.md`](../../workflows/exploration-time.md) |

---

## Cognitive Unit

This work lives inside the existing **[Frontier](../../cognitive-units/frontier.md)** unit. Frontier's whole purpose is curiosity-driven, time-boxed exploration of "what becomes possible when humans and AI combine." This is its archetypal project.

### Composition

| Member | Cognitive functions | 7-cap focus |
|---|---|---|
| Asha (Staff Eng, experiment lead) | Solution Architect + Fresh-Eyes Observer + Pattern Integrator | Eval/Observability (L4), Retrieval (L4) |
| Theo (ML Eng) | Builder + Pattern Integrator + Learner | Retrieval (L4 → L5 goal), Eval/Observability (L4) |
| Sami (Senior Backend, "skeptic-in-residence") | Quality Guardian + Fresh-Eyes Observer | Eval/Observability (L3), Tool/Contract (L3) |
| Devon (UX Researcher, half-time) | Resonance Sensor + Problem Framer + Stakeholder Harmonizer | Product Thinking (L4) |
| **Architecture Explorer** (AI) | Solution Architect + Pattern Integrator + Problem Framer | proposes 3 implementation architectures |
| **Code Co-Creator** (AI) | Builder + Quality Guardian + Pattern Integrator | builds the prototype |
| **Quality Analyst** (AI) | Quality Guardian + Resonance Sensor + Fresh-Eyes Observer | runs eval pipeline; classifies review comments |
| **Metrics Monitor** (AI) | Pattern Integrator + Quality Guardian + Problem Framer | tracks all kill-criterion metrics in real time |

Notable: a "skeptic-in-residence" — Sami — is intentionally on the team. Their job is to not get caught up in enthusiasm. The [Fresh-Eyes Observer](../../cognitive-functions/fresh-eyes-observer.md) function is structurally protected.

---

## The 7 Capabilities Exercised

Per [`reference/agent-engineering-7-skills.md`](../../reference/agent-engineering-7-skills.md):

| Capability | Why central here | Lead |
|---|---|---|
| **Eval/Observability** (Primary) | The whole experiment is an evaluation question. Build the evaluation rig before the agent. | Asha + Theo |
| **Retrieval** (Primary) | The hypothesis depends on the agent having repo + ADR + style-guide context. Retrieval quality is the cap on results. | Theo |
| **Product Thinking** (Strong) | A review comment with low confidence presented confidently is worse than no comment. Trust calibration in UX is decisive. | Devon |
| **Tool/Contract Design** (Strong) | The agent's "comment a PR" tool needs strict structure: comment type, confidence, citation. | Sami |
| **System Design** (Supporting) | The system is small. Don't over-design. | Asha |
| **Reliability** (Supporting) | If the agent is down, reviews fall back to humans. Acceptable. | Theo |
| **Security** (Supporting) | The agent reads private code; access controls matter, but no novel surface. | Sami |

---

## Kill Criteria (Defined Day 0)

This is the most important section. Without it, the experiment cannot be honest.

| Criterion | Threshold | Measured at |
|---|---|---|
| **Acceptance rate of mechanical-tier comments** | ≥ 70% by Week 8 | Weekly |
| **False-positive rate** (wrong/misleading comments) | ≤ 5% sustained | Weekly |
| **Reviewer trust score** (qualitative survey, 1-5) | ≥ 3.5 by Week 6 | Bi-weekly |
| **Time saved per accepted comment** | ≥ 2 minutes (positive) | Weekly |
| **Burnout risk on reviewers receiving AI comments** | Green (no rise) | Continuous |

**Any single threshold missed at the gate week → escalate to "continue with corrective work" or "kill" decision in the next sprint review.**

**Two thresholds missed → kill, or formally restart with a different hypothesis.**

The decision is not Asha's alone — per [`CLAUDE.md`](../../CLAUDE.md) Decision Spectrum, the kill decision is Pure-Human, made by Asha + Frontier unit lead, with the published evidence visible to all reviewers.

---

## Sprint Flow (6 sprints × 2 weeks)

Frontier sprints look different from execution-unit sprints. They are organized around *learning*, not *delivery*. See [`workflows/exploration-time.md`](../../workflows/exploration-time.md).

### Sprint 1 (Weeks 1-2): Eval Rig

**Goal**: Build the evaluation rig *before* the agent. Acceptance is measured against a labeled dataset of 200 historical PR comments.

| Activity | Lead |
|---|---|
| Curate dataset: 200 PRs across 4 infra repos, comments labeled by category | Asha + Sami + Quality Analyst |
| Build offline eval pipeline: input PR diff → agent comment → human accept/reject blind labels | Theo + Code Co-Creator |
| Pre-register Day-0 hypothesis and kill criteria as a public memo | Asha |

**Sprint 1 exit**: Eval rig operational; can score *any* candidate agent against the 200-PR set.

### Sprint 2 (Weeks 3-4): Baseline + v0 Agent

**Goal**: Establish a baseline and ship a deliberately simple v0.

| Activity | Lead |
|---|---|
| Baseline: how do *random* comments score? How does GPT-4 with no repo context score? | Theo |
| v0 agent: full PR diff + ADR retrieval + style guide as context | Theo + Code Co-Creator |
| First eval run; failure clustering; fresh-eyes review by Sami | Whole unit |

**Sprint 2 expected outcome**: v0 likely fails — but we now know *how* it fails. Failure modes drive Sprint 3.

### Sprints 3-4 (Weeks 5-8): Iterate or Kill

**Goal**: Drive acceptance rate up. Or kill.

This is where most experiments either thrive or die. Discipline:
- One change per week, evaluated against the same 200-PR set
- Sami reviews every "we improved!" claim with adversarial rigor
- Devon runs reviewer interviews mid-Sprint 4 (target: Reviewer Trust score ≥ 3.0)
- **Week 8 is the gate**: kill criteria evaluated; decision goes to memo.

### Sprints 5-6 (Weeks 9-12): If Surviving — Limited Production Trial

**Only reached if Week 8 gate is passed.**

**Goal**: 2 infra repos, real PRs, AI agent posts comments tagged `[ai-suggested]`. Reviewers may accept, ignore, or counter-argue. Telemetry tracks everything.

| Activity | Lead |
|---|---|
| Production deployment behind flag | Theo + Code Co-Creator |
| Live acceptance + trust + burnout tracking | Metrics Monitor + Devon |
| Final report: graduate to platform offering, continue iterating, or kill | Asha |

---

## Decision Spectrum in Practice

| Decision | Type | Who decides | Why |
|---|---|---|---|
| Hypothesis statement and kill criteria | Pure Human | Asha + Frontier unit lead | The single most important governance moment |
| Eval rig design | Hybrid | Theo + Architecture Explorer | Methodological choice; reversible but consequential |
| Retrieval strategy (chunk size, embedding model, reranker) | Pure AI | Theo + Quality Analyst tune from data | Reversible, data-driven |
| Whether to declare a Sprint 3 improvement "real" | Pure Human (Sami's veto explicit) | Sami + Asha | Confirmation bias is the failure mode here |
| Kill / continue / restart at Week 8 | Pure Human | Asha + Frontier unit lead | Irreversible (in spirit — once killed, do not unkill quietly) |
| Production rollout flag controls | Hybrid | Theo proposes; Asha + Devon ratify | Reviewer experience is at stake |

---

## Metrics Watched

| Metric | Source | Why primary here |
|---|---|---|
| **Exploration-to-Production rate** | [Innovation](../../metrics/innovation.md) | Frontier's headline metric — does exploration produce something real? |
| **Acceptance rate** (project-specific) | Quality Analyst on the eval rig | Direct hypothesis test |
| **False-positive rate** | Quality Analyst | Trust depends on this |
| **Reviewer Trust score** | Devon survey | Captures the human side that pure metrics miss |
| **AI Task Sophistication** | [AI Utilization](../../metrics/ai-utilization.md) | Will move from L2 to L4+ if hypothesis succeeds |
| **Emergence events** | [Harmonization](../../metrics/harmonization.md) | High likelihood — exploration is fertile |
| **Burnout risk on receiving reviewers** | [Human Fulfillment](../../metrics/human-fulfillment.md) | Watch for "AI comments are exhausting to deal with" pattern |

**A healthy kill is a metric victory.** A clean kill at Week 8 with a published memo, a reusable eval rig, and three captured emergence insights is a *better* outcome than a muddy survival into Sprint 5.

---

## Risks (Project-Specific)

| Risk | Mitigation |
|---|---|
| Confirmation bias — the team becomes invested in surviving | Sami's structural skeptic role; published kill criteria; Frontier unit lead has veto |
| Acceptance rate looks good but reviewers are accepting low-effort comments out of politeness | Devon's interviews catch this; counter-survey: "if this comment did not exist, would your PR be worse?" |
| Repo coverage too narrow → "works on this repo only" illusion | Eval set spans 4 infra repos with deliberately different styles |
| Production trial → reviewers feel surveilled | Devon owns the reviewer-experience contract; no metric is collected without consent |
| Hidden cost: cost-per-comment exceeds salary saved | Metrics Monitor tracks cost from Week 2 |
| Industry pattern: 95% pilots don't ship | Built-in: kill is a valid outcome; we measure quality of the kill, not just survival |

---

## Emergence Opportunities

- **Failure clusters reveal a different question.** The most interesting outcome is often: "the agent fails on PRs that touch the eval rig itself; agents reviewing agents is a deeper problem than we framed." A new hypothesis emerges from the experiment's failure.
- **Reviewers describe an unmet need the team didn't ask about.** Devon's interviews surface that reviewers want the AI to flag *missing tests for the things the PR breaks downstream* — a different agent capability entirely. That insight goes to the backlog regardless of this project's outcome.
- **The eval rig has more value than the agent.** A reusable infra-PR labeled dataset and rig become a permanent asset, even if the agent dies.

Log in [`emergence-detection.md`](../../transformation/emergence-detection.md).

---

## What You Can Reuse

| Asset | Notes |
|---|---|
| **Day-0 kill-criteria memo** | The single most important artifact. Pre-register before any code. |
| **Eval rig (offline + production trial)** | Reusable for *any* future agent experiment in code review |
| **Skeptic-in-residence role** | A team member whose explicit job is fresh-eyes adversarial review. Inverts the "everyone gets enthusiastic" failure mode. |
| **"Healthy kill" framing** | Cultural framing in [`workflows/exploration-time.md`](../../workflows/exploration-time.md) — a clean kill is a successful experiment |
| **Counter-survey pattern** | "If this comment didn't exist, would your PR be worse?" — escapes politeness bias |

---

## Tactical Business Gain Summary

Two outcomes, both gains:

### Outcome A: Hypothesis confirmed (estimated ~30% likelihood)
| Gain | Value |
|---|---|
| Senior eng time recovered | ~120 hours/month across infra org |
| Reusable eval rig | Asset for the next 5 experiments |
| Frontier proves its value | Cultural ammunition for next cycle |
| 1-2 emergence events captured | Inputs to next quarter's roadmap |

### Outcome B: Hypothesis killed cleanly (estimated ~70% likelihood)
| Gain | Value |
|---|---|
| Decision memo published | Next experiment doesn't repeat the same path |
| Eval rig still reusable | Same |
| Failure-mode taxonomy of code-review agents | The most-cited internal doc for the next year |
| Skeptic-in-residence pattern proven | Adopted across other Frontier experiments |
| Capability development | Theo moved L4 → L5 on Retrieval; Asha L3 → L4 on Eval |

A clean kill in 12 weeks is **dramatically cheaper** than the alternative (an unkilled, drifting, half-believed-in tool living on a wiki for 18 months). The structural insistence on kill criteria *is* the tactical gain.
