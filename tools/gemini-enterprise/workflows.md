# Gemini Enterprise -- HIO Workflows

Three workflows where Gemini Enterprise's large-context capabilities support HIO activities. These complement the Claude Code workflows in `tools/claude-code/workflows.md`.

---

## 1. Codebase Analysis

Full-repository analysis for architecture understanding, pattern detection, and health assessment.

**Trigger:** Sprint kickoff preparation, architecture review, new team member onboarding, or quarterly code health assessment.

**Flow:**

1. Export or provide access to the target repository (or multiple repositories for cross-system analysis)
2. Prompt Gemini to analyze the codebase for: architecture patterns, dependency structure, code health indicators, recurring anti-patterns, and areas of complexity
3. Request a structured report with: high-level architecture summary, pattern inventory, risk areas, and recommendations
4. Review the analysis for accuracy against team knowledge
5. Pass findings to Claude Code (Analysis Partner) for integration into sprint pre-analysis or architecture decision briefs

**Key Features Used:** Large context window, code understanding, pattern recognition across files.

**Expected Outcome:** A comprehensive codebase health picture that would take a human engineer days to compile manually, ready in minutes.

---

## 2. Document Analysis for Sprint Kickoff

Synthesizing long-form documents (RFCs, specs, compliance requirements) into actionable sprint inputs.

**Trigger:** New requirements arrive as lengthy documents, or external specifications need to be translated into sprint work.

**Flow:**

1. Upload the documents to Gemini (RFCs, product specs, compliance requirements, vendor documentation)
2. Prompt Gemini to extract: key requirements, constraints, dependencies on existing systems, open questions, and risk areas
3. Request a structured summary organized by sprint work potential: must-do items, should-do items, and investigation items
4. Cross-reference extracted requirements against the current backlog
5. Feed the synthesis into the Sprint Kickoff workflow (`tools/claude-code/workflows.md`)

**Key Features Used:** Long document processing, requirement extraction, structured summarization.

**Expected Outcome:** Dense documents translated into sprint-ready work items with clear traceability back to source requirements.

---

## 3. Large-Scale Pattern Detection

Cross-system analysis to identify patterns, inconsistencies, and optimization opportunities across the platform.

**Trigger:** Quarterly evolution review (`metrics/quarterly-evolution.md`), platform health assessment, or migration planning.

**Flow:**

1. Provide Gemini with access to multiple codebases, configuration files, or infrastructure definitions
2. Prompt for cross-cutting analysis: shared patterns, inconsistent implementations of the same pattern, configuration drift, dependency version skew, and naming convention violations
3. Request categorized findings: consistency issues (same thing done different ways), optimization opportunities (patterns that could be centralized), risk areas (divergent security or error handling), and migration candidates
4. Prioritize findings by impact and effort
5. Pass prioritized findings to Claude Code for sprint backlog item creation

**Key Features Used:** Multi-repository context, cross-system comparison, pattern matching at scale.

**Expected Outcome:** A cross-platform consistency and health report that surfaces optimization opportunities invisible when looking at any single system in isolation.
