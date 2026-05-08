---
description: >
  Scaffolds a new Micronaut microservice (Java 21 or Kotlin) with native
  GraalVM compilation, declarative HTTP clients, Bean Validation, and
  Datadog/OTel observability. Use when building new services where
  fast startup, low memory, and native image are priorities.
---

## Java Micronaut Service Scaffold

### Structure
- `src/main/java/<package>/Application.java` — entry point
- `src/main/java/<package>/api/<Resource>Controller.java`
- `src/main/java/<package>/api/<Resource>Request.java` (record)
- `src/main/java/<package>/api/<Resource>Response.java` (record)
- `src/main/java/<package>/client/<External>Client.java` — declarative HTTP client
- `src/main/java/<package>/service/<Resource>Service.java`
- `src/main/resources/application.yml`
- `src/test/java/<package>/api/<Resource>ControllerTest.java` (Micronaut Test)
- `Dockerfile` — multi-stage with GraalVM native-image

### Requirements
1. **Native compilation:** Configure `nativeImage` in `build.gradle.kts`. Add
   reflection / resource hints. Verify `./gradlew nativeCompile` succeeds.
2. **Validation:** Use Jakarta Bean Validation on request DTOs. `@Valid` on controllers.
3. **Declarative clients:** External calls via `@Client` interfaces. Configure
   timeouts and retries via `application.yml`, never hardcoded.
4. **Error handling:** Global `@Error(global = true)` handler returns RFC 7807.
5. **Observability:**
   - Micronaut Tracing + OTel exporter to Datadog APM.
   - Metrics via Micrometer to Datadog.
   - Structured JSON logs (logback JSON encoder).
6. **Health checks:** `/health` and `/health/readiness` configured. Liveness
   returns even during DB outage; readiness fails when DB unreachable.
7. **Config:** All tunables in `application.yml`. Secrets via env or AWS Secrets Manager.

### Performance Notes
- Native image startup: target < 100ms cold start.
- JIT mode: heap size tuned; set `-XX:+UseG1GC`.
- Avoid heavy reflection at runtime (breaks native image).

### Verification
- `./gradlew test` (Micronaut Test + Testcontainers)
- `./gradlew nativeCompile` succeeds
- Container image builds and `/health` returns 200

### Model Tier
Default: Sonnet. Escalate to Opus when designing native-image hints for
libraries with heavy reflection (Hibernate, Jackson polymorphism).
