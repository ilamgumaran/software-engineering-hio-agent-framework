# Agentic Development — Transition Plan & Best Practices

**Audience:** A platform engineering org adopting GitHub Copilot (CLI, chat, code review) and Claude Code CLI as everyday partners across many repos.

**Two questions this guide answers:**

1. How do we help agents understand a repo without re-analyzing it from scratch every session?
2. How do we store, share, and update prompts / skills / tools / sub-agents so the whole team gets the same agent capabilities, and so all agents stay aware of the latest repo state?

This document complements:

- `transition-playbook.md` — the longer org-level playbook (phases, governance, metrics).
- `config/` — model routing, cost policy, quality gates.
- `.claude/` and `.github/` — the skill / rule / instruction scaffolding.

---

## TL;DR

- Push **persistent context** into the repo (`CLAUDE.md`, `AGENTS.md`, `.github/copilot-instructions.md`, path-scoped instruction files). Agents read these on every session — no re-discovery needed.
- Treat **skills, prompts, sub-agents, and tool configs as code**. Version them in a single org-shared repo (`hio-framework`), distribute via submodule / plugin / symlink / GitHub org-level Copilot settings.
- Use **layered precedence**: org → repo → path. Most specific wins. Each layer answers a different question.
- Use **hooks and CI** to keep context fresh automatically: a PR cannot land if it changes architecture/contract without updating CLAUDE.md or runbook.
- Share **MCP servers and tool integrations** centrally. Developers should not be configuring identical Datadog / GitHub / Jira MCP servers individually.

---

## 1. The Problem with Naive Adoption

Without shared infrastructure, every developer’s agent rediscovers the same things:

- **Re-analysis tax.** Each new session, the agent crawls the repo to learn build commands, conventions, naming, gotchas. That’s tokens, latency, and inconsistent answers across teammates.
- **Skill fragmentation.** Alice has a great “scaffold a Spring Batch job” prompt. Bob doesn’t. Their output looks different in code review.
- **Drift.** Someone changes the on-call rotation or the chunk size. Agent guidance for that repo silently goes stale and now misleads everyone.
- **Tool sprawl.** Every dev sets up their own Datadog / GitHub / Jira MCP server with their own credentials and slightly different configs.

The fix is the same pattern we already use for code: a single source of truth, versioned, distributed, kept fresh by automation.

---

## 2. Make Repos Self-Describing (Persistent Context)

The single highest-leverage move. Every repo should answer these questions in files agents read automatically:

| Question | Where to put it |
|---|---|
| What does this service do? | `CLAUDE.md`, repo `README.md` (Claude reads CLAUDE; Copilot reads `.github/copilot-instructions.md`) |
| How do I build / run / test? | `CLAUDE.md` “How to Build and Test” section |
| What conventions does this repo follow? | `AGENTS.md` (shared by Copilot and other multi-agent tooling) |
| What rules apply only to certain files? | `.github/instructions/*.instructions.md` (Copilot path-scoped), `.claude/rules/*.md` with `applyTo` frontmatter (Claude Code) |
| What landmines must agents avoid? | A `## What Agents Need to Know` section in `CLAUDE.md` |
| What’s deliberately overridden vs. org default? | An `## Override:` section in `CLAUDE.md` |

### Concrete recommendations

1. **Bootstrap with `/init`.** In a fresh repo, run `claude` then `/init`. Edit the result — don’t just accept it. Aim for 100–300 lines of dense, agent-relevant content; not a copy of the README.
2. **Prefer pointers over duplication.** If a fact lives in `README.md` or a runbook, link to it. Duplicating invites drift.
3. **Use both `CLAUDE.md` and `AGENTS.md`.** They serve different agent ecosystems. Keep them in sync via a simple include pattern: have one of them link to the other and only put divergent content in each.
4. **Path-scope specialized rules.** Don’t put SQL conventions in the global file — put them in `.github/instructions/sql.instructions.md` with `applyTo: "**/*.sql"`. Smaller context window, clearer rules.
5. **Make the file readable in 30 seconds.** Headings, tables, no walls of prose. Agents read it on every turn; humans audit it on every PR.

### Layered precedence (use this consciously)

```
Path-level   .github/instructions/sql.instructions.md      ← most specific wins
Repo-level   CLAUDE.md, AGENTS.md, .github/copilot-instructions.md
Org-level    hio-framework (submodule / org Copilot settings)
Personal     ~/.claude/CLAUDE.md, personal Copilot prompts
```

Conflicts: more specific wins. Two files at the same level conflicting is a bug — keep each concern in exactly one place.

---

## 3. Storing & Sharing Skills, Prompts, Sub-Agents, Tools

Treat agent assets the way you treat shared libraries: versioned, reviewed, released. The `hio-framework` repo is the home.

### What lives where

