# Skill: Repo Cartographer

## Identity

This skill maps a repository's structure and either drafts a new `AGENTS.md` or validates an existing one against `agent-spec/AGENTS-SPEC-v1.md`. It is the entry point for onboarding a new repo to the family or auditing an existing one.

## Inputs

| Input | Source | Required |
|---|---|---|
| `repo` | Owner/name of the GitHub repository | Yes |
| `mode` | `draft` (no AGENTS.md exists) or `validate` (AGENTS.md exists) | Yes |
| `family-context` | Path to `multi-repo-orchestration/repo-registry.md` | Yes |

## Steps

1. List the top-level directories and files of the repo
2. Read `README.md`, `CLAUDE.md` (if present), and any existing `AGENTS.md`
3. Identify the layer the repo belongs to (Strategic, Generic, Operational, Domain content) using cues from `repo-registry.md`
4. Identify concepts the repo authoritatively owns (look for `cognitive-*`, `roles/`, `framework.md`, or domain-specific structures)
5. Identify sibling repos referenced or implied
6. **If mode = draft:**
   - Generate an `AGENTS.md` using the spec sections in order
   - Fill the Family, Purpose and scope, Key concepts owned here, Trace links from the analysis above
   - Pull dos/don'ts and HIO routing tables from `dos-and-donts/per-repo-<name>.md` and `hio-collaboration/per-repo-routing.md`
   - Append the spec version line
   - Submit a draft PR
7. **If mode = validate:**
   - Check each required section is present
   - Check the spec version line
   - Verify trace links resolve
   - Verify HIO routing table has at least five rows
   - Verify dos/don'ts are imperative and falsifiable
   - Produce a validation report

## Outputs

| Output | Location |
|---|---|
| Draft `AGENTS.md` (mode=draft) | Root of target repo, in a feature branch |
| Validation report (mode=validate) | Markdown comment on PR or as a file in the target repo's `multi-repo-orchestration-reports/` (if exists) |

## Stop conditions

- Repo is private or archived -- escalate to OI to confirm scope
- Repo has structural patterns not seen before in the family -- escalate to Interactive for SME judgment
- Multiple plausible owner-concepts compete -- escalate to OI
- Existing `AGENTS.md` references a spec version newer than the central -- abort and update central first

## Example: happy path (draft mode)

Input: repo = `ilamgumaran/thoughtexperiments`, mode = `draft`.

The skill identifies it as Domain content layer, owns Resonance/Contraction/Null vocabulary, related to `thought-org-with-human-ai-hybrid`. It pulls the per-repo dos/don'ts (child-safety overrides), the per-repo HIO routing (story safety), and produces a conformant `AGENTS.md`.

## Example: stop condition (validate mode)

Input: repo with existing `AGENTS.md` claiming `Spec: AGENTS-SPEC-v2`. Central spec is at v1. Skill aborts validation, opens an issue: "Repo claims spec version newer than central. Update central first or correct the repo file."
