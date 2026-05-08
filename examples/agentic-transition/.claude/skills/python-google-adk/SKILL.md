---
description: >
  Scaffolds a Google Agent Development Kit (ADK) agent with tool
  registration, Vertex AI integration, evaluation harness, and Cloud
  Run deployment. Use when building production agents on Google Cloud.
---

## Google ADK Agent Scaffold

### Structure
- `agent/agent.py` — root agent definition
- `agent/tools/` — tool implementations (one file per tool)
- `agent/sub_agents/` — specialist sub-agents if multi-agent
- `agent/prompts/` — system + tool prompts (versioned)
- `evals/` — eval datasets + runner (ADK eval harness)
- `deployment/` — Cloud Run service config (Terraform)
- `pyproject.toml` — google-adk pinned, Python 3.12+

### Requirements
1. **Model selection:**
   - Vertex AI primary (Gemini 2.x or Claude on Vertex).
   - Fallback model configured for outage resilience.
   - Model ID NOT hardcoded — read from env / config.
2. **Tool design:**
   - Each tool has typed args (Pydantic) and a clear description.
   - Idempotent where possible. Document side effects in docstring.
   - Tool errors return structured failure, never raise into the agent loop.
3. **Memory / state:**
   - Use ADK session state for conversation memory.
   - Persistent memory: Firestore or Cloud SQL with TTL.
   - Never store PII in agent state without encryption.
4. **Evaluation (REQUIRED before merge):**
   - At least 30 eval examples covering happy path + edge cases.
   - Eval runs in CI. Threshold: must not regress >2% on golden set.
5. **Observability:**
   - OTel traces to Cloud Trace.
   - Per-tool latency, error count, token usage metrics.
   - Conversation logs to Cloud Logging with `session_id` correlation.
6. **Deployment:**
   - Cloud Run with min-instances configured for warm starts.
   - Identity-Aware Proxy for internal agents; OAuth for user-facing.
   - Secrets via Secret Manager, never env in plaintext.
7. **Safety:**
   - System prompt includes refusal rules.
   - Output filter for known prohibited categories.
   - Rate limit per user/session.

### Verification
- `python -m agent.eval` passes regression threshold.
- `pytest tests/` (unit + integration with mocked tools).
- `terraform plan` clean for deployment dir.

### Model Tier (for the human writing the agent)
Default: Sonnet. Escalate to Opus for multi-agent orchestration design,
safety policy review, or eval-set construction for high-stakes domains.