| Asset | Claude Code home | Copilot home |
|---|---|---|
| Reusable instruction packs | `.claude/skills/<name>/SKILL.md` (auto-invoked when description matches) | `.github/prompts/<name>.prompt.md` (invoked via `/<name>`) |
| Custom slash commands | `.claude/commands/<name>.md` | Same as above (prompt files) |
| Specialist sub-agents | `.claude/agents/<name>.md` | `AGENTS.md` + per-agent role files; or chatmodes (`.github/chatmodes/`) |
| Path-scoped rules | `.claude/rules/<name>.md` with `applyTo` frontmatter | `.github/instructions/<name>.instructions.md` |
| Tool integrations (MCP, REST, etc.) | `.mcp.json` checked into repo, or org-level via `~/.claude/mcp.json` | Copilot extensions registered at GitHub org level |
| Personal preferences | `~/.claude/CLAUDE.md`, `~/.claude/skills/` | `~/.copilot/instructions/` |

### Skill design checklist

- **One concern per skill.** `batch-job-scaffold` does one thing well; don’t bundle migrations, scaffolds, and reviews.
- **Front-loaded description.** The `description:` frontmatter is what the agent matches against. Be specific about *when* the skill applies, not just *what* it does.
- **Reference shared rules** instead of copy-pasting. A skill says “follow `.claude/rules/security.md`” rather than restating security rules.
- **Declare model tier.** Skills should explicitly state “default: Sonnet” or “escalate to Opus when X.”
- **Include verification.** A skill that produces code should also list what to run to verify it (build, tests, lint).
- **Keep prompts under ~3K tokens.** Long skills crowd out the user’s task and reduce quality.

### MCP servers (tools): centralize

Don’t let every developer set up their own GitHub / Datadog / Jira / DB MCP server. Recommended:

1. Maintain an org-level `~/.claude/mcp.json` template in `hio-framework/config/mcp.example.json`.
2. Document which servers are blessed for org use, with credential setup steps using the org secret manager.
3. For repo-specific tools (e.g., a repo-specific DB schema introspector), check in `.mcp.json` so every contributor gets the same tooling.
4. Treat MCP server upgrades like dependency upgrades — announce, test, roll out.

### Sub-agents: when to create one

Create a Claude Code sub-agent when:

- The task is repeatedly delegated and benefits from an isolated context (e.g., independent code review).
- The task uses a different model tier than the parent session.
- The task is bounded and has clear success criteria.

Don’t create sub-agents for things a normal skill + prompt covers.

---

## 4. Distribution — Get the Same Skills to Every Developer

Pick *one* primary mechanism for the org. Mixing breeds confusion.

### Recommended: Git Submodule + GitHub org-level Copilot

This combination handles both CLIs cleanly.

**Claude Code (submodule):**

```bash
# One-time per repo
git submodule add git@github.com:your-org/hio-framework.git .hio

# Each session
claude --add-dir .hio
```

A git hook or devcontainer can keep `.hio` updated automatically.

**Copilot (GitHub org settings):**

In GitHub: **Org Settings → Copilot → Custom Instructions.** These apply across every repo automatically. Repo-level `.github/copilot-instructions.md` overrides them on conflict. No per-developer setup.

### Alternative: Plugin Marketplace (Claude Code only)

```bash
claude plugin marketplace add your-org/hio-framework
claude plugin install batch-job-scaffold@hio-framework
```

Granular installs and update notifications, but newer mechanism — less battle-tested at scale.

### Alternative: Symlink via devcontainer / bootstrap script

```bash
HIO_DIR="$HOME/.hio-framework"
[ -d "$HIO_DIR" ] || git clone git@github.com:your-org/hio-framework.git "$HIO_DIR"
( cd "$HIO_DIR" && git pull origin main )
ln -sfn "$HIO_DIR/.claude/skills" "$HOME/.claude/skills/hio-org"
```

Best when devs already use a standardized devcontainer or dotfiles setup.

### Comparison

| Mechanism | Auto-update | Per-repo pinning | Works for Copilot | Setup cost |
|---|---|---|---|---|
| Git submodule | Manual (or via hook) | Yes (commit SHA) | No | Low |
| Plugin marketplace | Yes | Per-skill version | No | Medium |
| Symlink / devcontainer | Yes (on bootstrap) | No (always latest) | No | Medium |
| GitHub org Copilot settings | Yes (instant) | No | **Yes** | Very low |

The combination of submodule + org Copilot settings is the recommended starting point.

---

## 5. Keeping Context Fresh (the Drift Problem)

Stale context is worse than no context — it confidently misleads. Three layers of defense:

### Layer 1: PR-time enforcement

Add a checkbox to your PR template:

```markdown
- [ ] If this PR changes architecture, batch schedule, API contract,
      or operational behavior, I have updated CLAUDE.md and the
      relevant runbook.
```

### Layer 2: CI guard

A simple GitHub Action that fails (or warns) when meaningful change happens without context updates:

```yaml
- name: Warn on missing context update
  run: |
    if git diff --name-only origin/main...HEAD | grep -qE '^src/'; then
      if ! git diff --name-only origin/main...HEAD | grep -qE '^(CLAUDE\.md|\.github/copilot-instructions\.md|docs/runbooks/)'; then
        echo "::warning::Source changed but agent context did not. Confirm this is intentional."
      fi
    fi
```

### Layer 3: Hooks

Use Claude Code hooks (configured in `.claude/settings.json`) to nudge at key events:

