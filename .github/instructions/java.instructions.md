---
applyTo: "**/*.java"
---

# Java Conventions

- Java 21, Spring Boot 3.x, Gradle.
- Follow Google Java Style. Format with Spotless.
- Use records for DTOs and value objects.
- Prefer `Optional<T>` over `null` returns from public APIs.
- Use slf4j for logging; never `System.out` / `System.err`.
- Tests: JUnit 5 + Mockito. Integration tests use Testcontainers.
- No `Thread.sleep()` in tests — use Awaitility for async.
- No network calls in unit tests.
- For Spring Batch jobs follow `.claude/skills/batch-job-scaffold/SKILL.md`.
- For controllers follow `.claude/skills/api-scaffold/SKILL.md`.
