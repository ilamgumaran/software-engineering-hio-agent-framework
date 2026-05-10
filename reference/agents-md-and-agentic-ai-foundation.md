# AGENTS.md and the Agentic AI Foundation (AAIF)

## Source

| Field | Value |
|---|---|
| **Title** | AGENTS.md -- a simple, open format for guiding coding agents |
| **Type** | Open standard |
| **Primary URL** | https://agents.md/ |
| **Repository** | https://github.com/agentsmd/agents.md |
| **Stewardship** | Linux Foundation -- Agentic AI Foundation (AAIF), launched December 2025 by Anthropic, OpenAI, and Block |
| **OpenAI guide** | https://developers.openai.com/codex/guides/agents-md |
| **Date extracted** | May 2026 |

---

## Core thesis

AGENTS.md is intentionally lightweight: a single markdown file at a repository root that gives AI coding agents the context they need to operate productively in that repository. Standard markdown, no schema, no frontmatter, freeform headings. Tooling parses it as plain text. Agents read it before doing meaningful work.

In December 2025, OpenAI's AGENTS.md convention was contributed to the Linux Foundation's new Agentic AI Foundation (AAIF), alongside Anthropic's Model Context Protocol and Google's Agent2Agent protocol -- consolidating the three core agentic-AI standards under a neutral consortium.

---

## Adoption (May 2026)

Native AGENTS.md support exists in:

- **OpenAI Codex** -- documented in OpenAI Developer guides
- **Cursor** -- referenced as project-level instructions
- **Windsurf** -- agent context loader
- **Kilo Code** -- documented in `kilo.ai/docs/customize/agents-md`
- **Builder.io** -- documented in `builder.io/c/docs/agents-md`
- **Factory** -- documented in `docs.factory.ai/cli/configuration/agents-md`
- Multiple internal coding agents at large enterprises

Research-backed evidence (cited at [asdlc.io/practices/agents-md-spec](https://asdlc.io/practices/agents-md-spec/) and [atlan.com/know/how-to-write-agents-md](https://atlan.com/know/how-to-write-agents-md/)) reports developer-written AGENTS.md files improve task success rates by ~4 percentage points and reduce agent-generated bugs by 35-55% in projects with detailed files. Notably, LLM-generated AGENTS.md files perform *worse than no file* in some settings -- specificity and correctness matter more than presence.

---

## What the public AGENTS.md does and does not specify

**Specifies:**

- File name and root location
- Markdown format, no frontmatter
- Intent: orient an agent to a repository

**Does not specify:**

- Section headings
- Required content fields
- Versioning conventions
- Multi-repo coordination
- Routing rules between humans and agents
- Security boundaries
- Scoring or rubrics

This is by design -- AGENTS.md is the connector at the file level, not a complete spec.

---

## Relationship to this framework's `AGENTS-SPEC-v1`

`multi-repo-orchestration/agent-spec/AGENTS-SPEC-v1.md` is **a superset** of the public AGENTS.md convention. Compatibility:

| Aspect | Public AGENTS.md | This framework's spec | Compatible? |
|---|---|---|---|
| File name | `AGENTS.md` | `AGENTS.md` | Yes |
| Location | Repo root | Repo root | Yes |
| Markdown only, no frontmatter | Required | Required | Yes |
| Section headings | Free | Defined (10 required) | Compatible -- public spec allows any headings; defined headings satisfy the public spec |
| Spec version line | Not specified | Required (last line: `Spec: AGENTS-SPEC-v1`) | Compatible -- additive; ignored by readers that don't know the convention |
| Cross-repo registry | Not specified | Required via Family + Trace links | Additive |
| Per-repo dos/don'ts | Not specified | Required | Additive |
| HIO routing | Not specified | Required | Additive |
| Security boundaries | Not specified | Required | Additive |

Any agent that understands public AGENTS.md (Codex, Cursor, Windsurf, Kilo, etc.) reads our files correctly and gets useful orientation. Agents aware of this framework's spec get the additional structure for free.

---

## HIO Integration Notes

- `multi-repo-orchestration/agent-spec/AGENTS-SPEC-v1.md` declares public-AGENTS.md compatibility explicitly
- Scoring rubric dimension **A1 -- Agent orientation** lifts to L5 only when the file passes both the public AGENTS.md check and this framework's section requirements
- When working with forks or external orgs, agents should expect *only* the public AGENTS.md baseline; the additional sections are an HIO-family extension

## Where this reference shows up

| Place | How it's used |
|---|---|
| `multi-repo-orchestration/agent-spec/AGENTS-SPEC-v1.md` | Header note declaring compatibility |
| `multi-repo-orchestration/scoring/scoring-rubric.md` | A1 level definitions reference public-spec compatibility |
| `multi-repo-orchestration/skills/repo-cartographer.md` | Validation step includes public-AGENTS.md compatibility check |
| `multi-repo-orchestration/governance/sme-update-workflow.md` | AAIF version tracking added to spec change procedure |
