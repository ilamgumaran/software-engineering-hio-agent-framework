# Agentic Development Transition Plan

## From Traditional Development to Agent-Assisted Engineering

**Framework:** HIO (Hierarchical Intelligence Orchestration)
**Scope:** Organization-wide adoption across hundreds of batch jobs and APIs
**Agents:** GitHub Copilot (cloud agent, chat, code review) + Claude Code CLI
**Version:** 1.0 — May 2026

---

## Governing Principles

These principles are non-negotiable. Every skill, instruction file, and agent configuration must align with them. They are encoded at the org level and inherited by every repo.

### 1. Quality Over Quantity — Outcome Is the Goal

Agents exist to produce correct, production-ready code — not to produce more code faster. A smaller, well-tested change that ships cleanly is always preferred over a large diff that requires multiple rounds of human fixup. Agent output is held to the same standard as human-authored code: it must pass CI, satisfy code review, and meet the team’s definition of done. Speed is a byproduct of doing things right the first time, not an end in itself.

### 2. Cost Harmonization — Org-Level Levers, Not Per-Dev Limits

Cost is managed at the organization level through model routing, token budgets, and task classification — not by restricting individual developers. The org provides a centralized configuration that maps task types to appropriate models (e.g., Haiku for linting and formatting, Sonnet for standard feature work, Opus for complex architectural reasoning). Developers should never need to think about which model to use; the agent infrastructure decides based on the task. Cost levers are tuned centrally and transparently so teams can focus on outcomes.

### 3. Reliability and Performance Over Platform Capability

If an agent feature introduces latency, flakiness, or non-determinism into the development or deployment pipeline, it is not used — regardless of how impressive the capability is. The application’s SLAs, batch job completion windows, and API response times are hard constraints. Agent tooling must prove it does not degrade these before it is adopted. When in doubt, the simpler, more predictable approach wins.

---

## Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                    ORG-LEVEL (hio-framework)                 │
│                                                             │
│  CLAUDE.md (global)          .github/copilot-instructions   │
│  .claude/skills/             .github/instructions/          │
│  .claude/rules/              .github/chatmodes/             │
│  .claude/agents/             AGENTS.md                      │
│  config/model-routing.md     config/cost-policy.md          │
│                                                             │
│  ─── Inherited by all repos via --add-dir or submodule ──── │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│                  REPO-LEVEL (per service/job)                │
│                                                             │
│  CLAUDE.md (repo)            .github/copilot-instructions   │
│  .claude/skills/             .github/instructions/          │
│  .claude/rules/              AGENTS.md                      │
│                                                             │
│  ─── Repo-level OVERRIDES org-level on conflict ─────────── │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│                  PATH-LEVEL (within repo)                    │
│                                                             │
│  src/batch/.claude/rules/    .github/instructions/batch.*   │
│  src/api/.claude/rules/      .github/instructions/api.*     │
│                                                             │
│  ─── Most specific scope wins ───────────────────────────── │
└─────────────────────────────────────────────────────────────┘
```

**Precedence rule:** Path-level > Repo-level > Org-level.

---

## Phase 1: Foundation — The Org-Level Framework (Weeks 1–3)

See:
- `AGENTS.md` — org-level multi-agent rules.
- `.github/copilot-instructions.md` — org Copilot instructions.
- `.github/instructions/` — path-scoped instructions.
- `.claude/skills/`, `.claude/rules/`, `.claude/agents/` — skills, rules, sub-agents.
- `config/` — model routing, cost policy, quality gates.
- `repo-setup-batch/`, `repo-setup-api/` — per-archetype repo templates.

### Universal Rules (excerpt)

- Never commit secrets, tokens, or credentials. Use AWS Secrets Manager.
- Every change must include tests.
- Batch jobs must be idempotent.
- APIs must return RFC 7807 problem details on errors.
- All database changes go through migration scripts, never ad-hoc DDL.
- Log INFO for business events, WARN for recoverable issues, ERROR for failures requiring human attention.
- Do not introduce new dependencies without license-compatibility check.

### Tech Stack Reference

- Languages: Java 21 (Spring Boot 3.x), Python 3.12, SQL (PostgreSQL 16)
- Build: Gradle (Java), Poetry (Python)
- CI: GitHub Actions
- Infrastructure: Terraform, AWS (ECS, Lambda, RDS, S3, SQS, EventBridge)
- Observability: Datadog (metrics, logs, traces)
- Testing: JUnit 5 + Mockito (Java), pytest (Python), min 80% coverage

---

## Phase 2: Org-Level Skills Library (Weeks 2–4)

Seven core skills live in `.claude/skills/`:

- `batch-job-scaffold` — idempotent Spring Batch job scaffolding.
- `api-scaffold` — REST endpoint with validation, RFC 7807 errors, OpenAPI.
- `db-migration` — reversible PostgreSQL migrations with lock/index analysis.
- `test-coverage` — gap analysis and deterministic test generation.
- `perf-review` — batch + API performance review.
- `cost-check` — sanity-check resource cost before merge.
- `incident-postmortem` — blameless post-incident review.

### Distribution Strategy

**Option A — Git Submodule (recommended).**

```bash
git submodule add git@github.com:your-org/hio-framework.git .hio
claude --add-dir .hio
```

**Option B — Claude Code Plugin Marketplace.**

```bash
claude plugin marketplace add your-org/hio-framework
claude plugin install batch-job-scaffold@hio-framework
```

**Option C — Symlink via CI / dev bootstrap.**

```bash
HIO_DIR="$HOME/.hio-framework"
[ -d "$HIO_DIR" ] || git clone git@github.com:your-org/hio-framework.git "$HIO_DIR"
( cd "$HIO_DIR" && git pull origin main )
ln -sfn "$HIO_DIR/.claude/skills" "$HOME/.claude/skills/hio-org"
```

For Copilot, use GitHub’s org-level custom instructions; they apply across all repos automatically.

---

## Phase 3: Repo-Level Configuration Templates

See `repo-setup-batch/` and `repo-setup-api/`.

---

## Phase 4: Team Onboarding and Workflow Integration

### Developer Setup Checklist

- GitHub Copilot license active (Business or Enterprise)
- Claude Code CLI installed (`npm install -g @anthropic-ai/claude-code`)
- Anthropic API key or Max subscription configured
- Clone hio-framework, run setup script, verify org skills load
- Per-repo: clone, init submodule, start with `claude --add-dir .hio`, run `/skills`

### Agent-Assisted Development Cycle

1. Task intake — agent loads CLAUDE.md + skills.
2. Planning (plan mode) — agent proposes approach; developer approves.
3. Implementation — skills auto-invoke; model routing selects tier.
4. Verification — quality gates from `config/quality-gates.md`.
5. Code review — Copilot review on PR + Claude `code-reviewer` subagent + human reviewer.
6. Merge and deploy — standard CI/CD; agents do not deploy.

### What Agents Do NOT Do

- Approve their own PRs or merge code.
- Deploy to any environment.
- Modify CI/CD pipeline configuration without human review.
- Change database schemas in production.
- Create or modify IAM policies, security groups, or network rules.
- Make decisions about data retention or PII handling without human sign-off.
- Bypass failing tests by deleting or skipping them.

---

## Phase 5: Transition Strategy for Existing Repos

### Repo Classification

| Tier                    | Criteria                                          | Agent Adoption Level                          |
|-------------------------|---------------------------------------------------|-----------------------------------------------|
| **Tier 1 — Lighthouse** | Low risk, active development, good test coverage  | Full agent workflow                           |
| **Tier 2 — Standard**   | Medium risk, regular changes, decent coverage     | Skills + code review                          |
| **Tier 3 — Legacy**     | High risk, infrequent changes, low coverage       | Read-only analysis, test generation only      |
| **Tier 4 — Frozen**     | No planned changes, maintenance mode              | Agent context file only (for emergency fixes) |

Legacy restriction snippet:

```markdown
## Agent Restrictions

This is a legacy codebase. Agent-generated changes are limited to:
1. Adding tests to existing code (do not modify production code)
2. Updating documentation and runbooks
3. Static analysis and bug identification (report only, do not fix)
4. Dependency vulnerability assessment

