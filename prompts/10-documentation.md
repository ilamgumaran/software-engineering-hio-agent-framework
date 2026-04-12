# Documentation Prompt: Generate Root Documentation Files (5 files)

## Objective

Generate the 5 root-level documentation files that orient readers to the HIO agent framework. These files are the entry points for different audiences: engineers, leaders, AI assistants, and adopters.

## Files to Generate

| File | Audience | Lines |
|------|----------|-------|
| README.md | Everyone -- first file people read | 80-120 |
| PLAN.md | Leaders -- executive summary of the transformation | 60-80 |
| CUSTOMIZATION.md | Adopters -- step-by-step guide to adapt the framework | 80-100 |
| DIRECTORY_GUIDE.md | Everyone -- map of every file and its purpose | 120-160 |
| CLAUDE.md | AI assistants -- context for operating within HIO | 40-60 |

## README.md Structure

Include these sections in order:

1. **Title and tagline**: "Harmonized Intelligence Orchestration Agent Framework" with one-line description
2. **What is HIO**: 2-3 paragraph explanation of the framework's purpose
3. **Core Concepts table**: 4-row table mapping Traditional to HIO equivalents (Roles->Functions, Teams->Units, Sprints->Harmonized Sprints, Metrics->Three-Layer Metrics)
4. **The HIO Model**: List of 10 functions, 6 agents, 5 units with one-line descriptions each
5. **Directory tree**: Text representation of the full project structure
6. **Getting Started**: 4-step quickstart (read overview, fill org templates, choose first unit, begin Phase 0)
7. **Links**: Cross-references to PLAN.md, CUSTOMIZATION.md, DIRECTORY_GUIDE.md

## PLAN.md Structure

Include these sections:

1. **Executive Summary**: 2-3 paragraphs on why HIO and what it achieves
2. **The 4 Phases**: Summary table with phase name, weeks, objective, and key deliverable
3. **Expected Outcomes**: Quantified targets (deployment frequency, developer satisfaction, AI utilization)
4. **Detailed Plans**: Links to all 6 plan/ documents
5. **Phase Details**: Links to all 4 plan/phases/ summaries

## CUSTOMIZATION.md Structure

Include a 7-step adoption guide:

1. **Step 1: Assess Current State** -- Fill in org/profile.md and org/infrastructure.md
2. **Step 2: Capture Baselines** -- Use metrics/baseline-survey.md, fill org/measurement-baseline.md
3. **Step 3: Map Cognitive Functions** -- Run function discovery, fill org/cognitive-profiles.md
4. **Step 4: Choose Your Domain** -- Copy domains/platform-engineering/ or create new domain
5. **Step 5: Adapt Metrics** -- Review 9 metric categories, adjust targets to your context
6. **Step 6: Configure Templates** -- Customize Jinja2 templates for your tooling (Confluence, Jira)
7. **Step 7: Begin Phase 0** -- Follow transformation/phase-0-seed.md

Each step should include: what to do, which files to edit, and expected time investment.

## DIRECTORY_GUIDE.md Structure

List every file in the project with a one-line description, organized by directory:

```markdown
## cognitive-functions/
- `README.md` -- Composition model and function mapping tables
- `builder.md` -- Builder function: code creation and system construction
...
```

Cover all directories: cognitive-functions/, agents/, cognitive-units/, workflows/, metrics/, transformation/, plan/, plan/phases/, org/, domains/platform-engineering/, templates/, prompts/, and root files.

## CLAUDE.md Structure

Include these sections for AI assistant context:

1. **Project Context**: One paragraph describing the HIO framework
2. **Canonical Names**: All 10 functions, 6 agents, 5 units listed
3. **Key Conventions**: No YAML frontmatter, Title Case names, bold actor labels, Organization Extension Points
4. **File Organization**: Brief description of each directory's purpose
5. **When Editing**: Rules for maintaining consistency (mapping tables, naming, cross-references)

## Formatting Rules

- No YAML frontmatter on any file
- README.md must be the most polished and inviting file in the project
- DIRECTORY_GUIDE.md must be comprehensive -- every single file listed
- CUSTOMIZATION.md must use numbered steps with clear action items
- CLAUDE.md must be concise and machine-readable
- Cross-references use relative paths throughout
