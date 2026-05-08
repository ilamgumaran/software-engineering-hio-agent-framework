---
mode: 'agent'
description: 'Set up an eval-first workflow for a new GenAI feature.'
---

# Eval-Driven GenAI

Use this when starting a new GenAI feature or evaluating prompt / model changes.

## What to Generate
- `evals/<feature>/dataset.jsonl` with 30+ examples covering happy path,
  edge cases, adversarial, and known failure modes.
- `evals/<feature>/runner.py` that runs the model on every example.
- Grading: programmatic where possible (schema, regex, tolerance), LLM-as-judge
  pairwise for open-ended.
- CI workflow that runs evals on every PR touching prompts / model config.
- Regression threshold (typical: 2–5% drop blocks merge).
- Dashboard / report markdown summarizing pass rate by category.

## Constraints
- Examples sourced from real production traffic (PII scrubbed) when possible.
- LLM-as-judge must be a stronger model than the one being tested.
- Cost cap per CI run.
- Eval set has a named owner.

## Reference
`.claude/skills/eval-driven-genai/SKILL.md`.
