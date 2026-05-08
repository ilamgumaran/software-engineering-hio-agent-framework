---
description: >
  Builds an eval-first GenAI development workflow: golden datasets,
  rubric grading, regression CI, A/B comparison. Use when starting
  any new GenAI feature or evaluating prompt / model changes.
---

## Eval-Driven GenAI Development

### Why Evals First
You cannot ship a GenAI feature responsibly without evals. Eyeballing 10
examples is not sufficient. Without an eval set, every prompt change is a
gamble; with one, you have ground truth.

### Eval Set Construction
1. **Size:** Start with 30–100 examples. Grow toward 500+ for production features.
2. **Coverage:**
   - Happy path (~40%)
   - Edge cases (~30%) — long inputs, ambiguous, multi-step
   - Adversarial (~20%) — prompt injection, refusal scenarios
   - Failure modes (~10%) — known regressions, bug reports
3. **Source:** Real production traffic (with PII scrubbed) > synthetic.
4. **Storage:** In the repo, versioned with the prompts. JSONL or YAML.
5. **Stewardship:** A named owner per eval set. Stale evals are worse than no evals.

### Grading Strategies
- **Programmatic (preferred when possible):**
  - Exact match for closed answers.
  - JSON schema validation for structured output.
  - Regex / contains for known phrases.
  - Numerical tolerance for math.
- **LLM-as-judge:**
  - Use a stronger model than the one being tested.
  - Pairwise comparison ("A vs. B, which better follows instructions?")
    is more reliable than absolute scoring.
  - Calibrate the judge: 50 manually labeled examples, check inter-rater
    agreement.
- **Human-in-the-loop:**
  - Sample 5–10% of eval results for human review.
  - Required for safety-sensitive features.

### CI Integration
- Eval runs on every PR that changes prompts, tools, or model config.
- Threshold: regression > N% blocks the merge (typical: 2–5%).
- Cost cap per CI run; full eval set on `main` nightly.
- Results logged with prompt + commit SHA for replay.

### A/B Comparison Harness
- Same eval set, two configurations (e.g., Sonnet 4.6 vs. Opus 4.6, or
  prompt v3 vs. v4).
- Pairwise judge marks each result A / B / Tie.
- Statistical significance (binomial test) before declaring winner.
- Cost-adjusted comparison: a 2% quality gain at 3× cost may not ship.

### Production Feedback Loop
- Sample real traffic (with consent / privacy review).
- Feed flagged outputs back into the eval set.
- Quarterly review: prune obsolete evals, promote new ones.

### Anti-patterns
- Evaluating only on examples the model has seen (data leakage).
- LLM-as-judge with the SAME model being evaluated.
- One-off "vibes-based" testing in a notebook, not committed.
- Treating evals as a one-time milestone instead of continuous.

### Verification
- Eval set in repo, with owner.
- CI runs evals on prompt PRs.
- Eval results dashboard visible to the team.
- At least one A/B harness run before model upgrades.

### Model Tier
Default: Opus (eval design is high-leverage; bad evals mislead for months).
