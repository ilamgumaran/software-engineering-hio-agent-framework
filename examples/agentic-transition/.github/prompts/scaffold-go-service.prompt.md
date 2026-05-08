---
mode: 'agent'
description: 'Scaffold a Go HTTP service with chi, slog, OTel, and table-driven tests.'
---

# Scaffold Go Service

Generate a Go HTTP service following org conventions.

## What to Generate
- `cmd/<service>/main.go` with graceful shutdown on SIGTERM.
- chi router with middleware order: recover → trace → log → auth → ratelimit.
- `slog` JSON handler with `trace_id` correlation.
- OTel auto-instrumentation (`otelhttp`).
- One example handler with table-driven tests.
- `Dockerfile` (multi-stage, distroless final).
- `Makefile` with build / test / lint targets.
- `golangci-lint` config with errcheck, govet, staticcheck, revive, gosec.

## Constraints
- Go 1.22+. No package-level mutable state.
- Every IO function takes `ctx context.Context`.
- `go test -race ./...` mandatory in CI.
- No panics in handlers.

## Reference
`.claude/skills/golang-service-scaffold/SKILL.md`.
