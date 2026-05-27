# Universal Agent-Ready Directory Structure

## Derived From

This structure synthesizes conventions from all six major agent platforms as of May 2026:

| Convention | Source | Adopted |
|------------|--------|---------|
| `AGENTS.md` at repo root | AAIF (OpenAI, Anthropic, Block via Linux Foundation) | Yes — universal entry point |
| `CLAUDE.md` layered hierarchy | Anthropic | Yes — agent-specific config |
| `.github/copilot-instructions.md` | Microsoft/GitHub | Yes — agent-specific config |
| `GEMINI.md` + `.gemini/` | Google | Yes — agent-specific config |
| `.amazonq/rules/` | Amazon | Yes — agent-specific config |
| `requirements.md` / `design.md` / `tasks.md` | Amazon Kiro | Yes — spec structure |
| `.claude/settings.json` permission model | Anthropic | Yes — adapted to generic form |
| YAML frontmatter scoping | Microsoft, Amazon | Yes — for path-specific rules |

## The Standard Structure

```
repo-root/
│
├── AGENTS.md                          # UNIVERSAL ENTRY POINT (AAIF standard)
│                                      # Agent-agnostic, read by ALL agents
│                                      # Pure markdown, no frontmatter
│
├── .agent-config/                     # GENERIC agent configuration
│   ├── AGENT_RULES.md                 # Detailed rules for any coding agent
│   ├── security-boundaries.md         # What agents must/must not do
│   ├── scoring/                       # Agent-readiness scoring
│   │   ├── rubric.md                  # Scoring dimensions and levels
│   │   └── self-score.md              # Current repo's self-assessment
│   └── prompt-injection-defenses.md   # Content fencing and sanitization rules
│
├── .claude/                           # CLAUDE CODE specific
│   ├── settings.json                  # Permissions, MCP servers
│   ├── settings.local.json            # User overrides (gitignored)
│   ├── commands/                      # Custom slash commands
│   └── skills/                        # Skill definitions
│
├── .github/                           # GITHUB COPILOT specific
│   ├── copilot-instructions.md        # Copilot-specific instructions
│   ├── instructions/                  # Path-scoped instruction files
│   └── agents/                        # Custom Copilot agent profiles
│
├── .gemini/                           # GEMINI specific
│   ├── settings.json                  # Gemini CLI config
│   └── agents/                        # Gemini subagent definitions
│
├── .amazonq/                          # AMAZON Q specific
│   └── rules/                         # Scoped rules with YAML frontmatter
│
├── CLAUDE.md                          # Claude Code instructions (loaded automatically)
├── GEMINI.md                          # Gemini CLI instructions (loaded automatically)
│
├── specs/                             # HUMAN-AUTHORED SPECIFICATIONS
│   ├── features/                      # What to build (behavior, not implementation)
│   ├── test-requirements/             # What tests must exist
│   └── acceptance-criteria/           # How to verify completeness
│
├── docs/                              # DOCUMENTATION
│   ├── architecture/                  # ADRs and system design
│   ├── human-learning/                # Concepts for human engineers
│   ├── agent-guides/                  # Task-specific guidance for agents
│   └── specs/                         # Spec templates and guidelines
│
├── src/                               # SOURCE CODE
├── tests/                             # TEST CODE
└── .gitignore                         # Must exclude agent local configs
```

## File Purposes

### Tier 1: Universal (Read by ALL Agents)

#### `AGENTS.md`
The single most important file. Every major coding agent (Codex, Claude Code, Copilot, Gemini, Q Developer, Cursor, Windsurf) reads this file. It must be:
- Pure markdown, no frontmatter, no schema
- At repo root
- Under 300 lines
- Self-contained (an agent reading only this file can start working)

Required content:
1. One-line repo identity
2. Project purpose and scope
3. Tech stack and directory layout
4. Build/test/lint commands
5. Coding conventions
6. What agents must not do
7. Links to detailed docs for agents that want more context

#### `specs/`
The source of truth for what the software should do. Human-authored, agent-read-only. Structured as feature specs + test requirements + acceptance criteria (the Kiro/HIO pattern).

### Tier 2: Generic Agent Config (Optional, Any Agent)

#### `.agent-config/AGENT_RULES.md`
Detailed rules that apply regardless of which agent is used. Includes TDD protocol, code standards, commit conventions, and architectural constraints. Agent-specific files (CLAUDE.md, etc.) should reference this rather than duplicate it.

#### `.agent-config/security-boundaries.md`
Explicit security boundaries: content fencing rules, permission model, sensitive surfaces. Referenced by all agent-specific configs.

#### `.agent-config/scoring/`
Self-assessment of how agent-ready the repo is. Uses the standardized rubric (A-axis: agentic readiness, B-axis: security).

### Tier 3: Agent-Specific (One Per Agent Platform)

Each agent platform has its own config directory and root-level file. These contain platform-specific settings (permissions, MCP servers, custom commands) and reference the generic AGENT_RULES.md for shared rules.

```
CLAUDE.md → references .agent-config/AGENT_RULES.md
.github/copilot-instructions.md → references .agent-config/AGENT_RULES.md
GEMINI.md → references .agent-config/AGENT_RULES.md
.amazonq/rules/general.md → references .agent-config/AGENT_RULES.md
```

## .gitignore Additions

```gitignore
# Agent local configs (user-specific, not committed)
.claude/settings.local.json
.gemini/settings.local.json
```

## Why This Structure

1. **Any agent can start working** by reading `AGENTS.md` alone
2. **Detailed agents get more context** from `.agent-config/` and agent-specific configs
3. **No duplication** — shared rules live in `.agent-config/AGENT_RULES.md`
4. **No lock-in** — switching agents means adding a new Tier 3 directory, not rewriting
5. **Security is centralized** — one security boundaries file, referenced everywhere
6. **Scoring is built-in** — repos can self-assess and improve their agent-readiness
7. **Specs drive development** — the Kiro/HIO pattern of specs → tests → code is structurally enforced
