# Skill: HIO Classifier

## Identity

This skill classifies a task as Organic Intelligence, Inorganic Intelligence, or Interactive Collaboration using the master matrix and per-repo overrides. It is mechanically simple but load-bearing: every PR in the family should run it.

The procedure includes a **deliberation step** -- the agent must explicitly cite the matrix row(s) and stop conditions that drove the classification, in the spirit of [Deliberative Alignment](../../reference/agent-alignment-research.md). "Outputting OI" is not enough; the agent must show its work.

## Inputs

| Input | Source | Required |
|---|---|---|
| `task-description` | The user request | Yes |
| `starting-repo` | The repo where the task starts | Yes |
| `additional-repos` | Sibling repos touched (from `cross-repo-tracer`) | If applicable |

## Steps

1. Identify the task signal: refactor, bug fix, doc edit, schema migration, security review, content edit, vocabulary change, agent-to-agent communication, etc. Use the rows in `hio-collaboration/matrix.md` as the alphabet.
2. Look up the default mode for that signal in `matrix.md`. **Cite the row.**
3. For each repo touched, look up the per-repo override in `per-repo-routing.md`. **Cite the override row if present.**
4. Take the most restrictive routing across central and overrides (OI > Interactive > II).
5. Check stop conditions: is the task irreversible, security-sensitive, child-safety adjacent, identity-level, ambiguous-by-design, or in any OWASP-flagged surface (agent-to-agent communication, supply chain, persistent memory)? Any "yes" forces OI. **Cite the stop condition.**
6. **Deliberation step:** before emitting the classification, the agent restates in one paragraph: the task signal, the cited rows, the override (if any), the stop conditions checked, and why the chosen routing follows.
7. Output:
   - Classification: OI | II | Interactive
   - Rationale: one line
   - Cited matrix row(s) and override row(s)
   - Stop conditions triggered (or "none")
   - Recommended next step

If the task is OI, do not propose any code or content changes. Produce an analysis only and hand off to a human.

## Outputs

| Output | Location |
|---|---|
| Classification block (with deliberation paragraph and cited rows) | PR description, top of body |

## Stop conditions

- Task signal does not match any row in the matrix -- default to **Interactive** and propose a new row in the matrix in the same PR
- Task touches a repo not in the registry -- halt; route to `repo-cartographer` first
- Multiple matrix rows match with conflicting modes -- take the most restrictive; flag for SME review
- Task involves agent-to-agent communication and the family has not yet adopted A2A signed Agent Cards -- escalate to OI per the agent-to-agent matrix row

## Example: happy path

Task: "Fix typo in `cognitive-functions/builder.md`."

Deliberation: signal = typo fix in non-canonical content. Master matrix row "Typo fix in docs" -> default II. No per-repo override applies (the override applies to canonical content only). Stop conditions: none. Therefore II.

Classification: **II**, rationale: typo fix in non-canonical content (matrix row "Typo fix in docs").

## Example: tightening

Task: "Translate `framework.md` to Spanish."

Deliberation: signal = translate doc to new language. Master matrix row "Translate doc to new language" -> default Interactive. Per-repo override for `thought-org-with-human-ai-hybrid` requires a native-fluent reviewer. Stop conditions: none additional, but reviewer requirement gates progress. Most-restrictive routing is Interactive plus explicit OI reviewer.

Classification: **Interactive** with explicit OI reviewer requirement, rationale: per-repo override.

## Example: stop condition

Task: "Have agent A in our family delegate the scoring task to agent B in another org."

Deliberation: signal = agent-acts-on-behalf-of-another-agent (matrix row in agent-to-agent table). Default OI. Stop conditions: Delegated Trust Abuse (OWASP) is in scope. A2A signed-agent-card not adopted in the family. Therefore OI, hard stop.

Classification: **OI**, rationale: agent-to-agent delegation; OWASP Delegated Trust Abuse and Inter-Agent Injection categories; A2A signed-agent-card requirement not yet met.
