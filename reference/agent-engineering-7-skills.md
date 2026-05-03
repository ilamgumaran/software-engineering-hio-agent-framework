# Agent Engineering: 7 Core Capabilities

## Source

| Field | Value |
|---|---|
| **Title** | Transitioning to an AI-Centric Engineering Organization — Mastering the 7 Core Skills to Build Production-Ready AI Agents |
| **Type** | Video / White Paper |
| **URL** | https://www.youtube.com/watch?v=mtiOK2QG9Q0 |
| **Date Extracted** | April 2026 |
| **Upstream** | https://github.com/ilamgumaran/thought-org-with-human-ai-hybrid/blob/main/reference/agent-engineering-7-skills.md |

---

## Core Thesis

The era of "prompt engineering" is ending. Building AI agents that function in the real world is an exercise in **engineering systems, not writing sentences**. Agents don't merely answer questions — they execute tasks, query databases, process transactions, and make complex decisions. Organizations must elevate from following AI "recipes" to mastering the architectural principles of system design.

---

## The 7 Capabilities

### 1. System Design

**What it is**: Architecting AI agents as complete systems — not standalone features. The system includes an LLM making decisions, tools executing actions, databases storing state, and potentially multiple sub-agents handling specialized tasks.

**Key requirements**:
- Architect how data flows through the entire system
- Plan for component failures
- Coordinate tasks among multiple specialist systems

**Existing skill bridge**: Teams experienced in designing backend systems with communicating services already possess this foundational language.

**Role relevance**: Backend Engineers, Architects, Staff/Principal Engineers, SREs

---

### 2. Tool and Contract Design

**What it is**: Agents interact with business systems through tools, and every tool must be bound by a strict technical contract. If a contract is vague, the agent will fill gaps using its "imagination" — dangerous for real-world operations like financial transactions.

**Key requirements**:
- Implement strict schemas
- Use exact pattern matching
- Provide comprehensive examples
- Zero ambiguity in tool definitions

**Existing skill bridge**: API design, schema definition, contract-first development, OpenAPI specs.

**Role relevance**: Backend Engineers, API Designers, Full-Stack Engineers, QA Engineers (contract validation)

---

### 3. Retrieval Engineering

**What it is**: Most production AI agents use Retrieval-Augmented Generation (RAG) rather than relying on model memorization. The operational ceiling of an agent is strictly bound by the quality of data it retrieves.

**Key requirements**:
- Master document chunking strategies
- Use proper embedding models to represent meaning
- Implement reranking passes to push highest-quality signal to top of context window
- Understand that irrelevant retrieval → confidently irrelevant output

**Existing skill bridge**: Search engineering, data pipeline design, information retrieval, database query optimization.

**Role relevance**: Data Engineers, Backend Engineers, Search Engineers, ML Engineers

---

### 4. Reliability Engineering

**What it is**: Agents rely heavily on external systems. Organizations must plan for API failures, network timeouts, and external service outages. An unconstrained agent can wait indefinitely or retry forever.

**Key requirements**:
- Retry logic with exponential backoff
- Strict operational timeouts
- Fallback paths and circuit breakers
- Prevention of cascading failures

**Existing skill bridge**: Backend reliability, SRE practices, distributed systems, resilience patterns.

**Role relevance**: SREs, DevOps Engineers, Backend Engineers, Platform Engineers

---

### 5. Security and Safety

**What it is**: AI agents introduce a new attack surface. Prompt injections — malicious instructions embedded in user inputs to override system directives — are a real threat. The threat model has changed but the security mindset remains the same.

**Key requirements**:
- Rigorous input validation
- Output filters for non-compliant responses
- Strict permission boundaries (agents cannot act beyond authorization)
- Defense against prompt injection

**Existing skill bridge**: Application security, input validation, OWASP practices, access control design.

**Role relevance**: Security Engineers, Backend Engineers, DevOps, QA Engineers

---

### 6. Evaluation and Observability

**What it is**: You cannot improve what you cannot measure. When an agent breaks in production, guesswork is not viable debugging. Organizations must mandate tracing across all AI deployments.

**Key requirements**:
- Full tracing: every tool interaction and decision logged as a complete timeline
- Automated evaluation pipelines
- Metrics: success rates, latency, cost-per-task
- Move from subjective "vibes" to scalable metrics

**Existing skill bridge**: Observability, monitoring, logging, APM, SRE practices, test automation.

**Role relevance**: SREs, QA Engineers, DevOps, Backend Engineers, Data Engineers

---

### 7. Product Thinking

**What it is**: Technical backend skills run the system, but product thinking ensures human adoption. LLM-based systems are inherently unpredictable and require specialized UX design.

**Key requirements**:
- Graceful error handling in UX
- Convey confidence vs. uncertainty clearly
- Appropriate human escalation
- Set expectations without undermining confidence
- Design for trust

**Existing skill bridge**: Product management, UX design, user research, customer empathy.

**Role relevance**: Product Managers, UX Designers, Frontend Engineers, UX Researchers

---

## Quick-Start: Two Highest-Leverage Actions

Two actions any team can take this week, no pause to production, no new hires:

1. **Refine Tool Schemas** — Audit existing tool schemas. If a human engineer can't immediately understand what a tool does and requires, tighten the contract with strict types and examples. This is the highest-leverage fix.

2. **Implement Tracing** — Find one recurring agent failure. Instead of adjusting the prompt, trace backward: was the correct tool selected? Was the proper document retrieved? 9/10 times the root cause is system-based, not word-based.

---

## Role Mapping Matrix

