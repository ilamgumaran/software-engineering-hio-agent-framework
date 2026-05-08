---
applyTo: "**/*.rs"
---

# Rust Conventions

- Rust stable, pinned via `rust-toolchain.toml`.
- `cargo fmt` and `cargo clippy --all-targets -- -D warnings` clean before commit.
- Errors: `thiserror` for libraries (typed variants), `anyhow` for app glue.
- Never `.unwrap()` / `.expect()` on user-affecting paths. Acceptable in `main`
  for startup invariants.
- Async: tokio multi-thread for services. `#[tracing::instrument]` on every handler.
- DB: sqlx with `query!` / `query_as!` macros. Run `cargo sqlx prepare` for offline mode.
- HTTP: axum + tower-http middleware (trace, compression, timeout).
- Logging: `tracing` + `tracing-subscriber` JSON formatter in prod.
- For new services follow `.claude/skills/rust-service-scaffold/SKILL.md`.
