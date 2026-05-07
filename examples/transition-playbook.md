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
┌───────────────────────────────────────────────────────────┐
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
├───────────────────────────────────────────────────────────┤
│                  REPO-LEVEL (per service/job)                │
│                                                             │
│  CLAUDE.md (repo)            .github/copilot-instructions   │
│  .claude/skills/             .github/instructions/          │
│  .claude/rules/              AGENTS.md                      │
│                                                             │
│  ─── Repo-level OVERRIDES org-level on conflict ─────────── │
│                                                             │
├───────────────────────────────────────────────────────────┤
│                  PATH-LEVEL (within repo)                    │
│                                                             │
│  src/batch/.claude/rules/    .github/instructions/batch.*   │
│  src/api/.claude/rules/      .github/instructions/api.*     │
│                                                             │
│  ─── Most specific scope wins ───────────────────────── │
└───────────────────────────────────────────────────────────┘
```

**Precedence rule:** Path-level > Repo-level > Org-level. Agents always use the most specific context available. Org-level provides defaults and guardrails; repos and paths refine or override as needed.

---

## Phase 1: Foundation — The Org-Level Framework (Weeks 1–3)

### 1.1 Create the hio-framework Repository

This repository is the single source of truth for all org-wide agent configuration. The full layout, files, and example contents for Phase 1 are reproduced inline in the original plan; the org-level files referenced below have been materialized in this repo:

- Org-level CLAUDE.md — see `CLAUDE.md` (existing) and the supplementary org-wide framework guidance below.
- Org-level AGENTS.md — see `AGENTS.md`.
- Copilot org instructions — see `.github/copilot-instructions.md`.
- Path-scoped instructions — see `.github/instructions/`.
- Skills, rules, sub-agents — see `.claude/skills/`, `.claude/rules/`, `.claude/agents/`.
- Model routing, cost policy, quality gates — see `config/`.
- Per-archetype repo templates — see `examples/repo-setup-batch/`, `examples/repo-setup-api/`.

### 1.2 Org-Level Universal Rules (excerpt)

- Never commit secrets, tokens, or credentials. Use AWS Secrets Manager.
- Every change must include tests. No exceptions.
- Batch jobs must be idempotent. Document retry behavior.
- APIs must return structured error responses (RFC 7807).
- All database changes go through migration scripts, never ad-hoc DDL.
- Log at INFO for business events, WARN for recoverable issues, ERROR only for failures requiring human attention.
- Do not introduce new dependencies without checking license compatibility.

### 1.3 Tech Stack Reference

- Languages: Java 21 (Spring Boot 3.x), Python 3.12, SQL (PostgreSQL 16)
- Build: Gradle (Java), Poetry (Python)
- CI: GitHub Actions
- Infrastructure: Terraform, AWS (ECS, Lambda, RDS, S3, SQS, EventBridge)
- Observability: Datadog (metrics, logs, traces)
- Testing: JUnit 5 + Mockito (Java), pytest (Python), min 80% coverage

---

## Phase 2: Org-Level Skills Library (Weeks 2–4)

Skills are the reusable instruction packs that agents invoke on demand. Org-level skills live in `.claude/skills/` and are distributed to all repos. The seven core skills are:

- `batch-job-scaffold` — scaffolds a new batch job with idempotency, checkpoint/restart, error handling, observability.
- `api-scaffold` — scaffolds a new REST endpoint with validation, RFC 7807 errors, rate limiting, OpenAPI.
- `db-migration` — generates reversible migrations with index/lock impact notes.
- `test-coverage` — analyzes gaps and generates deterministic tests.
- `perf-review` — reviews batch + API code for throughput / latency issues.
- `cost-check` — sanity-checks resource cost (compute, storage, model usage) before merge.
- `incident-postmortem` — drafts post-incident reviews following the org template.

### 2.2 Distribution Strategy

Three options. Pick one based on tooling maturity.

**Option A — Git Submodule (recommended to start).**

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

## Phase 3: Repo-Level Configuration Templates (Weeks 3–5)

Every repo gets its own agent context that inherits from the org and overrides where needed. See:

- `examples/repo-setup-batch/` — batch job repo template (e.g., `batch-order-processing`).
- `examples/repo-setup-api/` — API repo template (e.g., `api-customer-service`).

---

## Phase 4: Team Onboarding and Workflow Integration (Weeks 4–8)

### 4.1 Developer Setup Checklist

- GitHub Copilot license active (Business or Enterprise)
- Claude Code CLI installed (`npm install -g @anthropic-ai/claude-code`)
- Anthropic API key or Max subscription configured
- Clone hio-framework, run setup script, verify org skills load
- Per-repo: clone, init submodule, start with `claude --add-dir .hio`, run `/skills`

### 4.2 Agent-Assisted Development Cycle

1. Task intake — agent loads CLAUDE.md + skills.
2. Planning (plan mode) — agent proposes approach; developer approves.
3. Implementation — skills auto-invoke; model routing selects tier.
4. Verification — quality gates from `config/quality-gates.md`.
5. Code review — Copilot review on PR + Claude `code-reviewer` subagent + human reviewer.
6. Merge and deploy — standard CI/CD; agents do not deploy.

### 4.3 What Agents Do NOT Do

- Approve their own PRs or merge code.
- Deploy to any environment.
- Modify CI/CD pipeline configuration without human review.
- Change database schemas in production.
- Create or modify IAM policies, security groups, or network rules.
- Make decisions about data retention or PII handling without human sign-off.
- Bypass failing tests by deleting or skipping them.

---

## Phase 5: Transition Strategy for Existing Repos (Weeks 5–16)

### 5.1 Repo Classification

| Tier                    | Criteria                                          | Agent Adoption Level                          | Count (est.)  |
|-------------------------|---------------------------------------------------|-----------------------------------------------|---------------|
| **Tier 1 — Lighthouse** | Low risk, active development, good test coverage  | Full agent workflow                           | 5–10 repos    |
| **Tier 2 — Standard**   | Medium risk, regular changes, decent coverage     | Skills + code review                          | 50–100 repos  |
| **Tier 3 — Legacy**     | High risk, infrequent changes, low coverage       | Read-only analysis, test generation only      | 100+ repos    |
| **Tier 4 — Frozen**     | No planned changes, maintenance mode              | Agent context file only (for emergency fixes) | Remaining     |

### 5.2 Transition Playbook per Repo

- **Week 1 — Context File Creation (All Tiers).** Every repo gets a `CLAUDE.md` and `.github/copilot-instructions.md`.
- **Weeks 2–3 — Test Coverage Baseline (Tiers 1–2).** Get critical paths to 80% coverage.
- **Weeks 3–6 — Skill Validation (Tier 1).** Measure accuracy, speed, quality, cost.
- **Weeks 6–12 — Rollout to Tier 2.**
- **Weeks 12–16 — Tier 3 (Legacy).** Restricted-mode operation.

Legacy restriction snippet (drop into repo CLAUDE.md):

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

## Phase 6: Maintenance and Evolution (Ongoing)

### 6.1 Org Skills Governance

| Activity                                  | Frequency         | Owner                              |
|-------------------------------------------|-------------------|------------------------------------|
| Review org-level CLAUDE.md for accuracy   | Monthly           | Platform team                      |
| Update model routing based on cost data   | Quarterly         | Engineering leadership             |
| Audit skill usage metrics                 | Monthly           | Platform team                      |
| Review and prune auto-memory across repos | Monthly           | Each team                          |
| Update quality gates                      | Per release cycle | QA lead                            |
| Add new org skills                        | As needed         | Any developer (PR to hio-framework)|

### 6.2 Skill Contribution Process

1. Branch in hio-framework.
2. Add skill in `.claude/skills/<skill-name>/SKILL.md`.
3. Include `README.md` in the skill directory with examples.
4. Open PR with label `skill-proposal`.
5. Two approvals required (one platform team, one domain expert).
6. After merge, all repos pick up the skill on next session start.

### 6.3 Keeping Context Fresh

- PR template reminder for changes that affect architecture / batch schedules / API contracts.
- CI check that warns if `src/` changed significantly without updates to `.claude/` or `.github/copilot-instructions.md`.
- Monthly staleness audit comparing CLAUDE.md mtime vs. recent commit activity.

### 6.4 Cost Monitoring

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

Conflicts: when two levels give contradictory guidance, the more specific level wins. When two files at the same level conflict, behavior is non-deterministic — avoid this by keeping each concern in exactly one place.

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

*This plan is a living document. Update it as the org learns what works and what doesn’t. The best agent configuration is the one that evolves with your codebase.*
