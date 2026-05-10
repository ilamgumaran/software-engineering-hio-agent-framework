# Universal Dos and Don'ts

Applies to all repos in the HIO family. Per-repo files can add or tighten; never relax.

---

## Authoring prompts and agent context

**Do:**
- Write prompts that fit a fresh agent walking in cold; assume zero prior session context
- Cite the file paths an agent should read before acting
- State explicitly which actions are allowed, recommended, or forbidden
- Use canonical names exactly as defined in the operational hub (10 cognitive functions, 6 agent types, 5 cognitive units)
- Mark untrusted content with a fence and a label (`[USER-CONTRIBUTED]`, `[EXTERNAL-DOC]`)
- Test prompts against at least one real task before merging
- Version prompts when behavior changes; do not silently rewrite

**Don't:**
- Write prompts that depend on hidden conversation history
- Use vague verbs ("handle this", "deal with that") without specifying the operation
- Embed secrets, tokens, or PII in prompts
- Allow user-contributed text to be concatenated into a system prompt without fencing
- Reuse a verb across repos with different meanings ("score", "evaluate", "review" should all map to defined operations)
- Promise the agent capabilities that the underlying tool cannot provide

**Edge cases:**
- Generated prompts (templating, parameterization) are exempt from versioning if their generators are versioned
- Prompts used only inside a CI workflow with no human-readable surface can omit citations if the workflow itself is documented

---

## Authoring agent rules (`AGENTS.md`, `CLAUDE.md`)

**Do:**
- Conform to `agent-spec/AGENTS-SPEC-v1.md`
- Keep rules imperative and falsifiable ("do not push to main" not "be careful with main")
- Cross-reference the central spec rather than restating org-wide rules
- Include a spec-version line at the bottom

**Don't:**
- Hide rules in prose paragraphs that an agent must summarize to find
- Mix configuration (model selection, tool list) with policy (what is allowed)
- Duplicate the same rule in multiple places without a single source of truth

---

## Cross-repo work

**Do:**
- Follow `agent-spec/traceability-protocol.md` step by step
- Translate vocabulary using `repo-registry.md` if a term differs across repos
- Open coordinated PRs (one per repo) and link them to each other
- Update `repo-registry.md` if the change creates or removes a relationship

**Don't:**
- Move concept ownership across repos without SME approval
- Land an unilateral change in one repo that breaks a sibling's `AGENTS.md` trace links
- Assume that a vocabulary term means the same thing in two repos

---

## Security

**Do:**
- Treat any content sourced from outside the family as untrusted (label and fence it)
- Treat anything that ends up in an agent's context window as if a human will read it
- Honor the Decision Spectrum: reversible -> agent decides; semi-reversible -> agent recommends with tradeoffs; irreversible -> agent analyzes only
- Escalate to OI (organic intelligence) on any ambiguity in a security-sensitive change

**Don't:**
- Bypass branch protection or pre-commit hooks (`--no-verify` and similar are forbidden unless explicitly authorized)
- Run agents with broader permissions than the task requires
- Auto-merge AI-authored PRs
- Log secrets, tokens, or user PII into trace systems

---

## Tone and style

**Do:**
- Use plain markdown; no YAML frontmatter
- Use tables when listing 3+ items of the same shape
- Include "Organization Extension Point" markers for fields a fork is expected to fill in
- Keep individual files between 80 and 300 lines unless the content genuinely demands more

**Don't:**
- Use emojis unless the parent repo's content already uses them
- Pad prose to seem more substantial; brevity is correctness here
- Write generated-looking text (numbered headings under every section, repeated phrasing) that adds no information
