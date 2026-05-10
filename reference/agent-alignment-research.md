# Agent Alignment Research

## Sources

| Source | Type | Primary URL |
|---|---|---|
| Anthropic, Constitutional AI | Vendor research | https://www.anthropic.com/research/collective-constitutional-ai-aligning-a-language-model-with-public-input |
| Anthropic, Claude Constitution (Jan 2026) | Vendor research | https://constitutional.ai/ and https://bisi.org.uk/reports/claudes-new-constitution-ai-alignment-ethics-and-the-future-of-model-governance |
| OpenAI, Deliberative Alignment | Vendor research | https://openai.com/index/deliberative-alignment/ |
| LessWrong synthesis | Community comparison | https://www.lesswrong.com/posts/ezfHZtu85yXi2d9Qa/constitutional-ai-vs-rlhf-vs-deliberative-alignment |
| Stanford Deliberative Democracy Lab | Academic | https://deliberation.stanford.edu/ai-agent-good-alignment-safety-impact |

*Date extracted: May 2026.*

---

## What each approach does

### Constitutional AI (Anthropic)

A model is trained against a written **constitution** -- a structured set of principles (helpfulness, honesty, harmlessness) -- and learns to critique and revise its own responses against those principles. Anthropic's January 2026 constitution comprises 200+ principles and shifts from rule-based to reason-based alignment: the constitution explains the *logic* behind ethical principles rather than listing prescribed behaviors. Constitutional AI generalizes farther than rule-listing because the model can reason about novel situations.

### Deliberative Alignment (OpenAI)

The model is taught the *text* of its safety specifications and trained to **deliberate** over those specifications at inference time. At runtime, the model uses chain-of-thought to identify the relevant text from its safety policies and draft safer responses. Used to align OpenAI's o-series models.

### Debate-based safety (research)

Two models argue opposing viewpoints on safety-critical decisions; a smaller judge model (or human) evaluates. Reported 95% agreement with human expert panels on complex scenarios in some Anthropic experiments (per the 2026 syntheses cited above).

### Multi-agent alignment (open problem)

Aligning individual agents does not guarantee system-level safety. Coordination protocols and shared constitutions are necessary as autonomous systems interact (per the 2026 alignment surveys).

---

## Why this matters for HIO

HIO's **Decision Spectrum** (irreversible -> human, semi-reversible -> Interactive, reversible -> agent) plays the same role at the *task routing* layer that constitutional AI and deliberative alignment play at the *model behavior* layer. The two are complementary:

- An aligned model (constitutional or deliberative) is more likely to behave correctly on tasks it is asked to do
- A correct routing matrix decides whether the model should be asked to do the task at all

For multi-agent settings, the open-problem framing applies directly: HIO's per-repo `AGENTS.md`, the master matrix, the security-and-safety policy, and the SME workflow together act as a **shared constitution** for the family of agents -- partial alignment for system-level safety.

---

## Concrete improvements informed by this reference

1. Frame `multi-repo-orchestration/governance/security-and-safety.md` and `org/policies.md` together as a **shared constitution** for the agent family
2. Add a deliberation step to `skills/hio-classifier.md`: the agent must explicitly cite the matrix row(s) and stop conditions, not just emit a classification
3. Note in `governance/security-and-safety.md` that prompt-injection defense relies on the model *also* being aligned at the constitutional level -- our policy is necessary but not sufficient
4. Add a future research line: shared-constitution evaluation across the agent family (mapped to `hio-evals` proposal)

---

## HIO Integration Notes

HIO insists humans and AI are partners, not substitutes. Constitutional AI and Deliberative Alignment supply the model-level half of that partnership; HIO's routing and governance supply the system-level half. Neither replaces the other.

Multi-agent alignment is an open problem in the literature. The HIO multi-repo orchestration framework is one example of a *shared-constitution* approach: every agent in the family reads the same `AGENTS.md` family of files, applies the same matrix, and is bound by the same security policy. Whether this approach generalizes is itself a research question.

## Where this reference shows up

| Place | How it's used |
|---|---|
| `multi-repo-orchestration/governance/security-and-safety.md` | Framing as a shared constitution |
| `multi-repo-orchestration/skills/hio-classifier.md` | Deliberation step (cite matrix row + stop conditions) |
| `org/policies.md` | Note that policy alone does not substitute for model-level alignment |
