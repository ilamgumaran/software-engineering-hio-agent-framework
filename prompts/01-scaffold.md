# Scaffold Prompt: Generate Directory Structure and Root Files

## Objective

Create the complete directory structure and root-level files for the HIO agent framework. This establishes the skeleton that all other prompts populate.

## Directories to Create

Generate the following directory tree:

```
software-engineering-hio-agent-framework/
  cognitive-functions/
  agents/
  cognitive-units/
  workflows/
  metrics/
  transformation/
  plan/
    phases/
  org/
  domains/
    platform-engineering/
  templates/
  prompts/
```

Run these commands to create all directories:

```bash
mkdir -p cognitive-functions agents cognitive-units workflows metrics
mkdir -p transformation plan/phases org domains/platform-engineering
mkdir -p templates prompts
```

## Root Files to Create (7 files)

| File | Purpose | Lines |
|------|---------|-------|
| README.md | Project overview, role table, directory tree, getting started | 80-120 |
| PLAN.md | Executive summary referencing detailed plan/ documents | 60-80 |
| CUSTOMIZATION.md | 7-step guide for adapting the framework to a new organization | 80-100 |
| DIRECTORY_GUIDE.md | Every file in the project with a one-line purpose description | 120-160 |
| CLAUDE.md | Agent configuration providing HIO context for AI assistants | 40-60 |
| LICENSE | MIT license | standard |
| .gitignore | Ignore patterns for org/ secrets, OS files, editor files | 20-30 |

## File Creation Order

Generate files in this order to ensure cross-references resolve:

1. .gitignore and LICENSE (no dependencies)
2. CLAUDE.md (standalone agent config)
3. DIRECTORY_GUIDE.md (requires knowing all file paths)
4. README.md (references DIRECTORY_GUIDE and other root files)
5. PLAN.md (references plan/ directory)
6. CUSTOMIZATION.md (references org/ and domains/)

## Formatting Rules

- No YAML frontmatter on any file
- README.md must include a directory tree showing all top-level directories
- DIRECTORY_GUIDE.md must list every file across all directories with a one-line description
- CUSTOMIZATION.md must use numbered steps (Step 1 through Step 7)
- CLAUDE.md must list all 10 cognitive functions, 6 agents, and 5 units by name
- .gitignore must exclude org/ files that may contain sensitive organizational data