| Role | System Design | Tool/Contract | Retrieval | Reliability | Security | Eval/Observability | Product Thinking |
|---|---|---|---|---|---|---|---|
| **Backend Engineer** | Primary | Primary | Strong | Strong | Strong | Strong | Supporting |
| **Frontend Engineer** | Supporting | Supporting | — | — | Supporting | Supporting | Strong |
| **Full-Stack Engineer** | Strong | Strong | Supporting | Supporting | Supporting | Supporting | Strong |
| **Architect / Staff Eng** | Primary | Primary | Strong | Strong | Strong | Strong | Strong |
| **SRE / DevOps** | Strong | Supporting | — | Primary | Strong | Primary | — |
| **Platform Engineer** | Primary | Strong | Supporting | Primary | Strong | Strong | Supporting |
| **Data Engineer** | Supporting | Supporting | Primary | Supporting | Supporting | Strong | — |
| **ML Engineer** | Strong | Strong | Primary | Supporting | Supporting | Strong | Supporting |
| **QA Engineer** | Supporting | Strong | — | Supporting | Strong | Primary | Supporting |
| **Security Engineer** | Supporting | Supporting | — | Supporting | Primary | Strong | — |
| **Product Manager** | — | Supporting | — | — | — | Supporting | Primary |
| **UX Designer** | — | — | — | — | — | — | Primary |
| **UX Researcher** | — | — | — | — | — | Supporting | Primary |
| **Engineering Manager** | Strong | Supporting | — | Supporting | Supporting | Strong | Strong |

**Legend**: Primary = core responsibility, Strong = significant contribution, Supporting = contributes meaningfully, — = not directly involved.

---

## Readiness Assessment

Use this to gauge where a team currently stands on each capability. The level becomes input to a person's bandwidth-expansion plan, not a performance score.

| Capability | L1 Unaware | L2 Aware | L3 Practicing | L4 Proficient | L5 Leading |
|---|---|---|---|---|---|
| System Design | No agent architecture thinking | Understands agents are systems | Has built multi-component agent systems | Designs for failure, scale, evolution | Innovates architectural patterns |
| Tool/Contract | Vague tool descriptions | Knows contracts matter | Uses typed schemas | Zero-ambiguity contracts with examples | Designs contract frameworks others adopt |
| Retrieval | No RAG experience | Understands RAG concept | Has implemented basic RAG | Optimized chunking, embedding, reranking | Pushes retrieval state-of-art |
| Reliability | No agent reliability thinking | Knows agents can fail | Implements retries, timeouts | Full circuit breaker, fallback patterns | Designs self-healing agent systems |
| Security | No agent security awareness | Knows prompt injection exists | Basic input validation | Comprehensive threat model + defenses | Advances agent security practices |
| Eval/Observability | No tracing | Logs exist but unstructured | Full tracing implemented | Automated eval pipelines with metrics | Evaluation frameworks others adopt |
| Product Thinking | No agent UX consideration | Knows agents need UX | Handles errors gracefully | Trust-calibrated UX with escalation | Defines agent UX patterns |

---

## HIO Integration Notes

### Connection to the 10 Cognitive Functions

The 7 capabilities are **technical disciplines**. The 10 cognitive functions in [`cognitive-functions/`](../cognitive-functions/README.md) are **modes of engagement**. Both are required; neither replaces the other.

| 7-Capability Lens | 10-Function Lens |
|---|---|
| What you must *know* to build production AI agents | How you *engage* with any work, including non-AI |
| Technical, learnable, level-up-able (L1-L5) | Behavioral, composable, switchable in real time |
| Maps cleanly to roles (architect, SRE, QA) | Cuts across roles (a backend engineer holds Builder + Solution Architect + Pattern Integrator) |

A cognitive unit building AI agents needs all 7 capabilities covered across its members and all 10 cognitive functions represented. The two checks are independent — capability gaps and function gaps are different problems with different fixes.

### Connection to the 6 Agent Types

Each of the 6 [agent types](../agents/README.md) leans on specific capabilities when humans deploy it:

| Agent Type | Capabilities most exercised |
|---|---|
| Analysis Partner | Retrieval Engineering, Eval/Observability |
| Code Co-Creator | Tool/Contract Design, Reliability, Security |
| Architecture Explorer | System Design, Reliability |
| Quality Analyst | Eval/Observability, Security |
| Metrics Monitor | Eval/Observability |
| Documentation & Knowledge | Retrieval Engineering, Product Thinking |

### Connection to the Decision Spectrum

Per [`CLAUDE.md`](../CLAUDE.md), reversibility governs who decides:

| Capability domain | Who decides |
|---|---|
| Security boundaries, escalation policy | Pure Human (irreversible blast radius) |
| System Design tradeoffs, Tool/Contract Design | Hybrid (humans set direction, AI proposes options) |
| Retrieval optimization, eval thresholds | Pure AI (reversible, measurable) |

### Where this reference shows up

| Place | How it's used |
|---|---|
| [`domains/platform-engineering/skills.md`](../domains/platform-engineering/skills.md) | Skills inventory and learning paths |
| [`transformation/phase-1-first-unit.md`](../transformation/phase-1-first-unit.md) | Capability development goals for the first cognitive unit |
| [`workflows/deep-work-collaboration.md`](../workflows/deep-work-collaboration.md) | Deep-work blocks anchor on a specific capability per sprint |
| [`metrics/ai-utilization.md`](../metrics/ai-utilization.md) | Capability-level (L1-L5) is part of AI Utilization tracking |
| [`examples/`](../examples/) | Each example specifies which capabilities it exercises |
