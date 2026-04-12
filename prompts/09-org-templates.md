# Org Templates Prompt: Generate org/ and templates/ (14 files)

## Objective

Generate 6 organizational template files in org/ and 8 Jinja2 template files in templates/. The org/ directory holds organization-specific configuration that adapts the framework to a particular company. The templates/ directory holds reusable Jinja2 templates for generating ceremony artifacts.

## org/ Files (6 files)

### 3 Organizational Profile Templates

| File | Purpose | Lines |
|------|---------|-------|
| profile.md | Company context, team size, engineering culture | 70-90 |
| infrastructure.md | Tech stack, CI/CD, cloud provider, monitoring | 60-80 |
| policies.md | Engineering policies, compliance, security requirements | 60-80 |

These files use `[placeholder]` markers for organization-specific values:

```markdown
## Company Overview
- **Organization**: [Company Name]
- **Engineering Team Size**: [Total engineers]
- **Platform Team Size**: [Platform engineers]
- **Current Methodology**: [Scrum/Kanban/SAFe/Other]
```

### 3 HIO-Specific Templates

| File | Purpose | Lines |
|------|---------|-------|
| cognitive-profiles.md | Maps each team member to their cognitive functions | 80-100 |
| working-agreements.md | Unit-level working agreements template | 70-90 |
| measurement-baseline.md | Current metric values before transformation | 80-100 |

These files use tables with `[placeholder]` values:

```markdown
## Team Cognitive Profiles
| Person | Primary Function | Secondary Function | Tertiary Function |
|--------|-----------------|-------------------|-------------------|
| [Name] | [Function] | [Function] | [Function] |
```

Content guidance:
- **profile.md**: Sections for company overview, team structure, engineering culture assessment (5 questions), current pain points, transformation goals.
- **infrastructure.md**: Sections for cloud platform, CI/CD pipeline, monitoring stack, collaboration tools, AI tooling current state, integration readiness assessment.
- **policies.md**: Sections for code review policy, deployment policy, security requirements, compliance constraints, data handling, AI usage policy.
- **cognitive-profiles.md**: Team roster table, function discovery questionnaire (10 questions), function distribution visualization guide, and profile update cadence.
- **working-agreements.md**: Template for each unit covering communication norms, decision-making process, AI agent usage guidelines, escalation paths, and meeting cadence.
- **measurement-baseline.md**: Current values for all 9 metric categories, data collection method for each, confidence level, and date captured.

## templates/ Files (8 Jinja2 Templates)

All template files use `.md.j2` extension and Jinja2 syntax with `{{ variable }}` placeholders.

| File | Purpose | Lines |
|------|---------|-------|
| confluence-unit-page.md.j2 | Confluence page for a cognitive unit | 50-70 |
| confluence-sprint-report.md.j2 | Sprint report published to Confluence | 60-80 |
| jira-harmonized-sprint.md.j2 | Jira sprint configuration template | 40-60 |
| jira-emergence-ticket.md.j2 | Jira ticket for emergence events | 40-50 |
| sprint-kickoff-agenda.md.j2 | Agenda document for sprint kickoff ceremony | 50-70 |
| retrospective-template.md.j2 | Retrospective facilitation template | 50-70 |
| weekly-pulse-report.md.j2 | Weekly pulse survey results report | 40-60 |
| monthly-review-deck.md.j2 | Monthly review presentation outline | 50-70 |

Content guidance for Jinja2 templates:
- Use `{{ unit_name }}`, `{{ sprint_number }}`, `{{ date }}`, `{{ participants }}` as common variables
- Use `{% for metric in metrics %}` loops for dynamic metric sections
- Use `{% if phase >= 2 %}` conditionals for phase-dependent content
- Include `{# Comment explaining the variable #}` Jinja2 comments for documentation
- Each template should be immediately usable with a simple variable dictionary

## Formatting Rules

- org/ files use `[placeholder]` markers in square brackets
- templates/ files use `{{ variable }}` Jinja2 syntax
- Both directories must have no YAML frontmatter
- org/ files must include Organization Extension Point sections
- templates/ files must include a variable reference comment block at the top listing all required variables
- 40-100 lines per file
- Cross-reference cognitive functions and agents by canonical name
