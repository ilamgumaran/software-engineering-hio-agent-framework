# Metrics: AI Utilization

## Purpose

Metrics for how effectively AI agents are being used across the organization. These measure not just whether people use AI, but how deeply and creatively they engage with AI capabilities.

AI Utilization sits in Layer 3 (HIO) because how the organization uses AI agents is a defining characteristic of the HIO model. The goal is not maximum AI usage -- it is appropriate AI usage that amplifies human capability.

---

## KPIs

| KPI | What It Measures | How to Capture | Target Direction | Frequency |
|---|---|---|---|---|
| AI Usage Depth | Frequency and breadth of AI agent engagement across workflows | Agent interaction logs + self-report | Higher (all teams, multiple workflows) | Weekly |
| Task Sophistication Level | Complexity of tasks delegated to AI (1-5 scale) | Categorize agent interactions by sophistication tier | Higher (average trending toward L3+) | Weekly |
| Time Savings | Estimated hours saved by AI agents per sprint | Before/after task duration estimates + team self-report | Higher (trending up) | Sprint |
| Suggestion Acceptance Rate | % of AI suggestions used without major revision | Agent output tracking (accepted / modified / rejected) | Higher (>60% for routine tasks) | Weekly |
| Novel Applications | Creative or unexpected uses of AI agents | Team-reported novel use cases (innovation log) | Higher (1+ per sprint per unit) | Sprint |
| Capability Utilization Rate | % of available agent capabilities being actively used | Agent capability inventory vs. usage telemetry | Higher (>50%) | Monthly |

---

## Task Sophistication Levels

| Level | Description | Examples |
|---|---|---|
| L1: Autocomplete | AI completes fragments of in-progress work | Code completion, sentence finishing, template filling |
| L2: Generation | AI generates artifacts from specifications | Code from spec, test cases from requirements, docs from code |
| L3: Analysis & Recommendation | AI analyzes data and recommends actions | Code review, architecture suggestions, metric anomaly detection |
| L4: Autonomous Workflow | AI executes multi-step workflows with human oversight | Automated deployment pipelines, incident response, dependency updates |
| L5: Emergence Collaboration | AI and human co-create, producing outcomes neither could alone | Novel architecture patterns, creative problem-solving, workflow invention |

The target progression across the 26-week transformation:
- **Weeks 1-6:** Most interactions at L1-L2. L3 emerging.
- **Weeks 7-13:** L2-L3 dominant. L4 experiments begin.
- **Weeks 14-20:** L3-L4 dominant. L5 emergence events documented.
- **Weeks 21-26:** L3-L5 routine. Teams choosing the right level for each task.

---

## Baseline Capture

To establish your AI Utilization baseline:

1. Survey current AI tool usage across the org using the AI Collaboration section of the [baseline-survey.md](baseline-survey.md).
2. Categorize current usage by sophistication level.
3. Identify which agent capabilities exist but are not being used (capability gap).
4. Estimate current time savings from any AI tooling already in place.

Many orgs will find their baseline is heavily concentrated at L1-L2. This is normal and expected.

---

## Interpretation Guide

- **AI Usage Depth** that is high but narrow (one team, one workflow) means adoption has not spread. Investigate what is blocking other teams -- training, tooling access, or skepticism.
- **Task Sophistication Level** stuck at L1-L2 after Week 13 suggests the organization needs more training, better agent configuration, or reduced fear of delegation. See [../agents/](../agents/) for agent capability progression.
- **Time Savings** is the most politically useful metric. When stakeholders ask "is AI worth it?", time savings provides a concrete answer. Track conservatively -- overestimating erodes credibility.
- **Suggestion Acceptance Rate** below 40% for routine tasks means the agent is poorly calibrated to the codebase or the team's standards. Tune the agent rather than forcing adoption.
- **Novel Applications** is a leading indicator of L5 emergence. When teams start finding uses for AI that nobody planned, the human-AI collaboration pattern is working.
- **Capability Utilization Rate** below 30% means the org has invested in tools it is not using. Close the gap through training, workflow integration, or honest assessment of whether those capabilities are needed.

---

## Connection to Other Categories

**Feeds:**
- DORA -- AI-assisted code review and automated testing reduce lead time and change failure rate
- Code Health -- AI code analysis and automated refactoring improve rework and defect rates
- SPACE/DX -- appropriate AI use reduces friction and frees focus time
- Innovation -- AI handling maintenance frees human time for exploration
- Harmonization -- AI utilization depth is a prerequisite for human-AI harmonization

**Fed by:**
- Human Fulfillment -- AI Collaboration Readiness determines how quickly utilization can deepen
- Harmonization -- effective collaboration patterns increase willingness to use AI more deeply

---

## Organization Extension Point

> **YOUR_ORG:** Inventory your current AI tooling (Copilot, Claude, custom agents, etc.) and map each tool to the sophistication levels above. Identify which levels are accessible with current tooling and which require new capabilities. Define what L4 and L5 look like for your specific workflows -- these will differ significantly between orgs.