- **SessionStart hook:** verify `git status` is clean and the submodule is up to date; warn if not.
- **PostToolUse hook on Edit/Write:** if the edit modified `application.yml` or `build.gradle`, suggest updating CLAUDE.md.
- **Stop hook:** remind to update the runbook if a batch job file was edited.

Hooks are local automation — they don’t replace CI, but they catch issues before the developer pushes.

### Layer 4: Monthly staleness audit

A scheduled job script that flags repos where:

- `CLAUDE.md` mtime is older than 60 days but `src/` had ≥5 commits.
- Linked runbooks are missing or 404.
- A skill referenced in `CLAUDE.md` no longer exists in `hio-framework`.

Output is a list of repos for tech leads to review at their next monthly check-in.

---

## 6. Helping Agents Understand the Repo Without Re-Analyzing

Combining the above:

1. **Persistent files** (CLAUDE.md / AGENTS.md / instruction files) — read every session, no analysis needed.
2. **Generated artifacts** — commit a `docs/architecture.md` or `docs/api-catalog.md` that’s regenerated by CI from source-of-truth (OpenAPI, Terraform, schema). Agents read the rendered version.
3. **Memory files** — `~/.claude/CLAUDE.md` for personal preferences; `CLAUDE.md` (repo) for repo facts; `hio-framework/CLAUDE.md` for org rules.
4. **Skills as packaged context** — a skill loaded at the start of a task carries pre-curated instructions; the agent doesn’t need to discover the convention.
5. **MCP servers as live context** — instead of asking the agent to grep the repo for the schema, give it a schema introspection tool. Live > stale notes.
6. **Avoid `/init` in legacy repos.** Generate it once, then curate. Don’t let agents regenerate it on every onboarding — they’ll overwrite hand-tuned guidance.

### What NOT to put in CLAUDE.md

- Things that change weekly (current sprint goal, on-call schedule). Link to a runbook instead.
- Long architecture explanations. Use diagrams in `docs/` and link.
- Secrets, tokens, internal URLs that aren’t safe to share.
- Restated org rules that already live in `hio-framework`.

---

## 7. Migration Path — From Traditional to Agentic

A pragmatic 4-stage path. Each stage is shippable on its own.

### Stage 1 — Context Files Everywhere (Weeks 1–2)

- Every active repo gets `CLAUDE.md` and `.github/copilot-instructions.md`.
- Org-level CLAUDE.md and Copilot org instructions configured.
- `hio-framework` repo created, even if mostly empty.

**Outcome:** every agent session in every repo loads the same baseline. No skill investment yet, just shared facts.

### Stage 2 — First Skills (Weeks 2–4)

- Pick 3–5 high-value, high-frequency tasks (scaffold a job, scaffold an endpoint, generate tests).
- Build skills, dogfood in 1–2 lighthouse repos.
- Measure: did the agent need fewer rounds of correction?

**Outcome:** the framework starts paying back time.

### Stage 3 — Tooling & Governance (Weeks 4–8)

- MCP servers centralized.
- CI staleness checks added.
- Quality gates enforced.
- Model routing config in place; cost dashboards visible.

**Outcome:** the system is sustainable without a single hero maintainer.

### Stage 4 — Org-Wide (Weeks 8+)

- Onboarding doc for new developers (15-minute setup).
- Tier 2 / Tier 3 / Legacy repo policies (see playbook).
- Skill contribution process: any developer can PR a new skill; two approvers required.

**Outcome:** agentic development is the default; “traditional” development is the exception.

---

## 8. Best Practices Cheat Sheet

### DO

- Treat agent assets as code: PR-reviewed, versioned, released.
- Keep `CLAUDE.md` and `AGENTS.md` short and dense — link to longer docs.
- Use path-scoped instructions for language- or directory-specific rules.
- Use sub-agents for independent code review (not the same agent that wrote the code).
- Centralize MCP servers; prefer live tools over stale notes for changing data.
- Add a CI check that warns on source change without context update.
- Make every skill state its model tier and verification steps.

### DON’T

- Don’t auto-regenerate `CLAUDE.md`. Curate it.
- Don’t put rules in three places. Pick one and link from the others.
- Don’t let each developer build their own MCP setup for the same tool.
- Don’t let agents bypass failing tests, modify CI/CD, or change IAM without human review.
- Don’t restrict cost per developer — manage cost via routing and budgets centrally.
- Don’t adopt a flashy capability if it adds latency or non-determinism to the dev loop.

---

## 9. Reference

- Long-form transition playbook: `transition-playbook.md`
- Org-level Copilot instructions: `.github/copilot-instructions.md`
- Org-level multi-agent rules: `AGENTS.md`
- Path-scoped rules: `.github/instructions/`, `.claude/rules/`
- Skills: `.claude/skills/`
- Sub-agents: `.claude/agents/`
- Model routing / cost / quality gates: `config/`
- Per-archetype repo templates: `repo-setup-batch/`, `repo-setup-api/`

---

*This is a living document. PRs welcome — the best agent practices are the ones the team actually uses, so keep what works and prune what doesn’t.*
