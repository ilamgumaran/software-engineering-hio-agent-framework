# Agent-Readiness Scoring Mechanism

A generic, agent-agnostic scoring system for evaluating how effectively any repository can be worked on by coding agents. Derived from the HIO scoring rubric, adapted for universal use.

## How to Use This

1. Copy the rubric below into `.agent-config/scoring/rubric.md` in your repo
2. Score your repo by finding evidence for each dimension
3. Record your scores in `.agent-config/scoring/self-score.md`
4. Use the improvement guide to raise low scores
5. Re-score quarterly or after major restructuring

---

## Scoring Dimensions

Two axes, five dimensions each. Score each L1-L5.

### Axis A: Agentic Readiness

How well can an agent walk in cold and do useful work?

#### A1. Agent Orientation

Does the repo have an agent instruction file that orients the agent in under 30 seconds?

| Level | Criteria |
|-------|----------|
| **L1** | No agent guidance file |
| **L2** | README mentions agents informally |
| **L3** | AGENTS.md (or equivalent) exists but is incomplete or vague |
| **L4** | AGENTS.md follows AAIF standard with build commands, conventions, constraints, and explicit "must not" rules |
| **L5** | AGENTS.md validated in CI; agent-specific configs (CLAUDE.md, copilot-instructions.md) also present and consistent |

#### A2. Spec Clarity

Can an agent understand what to build from written specifications?

| Level | Criteria |
|-------|----------|
| **L1** | No specifications; requirements are verbal or in chat |
| **L2** | Issues or tickets describe features loosely |
| **L3** | Spec files exist but lack test requirements or acceptance criteria |
| **L4** | Complete spec triplets: feature spec + test requirements + acceptance criteria |
| **L5** | Specs templated, versioned, and linked from AGENTS.md; agents can discover specs programmatically |

#### A3. Test Infrastructure

Can an agent run tests and get fast, reliable feedback?

| Level | Criteria |
|-------|----------|
| **L1** | No tests or test framework |
| **L2** | Some tests exist but no clear run command |
| **L3** | Test suite exists with documented run command; some flaky tests |
| **L4** | Reliable test suite, <2 min for unit tests, documented in agent instruction file |
| **L5** | Test suite with coverage reporting, benchmark suite, CI integration, and agent can run tests autonomously |

#### A4. Build Simplicity

Can an agent build the project with a single command?

| Level | Criteria |
|-------|----------|
| **L1** | No build system or undocumented manual steps |
| **L2** | Build works but requires manual environment setup |
| **L3** | Build command documented; requires 2-3 setup steps |
| **L4** | Single-command build from clean checkout; all dependencies managed by build tool |
| **L5** | Build works in any CI environment; containerized dev environment available; agent can build without human help |

#### A5. Documentation for Agents

Does the repo provide structured documentation that agents can reference?

| Level | Criteria |
|-------|----------|
| **L1** | No documentation beyond README |
| **L2** | Some docs exist but unstructured |
| **L3** | Architecture docs and API docs exist |
| **L4** | Structured docs: ADRs, agent workflow guides, code conventions, domain knowledge |
| **L5** | Docs include agent-specific guides, templates, and examples; cross-referenced from agent instruction files |

---

### Axis B: Security

How safely can an agent operate in this repo?

#### B1. Security Boundary Documentation

Does the repo state what an agent must not do?

| Level | Criteria |
|-------|----------|
| **L1** | No security guidance for agents |
| **L2** | Generic security advice in README |
| **L3** | Agent instruction file lists "must not" rules |
| **L4** | Dedicated security boundaries file; references OWASP Agentic Top 10; Least-Agency principle applied |
| **L5** | Boundaries enforced by tooling (hooks, CI, permission configs); tested with red-team scenarios |

#### B2. Sensitive Surface Inventory

Are sensitive files and directories explicitly identified?

| Level | Criteria |
|-------|----------|
| **L1** | No inventory of sensitive areas |
| **L2** | Some sensitive files mentioned in passing |
| **L3** | Inventory exists but incomplete |
| **L4** | Complete inventory: secrets, configs, CI/CD pipelines, production data paths, agent memory |
| **L5** | Inventory drives access control (deny rules in agent config, CODEOWNERS) |

#### B3. Prompt Injection Defenses

Is content guarded against prompt injection attacks?

| Level | Criteria |
|-------|----------|
| **L1** | No awareness; external content rendered raw into agent context |
| **L2** | Docs mention injection risk; no implementation |
| **L3** | Some content fencing or labeling of untrusted sources |
| **L4** | All untrusted content (issues, PRs, agent output) fenced and labeled; agents instructed to refuse fenced instructions |
| **L5** | Defenses tested with red-team injection examples; covers OWASP Goal Manipulation and Inter-Agent Injection |

#### B4. Secret and Credential Handling

Are secrets handled cleanly?

| Level | Criteria |
|-------|----------|
| **L1** | Secrets in plaintext or committed to repo |
| **L2** | Secrets externalized but no automated scanning |
| **L3** | Secret scanning enabled (pre-commit or CI) |
| **L4** | Secret scanning + pre-commit hooks + rotation policy documented |
| **L5** | Zero-secret architecture (workload identity, OIDC); reasoning trace redaction validated |

#### B5. Change Reversibility and Review

Are irreversible changes guarded? Are AI changes always reviewed?

| Level | Criteria |
|-------|----------|
| **L1** | No protections; agent can push to main |
| **L2** | Branch protection only |
| **L3** | Branch protection + required human reviewers |
| **L4** | Reversibility-aware policy: agent may decide reversible, recommend semi-reversible, only analyze irreversible; per-task budgets enforced |
| **L5** | Policy enforced in tooling and audited; supply-chain controls for new tools/dependencies |

---

## Computing the Score

**Do not average into a single number.** Compute two summary levels:

- **Agentic Readiness Level** = floor(mean(A1..A5))
- **Security Level** = floor(mean(B1..B5))

Report both: "This repo is **A3 / B2**."

A repo at A4/B2 has a very different risk profile than A2/B4. **Treat low B levels as blocking issues** — a well-configured but insecure repo is worse than a poorly-configured but safe one.

## Level Thresholds

| Level | Label | Meaning |
|-------|-------|---------|
| **L1** | Unaware | Agents cannot safely or effectively work here |
| **L2** | Aware | Basic recognition that agents will interact with the repo |
| **L3** | Structured | Foundational structures in place; agents can do basic work |
| **L4** | Optimized | Agents can work effectively with appropriate guardrails |
| **L5** | Leading | Best-in-class; agents are full development partners |

## Improvement Priorities

1. **If B < 3**: Fix security first. Add boundary documentation (B1), secrets scanning (B4), and branch protection (B5).
2. **If A1 < 3**: Add AGENTS.md. This is the single highest-leverage improvement.
3. **If A3 < 3**: Fix test infrastructure. Agents without tests produce unverifiable code.
4. **If A2 < 3**: Add specs. Without specs, agents guess — and guesses produce bugs.
5. **If A4 < 3**: Simplify the build. If an agent can't build the project, it can't verify its work.

## Re-Scoring Triggers

| Trigger | Scope |
|---------|-------|
| Quarterly cadence | Full re-score |
| Major restructuring | Affected dimensions |
| Security incident | B1-B5 immediate |
| New agent platform added | A1, A5 |
| New contributors (human or agent) | A1, A2, B1 |
