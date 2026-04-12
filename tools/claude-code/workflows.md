# Claude Code -- HIO Workflows

Six HIO-specific workflows executed through Claude Code. Each workflow maps to a harmonized sprint ceremony or recurring agent task defined in `workflows/`.

---

## 1. Execute a Sprint Kickoff

Pre-analysis workflow that feeds into the Sprint Kickoff ceremony (`workflows/sprint-kickoff.md`).

**Trigger:** Beginning of each harmonized sprint (typically every 2 weeks).

**Flow:**

1. Activate as **Analysis Partner**
2. Review the sprint backlog items and acceptance criteria
3. For each item, analyze: prior art in the codebase, related patterns, dependencies, risk factors
4. Cross-reference with `metrics/` current state for relevant metric categories
5. Generate a pre-analysis brief per item with complexity estimate, suggested approach, and risks
6. Activate as **Metrics Monitor** to compile baseline metrics snapshot for the sprint
7. Produce the Sprint Kickoff document using `templates/hio/sprint-kickoff.md.j2`

**Expected Outcome:** A pre-analysis package ready for the human team to review during the Sprint Kickoff ceremony, reducing ceremony time and increasing decision quality.

---

## 2. Run a Harmony Check

Daily metrics snapshot supporting the Daily Harmony Check (`workflows/daily-harmony-check.md`).

**Trigger:** Daily, before the harmony check ceremony.

**Flow:**

1. Activate as **Metrics Monitor**
2. Pull overnight alerts from monitoring systems (via MCP integrations)
3. Check deployment pipeline status and any failures
4. Scan for open incidents or degraded services
5. Compile a 5-line summary: what shipped, what broke, what needs attention, what is on track, what is at risk
6. Flag any anomalies in DORA or platform health metrics

**Expected Outcome:** A concise daily snapshot that keeps the harmony check under 10 minutes.

---

## 3. Perform Agent-Assisted Code Review

Collaborative code review combining Quality Analyst and Code Co-Creator perspectives.

**Trigger:** Pull request opened or review requested.

**Flow:**

1. Activate as **Quality Analyst**
2. Analyze the changeset for: correctness, security implications, performance impact, test coverage, code health metrics
3. Flag issues by severity (blocking, important, suggestion)
4. Switch to **Code Co-Creator**
5. For each blocking or important issue, generate a suggested fix with explanation
6. Assess overall alignment with architecture patterns from `domains/platform-engineering/`
7. Produce a structured review comment with findings and suggestions

**Expected Outcome:** A thorough review that catches issues early and provides actionable fixes, not just complaints.

---

## 4. Generate Architecture Options

Architecture exploration workflow supporting design decisions (`workflows/deep-work-collaboration.md`).

**Trigger:** New feature design, system redesign, or technology evaluation.

**Flow:**

1. Activate as **Architecture Explorer**
2. Gather constraints: performance requirements, team capabilities, timeline, existing systems
3. Generate 3-5 architecture options, each with: description, diagram sketch, tradeoff analysis, implementation estimate
4. Evaluate each option against the constraint set
5. Rank options with reasoning
6. Activate as **Analysis Partner** to check for patterns from similar decisions in the codebase or documentation
7. Produce a decision brief with options, recommendation, and reversibility assessment

**Expected Outcome:** A structured options analysis that enables informed architecture decisions in the Sprint Kickoff or dedicated design sessions.

---

## 5. Create Sprint Outcome Report

End-of-sprint reporting combining metrics and narrative (`workflows/sprint-outcome-review.md`).

**Trigger:** End of each harmonized sprint.

**Flow:**

1. Activate as **Metrics Monitor**
2. Compute sprint metrics across all 9 categories (see `metrics/README.md`)
3. Compare against baseline and previous sprint
4. Identify trends (improving, stable, declining) per category
5. Switch to **Documentation & Knowledge**
6. Compile emergence events logged during the sprint
7. Synthesize narrative: what was accomplished, what emerged, what was learned
8. Generate the Sprint Outcome Report and Weekly Harmony Pulse (`templates/hio/harmony-pulse.md.j2`)

**Expected Outcome:** A data-rich outcome report that serves the Sprint Outcome Review ceremony and feeds the retrospective.

---

## 6. Log an Emergence Event

Capture unexpected value from human-AI collaboration (`transformation/emergence-detection.md`).

**Trigger:** When an unexpected insight, capability, or outcome is observed during any workflow.

**Flow:**

1. Activate as **Documentation & Knowledge**
2. Capture the event: what happened, who was involved, what was unexpected
3. Classify the emergence type: insight (new understanding), capability (new skill), serendipity (lucky discovery), synergy (1+1=3 collaboration)
4. Assess impact: immediate value, potential future value, replicability
5. Log the event using `templates/hio/emergence-log.md.j2`
6. Cross-reference with existing emergence patterns to identify recurring themes

**Expected Outcome:** A structured emergence log entry that feeds the retrospective and contributes to the organization's understanding of where human-AI collaboration creates outsized value.
