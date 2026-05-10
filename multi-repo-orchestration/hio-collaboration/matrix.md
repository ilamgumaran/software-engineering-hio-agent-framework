# Master HIO Routing Matrix

Default classification for common task signals across the family. Per-repo files can tighten (OI for tasks default-rated II), never relax.

---

## Reading the table

- **Task signal** -- a recognizable type of work
- **Default mode** -- the recommended OI / II / Interactive routing
- **Why** -- one-line rationale
- **Stop condition** -- circumstance in which the agent must escalate or pause

---

## Engineering tasks

| Task signal | Default mode | Why | Stop condition |
|---|---|---|---|
| Typo fix in docs | II | Reversible, mechanical | Doc is canonical methodology -- escalate to Interactive |
| Bug fix with tests | II | Reversible, well-specified | Touches security boundary or migrates data |
| Refactor within a single file | II | Reversible, no contract change | Public API affected |
| Refactor across files | Interactive | Touchpoints expand quickly | Cross-repo touchpoints required |
| New public API or contract | Interactive | Affects downstream consumers | API is irreversible (external SDK) -- escalate to OI |
| Schema migration | Interactive | Semi-reversible | Production data affected -- OI |
| Security review | OI | High-stakes judgment | n/a |
| Dependency upgrade (patch) | II | Reversible | Known vulnerability or major version |
| Dependency upgrade (major) | Interactive | Behavioral change risk | Multiple repos affected -- OI |
| CI workflow change | Interactive | Affects all future agent runs | Disabling tests or signing -- OI |
| Branch protection change | OI | Permanent governance change | n/a |

## Documentation tasks

| Task signal | Default mode | Why | Stop condition |
|---|---|---|---|
| Update broken link | II | Reversible | Link points to retracted source |
| Reword for clarity | II | Reversible | Touches canonical definition |
| Define new term | Interactive | Vocabulary impact | Term collides with existing concept |
| Rename canonical term | OI | Vocabulary cascade across family | n/a |
| Translate doc to new language | Interactive | Linguistic accuracy required | Native-fluent reviewer not available |

## Methodology and principle tasks

| Task signal | Default mode | Why | Stop condition |
|---|---|---|---|
| Add example to existing principle | Interactive | Anchors the principle | Example contradicts existing examples |
| Modify HIO principle wording | OI | Identity-level change | n/a |
| Add new HIO principle | OI | Identity-level change | n/a |
| Update transformation phase guidance | Interactive | Practitioners depend on it | Affects in-flight transformations |

## Content tasks (thoughtexperiments)

| Task signal | Default mode | Why | Stop condition |
|---|---|---|---|
| Add story for existing age range | Interactive | Drafted by agent, reviewed by OI | n/a |
| Modify story addressing trauma or dissociation | OI | Safety-loaded | n/a |
| Translate story to new language | OI | Linguistic + developmental accuracy | n/a |
| Add metadata (age, themes, safety flags) to existing story | II | Mechanical, reversible | Tags incorrectly suggest safe content for unsafe story |
| Recommend a story to a child via agent integration | II under safety constraints | Agent respects metadata | Trauma flag without explicit human opt-in -- escalate to OI |

## Multi-repo tasks

| Task signal | Default mode | Why | Stop condition |
|---|---|---|---|
| Update `AGENTS.md` in a single repo | II | Spec-conformant | Spec version bump required |
| Update `multi-repo-orchestration/` central spec | OI | Cascades to entire family | n/a |
| Add new sibling repo to family | Interactive | Requires registry, scorecard, AGENTS.md | First-of-its-kind domain -- OI |
| Coordinated change across 2+ repos | Interactive | Atomic delivery required | Any one repo refuses the change -- OI |
| Cross-repo vocabulary translation | II | Reads `repo-registry.md` table | New translation row needed -- Interactive |

## Operations and security tasks

| Task signal | Default mode | Why | Stop condition |
|---|---|---|---|
| Rotate a secret | OI | High-trust operation | n/a |
| Add a sensitive-surface inventory entry | Interactive | Affects policy | Surface contains PII or production data -- OI |
| Respond to security incident | OI | Judgment-loaded under pressure | n/a |
| Configure agent permissions (MCP tool list) | OI | Permanent capability change | n/a |
| Audit log review | II | Pattern detection at scale | Anomaly found -- escalate to Interactive then OI |

---

## Default for unlisted task signals

If the task does not appear in any table above, the default is **Interactive**. Do not assume II.

---

## Anti-patterns

| Anti-pattern | Symptom | Fix |
|---|---|---|
| Routing all changes to OI | Throughput collapses; humans burn out | Identify the genuinely reversible subset; reroute to II |
| Routing security-sensitive changes to II | Slow-burn risk accumulation | Restore the OI floor on the matrix |
| Skipping the matrix for "obvious" tasks | Drift; same task routed differently in different sessions | Make routing the first step of every PR description |
| Letting per-repo overrides relax central rules | Erosion of safety floor | Reject the override; tighten only |
