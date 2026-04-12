# Customization Guide

How to adopt the HIO framework for your organization. This guide walks through a 7-step process from fork to first sprint.

---

## Step 1: Fork and Read

Fork this repository into your organization's source control. Before changing anything, read these files to understand the full picture:

- `plan/00-overview.md` -- strategic context and end-state vision
- `transformation/README.md` -- the 26-week transformation approach
- `cognitive-functions/README.md` -- the 10 cognitive functions model
- `agents/README.md` -- the 6 AI agent types

**Time:** 2-3 hours for a thorough read.

---

## Step 2: Define Your Purpose

Workshop a purpose statement with your leadership team. A strong HIO purpose statement passes the **4 HIO Tests**:

1. **Curiosity Test** -- Does it make people want to explore further?
2. **Translation Test** -- Can every team member explain it in their own words?
3. **Win-Win Test** -- Does it serve both the organization and the individual?
4. **Horizon Test** -- Is it ambitious enough to sustain a multi-year journey?

Update `org/profile.md` with your purpose statement, team context, and organizational constraints.

**Time:** Half-day workshop.

---

## Step 3: Map Your Team

Have each team member complete a cognitive profile using `org/cognitive-profiles.md`. This maps their current strengths and growth interests across the 10 cognitive functions. Use the results to:

- Identify coverage gaps (functions with no strong practitioners)
- Find natural pioneers (people drawn to multiple functions)
- Plan growth paths (where people want to develop)

**Time:** 30 minutes per person + 2-hour synthesis session.

---

## Step 4: Choose Your Domain

Platform engineering is the reference domain in `domains/platform-engineering/`. If you are a platform engineering team, review and customize those files. If you are in a different discipline:

1. Create a new directory under `domains/` (e.g., `domains/data-engineering/`)
2. Follow the structure in `domains/README.md`
3. Define domain-specific skills, workflows, evaluation criteria, and glossary

**Time:** 1-2 days for a new domain.

---

## Step 5: Configure Your Agents

Set up AI tooling for your team:

1. Review `tools/` for guides on each supported tool (Claude Code, GitHub Copilot, Gemini Enterprise, Glean)
2. Customize `CLAUDE.md` with your organization's context, policies, and domain references
3. Configure agent-specific integrations per `tools/claude-code/workflows.md`
4. Ensure all team members have access to required AI tools per `org/infrastructure.md`

**Time:** 1-2 days for setup and verification.

---

## Step 6: Capture Your Baseline

Before starting the transformation, measure where you are today:

1. Complete the **baseline survey** using `metrics/baseline-survey.md`
2. Fill in **measurement baseline** at `org/measurement-baseline.md`
3. Gather existing metrics (DORA, developer surveys, incident data)
4. Document current processes and pain points

This baseline is critical -- you cannot demonstrate improvement without it.

**Time:** 1 week for data collection.

---

## Step 7: Begin Transformation

Start Phase 0 with `transformation/phase-0-seed.md`. Follow the 26-week guide through all 4 phases. Key checkpoints:

- **Week 3:** Phase gate review (Phase 0 exit criteria in `plan/phases/phase-0-seed.md`)
- **Week 10:** First unit retrospective and scaling decision
- **Week 18:** Multi-unit data review and full-org commitment
- **Week 26:** Transformation outcome assessment

**Time:** 26 weeks, with ongoing effort.

---

## What to Customize vs. What to Keep

| Keep As-Is | Customize | Optional |
|---|---|---|
| `cognitive-functions/` definitions | `org/profile.md` -- your team context | `domains/` -- add your discipline |
| `agents/` definitions | `org/cognitive-profiles.md` -- your people | `templates/` -- match your tools |
| `workflows/` ceremony structures | `org/policies.md` -- your constraints | `prompts/` -- regeneration prompts |
| `metrics/` category definitions | `org/working-agreements.md` -- your norms | `tools/` -- your AI tool stack |
| `transformation/` principles | `org/measurement-baseline.md` -- your data | |
| `cognitive-units/` structure | `org/infrastructure.md` -- your environment | |
| | `CLAUDE.md` -- your agent configuration | |
| | `metrics/` targets -- your goals | |
| | `transformation/` timeline -- your pace | |

---

## Organization Extension Points

The framework is designed for extension in these areas:

- **New cognitive functions** -- If your domain requires functions beyond the core 10, add them to `cognitive-functions/` following the existing format
- **New agent types** -- If you integrate AI tools beyond the core 6, add agent definitions to `agents/`
- **New cognitive units** -- If your organization has outcome areas beyond the core 5, add units to `cognitive-units/` using `cognitive-units/_template.md`
- **New metrics categories** -- If you need measurement dimensions beyond the core 9, add them to `metrics/`
- **New workflows** -- If your team has ceremonies beyond the core set, add them to `workflows/`
