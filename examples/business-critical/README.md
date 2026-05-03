# Example: Business-Critical Short-Term Tactical Gain — PCI-DSS Audit Remediation Strike

> **Archetype**: Business-Critical / Short-Term Tactical
> **Tactical gain**: Close 14 PCI-DSS audit findings in **21 days** to retain PCI compliance and protect ~$8M in quarterly revenue exposure. Use **only what is already in this framework** — no new tools, no new hires, no waiting on procurement.
> **Reversibility**: Irreversible (compliance loss). Decisions skew Pure-Human; AI accelerates execution under strict oversight.

---

## Scenario

The Q3 PCI-DSS external audit identifies 14 findings across the platform: 5 Critical, 6 High, 3 Medium. Remediation deadline: **21 days** from receipt of findings or the company loses PCI compliance, which would force a halt to card-payment processing on the platform's most lucrative product line. Estimated direct revenue exposure: ~$8M/quarter. Indirect (brand, partner trust): much larger.

The auditor has been clear: every finding requires evidence of remediation *plus* evidence of the control that prevents recurrence. "We patched it" is insufficient.

This is exactly the situation HIO must serve: **a real, urgent, high-stakes business need, met with the framework already in place.** No re-platforming. No new units. Reuse the cognitive functions, agent types, and ceremonies already operational.

| Constraint | Implication |
|---|---|
| 21 days, fixed | No slipping. The remediation window is set externally. |
| 14 findings, not all in one repo | Cross-cutting work; coordination is the bottleneck |
| All AI-assisted code requires senior sign-off | Per [`org/policies.md`](../../org/policies.md), Amazon-Kiro lesson applied |
| Audit trail required for every change | Eval/Observability capability is non-negotiable |
| Business cannot pause | Platform serves real customers throughout |
| Use what's already here | No procurement, no new tooling, no new hires |

See [`reference/industry-lessons-2024-2026.md`](../../reference/industry-lessons-2024-2026.md) — the Amazon (post-incident senior sign-off) and Goldman Sachs (aggressive + governed) lessons are directly applied.

---

## Cognitive Unit (Temporary Strike Form)

A **temporary cognitive unit** is convened for 21 days: **Compliance Strike**. This is an explicit pattern from [`cognitive-units/README.md`](../../cognitive-units/README.md) — units can be ephemeral when the work demands it. The unit dissolves when the audit is closed.

Members are pulled with their primary unit's consent. Each member's home unit absorbs the temporary capacity loss; a written backfill agreement exists per [`org/working-agreements.md`](../../org/working-agreements.md).

### Composition

| Member | From unit | Cognitive functions | 7-cap focus |
|---|---|---|---|
| Aki (Principal Eng, strike lead) | Scale & Reliability | Solution Architect + Stakeholder Harmonizer + Pattern Integrator | Security (L5), Eval/Observability (L4) |
| Ren (Security Eng) | Scale & Reliability | Quality Guardian + Fresh-Eyes Observer | Security (L5), Tool/Contract (L4) |
| Marco (Senior Backend) | Scale & Reliability | Builder + Quality Guardian | System Design (L4), Reliability (L4) |
| Lin (SRE) | Scale & Reliability | Quality Guardian + Pattern Integrator | Reliability (L5), Eval/Observability (L4) |
| Jordan (QA) | Developer Experience | Quality Guardian + Problem Framer | Eval/Observability (L4), Security (L4) |
| **Code Co-Creator** (AI) | — | Builder + Quality Guardian + Pattern Integrator | implements remediations from the brief |
| **Quality Analyst** (AI) | — | Quality Guardian + Resonance Sensor + Fresh-Eyes Observer | continuous security scanning, regression detection, anomaly flagging |
| **Documentation & Knowledge** (AI) | — | Pattern Integrator + Learner + Growth Catalyst | produces audit evidence package per finding; maintains living remediation log |
| **Architecture Explorer** (AI) | — | Solution Architect + Pattern Integrator + Problem Framer | called when a finding requires structural change, not patch |
| **Metrics Monitor** (AI) | — | Pattern Integrator + Quality Guardian + Problem Framer | real-time burn-down, change failure rate watch, audit-evidence completeness tracking |

5 humans + 5 AI agents. AI agent count is intentionally high because the work is execution-heavy under tight time and the humans are the constraint, not the AI.

---

## The 7 Capabilities Exercised

Per [`reference/agent-engineering-7-skills.md`](../../reference/agent-engineering-7-skills.md):

