# Skill: HIO Classifier

## Identity

This skill classifies a task as Organic Intelligence, Inorganic Intelligence, or Interactive Collaboration using the master matrix and per-repo overrides. It is mechanically simple but load-bearing: every PR in the family should run it.

## Inputs

| Input | Source | Required |
|---|---|---|
| `task-description` | The user request | Yes |
| `starting-repo` | The repo where the task starts | Yes |
| `additional-repos` | Sibling repos touched (from `cross-repo-tracer`) | If applicable |

## Steps

1. Identify the task signal: refactor, bug fix, doc edit, schema migration, security review, content edit, vocabulary change, etc. Use the rows in `hio-collaboration/matrix.md` as the alphabet.
2. Look up the default mode for that signal in `matrix.md`.
3. For each repo touched, look up the per-repo override in `per-repo-routing.md`.
4. Take the most restrictive mode across central and overrides (OI > Interactive > II).
5. Check stop conditions: is the task irreversible, security-sensitive, child-safety adjacent, identity-level, or ambiguous? Any "yes" forces OI.
6. Output the classification, citing the row that determined it.

## Outputs

| Output | Location |
|---|---|
| Classification (`OI` / `II` / `Interactive`) with one-line rationale and matrix-row cite | PR description, top of body |

## Stop conditions

- Task signal does not match any row in the matrix -- default to **Interactive** and propose a new row in the matrix in the same PR
- Task touches a repo not in the registry -- halt; route to `repo-cartographer` first
- Multiple matrix rows match with conflicting modes -- take the most restrictive; flag for SME review

## Example: happy path

Task: "Fix typo in `cognitive-functions/builder.md`."

Signal: typo fix. Matrix default: II. Per-repo override (HIO operational hub): no override for typos. Stop conditions: none. Classification: **II**, rationale: typo fix in non-canonical content.

## Example: tightening

Task: "Translate `framework.md` to Spanish."

Signal: translate doc. Matrix default: Interactive. Per-repo override (`thought-org-with-human-ai-hybrid`): tighten to Interactive plus native-fluent reviewer. Stop conditions: none additional. Classification: **Interactive** with explicit OI reviewer requirement, rationale: per-repo override.

## Example: stop condition

Task: "Have the agent answer questions from a child about loss."

Signal: child-safety adjacent. Matrix: not directly listed but the content rules in `per-repo-thoughtexperiments.md` make it OI. Stop conditions: child safety. Classification: **OI**, escalate.
