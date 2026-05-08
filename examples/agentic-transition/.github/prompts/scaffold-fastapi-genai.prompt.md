---
mode: 'agent'
description: 'Scaffold a FastAPI service for Claude-backed GenAI apps with prompt caching, streaming, and tool use.'
---

# Scaffold FastAPI GenAI Service

Use this prompt to scaffold a new Python service following the org's
conventions for GenAI applications.

## What to Generate
- FastAPI application with async Anthropic SDK client.
- SSE streaming endpoint and a non-streaming endpoint.
- Prompt caching enabled on the system prompt.
- Tool use endpoint with at least one example tool.
- Pydantic v2 request/response models with full type hints.
- Pytest tests with mocked Anthropic client.
- Dockerfile (multi-stage, non-root) and `pyproject.toml` (Poetry).
- Health endpoints: `/healthz`, `/readyz`.
- OTel auto-instrumentation for FastAPI + httpx.
- Structured logging with `request_id` and token usage per request.

## Constraints
- Default model: `claude-sonnet-4-6` (configurable via env).
- Map Anthropic SDK exceptions to RFC 7807 problem details.
- No PII in logs.
- Per-request `max_tokens` cap.

## Reference
Follow the patterns in `.claude/skills/python-fastapi-genai/SKILL.md` and
`.claude/skills/prompt-caching-claude/SKILL.md`.