| Capability | Why central here | Lead |
|---|---|---|
| **Security/Safety** (Primary) | This is *the* security project | Ren + Aki |
| **Eval/Observability** (Primary) | Auditor wants evidence + recurrence-prevention controls. Tracing every change. | Jordan + Lin |
| **Tool/Contract Design** (Strong) | 4 of 14 findings require API contract changes (auth tightening, rate limits) | Ren + Marco |
| **Reliability** (Strong) | Some patches risk introducing regressions in the revenue path; circuit breakers + canaries mandatory | Lin |
| **System Design** (Supporting) | 2 findings require structural changes (network segmentation, isolated key store) | Architecture Explorer + Aki |
| **Retrieval** (Supporting) | Documentation & Knowledge agent retrieves prior remediations and audit history | AI agent |
| **Product Thinking** (—) | Internal-only work; Product Thinking minimal here |

---

## The Sprint That Isn't a Sprint

A 21-day strike does **not** run as a 2-week Harmonized Sprint — that cadence is wrong for this shape. It runs as **3 × 7-day micro-sprints**, with daily ceremonies tightened.

Per [`workflows/`](../../workflows/), the ceremonies are kept but compressed:

| Standard ceremony | Strike-mode adaptation |
|---|---|
| Sprint Kickoff | **Day 0** — 3-hour kickoff: full unit + auditor liaison + CISO; every finding owned, classified, scoped |
| [Daily Harmony Check](../../workflows/daily-harmony-check.md) | Twice-daily, 15 min each (start of day, end of day); burn-down + risk surface + energy check |
| [Deep Work + Collaboration](../../workflows/deep-work-collaboration.md) | 5 hrs/day deep work blocks; senior sign-off windows scheduled twice a day so AI-assisted PRs are never blocked > 4 hrs |
| Sprint Outcome Review | **Day 7, 14, 21** — gate reviews. Day 7: are we on track? Day 14: are findings closed? Day 21: audit-ready? |
| [Harmonization Retrospective](../../workflows/harmonization-retrospective.md) | Day 21 only, but extended (2 hrs) — capture pattern for future strikes |
| Exploration Time | **Suspended** for 21 days — the strike has full priority |

### Day-by-Day Shape

| Days | Focus |
|---|---|
| 0 | Kickoff. Classify findings. Assign owners. Approve remediation strategies. |
| 1-7 | Critical findings (5). One Critical per day target. AI-assisted patches; senior sign-off mandatory. |
| 8-14 | High findings (6). Run two High findings per day with two pairs working. |
| 15-18 | Medium findings (3) + cross-cutting recurrence-prevention controls (the "control" half of "patch + control") |
| 19-20 | Audit evidence package compiled and reviewed; full regression check; auditor pre-walkthrough |
| 21 | Auditor formal walkthrough; audit closure |

---

## Decision Spectrum in Practice

This is the archetype where the Decision Spectrum from [`CLAUDE.md`](../../CLAUDE.md) earns its place. **Default skews Pure-Human under time pressure.**

| Decision | Type | Who decides | Why |
|---|---|---|---|
| Remediation strategy per finding | Pure Human | Aki + Ren | Compliance interpretation is human judgment |
| AI-assisted patch implementation | Pure AI then Hybrid sign-off | Code Co-Creator generates; senior eng (Aki, Marco, or Ren) signs off line-by-line | **No AI-assisted code reaches main without senior sign-off** — Amazon-Kiro lesson |
| "Control" design (recurrence prevention) | Pure Human | Aki + Ren + auditor liaison | Wrong control = audit reopens later |
| Production deploy timing | Pure Human (Lin, oncall) | Lin + Aki | Revenue path; irreversible blast radius |
| Audit evidence package wording | Hybrid | Documentation & Knowledge drafts; Aki + auditor liaison ratify | Auditor reads this; tone matters |
| Whether to escalate "we will miss Day 21" | Pure Human | Aki, immediately, to CTO + CISO | Earlier honesty is cheaper than later excuse |
| Continuing vs. stopping the strike if a regression goes to prod | Pure Human | Aki + Lin | All-stop authority is named ahead of time |

---

## Metrics Watched

| Metric | Target | Why primary |
|---|---|---|
| **Audit-finding closure rate** | 14/14 by Day 21 | The mission |
| **Change Failure Rate** | < 2% — no regression in revenue path tolerable | Speed cannot break the production path |
| **Senior sign-off latency** | < 4 hours, p95 | If sign-off is the bottleneck, the strike fails |
| **Audit-evidence completeness** | 100% per finding by Day 19 | Auditor wants paper trail, not promises |
| **MTTR** | < 30 min if a regression occurs | Reliability discipline holds |
| **AI Task Sophistication** | L4 avg | AI is doing real work; not autocomplete |
| **Burnout risk** | Green throughout | Strike + tight deadline = highest risk; daily check |
| **Emergence events** | ≥ 1 logged | Even strikes produce insights worth keeping |

