# Skill: Agentic Scorer

## Identity

This skill produces a draft scorecard for a repo using the rubric in `scoring/scoring-rubric.md`. It is run quarterly against every repo in the family and ad-hoc when a major change lands.

## Inputs

| Input | Source | Required |
|---|---|---|
| `repo` | Owner/name of the GitHub repository | Yes |
| `mode` | `baseline` (first-time) or `re-score` (subsequent) | Yes |
| `previous-scorecard` | Previous scorecard file path | If mode = re-score |

## Steps

1. List the top-level structure of the repo and read `README.md`, `AGENTS.md`, `CLAUDE.md` (if present), and `org/policies.md` (if present).
2. For each rubric dimension (A1-A5, B1-B5):
   a. Find evidence in the repo (file path, link, line excerpt)
   b. Cite the evidence -- do not assert without citation
   c. Map evidence to L1-L5 using the rubric's level definitions
3. Compute axis-level summaries: floor of mean across A-dimensions and B-dimensions separately. N/A dimensions are excluded from the mean.
4. Identify the strongest two dimensions and weakest two dimensions.
5. Produce a prioritized improvement plan -- five items, ordered by impact-per-effort.
6. If mode = re-score, diff against the previous scorecard and note movements.
7. Submit the draft scorecard as a PR to `multi-repo-orchestration/scoring/scorecard-<repo>.md`.

## Outputs

| Output | Location |
|---|---|
| Draft scorecard | `multi-repo-orchestration/scoring/scorecard-<repo>.md` |
| Updated `summary.md` row | `multi-repo-orchestration/scoring/summary.md` |
| (If re-score) Diff narrative | PR description |

## Stop conditions

- Cannot find evidence for a dimension -- score it L1 with the citation "no evidence found in repo" rather than guessing
- Repo is empty or not yet structured -- halt; route to `repo-cartographer` to scaffold first
- Security dimensions cannot be scored without sensitive-surface knowledge -- mark them "requires SME" rather than scoring them

## Example: happy path (baseline)

Input: repo = `ilamgumaran/thoughtexperiments`, mode = `baseline`.

The skill reads the structure, finds no `AGENTS.md` (A1 = L1), no sibling-repo links (A2 = L1), `TODO.md` lists owned concepts but no glossary (A3 = L3), no prompts directory (A4 = L1), no tools (A5 = N/A). Security dimensions assessed conservatively. Produces the scorecard already present in this directory.

## Example: stop condition (security)

Input: repo with production secrets in env files (hypothetical). The skill reaches B4 and detects a `.env` file with what looks like a real key. It halts B4, marks it "requires SME -- potential exposed secret", and continues with B1-B3 and B5. The PR description flags the finding for immediate human review.
