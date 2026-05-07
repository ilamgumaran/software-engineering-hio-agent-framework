---
description: >
  Analyzes test coverage gaps and generates missing tests. Use when
  asked to improve coverage, add tests, or when a PR is missing tests.
  Operates at Sonnet tier per model-routing policy.
---

## Test Coverage Analysis

### Process
1. Run `./gradlew jacocoTestReport` (Java) or `pytest --cov` (Python).
2. Identify files below 80% line coverage.
3. Prioritize by risk: code touching money, PII, external APIs, or batch
   processing logic gets tested first.
4. Generate tests following the Arrange-Act-Assert pattern.
5. Verify tests are deterministic.

### Test Quality Rules
- One assertion concept per test method.
- Test names describe scenario: `should_returnNotFound_when_orderDoesNotExist`.
- No network calls in unit tests.
- Integration tests use Testcontainers.
- Test data builders over raw constructors.
- Never `Thread.sleep()` — use Awaitility for async.
