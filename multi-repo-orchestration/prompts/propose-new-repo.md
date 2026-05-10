# Prompt: Propose a New Repo

Use this when the family has a structural gap that an existing repo cannot absorb without distorting its purpose. The output is a proposal, not a creation -- new repos require SME approval.

---

## Inputs

- **Gap description:** `[what concept or capability has no owner]`
- **Current candidates considered:** `[which existing repos were considered, why each is unfit]`
- **Family registry:** `multi-repo-orchestration/repo-registry.md`

---

## Prompt

```
Propose a new repo to fill the gap below.

Gap: [gap description]
Current candidates considered: [list with reasons each is unfit]

Procedure:
1. State the gap in one sentence -- what concept or capability is missing.

2. Verify the gap against the family registry. Confirm no existing repo can
   absorb it without distorting its purpose. Cite the per-repo dos/don'ts
   that would be violated by absorption.

3. Propose the new repo:
   - Name (kebab-case, descriptive, scoped narrowly)
   - Layer (Strategic | Generic | Operational | Domain content)
   - Primary content (3-5 directories or file groups)
   - Concepts owned
   - Sibling repos and trace links
   - Initial agentic and security scoring targets
   - Smallest-first deliverable that proves the repo's value

4. Identify dependencies the new repo creates -- which existing repos must
   coordinate, which will need AGENTS.md updates.

5. Estimate setup cost: hours of OI time, time to first useful artifact.

6. Risk register: three risks with mitigation per risk.

7. Output the proposal in the format of new-repos-proposed.md and append
   it as a new section there.

Do not create the repo. Submit the proposal as a PR for SME review.
```

---

## When to use

- A task has no plausible owner repo
- An existing repo would have to distort its scope to absorb a concept
- The family has expanded enough that a new layer is justified

## When not to use

- The gap can be filled by extending an existing directory in an existing repo
- The work is one-off and does not need a permanent home
