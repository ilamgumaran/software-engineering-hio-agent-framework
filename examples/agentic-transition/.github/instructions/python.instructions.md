---
applyTo: "**/*.py"
---

# Python Conventions

- Python 3.12, Poetry for dependency management.
- Follow PEP 8. Format with Black; lint with Ruff.
- Type hints on every function signature; run mypy --strict on new code.
- Use `structlog` for structured logging; never `print` for diagnostics.
- Tests: pytest. Use `pytest-asyncio` for async tests.
- Mock all external IO in unit tests; integration tests use Testcontainers.
- Public functions get docstrings only when behavior is non-obvious.
