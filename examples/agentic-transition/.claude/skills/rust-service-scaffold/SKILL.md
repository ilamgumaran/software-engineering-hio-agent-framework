---
description: >
  Scaffolds a Rust HTTP service with axum + tokio, tracing, sqlx,
  and proper error handling. Use when creating new Rust microservices
  or rewriting hot-path services where memory safety and tail latency
  matter.
---

## Rust Service Scaffold

### Structure
- `src/main.rs` — wiring + shutdown
- `src/api/` — axum routes + handlers
- `src/service/` — business logic
- `src/store/` — sqlx queries (offline mode for CI)
- `src/error.rs` — thiserror / anyhow split
- `src/observability.rs` — tracing-subscriber + OTel
- `migrations/` — sqlx migrate
- `Cargo.toml`, `rust-toolchain.toml` (pin stable)
- `Dockerfile` — multi-stage, distroless or scratch

### Requirements
1. **Toolchain:** Rust stable, pinned via `rust-toolchain.toml`.
2. **Runtime:** tokio multi-thread for services, current-thread for CPU-bound workers.
3. **HTTP:** axum + tower-http for middleware (trace, compression, timeout, cors).
4. **Errors:**
   - **Libraries:** `thiserror` for typed errors with stable variants.
   - **Apps / handlers:** `anyhow::Result` + an `IntoResponse` impl mapping
     to RFC 7807.
   - NEVER `.unwrap()` or `.expect()` in production paths. Acceptable in
     `main` for startup invariants only.
5. **Database:** sqlx with `query!` / `query_as!` macros (compile-time checked).
   Run `cargo sqlx prepare` in CI for offline mode.
6. **Async correctness:**
   - No blocking calls in async fns. Use `tokio::task::spawn_blocking` for
     CPU-bound work or sync libs.
   - Cancellation safety: every `.await` point must be safe to cancel.
7. **Observability:**
   - `tracing` + `tracing-subscriber` with JSON formatter in prod.
   - OTel via `opentelemetry-otlp` exporter.
   - Spans on every handler; instrument with `#[tracing::instrument]`.
8. **Testing:**
   - `tokio::test` for async tests.
   - `axum::Router` testable via `tower::ServiceExt::oneshot`.
   - Property tests via `proptest` for parsers / serializers.
   - Benchmarks via `criterion` for hot paths.
9. **Lint:** `cargo clippy --all-targets -- -D warnings`. `rustfmt` on every commit.

### Anti-patterns
- Don't `Box<dyn Error>` everywhere — use specific error types in libraries.
- Don't share `&mut` across tasks; prefer message-passing or `Arc<Mutex<...>>`
  *only* when state is small and contention is low.
- Don't write your own async retry; use `tokio-retry` or `backon`.

### Verification
- `cargo test --all-features` passes.
- `cargo clippy -- -D warnings` clean.
- `cargo audit` no known vulnerabilities.
- Image builds and `/healthz` returns 200.

### Model Tier
Default: Sonnet. Escalate to Opus for unsafe code review, lifetime-heavy
APIs, or designing zero-copy parsing.
