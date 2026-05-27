# Agent Security Safeguards Checklist

A practical checklist for securing a repository against AI coding agent threats. Based on OWASP Top 10 for Agentic Applications, industry practices from Anthropic/OpenAI/Google/Microsoft/Amazon/Meta, and the HIO security policy.

## Before Agent Access (Repo Setup)

### Content Fencing
- [ ] All user-contributed content (issues, PR descriptions, comments) is labeled `[USER-CONTRIBUTED]` or equivalent before agent ingestion
- [ ] External documentation quoted in repo files is fenced with `[EXTERNAL-DOC]` attribution
- [ ] Agent-to-agent output is labeled `[AGENT-OUTPUT]` when passed between systems
- [ ] No "ignore previous instructions" examples exist without explicit injection-test fencing
- [ ] HTML content sanitized (no inline scripts, no unusual link structures)

### Permission Boundaries
- [ ] Agent instruction file (AGENTS.md or equivalent) states explicit "must not" rules
- [ ] Agent cannot push to default branch (main/master)
- [ ] Agent cannot force-push to any shared branch
- [ ] Agent cannot bypass CI/CD gates (--no-verify, signing skips)
- [ ] Agent cannot auto-merge PRs it authored
- [ ] Agent cannot modify CI/CD pipelines without human review
- [ ] Agent cannot disable tests, linters, or security scans
- [ ] Write access is per-task, not global

### Secret Protection
- [ ] No secrets in plaintext in any committed file
- [ ] Secret scanning enabled (GitHub secret scanning, git-secrets, or equivalent)
- [ ] Pre-commit hooks scan for credential patterns
- [ ] `.env` and credential files in `.gitignore`
- [ ] Agent instruction files explicitly state "never commit secrets"

### Dependency Security
- [ ] Dependencies pinned to immutable refs (SHA, signed releases) — no `latest` or branch refs
- [ ] New dependency additions require human review
- [ ] Automated vulnerability scanning on dependencies
- [ ] MCP servers and tool integrations inventoried

## During Agent Operation (Runtime)

### Sandboxing
- [ ] Agent runs in isolated environment (container, VM, or microVM)
- [ ] Filesystem write access limited to working directory
- [ ] Network egress filtered (allowlist-only outbound, or no network)
- [ ] Resource limits enforced (CPU, memory, time, token budget)
- [ ] No persistent state between sessions (stateless execution)

### Action Validation
- [ ] Irreversible actions require human approval (Decision Spectrum)
- [ ] Agent actions logged for audit trail
- [ ] Agent-generated code passes SAST before merge
- [ ] Output scanning for secrets/PII in commits, comments, and PR descriptions
- [ ] Reasoning traces redacted of sensitive content before persistence

### Task Scoping
- [ ] Per-task permissions (Least-Privilege)
- [ ] Per-task autonomy limits (Least-Agency)
- [ ] Per-task budgets: token limit, time limit, cost limit
- [ ] Agent cannot decide to make unbounded tool calls (fan-out protection)
- [ ] Task scope explicitly stated — agent validates actions against scope

## After Agent Operation (Review)

### Human Review Gates
- [ ] All agent-generated PRs require human review before merge
- [ ] Reviewer checks implementation against spec (not just "tests pass")
- [ ] New dependencies reviewed for supply chain risk
- [ ] Performance impact assessed
- [ ] Security implications considered

### Audit
- [ ] Agent action logs retained for review period
- [ ] Quarterly audit of agent activity patterns
- [ ] Anomalous behavior (unusual file access, unexpected tool calls) flagged
- [ ] Incident response procedure documented and tested

## Scoring Integration

This checklist maps to the HIO scoring rubric B-axis:

| Checklist Section | Scoring Dimension |
|-------------------|-------------------|
| Content Fencing | B3 Prompt injection awareness |
| Permission Boundaries | B1 Security boundary documentation, B5 Change reversibility |
| Secret Protection | B4 Secret and credential handling |
| Dependency Security | B4, B2 Sensitive surface inventory |
| Sandboxing | B5 Change reversibility |
| Action Validation | B5, B3 |
| Task Scoping | B1, B5 |
| Human Review Gates | B5 |
| Audit | B2 Sensitive surface inventory |
