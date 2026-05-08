# Agentic Transition — Application Layer

This directory contains an opinionated, end-to-end example of how an
org can adopt GitHub Copilot + Claude Code CLI across many repos. It
is deliberately kept under `examples/` so the core HIO framework
(cognitive functions, units, agents, workflows in the repo root) is
not disturbed by application-level material.

## Read in this order

1. `BEST_PRACTICES.md` — the focused plan and best practices: how
   agents stay repo-aware without re-analysis, and how skills /
   prompts / tools / sub-agents are stored, shared, and kept fresh.
2. `transition-playbook.md` — the longer phased rollout (governance,
   metrics, repo tiers, distribution mechanisms).
3. `AGENTS.md`, `.github/copilot-instructions.md`,
   `.github/instructions/` — example org-level multi-agent /
   Copilot instructions and path-scoped rules.
4. `.claude/skills/`, `.claude/rules/`, `.claude/agents/` — example
   reusable Claude Code skills, path-scoped rules, and specialist
   sub-agents.
5. `.github/prompts/` — Copilot slash-command prompt files mirroring
   the most-used skills.
6. `config/` — example model routing, cost policy, and quality gates.
7. `repo-setup-batch/`, `repo-setup-api/` — per-archetype repo
   templates (CLAUDE.md, AGENTS.md, copilot-instructions, rules).

## Skills Index

### Foundational scaffolds (Java / Spring)
| Skill | What it does |
|---|---|
| `batch-job-scaffold` | Spring Batch job with idempotency, checkpoint/restart, observability |
| `api-scaffold` | Spring REST endpoint with validation, RFC 7807, OpenAPI |

### Language / framework scaffolds
| Skill | What it does |
|---|---|
| `java-micronaut-scaffold` | Micronaut microservice, GraalVM native, declarative HTTP clients |
| `python-fastapi-genai` | FastAPI service for Claude-backed GenAI apps |
| `python-google-adk` | Google Agent Development Kit agent on Vertex AI |
| `golang-service-scaffold` | Go HTTP service with chi, slog, OTel |
| `rust-service-scaffold` | Rust HTTP service with axum, tokio, sqlx |

### Cloud / data
| Skill | What it does |
|---|---|
| `gcp-cloud-run` | Cloud Run service with concurrency, scaling, traffic mgmt |
| `gcp-bigquery` | BigQuery schema, partitioning, clustering, query patterns |
| `gcp-pubsub` | Pub/Sub publisher/subscriber, DLT, ordering, exactly-once |
| `gcp-dataflow-beam` | Apache Beam / Dataflow pipelines (batch + streaming) |
| `elasticsearch-query` | ES / OpenSearch mappings, queries, ILM |
| `db-migration` | Reversible PostgreSQL migrations with lock/index analysis |

### GenAI / LLM
| Skill | What it does |
|---|---|
| `prompt-caching-claude` | Anthropic prompt caching for cost / latency |
| `claude-tool-use` | Tool design, parallel calls, error handling, loop control |
| `eval-driven-genai` | Eval-first workflow with golden sets and CI regression gates |

### Engineering excellence
| Skill | What it does |
|---|---|
| `test-coverage` | Coverage gap analysis and deterministic test generation |
| `perf-review` | Batch + API performance review |
| `cost-check` | Resource cost sanity-check before merge |
| `slo-error-budget` | SRE-style SLOs and error budget policy |
| `observability-otel` | OTel traces / metrics / logs with correlation |
| `dependency-security-scan` | SBOM, SCA, vulnerability + license scanning |
| `incident-postmortem` | Blameless post-incident review template |

### Sub-agents
| Agent | When to invoke |
|---|---|
| `code-reviewer` | Independent diff review before merge |
| `batch-specialist` | Batch / data-pipeline design or refactor |
| `api-specialist` | REST API design, contract evolution, breaking-change review |

### Path-scoped instructions (`.github/instructions/`)
| File | Scope |
|---|---|
| `java.instructions.md` | `**/*.java` |
| `python.instructions.md` | `**/*.py` |
| `sql.instructions.md` | `**/*.sql` |
| `terraform.instructions.md` | `**/*.tf` |
| `go.instructions.md` | `**/*.go` |
| `rust.instructions.md` | `**/*.rs` |

## How to adopt

Treat this directory as a starter kit you copy *into a separate
org-level repo* (e.g., `hio-framework`) — not as something the core
HIO framework repo enforces. The core framework defines cognitive
structure; this example shows one concrete way to operationalize it
for batch / API / data / GenAI engineering teams at scale.