Full implementation changes require explicit human approval of
the plan before any code is written.
```

---

## Phase 6: Maintenance and Evolution

### Org Skills Governance

| Activity                                  | Frequency         | Owner                              |
|-------------------------------------------|-------------------|------------------------------------|
| Review org-level CLAUDE.md for accuracy   | Monthly           | Platform team                      |
| Update model routing based on cost data   | Quarterly         | Engineering leadership             |
| Audit skill usage metrics                 | Monthly           | Platform team                      |
| Review and prune auto-memory across repos | Monthly           | Each team                          |
| Update quality gates                      | Per release cycle | QA lead                            |
| Add new org skills                        | As needed         | Any developer (PR to hio-framework)|

### Skill Contribution Process

1. Branch in hio-framework.
2. Add skill in `.claude/skills/<skill-name>/SKILL.md`.
3. Include `README.md` in the skill directory with examples.
4. Open PR with label `skill-proposal`.
5. Two approvals required (one platform team, one domain expert).
6. After merge, all repos pick up the skill on next session start.

### Keeping Context Fresh

- PR template reminder for changes that affect architecture / batch schedules / API contracts.
- CI check that warns if `src/` changed significantly without updates to `.claude/` or `.github/copilot-instructions.md`.
- Monthly staleness audit comparing CLAUDE.md mtime vs. recent commit activity.

### Cost Monitoring

Track centrally: token spend per dev/week, per repo/week, cost per ticket, model tier distribution, rejected output rate. Alert on outlier sessions, runaway Opus usage (>30% of total), and rising rejection rate.

---

## Quick Reference: File Locations and Precedence

| Context Type            | Copilot Location                                     | Claude Code Location                                    | Scope          |
|-------------------------|------------------------------------------------------|---------------------------------------------------------|----------------|
| Org-wide instructions   | GitHub Org Settings → Copilot → Custom Instructions  | `~/.claude/CLAUDE.md` or hio-framework via `--add-dir`  | All repos      |
| Repo instructions       | `.github/copilot-instructions.md`                    | `CLAUDE.md` (repo root)                                 | This repo      |
| Path-scoped rules       | `.github/instructions/*.instructions.md`             | `.claude/rules/*.md` (with frontmatter)                 | Matching files |
| Skills (org)            | N/A (use prompts)                                    | `hio-framework/.claude/skills/` via `--add-dir`         | All repos      |
| Skills (repo)           | N/A                                                  | `.claude/skills/` in repo                               | This repo      |
| Multi-agent             | `AGENTS.md`                                          | `.claude/agents/`                                       | Per config     |
| Personal                | `~/.copilot/instructions/`                           | `~/.claude/CLAUDE.md`                                   | Per developer  |

**Precedence (highest to lowest):**

1. Path-scoped rules (most specific)
2. Repo-level CLAUDE.md / copilot-instructions.md
3. Org-level (hio-framework or GitHub org settings)
4. Personal / global (`~/.claude/CLAUDE.md`)

Conflicts: when two levels give contradictory guidance, the more specific level wins.

---

## Appendix A: Checklist Summary

### Before You Start (Org Admin)

- Create hio-framework repo with org CLAUDE.md, AGENTS.md, skills, rules
- Configure GitHub Copilot org-level custom instructions
- Define model routing policy
- Define quality gates
- Choose distribution strategy (submodule / plugin / symlink)
- Set up cost monitoring dashboard

### Per-Repo (Tech Lead)

- Add CLAUDE.md with service-specific context
- Add `.github/copilot-instructions.md`
- Add path-scoped rules for specialized directories
- Add repo-specific skills if needed
- Verify test coverage baseline ≥ 60% (target 80%)
- Run agent through one real ticket as validation

### Per-Developer (Individual)

- Install Claude Code CLI
- Clone hio-framework and run setup script
- Verify org skills load in session
- Complete one guided task with agent before solo use

---

*This plan is a living document. Update it as the org learns what works and what doesn’t.*
