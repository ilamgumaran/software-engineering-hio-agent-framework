---
description: >
  Scaffolds a new REST API endpoint with validation, error handling,
  rate limiting, and OpenAPI documentation. Use when asked to create
  a new endpoint, controller, or API resource.
---

## API Endpoint Scaffold

### Structure
- `src/main/java/<package>/api/<Resource>Controller.java`
- `src/main/java/<package>/api/<Resource>Request.java` (record)
- `src/main/java/<package>/api/<Resource>Response.java` (record)
- `src/main/java/<package>/service/<Resource>Service.java`
- `src/main/java/<package>/exception/<Resource>Exception.java`
- `src/test/java/<package>/api/<Resource>ControllerTest.java`
- `src/test/java/<package>/service/<Resource>ServiceTest.java`

### Requirements
1. **Validation:** Jakarta Bean Validation; custom validators for business rules.
2. **Error handling:** Global exception handler returns RFC 7807:
   ```json
   {
     "type": "https://api.example.com/errors/resource-not-found",
     "title": "Resource Not Found",
     "status": 404,
     "detail": "Order 12345 does not exist",
     "instance": "/api/v1/orders/12345"
   }
   ```
3. **OpenAPI:** `@Operation`, `@ApiResponse`, `@Schema`. Spec auto-generates at build time.
4. **Rate limiting:** Default 100 req/s per client.
5. **Observability:** Request/response logging at DEBUG (sanitize PII); metrics
   `api.<resource>.<method>.latency`, `.count`, `.error_count`; Datadog trace propagation.
6. **Versioning:** New resources start at v1. Breaking changes get a new version.

### Model Tier
Default: Sonnet. Escalate to Opus for new public APIs or any contract change
that affects ≥2 consumers.
