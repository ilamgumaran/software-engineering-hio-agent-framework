# Agent Benchmarks (2026)

## Sources

| Benchmark | Primary URL | Purpose |
|---|---|---|
| **SWE-bench** (and SWE-bench Verified) | https://www.swebench.com/ | Real-world software engineering tasks from GitHub issues; verifies generated patches against test suites |
| **GAIA** | https://huggingface.co/gaia-benchmark | General assistant tasks: multi-step web browsing, file parsing, tool use; 466 tasks scored against ground-truth answers |
| **TAU-bench / TAU2-bench** | https://sierra.ai/blog/announcing-tau-bench | Customer-service interactions across retail, airline, telecom; dual-control design where AI agent and simulated user both modify a shared environment |
| **WebArena** | https://webarena.dev/ | Realistic web-agent tasks across e-commerce, forums, coding, content management |
| **AgentBench** | https://github.com/THUDM/AgentBench | LLM-as-agent across 8 distinct environments; tracks progress per environment |
| **HAL Reliability Dashboard** | https://hal.cs.princeton.edu/ | Holistic Agent Leaderboard; evaluates consistency, predictability, robustness, safety, self-awareness |
| **Multi-dimensional enterprise eval framework (paper)** | https://arxiv.org/html/2511.14136v1 | Beyond Accuracy: enterprise agentic AI evaluation framework |
| **2H-2026 leaderboard trends** | rapidclaw.dev `/blog/ai-agent-benchmarks-2026`, marktechpost.com `/2026/04/26/top-7-benchmarks-that-actually-matter-for-agentic-reasoning-in-large-language-models/` | Emerging emphasis on N-run consistency, policy adherence, cost-adjusted accuracy |

*Date extracted: May 2026.*

---

## What the major benchmarks measure

### SWE-bench Verified

Software-engineering benchmark on real GitHub issues. The agent must produce a patch that passes the project's existing test suite. Tracks the most dramatic progress curve in agentic AI: from 1.96% (Claude 2, 2023) to above 80% in vendor-reported late-2025 / early-2026 results. As of April 2026, Claude Opus 4.7 reports 87.6%.

### GAIA

General-assistant benchmark. 466 multi-step tasks requiring web browsing, file parsing, and tool use; scored by human graders against ground-truth answers. As of April 2026, Claude Sonnet 4.5 reports 74.6%; Anthropic models hold the top 6 positions on the public leaderboard.

### TAU-bench / TAU2-bench

Customer-service simulation from Sierra Research. Dual-control design: both the AI agent *and* a simulated user actively modify a shared environment, exposing policy adherence and tool misuse. Particularly stresses the OWASP Top 10 dimensions of Tool Misuse and Goal Manipulation.

### WebArena

Realistic web-agent tasks. The agent operates a browser inside a sandboxed environment containing recreations of an e-commerce site, a forum, a coding platform, and a content management system. Stresses long-horizon planning and recovery.

### HAL Reliability Dashboard

Does not just score correctness; scores **consistency** (same task, multiple runs), predictability, robustness to perturbation, safety (refusal of unsafe requests), and self-awareness (calibrated confidence). The 2H-2026 trend is for vendors and academic leaderboards to report HAL-style metrics alongside accuracy.

### 2026 trend: cost-adjusted accuracy and N-run consistency

Leaderboards increasingly report:

- **Cost-adjusted accuracy** -- accuracy / dollars per task
- **N-run consistency** -- pass@k for k > 1; how often the agent gets the same answer
- **Policy adherence** (TAU-bench style) -- did the agent stay within rules even when the simulated user pressed it

These three metrics separate production-ready from demo-ready, per the May-2026 surveys.

---

## Why this matters for the framework

The proposed `hio-evals` repo (in `multi-repo-orchestration/new-repos-proposed.md`) should **adopt these benchmarks rather than reinvent**:

- **SWE-bench Verified** for any HIO unit that produces code (Code Co-Creator, Architecture Explorer)
- **GAIA** for general-assistant tasks (Analysis Partner, Documentation & Knowledge)
- **TAU2-bench** for the routing matrix -- agents must respect routing under pressure, just as TAU-bench tests policy adherence under user pressure
- **HAL** dimensions (consistency, predictability, robustness, safety, self-awareness) become the eval categories for HIO agent behavior in `metrics/ai-utilization.md`

For the multi-repo orchestration framework specifically, there is no existing benchmark for **multi-repo coordination**. This is a real gap -- the proposed `hio-evals` repo would create one, modeled on TAU2-bench's dual-control design but with a repo registry as the shared environment.

---

## Concrete improvements informed by this reference

1. Add HAL dimensions (consistency, predictability, robustness, safety, self-awareness) to `metrics/ai-utilization.md`
2. Refine `hio-evals` proposal to use SWE-bench, GAIA, TAU2-bench as building blocks; design a multi-repo eval new
3. Add cost-adjusted accuracy and N-run consistency as scoring dimensions for **agent runs** (distinct from the existing **repo** scoring rubric)

---

## Where this reference shows up

| Place | How it's used |
|---|---|
| `multi-repo-orchestration/new-repos-proposed.md` | `hio-evals` proposal updated to use these benchmarks |
| `metrics/ai-utilization.md` | HAL dimensions added |
| `transformation/phase-2-prove-expand.md` | Capability development can target a benchmark per sprint |