The **critical rule** ([`metrics/README.md`](../../metrics/README.md)) applies hardest here: if findings close while change failure rate spikes, that is a **failure**, not a partial win.

---

## Risks (Project-Specific)

| Risk | Mitigation |
|---|---|
| Senior sign-off becomes the bottleneck | Twice-daily sign-off windows scheduled; Aki + Marco + Ren rotate; no senior single point of failure |
| AI-assisted patch passes review but introduces subtle regression | Quality Analyst's continuous regression check; Lin's traffic-shadowing on revenue paths; canaries before full rollout |
| Burnout in days 14-21 | Twice-daily energy check; Aki has explicit authority to call hard stops; the strike model has a built-in expiration |
| Auditor adds a finding mid-strike | Aki escalates to CISO immediately; do not silently absorb scope |
| One finding cannot be remediated in 21 days | Day 7 gate reviews would surface this; compensating control + auditor exception path agreed Day 0 |
| The unit produces compliance debt (rushed control = future finding) | Day 21 retrospective produces a "follow-up backlog" with named owners and dates |
| Industry pattern: rushed AI-assisted code → incident | Amazon-Kiro lesson direct counter: senior sign-off is non-negotiable; Goldman lesson: aggressive *and* governed |

---

## Emergence Opportunities

Even under strike conditions:
- **A "patch + control" generalizes to a platform pattern.** Ren + Architecture Explorer design a recurrence-prevention control for finding #3 that is so clean it becomes the platform-default approach for all future authn boundaries — captured for the [Scale & Reliability unit](../../cognitive-units/scale-reliability.md) backlog post-strike.
- **The audit-evidence-package format becomes a template.** Documentation & Knowledge produces evidence packages so consistently good that compliance + legal adopt them as the company-wide format.
- **The strike-form cognitive unit is itself the pattern.** Aki notices on Day 21 that 21-day strike units are the right answer for *several* situations (regulatory deadlines, security incidents, partner integrations with hard dates). The retrospective produces a "Strike Unit Playbook."

Log in [`emergence-detection.md`](../../transformation/emergence-detection.md).

---

## What You Can Reuse

| Asset | Notes |
|---|---|
| **Strike unit pattern** | Temporary cognitive unit, dissolves when work is done. Use for any 14-30 day high-stakes work. |
| **Compressed ceremony cadence** | Twice-daily Harmony Check; Day-7/14/21 gate reviews; suspended Exploration Time |
| **Senior sign-off windows** | Time-boxed twice a day so AI-assisted PRs never block > 4 hrs |
| **"Patch + control" remediation pattern** | Every audit finding gets both: the fix and the recurrence-prevention control |
| **Audit-evidence package format** | Template lifted from Documentation & Knowledge agent's outputs |
| **All-stop authority named on Day 0** | Aki + Lin can stop deploys without negotiation; named explicitly in the kickoff |

---

## Why This Example Belongs in HIO

It is tempting to think HIO is a long-game framework — 26 weeks, identity work, cultural transformation. This example is here to refute that. **HIO produces tactical short-term gain on Day 1.** The framework's pieces — agent types, cognitive functions, ceremonies, decision spectrum, metrics — are *load-bearing* under 21-day pressure. Specifically:

| HIO mechanism | What it does in 21 days |
|---|---|
| 6 AI agent types | 5 of them deployed; AI handles execution while humans handle judgment |
| 10 cognitive functions | Quality Guardian + Solution Architect + Stakeholder Harmonizer composition fits the work; named explicitly so members can switch frequencies fast |
| Decision Spectrum | Tells everyone *who decides what* without a meeting |
| Senior sign-off (per `org/policies.md`) | Industry lesson made operational; the difference between Amazon's outage and a clean strike |
| Metrics layered (DORA + AI Util + Fulfillment) | Speed without quality is failure; metrics catch the trade-off in real time |
| Ephemeral cognitive unit | The unit forms for the work and dissolves when done — a `cognitive-units/README.md` first-class pattern |

---

## Tactical Business Gain Summary

| Gain | Value |
|---|---|
| PCI-DSS compliance retained | ~$8M quarterly revenue protected |
| 14 findings closed | Audit closed clean |
| Patch + control pattern established | 6+ audit findings prevented in next cycle |
| Strike unit pattern proven | Reusable for the next regulatory or partner deadline |
| Audit evidence package format adopted company-wide | Compliance velocity for the next year |
| AI-assisted execution under governance proven | Cultural ammunition that "aggressive + governed" works (Goldman lesson made local) |
| Capability development visible | Marco moved L3 → L4 on System Design; Jordan moved L3 → L4 on Eval/Observability and Security |
| Burnout green at Day 21 | Validated that the strike model has guardrails the team trusts |
