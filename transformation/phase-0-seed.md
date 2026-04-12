# Phase 0: Seed (Weeks 1-3)

## Goal

Establish baseline metrics across all 9 categories, secure leadership alignment with explicit commitment, select the pioneer group, and stand up measurement infrastructure.

---

## Week 1: Foundation

### Day 1-2: Leadership Alignment

- Present the HIO framework to leadership — purpose, phases, expected outcomes
- Set expectations explicitly: **15% temporary productivity dip** in Phase 1, 6-month horizon to full transformation
- Agree on success criteria and reporting cadence (recommend monthly leadership briefings with the comparison board)
- Secure commitment to **not pull the plug during the dip** — this is the single most important leadership agreement
- Define the escalation path: what happens if exit criteria aren't met on schedule (answer: phases extend)

### Day 3: All-Hands Introduction

- Present the purpose: "Build the platform that makes impossible customer experiences possible — reinventing how humans and AI build software together along the way"
- Introduce **cognitive functions** concept — this is not a reorg, it's an evolution of how people contribute
- Walk through all 10 cognitive functions: **Builder**, **Problem Framer**, **Pattern Integrator**, **Resonance Sensor**, **Quality Guardian**, **Growth Catalyst**, **Solution Architect**, **Stakeholder Harmonizer**, **Fresh-Eyes Observer**, **Learner**
- Show the end-state vision and timeline
- Emphasize: this is **invitational, not mandatory** — nobody will be forced into anything

### Day 4-5: Baseline Capture

- Deploy baseline survey (see [../metrics/baseline-survey.md](../metrics/baseline-survey.md))
- Pull DORA metrics from CI/CD pipelines (4 weeks of historical data minimum)
- Capture current sprint velocity, backlog health, and cycle time
- Document current team structures, responsibilities, and informal collaboration patterns
- Record current AI tool usage levels across the org

---

## Week 2: Pioneer Selection

### Pioneer Selection Criteria

Select **6-8 people** for the first cognitive unit based on:

- **Genuinely curious** about new ways of working (not just compliant or looking for a promotion)
- **Mix of experience levels** — senior + mid + junior, not all seniors
- **Diverse cognitive function potential** — people who naturally gravitate toward different functions
- **Willing to be visible** and share learnings with the broader org
- **Psychologically safe enough** to admit when things aren't working

### Pioneer Workshop (1 Full Day)

- Deep dive into the HIO framework — not just overview, but working-level understanding
- **Cognitive function self-assessment** — each person maps their natural strengths and growth edges across the 10 functions (see [../cognitive-functions/](../cognitive-functions/))
- AI agent introduction and hands-on exploration — **Analysis Partner**, **Code Co-Creator**, **Architecture Explorer**, **Quality Analyst**, **Metrics Monitor**, **Documentation & Knowledge** (see [../agents/](../agents/))
- Co-create the first unit's **purpose statement** and **working agreements**
- Choose which cognitive unit to pilot — recommend **Experiment Velocity** for most visible early value (see [../cognitive-units/](../cognitive-units/))

---

## Week 3: Infrastructure Setup

### Measurement Infrastructure

- Set up automated DORA metric capture from CI/CD pipelines
- Configure AI utilization tracking (tool usage, task sophistication levels)
- Create **Harmony Pulse** template in the team's existing tools
- Establish the baseline comparison board — this becomes the central artifact for all phases
- Configure dashboards for all 9 metric categories (see [../metrics/](../metrics/))

### AI Agent Setup

- Configure **Claude Code** with the HIO agent framework prompts and context
- Set up **Code Co-Creator** workflows integrated with the team's IDE and review process
- Configure **Analysis Partner** for sprint pre-analysis with access to backlog and metrics
- Test **Metrics Monitor** with current data sources to validate automated capture
- Verify **Architecture Explorer** has access to codebase and documentation
- Ensure **Quality Analyst** integrates with test infrastructure

### Communication Setup

- Create a weekly update channel for the broader org (transparency, not broadcasting)
- Build the monthly leadership briefing template with comparison board data
- Establish an open invitation for anyone curious to observe sprint ceremonies
- Set up the emergence log (see [emergence-detection.md](emergence-detection.md))

---

## Exit Criteria

- [ ] Baseline metrics captured across all 9 categories (DORA, SPACE/DX, Platform Outcomes, Code Health, Innovation, Human Fulfillment, AI Utilization, Harmonization, Current/Legacy)
- [ ] Leadership committed to 6-month timeline with defined reporting cadence
- [ ] Pioneer group of 6-8 selected and briefed through full-day workshop
- [ ] First cognitive unit purpose defined and working agreements created
- [ ] AI agents configured and tested with real data
- [ ] Measurement infrastructure operational and producing automated dashboards
- [ ] Communication channels established and first update sent
- [ ] All-hands completed with positive or neutral reception (>70% engagement survey)

---

## Risks in This Phase

| Risk | Trigger | Mitigation | Monitor |
|------|---------|------------|---------|
| Leadership skepticism | Questions about ROI before data exists | Concrete metrics framework, industry benchmarks, commitment to exit criteria | Leadership sentiment in weekly check-ins |
| Low volunteer rate | Fewer than 6 willing pioneers | Make it invitational, highlight growth opportunity, ensure no career penalty for participating or not | Number of expressions of interest after all-hands |
| AI tool readiness | Security blocks, provisioning delays | Engage security team in Week 1, test tools in Week 3, have fallback plans | Tool access status tracker |
| Baseline data gaps | Missing metric categories | Identify gaps early, use manual capture as interim, prioritize automated sources | Baseline completeness checklist |

---

### Organization Extension Point

> **YOUR_ORG:** Adjust pioneer selection criteria based on your org's culture. If your org is highly skeptical, select pioneers who are respected and credible, not just enthusiastic. If your org already uses AI tools extensively, adjust baseline capture to differentiate casual use from sophisticated collaboration. Modify the first cognitive unit choice based on where the most visible pain exists.
