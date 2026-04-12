# Metrics: Innovation

## Purpose

Innovation and exploration capacity metrics. These measure whether the organization is investing in the future -- generating new ideas, exploring novel approaches, and converting exploration into production value.

Innovation sits in Layer 2 (Outcome) because innovation capacity is a tangible organizational outcome, not just a cultural aspiration. Without measurement, exploration time gets consumed by maintenance pressure.

---

## KPIs

| KPI | What It Measures | How to Capture | Target Direction | Frequency |
|---|---|---|---|---|
| Innovation Rate | % of total engineering time spent on new capabilities vs. maintenance | Time tracking or work item classification (new feature vs. bug/debt/ops) | Higher (targeting 30%+) | Monthly |
| New vs Maintenance Ratio | Count of new feature work items / maintenance work items | Work item tracker labels and categories | Higher (trending toward 1:1 or better) | Sprint |
| Exploration-to-Production Rate | % of exploration/spike time that produces shippable ideas | Exploration log tracking from spike to production decision | Higher (>30%) | Quarterly |
| Ideas Generated | Number of new ideas logged per quarter | Idea backlog or innovation log (see Frontier cognitive function) | Higher (trending up) | Quarterly |

---

## Baseline Capture

To establish your Innovation baseline:

1. Classify the last quarter of completed work items into categories: new capability, maintenance/bug fix, tech debt remediation, operational toil.
2. Calculate the current innovation rate (new capability time / total time).
3. Review any formal exploration time (hack days, spike sprints, 20% time) from the last quarter. How many produced something that reached production or influenced a production decision?
4. Count ideas generated in any existing ideation process (brainstorms, retro action items, spike outcomes).

If your org does not currently track these categories, start with a simple classification pass on the last sprint's work items. Imperfect data now beats perfect data later.

---

## Interpretation Guide

- **Innovation Rate** below 15% means the team is in maintenance mode. This is common before transformation and is not a failure -- it is the starting condition the HIO model addresses. The Frontier cognitive function (see [../cognitive-functions/](../cognitive-functions/)) is specifically designed to protect and expand exploration capacity.
- **New vs Maintenance Ratio** below 1:3 means the team ships one new thing for every three maintenance tasks. During transformation, this ratio should steadily improve as AI agents absorb routine maintenance work.
- **Exploration-to-Production Rate** below 20% suggests exploration time is unfocused or disconnected from delivery. The Frontier function's role is to bridge exploration and production through structured experimentation.
- **Ideas Generated** is a leading indicator. A team that stops generating ideas has either lost exploration time or lost psychological safety. Check both.

---

## Innovation and the Frontier Function

The Frontier cognitive function (see [../cognitive-functions/](../cognitive-functions/)) is the primary driver of innovation metrics. When people operate in the Frontier function, they are:

- Exploring new technologies and approaches
- Running structured experiments
- Documenting learnings whether the experiment succeeds or fails
- Bridging exploration back to production workflows

Innovation metrics track whether the Frontier function is being activated and producing value. If innovation metrics are flat while other HIO metrics improve, check whether the unit is investing enough bandwidth in Frontier work.

---

## Connection to Other Categories

**Feeds:**
- Platform Outcomes -- innovation drives new platform capabilities and faster ask-to-experiment cycles
- Human Fulfillment -- intellectual challenge and growth come from exploration work
- Harmonization -- new human-AI workflow patterns often emerge from innovation experiments

**Fed by:**
- SPACE/DX -- focus time creates the space for exploration
- AI Utilization -- AI agents handling maintenance frees human time for innovation
- Current/Legacy -- lower maintenance burden (fewer bugs, less toil) releases capacity for new work

---

## Organization Extension Point

> **YOUR_ORG:** Define what counts as "innovation" vs. "maintenance" for your specific context. Some teams classify any non-backlog work as innovation; others require a formal experiment design. Choose a definition that is honest and consistent, then stick with it. If you have existing innovation programs (hack days, guild time, spike sprints), map their outputs to the Exploration-to-Production Rate metric.
