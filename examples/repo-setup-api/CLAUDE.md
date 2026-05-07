# api-customer-service (template)

## What This Repo Does
Public-facing customer profile API. Handles read-heavy traffic (~3000 req/s p99)
and low-volume writes through a separate write path with stricter validation.

## How to Build and Test
- Build: `./gradlew build`
- Test: `./gradlew test`
- Run locally: `./gradlew bootRun --args='--spring.profiles.active=local'`
- API docs: `http://localhost:8080/swagger-ui.html`

## Key Design Decisions
- Reads served from Redis cache with 60s TTL; cache miss falls back to read replica.
- Writes go to primary with synchronous validation against the address service.
- All endpoints are versioned (`/api/v1/...`). Breaking changes get `/v2/...`.
- p99 latency budget: 200ms.

## What Agents Need to Know
- `customer.email` and `customer.phone` are PII. Mask in logs.
- Address validation calls an external service; mock it in unit tests.
- Adding a new endpoint requires updating the OpenAPI spec AND the
  internal API catalog (link in `docs/api-catalog.md`).

## Override: Stricter PII Handling
This repo enforces stricter PII rules than the org default — see
`.claude/rules/pii-handling.md`.
