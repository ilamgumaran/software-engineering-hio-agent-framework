# Prompts

## Purpose

These prompts can regenerate the entire HIO agent framework from scratch. Use them to:

- Create a new instance for a different organization
- Regenerate sections after significant customization
- Adapt the framework for a different engineering domain

## Prompt System

| Prompt | What It Generates | File Count |
|--------|-------------------|------------|
| 00-master.md | Everything (single comprehensive prompt) | ~106 files |
| 01-scaffold.md | Directory structure and root files | ~7 files |
| 02-cognitive-functions.md | All 10 function definitions + README | 11 files |
| 03-agents.md | All 6 agent definitions + README | 7 files |
| 04-cognitive-units.md | All 5 unit definitions + README + template | 7 files |
| 05-workflows.md | All 6 workflow definitions + README | 7 files |
| 06-metrics.md | 9 metric categories + 4 templates + README | 14 files |
| 07-transformation.md | 4 phase guides + risk + coach + emergence + README | 8 files |
| 08-plan.md | 6 plan documents + 4 phase summaries | 10 files |
| 09-org-templates.md | 6 org config files + 8 Jinja2 templates | 14 files |
| 10-documentation.md | README, PLAN, CUSTOMIZATION, DIRECTORY_GUIDE, CLAUDE.md | 5 files |

## How to Use

1. **Full generation:** Use `00-master.md` to generate the complete framework
2. **Section regeneration:** Use individual prompts (01-10) for specific sections
3. **Customization:** After generation, fill in `org/` templates and adapt for your domain
4. **New domain:** Copy `domains/platform-engineering/` and use as template for your domain

## Design Principles

All prompts enforce these patterns:

- No YAML frontmatter -- pure markdown
- Consistent naming: Title Case for functions, agents, units
- Tables with 3+ data rows
- Bold actor labels in workflows
- Organization Extension Points for customization
- Cross-references between files

## Prompt Dependencies

Each prompt (01-10) is self-contained and can be used independently. However, for best results when regenerating individual sections, generate in numeric order so that cross-references align. The master prompt (00-master.md) handles all ordering automatically.

## Canonical Names

These names must be used identically in every generated file:

- **10 Cognitive Functions:** Builder, Problem Framer, Pattern Integrator, Resonance Sensor, Quality Guardian, Growth Catalyst, Solution Architect, Stakeholder Harmonizer, Fresh-Eyes Observer, Learner
- **6 AI Agents:** Analysis Partner, Code Co-Creator, Architecture Explorer, Quality Analyst, Metrics Monitor, Documentation & Knowledge
- **5 Cognitive Units:** Experiment Velocity, Scale & Reliability, Developer Experience, Intelligence Layer, Frontier
