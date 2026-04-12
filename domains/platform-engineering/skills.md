# Platform Engineering Skills

Skills organized by cognitive function. Each skill set represents how a cognitive function manifests in the platform engineering domain.

---

## Builder Skills

The **Builder** function in platform engineering focuses on constructing reliable, reusable infrastructure components.

| Skill | Technologies | Proficiency Indicators |
|-------|-------------|----------------------|
| Infrastructure as Code | Terraform, Pulumi, CDK, CloudFormation | Modules are composable, tested, and versioned |
| CI/CD Pipeline Construction | GitHub Actions, GitLab CI, Jenkins, ArgoCD | Pipelines are self-service and parameterized |
| API Development | REST, gRPC, GraphQL | APIs are versioned, documented, and backward-compatible |
| Container Orchestration | Kubernetes, Helm, Kustomize | Workloads are declarative with health checks and resource limits |
| Observability Instrumentation | OpenTelemetry, Prometheus, Grafana | Services emit structured logs, metrics, and traces by default |

---

## Solution Architect Skills

The **Solution Architect** function selects patterns that balance platform needs against organizational constraints.

| Pattern | When to Use | Tradeoffs |
|---------|------------|-----------|
| Service Mesh | Multi-service communication requiring mTLS, retries, observability | Complexity vs observability and security |
| Event-Driven | Asynchronous processing, decoupled services, audit trails | Eventual consistency vs decoupling and scalability |
| GitOps | Infrastructure management, declarative desired-state | Auditability and reproducibility vs initial complexity |
| Cell-Based Architecture | Blast radius control, regional isolation | Isolation and fault containment vs resource efficiency |
| Platform API Gateway | Unified entry point for platform services | Centralized governance vs single point of failure |

**Architecture Decision Records (ADRs):** Solution Architects produce ADRs for every significant platform decision. ADRs capture context, decision, consequences, and alternatives considered.

---

## Quality Guardian Skills

The **Quality Guardian** function ensures platform reliability, security, and compliance.

- **Platform Reliability Engineering** -- Define and track SLIs and SLOs for every platform service. Manage error budgets. Escalate when burn rate exceeds thresholds.
- **Chaos Engineering** -- Design and execute failure injection experiments. Validate that platform services degrade gracefully under partial failure conditions.
- **Security Hardening** -- Enforce supply chain security (SBOM generation, dependency scanning). Manage secrets rotation. Implement network policies and pod security standards.
- **Compliance Automation** -- Codify compliance requirements as policy-as-code (OPA, Kyverno). Automate audit evidence collection. Maintain compliance dashboards.

---

## Problem Framer Skills

The **Problem Framer** function identifies what to build and why.

- **Developer Experience Research** -- Conduct developer surveys, interviews, and time-motion studies. Identify friction points in the developer workflow. Quantify time spent on toil.
- **Platform Adoption Analysis** -- Track which platform capabilities are adopted and which are bypassed. Analyze why teams build workarounds instead of using golden paths.
- **Self-Service Gap Analysis** -- Map the end-to-end developer workflow and identify steps that still require manual intervention or ticket-based requests.
- **Stakeholder Need Synthesis** -- Consolidate requirements from multiple downstream teams into platform capabilities that serve the broadest set of needs.

---

## Pattern Integrator Skills

The **Pattern Integrator** function synthesizes trends and patterns across the platform ecosystem.

- **Cross-Platform Pattern Recognition** -- Identify recurring architectural patterns across downstream teams. Surface opportunities for platform-level abstractions.
- **Industry Trend Synthesis** -- Monitor CNCF landscape, platform engineering community, and vendor developments. Distinguish signal from noise.
- **Technology Radar Management** -- Maintain an organizational technology radar. Classify technologies as Adopt, Trial, Assess, or Hold. Update quarterly.
- **Metrics Correlation** -- Connect platform metrics across categories. Identify leading indicators (e.g., "when deployment frequency drops, incident rate rises 2 weeks later").

---

## Resonance Sensor Skills

The **Resonance Sensor** function detects the human dynamics of platform work.

- **Developer Satisfaction Monitoring** -- Track downstream developer NPS and satisfaction scores. Surface qualitative feedback themes.
- **Team Energy Assessment** -- Observe team energy levels during ceremonies. Flag burnout signals early.
- **Adoption Resistance Detection** -- Identify when teams resist platform adoption not from technical issues but from trust, autonomy, or cultural concerns.

---

## Growth Catalyst Skills

The **Growth Catalyst** function accelerates learning and capability development.

- **Onboarding Path Design** -- Create progressive onboarding experiences that move teams from basic platform usage to advanced self-service.
- **Knowledge Sharing Facilitation** -- Design internal tech talks, platform office hours, and community-of-practice structures.
- **Experiment Design** -- Help teams design safe-to-fail experiments for new platform capabilities or workflow changes.

---

## Fresh-Eyes Observer Skills

The **Fresh-Eyes Observer** function challenges assumptions and introduces outside perspectives.

- **Technology Evaluation** -- Evaluate emerging tools and platforms without bias toward the current stack.
- **Process Audit** -- Question existing platform processes. Identify ceremony theater and unnecessary gates.
- **Cross-Industry Inspiration** -- Bring patterns from other industries (e.g., manufacturing lean principles, aviation safety practices) into platform engineering.

---

*Reference: [cognitive-functions/](../../cognitive-functions/) | [overview.md](overview.md)*
