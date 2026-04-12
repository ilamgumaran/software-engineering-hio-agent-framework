# Gemini Enterprise -- HIO Tool Guide

## What It Does

Gemini Enterprise provides large-context AI analysis capabilities within the Google Cloud ecosystem. It can process extensive documents, large codebases, and broad datasets in a single pass. Within HIO, it supports the **Analysis Partner** agent type for tasks requiring wide-context understanding.

---

## Role in HIO

Gemini Enterprise is the **large-context analysis engine**. Where Claude Code excels at deep, multi-step workflows, Gemini Enterprise handles breadth -- analyzing massive inputs in a single context window.

| HIO Activity | Gemini Enterprise Role |
|---|---|
| Sprint Kickoff pre-analysis | Process large backlogs and historical data |
| Codebase-wide pattern detection | Analyze entire repositories for patterns and anti-patterns |
| Document analysis | Synthesize long specifications, RFCs, and design documents |
| Cross-system analysis | Compare patterns across multiple services or repositories |

---

## Best For

- **Analyzing large codebases** -- understanding patterns, dependencies, and architecture across thousands of files
- **Processing long documents** -- RFCs, specifications, compliance documents, audit reports
- **Extensive data analysis** -- large CSV files, log aggregations, metric time series
- **Cross-repository comparison** -- finding patterns and inconsistencies across multiple projects

---

## HIO Integration

- Feeds the **Analysis Partner** agent (`agents/analysis-partner.md`) during sprint kickoff preparation
- Supports the **Pattern Integrator** cognitive function (`cognitive-functions/pattern-integrator.md`) with cross-system analysis
- Results from Gemini analysis can be passed to Claude Code for action-oriented follow-up
- Complements Glean's knowledge search with deep-analysis capabilities

---

## Setup and Configuration

1. **Enable Gemini Enterprise** in your Google Cloud organization
2. **Configure access** for team members through Google Workspace admin
3. **Set up integrations** with your code repositories and document stores
4. **Define analysis templates** for recurring HIO workflows (sprint kickoff, quarterly review)
5. **Review policies** in `org/policies.md` for data handling requirements with cloud AI services

---

## Limitations

- Cloud-based processing -- data leaves your environment (review `org/policies.md` for constraints)
- Not designed for multi-step workflow orchestration (use Claude Code for that)
- Cannot execute code or make changes to your systems
- Best for analysis and synthesis, not implementation

---

## Related Files

- Analysis Partner agent: `agents/analysis-partner.md`
- Pattern Integrator function: `cognitive-functions/pattern-integrator.md`
- Gemini workflows: `tools/gemini-enterprise/workflows.md`
- AI policies: `org/policies.md`
