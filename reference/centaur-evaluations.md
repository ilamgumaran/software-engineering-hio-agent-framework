# Centaur Evaluations -- Stanford Digital Economy Lab

## Source

| Field | Value |
|---|---|
| **Title** | Centaur Evaluations -- AI Centaur Benchmarks project |
| **Type** | Academic research program |
| **Institution** | Stanford Digital Economy Lab (within Stanford HAI) |
| **Primary URL** | https://digitaleconomy.stanford.edu/project/ai-centaur-benchmarks/ |
| **Stanford HAI** | https://hai.stanford.edu/ |
| **Date extracted** | May 2026 |

---

## Core thesis

Most AI benchmarks ask: *can the model do the task as well as a human?* Centaur Evaluations propose a different unit of measurement: **the human + AI team**. The relevant question becomes *does the model help a human do the task better, faster, or more safely?*

A Centaur Evaluation has three required components:

1. **Human** -- who participates, what training is allowed, prior expertise
2. **Interface** -- what the human and the model can see and do; how collaboration and submissions work
3. **Scoring** -- how outcomes are scored, including token and time budgets

This reframes evaluation away from *AI replaces human* and toward *AI augments human*, which closely parallels the philosophical posture of HIO.

---

## Why this matters for HIO

HIO's central premise -- that humans (organic intelligence) and AI (inorganic intelligence) are partners producing outcomes neither could produce alone -- has, until Centaur Evaluations, lacked a published academic measurement framework. Centaur Evaluations supply one.

Key alignments:

| HIO concept | Centaur Evaluation parallel |
|---|---|
| Cognitive ecosystem | Human + AI team as the unit of measurement |
| Emergence | Performance lift attributable to collaboration vs. either alone |
| Harmonization, not division | Three required components (Human, Interface, Scoring) treated as one system |
| Fulfillment as the engine | Token *and* time budgets reflect human attention as a real resource |

Differences:

| HIO concept | Where Centaur is silent |
|---|---|
| Purpose as a Living Force | Centaur scopes to a task; HIO scopes to ecosystem purpose over time |
| Human Fulfillment metrics | Centaur measures task outcomes; HIO measures fulfillment alongside |
| Quarterly cadence and transformation phases | Centaur is a benchmark, not a transformation framework |

In short: Centaur Evaluations are an *evaluation lens* compatible with HIO. HIO is a broader *operational framework* that can adopt Centaur lenses for its measurement layer.

---

## HIO Integration Notes

- `multi-repo-orchestration/hio-collaboration/matrix.md` is essentially a routing version of a Centaur design: it specifies who participates (OI, II, Interactive), what they may see and do, and what counts as success per row
- The `metrics/harmonization.md` category should add a Centaur-style measurement: human+AI team performance vs. either alone, on a representative task set
- The proposed `hio-evals` repo (in `multi-repo-orchestration/new-repos-proposed.md`) should adopt Centaur Evaluation structure rather than reinventing it

## Concrete improvements informed by this reference

1. Add a Centaur-style measurement instrument to `metrics/harmonization.md` -- pick three representative tasks per cognitive unit and measure team-level performance
2. In `hio-collaboration/matrix.md`, link Centaur Evaluations as the academic foundation
3. In `new-repos-proposed.md`, refine `hio-evals` to use Centaur structure (Human / Interface / Scoring) for every eval set

---

## Where this reference shows up

| Place | How it's used |
|---|---|
| `multi-repo-orchestration/hio-collaboration/matrix.md` | Citation under "Why this matters" |
| `metrics/harmonization.md` | Future Centaur-style team-performance measure |
| `multi-repo-orchestration/new-repos-proposed.md` | `hio-evals` proposal updated to adopt Centaur structure |
