# Metrics: Harmonization

## Purpose

Metrics for how well humans and AI work together -- the defining differentiator of the HIO model. Harmonization captures the quality of collaboration between human and artificial intelligence, and the emergence of patterns that neither could produce alone.

Harmonization sits in Layer 3 (HIO) and is the most important category for HIO transformation success. If DORA improves but harmonization does not, you have a faster engineering org but not an HIO org. If harmonization improves, the other metrics will follow.

---

## KPIs

| KPI | What It Measures | How to Capture | Target Direction | Frequency |
|---|---|---|---|---|
| Emergence Rate | Documented emergence events per quarter | Emergence log (team-reported moments where human-AI collaboration produced unexpected value) | Higher (target 8+ per quarter) | Quarterly (tracked continuously) |
| Cross-Role Contribution | Frequency of people contributing outside their primary cognitive function | Cognitive function rotation logs + peer observation | Higher (trending up) | Monthly |
| Workflow Experimentation | New human-AI workflow patterns tried per sprint | Experiment log from weekly retrospectives | Higher (1+ per unit per sprint) | Sprint |
| Bandwidth Expansion | Number of people actively developing new cognitive functions | Self-report + function rotation records | Higher (>50% of org) | Monthly |
| Collaboration Effectiveness | Outcomes achieved through human-AI collaboration vs. solo work | Comparative task analysis (paired vs. solo outcomes) | Higher (collab outperforms solo) | Monthly |
| Task-Fulfillment Alignment | % of tasks matched to people's growth goals | Task assignment records cross-referenced with growth goals | Higher (>60%) | Sprint |

---

## What Is an Emergence Event?

An emergence event is a documented instance where human-AI collaboration produced an outcome that neither the human nor the AI would have reached independently. Examples:

- A developer uses AI analysis to discover an architectural pattern that solves a long-standing design problem in a novel way.
- An AI agent surfaces a cross-repository dependency issue that leads a team to redesign their service boundary -- a change no individual would have initiated.
- A team's workflow experiment (human ideation + AI prototyping + human refinement) produces a feature in 2 days that the team estimated would take 2 weeks.

Emergence events are not just "AI saved time." They are qualitative breakthroughs in capability. The Emergence Rate target of 8+ per quarter means roughly 2 per month across the ~30-person org.

---

## Baseline Capture

Harmonization metrics will likely have a near-zero baseline for most organizations. This is expected -- these patterns do not exist before the HIO transformation begins.

To establish what baseline exists:

1. Ask teams whether they have experienced anything resembling emergence in the [baseline-survey.md](baseline-survey.md) Team Collaboration section.
2. Review whether any cross-function contribution patterns already exist (people contributing outside their role).
3. Document current human-AI workflow patterns as the starting point for experimentation tracking.

---

## Interpretation Guide

- **Emergence Rate** of 0 in the first month is normal. If still 0 by Week 10, investigate whether the org has sufficient AI utilization depth (L3+) and psychological safety to experiment.
- **Cross-Role Contribution** measures whether the cognitive unit model is working. If people stay locked in one function, the unit is a renamed team, not a cognitive unit. See [../cognitive-functions/](../cognitive-functions/) for rotation guidance.
- **Workflow Experimentation** at 0 per sprint means the unit has stopped trying new approaches. This is the first signal of stagnation. Even failed experiments count -- the metric tracks experimentation behavior, not success rate.
- **Bandwidth Expansion** below 30% of the org by Week 13 means the identity and growth dimension of the transformation is lagging. People need explicit encouragement, safety, and time to develop new cognitive functions.
- **Collaboration Effectiveness** where solo consistently outperforms collaboration means human-AI workflows are poorly designed. The collaboration is adding friction rather than value. Redesign the workflow before pushing more collaboration.
- **Task-Fulfillment Alignment** below 40% means task assignment is purely delivery-driven with no attention to growth. This undermines human fulfillment and eventually undermines delivery as well.

---

## Connection to Other Categories

**Feeds:**
- All Layer 2 categories -- harmonization is the engine that drives better outcomes
- Human Fulfillment -- effective collaboration and growth directly increase fulfillment
- Innovation -- emergence events are a form of innovation; cross-function contribution brings diverse perspectives

**Fed by:**
- AI Utilization -- deep AI engagement (L3+) is a prerequisite for harmonization
- Human Fulfillment -- fulfilled, psychologically safe humans are more willing to experiment with collaboration
- SPACE/DX -- focus time and low friction create the conditions for deep collaboration

---

## Harmonization and the Transformation Arc

Across the 26-week transformation, expect harmonization to follow this arc:

- **Weeks 1-6 (Phase 1):** Baseline near zero. First workflow experiments begin. Cross-role contribution is awkward.
- **Weeks 7-13 (Phase 2):** First emergence events documented. Workflow experimentation becomes routine. Bandwidth expansion accelerates.
- **Weeks 14-20 (Phase 3):** Emergence rate reaches target. Collaboration effectiveness demonstrably exceeds solo work. Task-fulfillment alignment improves.
- **Weeks 21-26 (Phase 4):** Harmonization patterns are self-sustaining. The org generates new patterns without external prompting.

---

## Organization Extension Point

> **YOUR_ORG:** Define what emergence looks like in your specific domain. The examples above are generic -- your emergence events will be specific to your platform, your consumers, and your technical context. Create a shared emergence log (wiki page, Slack channel, or dedicated tool) where anyone can document emergence events as they happen. Review the log in weekly Harmony Pulse sessions and monthly deep dives.
