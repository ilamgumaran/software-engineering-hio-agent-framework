# Dos and Don'ts: thought-org-with-human-ai-hybrid

Applies on top of `universal.md`. Repo-specific rules can tighten; never relax.

---

## Why this repo is different

This is the methodology repo -- the philosophical and strategic source for HIO. Vocabulary defined here propagates to every operational repo and every fork that consumes those repos. Treat edits to canonical definitions as high-blast-radius changes.

---

## Authoring methodology content

**Do:**
- Preserve the 4 HIO Tests intact: Curiosity, Translation, Win-Win, Horizon
- Anchor new content to the 4 Core Principles (Purpose as a Living Force, Harmonize Don't Divide, Fulfillment as the Engine, Measure the Whole Ecosystem)
- Keep `framework.md` as the canonical document; sub-documents reference it
- When introducing a new term, define it once in `framework.md` and link from elsewhere

**Don't:**
- Rename canonical terms (organic intelligence, inorganic intelligence, harmonization, emergence, cognitive ecosystem) without explicit deprecation
- Embed prompts or agent instructions in `framework.md` itself; they belong in `proposals/` or downstream operational repos
- Add operational detail (sprint cadence, CI rules, role definitions) to this repo; that belongs in the operational hub
- Allow user-contributed examples in `framework.md` without SME review (the methodology is the framework's voice)

---

## Cross-repo coupling

**Do:**
- Recognize that `software-engineering-hio-agent-framework` operationalizes this repo; vocabulary changes here ripple downstream
- Use the trace links table in `AGENTS.md` to show consumers where to look

**Don't:**
- Reference downstream operational specifics (cognitive functions, agent types) as if they were part of the methodology -- they are operationalizations of it
- Move methodology decisions into operational repos

---

## Prompt injection and content safety

This repo's content is consumed by agents in other repos as canonical reference. Untrusted edits here distort prompts elsewhere.

**Do:**
- Mark any directly-quoted user content with a labeled fence
- Treat unsigned PRs from new contributors as candidates for prompt injection until reviewed

**Don't:**
- Embed sample prompts containing phrases like "ignore previous instructions" without a clear injection-test fence
- Quote external sources verbatim without attribution and review

---

## Examples

- Adding a 5th HIO Test: requires SME deliberation; the 4 are part of the framework's identity.
- Updating the definition of "emergence": requires a coordinated change with the operational hub's `agents/` and `metrics/harmonization.md`.
- Translating to a new language: copy `framework.md` into a new file (`framework.<lang>.md`); do not replace the canonical English version.
