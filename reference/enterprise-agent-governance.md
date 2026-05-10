# Enterprise Agent Governance (2026)

How major enterprise vendors are structuring governance for multi-agent AI systems. Read alongside [`owasp-top-10-agentic-applications.md`](owasp-top-10-agentic-applications.md), [`agent-protocols-mcp-a2a.md`](agent-protocols-mcp-a2a.md), and the framework's own [`governance/`](../multi-repo-orchestration/governance/) directory.

## Sources

| Source | Type | Primary URL |
|---|---|---|
| Salesforce -- Governing AI Agents with Agentforce 360 Platform | Vendor blog | https://www.salesforce.com/blog/data-governance-for-the-agentic-era/ |
| Salesforce -- Agentforce 360 Announcements | Vendor product page | https://www.salesforce.com/agentforce/what-is-new/ |
| Salesforce TDX 2026 reporter's notebook | Independent reporting | https://salesforcedevops.net/index.php/2026/04/15/tdx-2026-reporters-notebook-salesforce-goes-headless-and-widens-the-builder-gap/ |
| ISG -- Salesforce Tackles the Entire Agent Development Lifecycle | Industry analyst | https://research.isg-one.com/analyst-perspectives/salesforce-tackles-the-entire-agent-development-lifecycle |
| HyperFRAME Research -- IBM Watsonx Orchestrate and the Friction of Autonomous Agent Governance | Industry analyst | https://hyperframeresearch.com/2026/05/05/ibm-watsonx-orchestrate-and-the-friction-of-autonomous-agent-governance/ |
| IBM -- What Is Agent2Agent (A2A) Protocol? | Vendor explainer | https://www.ibm.com/think/topics/agent2agent-protocol |
| Kai Waehner -- Enterprise Agentic AI Landscape 2026 | Independent analysis | https://www.kai-waehner.de/blog/2026/04/06/enterprise-agentic-ai-landscape-2026-trust-flexibility-and-vendor-lock-in/ |

*Date extracted: May 2026.*

---

## Salesforce -- Agentforce 360 and Agent Fabric

### What it is

Salesforce's enterprise agent platform, rebranded from "Salesforce Platform" to "Agentforce 360" at TDX 2026. The headline governance addition in 2026 is **Agent Fabric** -- a governed control plane for multi-vendor AI landscapes that spans agents created across Salesforce, Amazon Bedrock, GoDaddy, and other platforms.

### Core governance capabilities

| Capability | What it does |
|---|---|
| **Agent Fabric** | Multi-vendor control plane: deterministic orchestration, centralized policy enforcement, consistency in permissions / compliance / behavior across heterogeneous agent platforms |
| **MCP Bridge** | Surfaces existing enterprise APIs as MCP-callable tools at scale -- agents in any compliant runtime can call them through the bridge |
| **Agent Script** | Pre-deployment control: declares which parts of agent behavior must follow explicit business logic vs. which may reason freely |
| **Testing Center** | Environment for running agents against representative scenarios before production |
| **Custom Scoring Evals** | Vendor-supplied evaluation framework for agent outputs |
| **Session Tracing** | Post-deployment observability -- diagnose why an agent did what it did in hours, not weeks |
| **A/B Testing** | Run multiple agent versions against real traffic; promote based on data |
| **Agentforce Command Center** | Operations dashboard for running agents |

Salesforce's stated governance philosophy from the announcement: "Governance is not just a guardrail to your AI strategy -- it is your AI strategy. Without it, you don't have a strategy, you have an experiment."

### Notable architectural choices

- **MCP-first interop:** the MCP Bridge means Salesforce's governance choices are interoperable with non-Salesforce agents that speak MCP
- **Multi-vendor by design:** Agent Fabric is explicitly *not* a vendor-lock-in play; it discovers and governs agents from competing vendors
- **Lifecycle coverage:** the Agent Governance Suite spans pre-launch (Agent Script, Testing Center, Custom Scoring Evals) and post-launch (Session Tracing, A/B Testing, Command Center) -- a fuller lifecycle than most 2025 offerings

---

## IBM -- watsonx Orchestrate

### What it is

IBM's enterprise agent orchestration platform. Positioned at IBM Think 2026 as a **neutral, cross-platform control plane** for managing multi-agent AI deployments, in deliberate contrast to vertically-integrated stacks (Salesforce Agentforce, Microsoft Agent Framework).

### Core governance capabilities

| Capability | What it does |
|---|---|
| **watsonx Orchestrate** | Control plane to manage AI agents from various sources, ensuring policies, traceability, and governance are consistent across agents created on different platforms |
| **watsonx.governance** | Companion governance platform; framework for auditing agent behavior; ensures autonomous actions remain within corporate policy guardrails |
| **Cross-platform connectors** | 150+ enterprise tool integrations (Salesforce, Workday, ServiceNow); agents created elsewhere can be orchestrated through watsonx |
| **A2A support** | First-class Agent2Agent protocol implementation per IBM's A2A explainer page |

### Notable architectural choices

- **Neutrality as differentiation:** IBM's strategic bet is that organizations will resist vendor lock-in for the agent control plane even if they use vendor-specific agents underneath
- **Governance-first messaging:** IBM Think 2026's coverage emphasized auditing and guardrails over raw capability
- **A2A-native:** IBM is one of the most visible enterprise A2A adopters; this signals that agent-to-agent interop across vendor boundaries is reaching enterprise readiness

