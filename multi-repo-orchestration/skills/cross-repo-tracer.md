# Skill: Cross-Repo Tracer

## Identity

This skill follows trace links between repos in the family, normalizes vocabulary using the registry's translation table, and produces a coordinated change plan when a task spans repos. It is the operational form of `agent-spec/traceability-protocol.md`.

## Inputs

| Input | Source | Required |
|---|---|---|
| `task-description` | The user request being worked on | Yes |
| `starting-repo` | Repo where the task arrived | Yes |
| `family-registry` | Path to `repo-registry.md` | Yes |

## Steps

1. Read `AGENTS.md` of the starting repo. If absent, halt and route to `repo-cartographer` first.
2. Identify concepts in the task description and check ownership using `repo-registry.md` and the starting repo's "Key concepts owned here" section.
3. For each concept owned by a *different* repo, fetch that repo's `AGENTS.md` and add it to the working set.
4. Build a vocabulary translation list using the table in `repo-registry.md`. If a term differs across repos, decide which form to use in the task and document why.
5. List concrete file touchpoints in each repo. Mark each touchpoint as: this-repo-only, sibling-only, or both.
6. Apply `hio-classifier.md` to the task. Take the most restrictive routing across all repos.
7. Produce the coordinated plan: ordered file changes per repo, PR linkage strategy, spec-version impacts, SME review surface.
8. If routing requires Interactive or OI, halt before any commits and post the plan for human input.

## Outputs

| Output | Location |
|---|---|
| Coordinated change plan | PR description (or pre-PR markdown if Interactive/OI) |
| Vocabulary translation list | PR description |
| Updated `AGENTS.md` trace links (if scope changed) | Each affected repo, in the same coordinated PR set |

## Stop conditions

- A trace link 404s -- log and propose a fix in the same PR
- Two repos disagree on which one owns a concept -- escalate to SME via `governance/sme-update-workflow.md`
- Vocabulary collision (same word, different meaning) not in the translation table -- pause, propose a translation row, escalate to Interactive
- Coordinated change requires more than three repos -- escalate to OI; multi-repo cascades >3 are programs, not tasks

## Example: happy path

Task: "Update emergence definition to include team-shared cognitive load relief."

Starting repo: `software-engineering-hio-agent-framework` (`metrics/harmonization.md` references emergence).

The skill discovers `thought-org-with-human-ai-hybrid` owns the canonical "emergence" definition. Vocabulary is consistent. Plan: change `framework.md` upstream first, then `metrics/harmonization.md`, then update `cognitive-units/README.md` references. Routing: Interactive (it touches a methodology concept). Two coordinated PRs proposed.

## Example: stop condition

Task: "Make the agent recommend stories to children."

Starting repo: `software-engineering-hio-agent-framework`. Concepts: child, story, recommendation. Ownership: stories live in `thoughtexperiments`; recommendation logic does not yet have an owner repo.

The skill detects a missing owner-repo for recommendation logic. Halts and routes to `prompts/propose-new-repo.md` to consider whether `hio-evals` or `agent-spec-registry` should own it, or whether a new sibling is needed.
