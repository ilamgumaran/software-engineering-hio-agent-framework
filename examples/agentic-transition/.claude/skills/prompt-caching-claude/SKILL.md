---
description: >
  Adds Anthropic prompt caching to Claude API calls to reduce cost
  and latency on repeated context. Use when building LLM apps that
  send the same system prompt, tool definitions, or document corpus
  across many requests.
---

## Anthropic Prompt Caching

### When to Use
- System prompt > ~1024 tokens that's stable across requests.
- Tool definitions repeated across calls.
- Long documents fed into many turns of a conversation.
- Few-shot examples used as part of system context.
- RAG pipelines where retrieved chunks are reused within a session.

Do NOT cache:
- Per-request user input.
- Highly dynamic context that changes every call.
- Content under 1024 tokens (cache miss often costs more than savings).

### Mechanics
- Mark cacheable content with `cache_control: {"type": "ephemeral"}`.
- Cache breakpoints can appear in `system`, `messages`, `tools`.
- Up to 4 breakpoints per request.
- Default TTL: 5 minutes. Use `"ttl": "1h"` for longer-lived caches.
- **Order matters:** cached blocks must appear BEFORE dynamic blocks. The
  cache is a prefix match.

### Code Pattern (Python SDK)
```python
response = client.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=1024,
    system=[
        {
            "type": "text",
            "text": LARGE_STABLE_SYSTEM_PROMPT,
            "cache_control": {"type": "ephemeral"},
        }
    ],
    tools=[
        {"name": "...", "description": "...", "input_schema": {...},
         "cache_control": {"type": "ephemeral"}},
    ],
    messages=[{"role": "user", "content": user_message}],
)
```

### Verification
- Inspect `usage.cache_creation_input_tokens` (first call) and
  `usage.cache_read_input_tokens` (subsequent calls).
- Cache hit cost is ~10% of regular input cost. Track in logs.
- Set up a metric `claude.cache_hit_rate` and alert if it drops below target.

### Common Mistakes
- Putting dynamic data BEFORE cached blocks — invalidates cache.
- Cache breakpoint on content that varies (timestamps, request IDs).
- Forgetting that whitespace and ordering matter for the prefix match.
- Caching too aggressively — cache write costs 25% more on first call.

### Cost Math
- Cache write: 1.25× input cost.
- Cache read: 0.1× input cost.
- Break-even: 2 cache hits within TTL on the same prefix.
- Realistic savings: 60–90% on input tokens for chat / agent loops.

### Model Tier
Default: Sonnet. The skill applies to whatever model the calling code uses.
