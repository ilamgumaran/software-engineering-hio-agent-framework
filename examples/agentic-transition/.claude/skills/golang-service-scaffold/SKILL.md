---
description: >
  Scaffolds a Go HTTP service with chi router, slog structured logging,
  OpenTelemetry tracing, graceful shutdown, and table-driven tests.
  Use when creating new Go microservices or batch workers.
---

## Go Service Scaffold

### Structure
- `cmd/<service>/main.go` — entry point, wiring
- `internal/api/` — HTTP handlers
- `internal/service/` — business logic
- `internal/store/` — DB access (sqlc-generated preferred)
- `internal/observability/` — OTel, slog setup
- `internal/config/` — env-driven config (envconfig or koanf)
- `Dockerfile` — multi-stage, distroless final
- `Makefile` or `magefile.go` — build, test, lint targets

### Requirements
1. **Go 1.22+.** Use `slog` (stdlib), not third-party loggers.
2. **Router:** chi (preferred for stdlib compat) or gin. Middleware order:
   recover → trace → log → auth → ratelimit → handler.
3. **Context everywhere:** every IO function takes `ctx context.Context`.
   Never use `context.Background()` outside `main`.
4. **Errors:**
   - Wrap with `fmt.Errorf("...: %w", err)`.
   - Sentinel errors via `errors.Is`; typed errors via `errors.As`.
   - Never `panic` in handlers.
5. **Concurrency:**
   - `errgroup.Group` for goroutine lifecycle.
   - Channels typed; closer documented.
   - Run `go test -race` in CI — race detector mandatory.
6. **Graceful shutdown:** SIGTERM → stop accepting → drain → close DB → exit.
   Default drain timeout 30s.
7. **Observability:**
   - OTel auto-instrumentation for net/http (otelhttp).
   - W3C trace context propagation.
   - Metrics via OTel: `http.server.duration`, `http.server.requests`, error rate.
   - Log correlation: include `trace_id` in every log line.
8. **Tests:**
   - Table-driven with `t.Run(name, ...)` subtests.
   - `httptest.Server` for integration; Testcontainers for DB.
   - Coverage: `go test -coverprofile`, target 80%+ on `internal/`.
9. **Lint:** `golangci-lint` with `errcheck`, `govet`, `staticcheck`, `revive`,
   `gosec`, `ineffassign`, `unused`.

### Anti-patterns
- No package-level mutable state.
- No `init()` doing IO or panicking.
- Don't ignore returned errors (`errcheck` enforces).
- Don't use `interface{}` / `any` when a real type works.
- Don't reuse `context.WithValue` for non-request-scoped data.

### Verification
- `go test -race ./...` passes.
- `golangci-lint run` clean.
- Container builds and `/healthz` returns 200.

### Model Tier
Default: Sonnet. Escalate to Opus for concurrency-heavy designs or
performance-critical hot paths (>10k req/s).