### Tension worth noting

The HyperFRAME analyst piece flags real friction: a *centralized* control plane that touches agents across vendors creates a single high-blast-radius governance surface. Misconfiguration, schema drift between vendor agents, and the trust model for inter-agent calls (without A2A signed Agent Cards) become organizational risks rather than technical bugs.

---

## The broader enterprise landscape

From Kai Waehner's 2026 landscape analysis:

- **Three enterprise vendor postures**:
  1. **Vertically-integrated stacks** (Salesforce Agentforce 360 with Agent Fabric, Microsoft Agent Framework / Semantic Kernel) -- deepest governance for agents within the vendor's ecosystem; harder to govern external agents
  2. **Neutral control planes** (IBM watsonx Orchestrate) -- easier multi-vendor; less visibility into vendor-specific agent internals
  3. **Open-protocol foundations** (Linux Foundation Agentic AI Foundation: AGENTS.md, MCP, A2A) -- lowest lock-in; least built-in governance, but governance can be layered on by anyone
- **Vendor lock-in is the dominant 2026 enterprise concern**, exceeding capability gaps
- **Trust** -- defined as the combination of provenance, auditability, and reversibility -- has become the explicit purchase criterion ahead of accuracy in many enterprise procurement processes
- **Enterprise agent failures in 2025** were dominated by goal misalignment and supply-chain compromise, mapping cleanly to OWASP Top 10 categories rather than novel failure modes

---

## How this informs the HIO multi-repo orchestration framework

### Direct alignments

| Framework element | Vendor analogue |
|---|---|
| `multi-repo-orchestration/repo-registry.md` | Salesforce Agent Fabric automated discovery; IBM watsonx cross-platform connectors |
| `governance/security-and-safety.md` (shared constitution) | Salesforce Agent Script (declared behavior bounds); IBM watsonx.governance (policy enforcement) |
| `governance/sme-update-workflow.md` (quarterly cadence, sign-offs) | Salesforce Agent Governance Suite (lifecycle stages) |
| `scoring/` (rubric + scorecards) | Salesforce Custom Scoring Evals; HAL Reliability Dashboard for production observability |
| `skills/` (cartographer, tracer, classifier, scorer) | Salesforce Testing Center scenarios; running agents pre-deployment |
| Future `hio-evals` proposal | Salesforce A/B Testing; Custom Scoring Evals as a vendor reference point |
| Proposed `agent-spec-registry` MCP server | Salesforce MCP Bridge -- pattern-equivalent for the open-protocol world |

### Genuine gaps the enterprise landscape exposes

1. **No Session Tracing equivalent** -- the framework has audit logging in policy but no operational tracing surface that lets an SME diagnose an agent run quickly. Needs a deferred proposal.
2. **No A/B Testing pattern** -- the framework treats `AGENTS.md` and skills as a single canonical version. Salesforce's A/B Testing pattern suggests a useful future where a repo can carry alternate versions to measure differential effects.
3. **No Command Center** -- there is nothing in the framework that *operates* the agents (only documents and rules). When the family includes runtime agents (proposed `hio-evals`), an operations surface will be needed.

These are deferred, not accepted as silent gaps. They belong on a future roadmap iteration.

### Strategic posture for the HIO family

The Kai Waehner three-posture taxonomy is useful as a self-locator. The HIO multi-repo orchestration framework is best understood as **layered on top of the open-protocol foundation** (AGENTS.md, MCP, A2A). It does not compete with vertically-integrated stacks or neutral control planes; it adds the human+AI collaboration layer that none of those vendor offerings explicitly model.

When an enterprise adopts HIO, they typically already have one of the vendor stacks. HIO does not displace it; it sits above it as the routing and governance layer that defines *who decides* (human, agent, or both) on top of *who acts* (the vendor's runtime).

---

## Concrete improvements informed by this reference (deferred -- proposed for a follow-up PR)

1. Add a `multi-repo-orchestration/governance/observability.md` policy describing minimum trace/audit surface a runtime agent in the family must support
2. Consider an `A/B Testing` deferred proposal: a way for the family to carry alternate versions of `AGENTS.md` or skills to measure differential effects
3. When the proposed `hio-evals` repo is built, evaluate Custom Scoring Evals (Salesforce) as one of the design references
4. When the proposed `agent-spec-registry` MCP server is built, evaluate MCP Bridge (Salesforce) as one of the design references
5. Document the HIO framework's strategic posture in `multi-repo-orchestration/PLAN.md` -- explicitly "layered on the open-protocol foundation"

---

## Where this reference shows up

| Place | How it's used |
|---|---|
| `multi-repo-orchestration/governance/sme-update-workflow.md` | Lifecycle parallels (pre/post launch governance) |
| `multi-repo-orchestration/new-repos-proposed.md` | `agent-spec-registry` and `hio-evals` proposals reference enterprise design points |
| Future `multi-repo-orchestration/governance/observability.md` | Inspired by Salesforce Session Tracing; not yet written |
| `multi-repo-orchestration/PLAN.md` | Strategic-posture self-location (open-protocol-layered) |
