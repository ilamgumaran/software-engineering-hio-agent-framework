# OWASP Top 10 for Agentic Applications 2026

## Source

| Field | Value |
|---|---|
| **Title** | OWASP Top 10 for Agentic Applications 2026 |
| **Type** | Open security standard |
| **Publisher** | OWASP Foundation -- GenAI Security Project |
| **Primary URL** | https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/ |
| **Release announcement** | https://genai.owasp.org/2025/12/09/owasp-genai-security-project-releases-top-10-risks-and-mitigations-for-agentic-ai-security/ |
| **Companion** | https://owasp.org/www-project-agentic-skills-top-10/ |
| **Date extracted** | May 2026 |

---

## Core thesis

The 2026 edition explicitly separates **agentic application security** from earlier LLM-application security. Agentic systems combine reasoning, memory, tools, and multi-step execution -- introducing new classes of vulnerabilities that flow from goal misalignment, tool misuse, delegated trust, inter-agent communication, persistent memory, and emergent autonomous behavior.

A minor vulnerability (e.g., simple prompt injection) can cascade in agentic systems into system-wide compromise, data exfiltration, or financial loss because the agent chains actions autonomously.

Two core defensive principles:

- **Least-Privilege** (classic) -- minimum credentials
- **Least-Agency** (new) -- the agent should be granted the minimum *autonomy* required to complete its defined task; expand only as evidence accumulates

Prompt Injection is recognized in two forms:

- **Direct Goal Manipulation** -- explicit override of agent objectives in user input
- **Indirect Instruction Injection** -- hidden instructions in documents, RAG content, or tool outputs that alter agent behavior

"Agent Goal Hijack is the new SQL Injection for the autonomous world" -- the framing summary published in the December 2025 release announcement.

---

## The 10 risk categories (summary)

The full document is the source of truth; these categories are the framing the framework adopts:

1. **Goal Manipulation** -- direct or indirect override of agent objectives
2. **Tool Misuse** -- agent invoking tools outside intended scope
3. **Memory Poisoning** -- adversarial content persisted into long-term agent memory
4. **Delegated Trust Abuse** -- one agent acting on behalf of another without sufficient verification
5. **Inter-Agent Injection** -- prompt injection delivered through agent-to-agent communication
6. **Emergent Misalignment** -- autonomous behavior diverging from intent over time
7. **Resource Exhaustion** -- agents looping or fanning out without bounds
8. **Supply Chain (Tool / Agent)** -- malicious or compromised tool servers or agent components
9. **Data Leakage via Reasoning** -- sensitive information emerging through chain-of-thought traces or tool outputs
10. **Identity & Authorization Drift** -- agent operating with permissions exceeding the user's actual authorization

Numbering above is a simplification for cross-reference; consult the OWASP source for the canonical ordering and full descriptions.

---

## Mapping to this framework's security rubric (B-axis)

| OWASP category | Maps to scoring dimension | Maps to governance section |
|---|---|---|
| Goal Manipulation | B3 Prompt injection awareness | `security-and-safety.md` Prompt injection defense |
| Tool Misuse | B5 Change reversibility | `security-and-safety.md` Permission scoping |
| Memory Poisoning | B3 + sensitive surface inventory (B2) | `security-and-safety.md` Audit and observability |
| Delegated Trust Abuse | B5 + B1 | A2A signed-agent-card requirement (when adopted) |
| Inter-Agent Injection | B3 | A2A signed-agent-card requirement (when adopted) |
| Emergent Misalignment | B5 + governance Decision Spectrum | `security-and-safety.md` Decision Spectrum |
| Resource Exhaustion | B5 | Per-task budget limits in policies |
| Supply Chain | B4 (secrets) + B2 (sensitive surfaces) | New: `governance/supply-chain.md` (proposed) |
| Data Leakage via Reasoning | B2 + B4 | `security-and-safety.md` Audit and observability |
| Identity & Authorization Drift | B5 + B1 | `security-and-safety.md` Permission scoping |

---

## Concrete improvements informed by this reference

1. Add an explicit OWASP-mapping table to `governance/security-and-safety.md`
2. Adopt **Least-Agency** as a named principle alongside Least-Privilege
3. Add a row to the master HIO routing matrix for Agent-to-Agent communications (forces Interactive routing pending A2A signed-agent-card adoption)
4. Update the security rubric (B-axis) level definitions to reference OWASP categories so re-scoring is consistent with industry standard
5. Add a `Supply Chain` clause to `governance/security-and-safety.md` -- agents must not introduce new MCP servers, tool servers, or agent dependencies without OI review

---

## HIO Integration Notes

The HIO Decision Spectrum (irreversible -> human; semi-reversible -> Interactive; reversible -> agent) is well-aligned with OWASP's Least-Agency principle. The framework already routes high-blast-radius decisions to OI; OWASP supplies the vocabulary and threat taxonomy that lets us name the risks more precisely.

## Where this reference shows up

| Place | How it's used |
|---|---|
| `multi-repo-orchestration/governance/security-and-safety.md` | OWASP mapping table; Least-Agency principle |
| `multi-repo-orchestration/scoring/scoring-rubric.md` | B-axis level definitions reference OWASP categories |
| `multi-repo-orchestration/hio-collaboration/matrix.md` | Agent-to-agent communication row added |
| `org/policies.md` | Supply-chain policy clause |
