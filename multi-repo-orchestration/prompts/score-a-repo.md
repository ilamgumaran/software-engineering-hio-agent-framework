# Prompt: Score a Repo

Use this to produce or refresh a scorecard against the rubric in `scoring/scoring-rubric.md`.

---

## Inputs

- **Target repo:** `[owner/name]`
- **Mode:** `[baseline | re-score]`
- **Previous scorecard (if re-score):** `[path]`
- **Rubric:** `https://github.com/ilamgumaran/software-engineering-hio-agent-framework/blob/main/multi-repo-orchestration/scoring/scoring-rubric.md`

---

## Prompt

```
You are scoring [owner/name] using the agentic-readiness and security rubric.

1. Fetch the repo's top-level structure. Read README.md, AGENTS.md (if any),
   CLAUDE.md (if any), and any policies file.

2. For each rubric dimension (A1-A5 agentic, B1-B5 security):
   - Find evidence in the repo (file path, line excerpt). If no evidence,
     score L1 with the citation "no evidence found".
   - Map the evidence to a level using the rubric's level definitions.
   - Cite a specific file path and excerpt for every score above L1.

3. Compute axis levels: floor of mean of A-dimensions, floor of mean of
   B-dimensions. Exclude N/A dimensions.

4. Identify two strongest dimensions and two weakest.

5. Produce an improvement plan -- exactly five items, ordered by
   impact-per-effort, each with the dimension it lifts and the new level
   it would reach.

6. (re-score only) Diff against the previous scorecard. Note movements
   per dimension. Flag any score that dropped.

7. Output the scorecard in the format used by
   scoring/scorecard-software-engineer-core-structure.md (or any other
   existing scorecard). Sign-off block left blank for SMEs.

8. If you encounter a stop condition (potential exposed secret, structural
   pattern not seen before, security dimension that requires SME knowledge),
   halt and report -- do not guess.
```

---

## Stop conditions

If the agent returns a partial scorecard, do not merge. Address the stop conditions first.
