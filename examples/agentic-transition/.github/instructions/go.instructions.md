---
applyTo: "**/*.go"
---

# Go Conventions

- Go 1.22+. `slog` (stdlib) for logging.
- Format with `gofumpt`. Lint with `golangci-lint`.
- Always `context.Context` as first param on IO functions.
- Errors: wrap with `fmt.Errorf("...: %w", err)`. `errors.Is` / `errors.As` for inspection.
- No `panic` in handlers. No package-level mutable state.
- Tests: table-driven with `t.Run` subtests. `go test -race` enforced in CI.
- Concurrency: `errgroup.Group`. Channels typed; document closer.
- HTTP: chi router with `otelhttp` instrumentation.
- For new services follow `.claude/skills/golang-service-scaffold/SKILL.md`.
