---
description: >
  Scaffolds a FastAPI service for GenAI applications using the Anthropic
  Python SDK with prompt caching, SSE streaming, tool use, and structured
  error handling. Use when building LLM-backed APIs, chatbots, or agent
  endpoints in Python.
---

## FastAPI for GenAI Apps

### Structure
- `app/main.py` — FastAPI app, middleware, routers
- `app/clients/anthropic.py` — typed wrapper around the Anthropic SDK
- `app/routes/chat.py` — streaming + non-streaming endpoints
- `app/routes/tools.py` — tool-use endpoints
- `app/models/` — Pydantic v2 request/response models
- `app/observability/` — OTel + Prometheus setup
- `app/evals/` — eval harness (see `eval-driven-genai` skill)
- `tests/` — pytest + httpx.AsyncClient
- `pyproject.toml` — Poetry, Python 3.12+
- `Dockerfile` — distroless or python:3.12-slim, non-root user

### Requirements
1. **Anthropic SDK:**
   - Default model: `claude-sonnet-4-6` (configurable).
   - Prompt caching ON for system prompts and large static context.
   - Use `anthropic.AsyncAnthropic` everywhere; never block the event loop.
2. **Streaming:** SSE endpoints return `text/event-stream`. Client disconnects
   must cancel the upstream request via `asyncio.CancelledError`.
3. **Tool use:** Tools defined as Pydantic models. JSON Schema generated from
   the model. See `claude-tool-use` skill for design rules.
4. **Error handling:**
   - Map `anthropic.RateLimitError` → 429 + Retry-After.
   - Map `anthropic.APITimeoutError` → 504.
   - Map `anthropic.APIStatusError` → 502 with sanitized detail.
   - All errors RFC 7807-shaped.
5. **Observability:**
   - OTel auto-instrumentation for FastAPI + httpx.
   - Metrics: request count/latency, tokens in/out, cache hit rate, tool-call count.
   - Log every request with `request_id`, model, tokens, latency.
   - NEVER log full prompt content if it may contain PII.
6. **Health:** `/healthz` (liveness), `/readyz` (checks Anthropic API reachability).
7. **Auth:** API key via header; rate limit per key (slowapi or external).
8. **Cost guardrails:** Per-request `max_tokens` cap; per-API-key daily token budget.

### Anti-patterns
- Don't `time.sleep` in async code — use `asyncio.sleep`.
- Don't pass user-controlled strings as system prompt without sanitization.
- Don't disable streaming for long completions — it doubles perceived latency.
- Don't forget `cache_control` on stable system prompts — 90% cost savings on repeated calls.

### Verification
- `pytest -q` with mocked Anthropic client.
- Smoke test against real API in CI nightly (small budget).
- Lint: `ruff check`, type: `mypy --strict`.

### Model Tier
Default: Sonnet. Escalate to Opus for agent loop design or when adding
multi-tool orchestration with parallel calls.
