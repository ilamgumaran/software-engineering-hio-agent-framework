# Foundational Tools

## 8-Layer Infrastructure Toolchain

The HIO framework operates on an 8-layer infrastructure stack. Each layer serves a specific purpose in the framework, and specific AI agents depend on each layer for their capabilities.

---

### Layer 1: Source Control

**Purpose:** Version history, collaboration, and the foundation for DORA metrics.

| Tool | Role | Primary Agent Users |
|------|------|-------------------|
| **Git** | Distributed version control | All agents |
| **GitHub / GitLab** | Hosting, PRs, code review, Actions/CI | Code Co-Creator, Quality Analyst |

**HIO-specific configuration:** Branch protection rules aligned with the Decision Spectrum -- reversible changes can merge with agent review; irreversible changes require human approval.

---

### Layer 2: Issue Tracking

**Purpose:** Work decomposition, sprint planning, and platform outcome tracking.

| Tool | Role | Primary Agent Users |
|------|------|-------------------|
| **Jira** | Issue tracking, sprint management, roadmapping | Metrics Monitor, Analysis Partner |
| **Linear** | Lightweight alternative with better API | Metrics Monitor, Analysis Partner |

**HIO-specific configuration:** Issue types mapped to cognitive unit outcomes rather than component teams. Labels for cognitive functions involved in each issue.

---

### Layer 3: Documentation

**Purpose:** Decision records, knowledge capture, and institutional memory.

| Tool | Role | Primary Agent Users |
|------|------|-------------------|
| **Confluence** | Long-form documentation, ADRs, runbooks | Documentation & Knowledge |
| **Notion** | Lightweight alternative with better real-time collaboration | Documentation & Knowledge |

**HIO-specific configuration:** Dedicated spaces per cognitive unit. Emergence log template. ADR template aligned with HIO decision framework.

---

### Layer 4: CI/CD Pipeline

**Purpose:** Automated build, test, deploy -- the engine behind deployment frequency and lead time metrics.

| Tool | Role | Primary Agent Users |
|------|------|-------------------|
| **GitHub Actions / GitLab CI** | Pipeline orchestration | Code Co-Creator, Quality Analyst |
| **ArgoCD / Flux** | GitOps deployment | Code Co-Creator |
| **Terraform / Pulumi** | Infrastructure as code | Code Co-Creator, Architecture Explorer |

**HIO-specific configuration:** Quality gates enforced by the Quality Analyst agent. Deployment events emitted to the Metrics Monitor for DORA tracking.

---

### Layer 5: Observability

**Purpose:** Runtime visibility, incident detection, and SLI/SLO tracking.

| Tool | Role | Primary Agent Users |
|------|------|-------------------|
| **Datadog / Grafana** | Metrics, traces, logs, dashboards | Quality Analyst, Metrics Monitor |
| **PagerDuty / OpsGenie** | Incident management and alerting | Quality Analyst |

**HIO-specific configuration:** Dashboards per cognitive unit. Alert routing to the unit that owns the system. SLO definitions co-authored by Quality Analyst agent and human Quality Guardian.

---

### Layer 6: Data Infrastructure

**Purpose:** Analytics, metric storage, and trend analysis.

| Tool | Role | Primary Agent Users |
|------|------|-------------------|
| **BigQuery / Snowflake** | Data warehouse for metric aggregation | Metrics Monitor, Analysis Partner |
| **dbt** | Data transformation and modeling | Metrics Monitor |

**HIO-specific configuration:** Metric tables for all 9 HIO categories. Transformation jobs that compute DORA metrics from Git and CI/CD events.

---

### Layer 7: AI Tools

**Purpose:** The cognitive amplification layer that powers the 6 AI agents.

| Tool | Role | Primary Agent Users |
|------|------|-------------------|
| **Claude Code** | Orchestration layer, agent execution, MCP integrations | All agents (primary runtime) |
| **GitHub Copilot** | IDE-level code generation and suggestion | Code Co-Creator |
| **Gemini Enterprise** | Large-context analysis, document reasoning | Analysis Partner, Architecture Explorer |
| **Glean** | Enterprise knowledge search and retrieval | Documentation & Knowledge, Analysis Partner |

**HIO-specific configuration:** Claude Code configured with MCP servers for each integration point. Agent-specific system prompts stored in `agents/`. Tool access policies defined in `org/policies.md`.

---

### Layer 8: HIO-Specific Systems

**Purpose:** Infrastructure unique to the HIO framework that does not exist in a traditional engineering org.

| System | Purpose | Primary Agent Users |
|--------|---------|-------------------|
| **Metrics Monitor Dashboard** | 9-category metric visualization, per-unit and org-wide views | Metrics Monitor |
| **Emergence Log** | Structured capture of emergence events with context and impact | Documentation & Knowledge |
| **Harmony Pulse** | Weekly snapshot of unit health across delivery, fulfillment, and harmonization | Metrics Monitor, Analysis Partner |
| **Comparison Board** | Side-by-side view of HIO units vs. legacy team metrics | Metrics Monitor |
| **Cognitive Profile Registry** | Team member cognitive function profiles and development goals | Documentation & Knowledge |

**Implementation approach:** These systems can be built as dashboards (Grafana/Looker), Confluence templates, and lightweight scripts during Phase 0. They do not require custom application development.

---

## Tool Provisioning by Phase

| Phase | Tools to Provision | Priority |
|-------|--------------------|----------|
| **Phase 0** | Claude Code, GitHub Copilot, Metrics Monitor Dashboard, Baseline surveys | Must-have |
| **Phase 1** | All 6 agents configured, Emergence Log, Harmony Pulse, Comparison Board | Must-have |
| **Phase 2** | Gemini Enterprise, Glean, Cross-unit dashboards | Should-have |
| **Phase 3** | Self-service agent configuration, Org-wide dashboard rollup | Should-have |

See `org/infrastructure.md` for organization-specific tool configuration and `org/policies.md` for agent access guardrails.
