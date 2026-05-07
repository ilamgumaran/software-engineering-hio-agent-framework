---
description: >
  Scaffolds a new REST API endpoint with validation, error handling,
  rate limiting, and OpenAPI documentation. Use when asked to create
  a new endpoint, controller, or API resource.
---

## API Endpoint Scaffold

### Structure
- `src/main/java/<package>/api/<Resource>Controller.java` — REST controller
- `src/main/java/<package>/api/<Resource>Request.java` — request DTO (record)
- `src/main/java/<package>/api/<Resource>Response.java` — response DTO (record)
- `src/main/java/<package>/service/<Resource>Service.java` — business logic
- `src/main/java/<package>/exception/<Resource>Exception.java` — domain exception
- `src/test/java/<package>/api/<Resource>ControllerTest.java` — MockMvc tests
- `src/test/java/<package>/service/<Resource>ServiceTest.java` — unit tests

### Requirements
1. **Validation:** Jakarta Bean Validation on request DTOs. Custom validators for business rules.
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
3. **OpenAPI:** Annotate with `@Operation`, `@ApiResponse`, `@Schema`. Spec auto-generates at build time.
4. **Rate limiting:** Default 100 req/s per client; override via annotation for high-throughput endpoints.
5. **Observability:**
   - Request/response logging at DEBUG (sanitize PII).
   - Metrics: `api.<resource>.<method>.latency`, `.count`, `.error_count`.
   - Trace propagation via Datadog headers.
6. **Versioning:** New resources start at v1. Breaking changes get a new version. Old versions get a deprecation header and sunset date.

### Model Tier
Default: Sonnet. Escalate to Opus for new public APIs or any contract change
that affects ≥2 consumers.
