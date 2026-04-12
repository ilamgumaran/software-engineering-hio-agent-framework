# Infrastructure

> Replace all [placeholder] values with your organization's specific tool selections and configurations.

---

## Source Control

- **Provider:** [GitHub / GitLab / Bitbucket]
- **Repository structure:** [Monorepo / Polyrepo / Hybrid]
- **Branch strategy:** [Trunk-based / GitFlow / GitHub Flow]
- **Code review policy:** [Required approvals, agent-assisted review enabled?]

---

## Languages and Frameworks

| Language / Framework | Usage | Cognitive Units Using |
|---------------------|-------|----------------------|
| [e.g., Go] | [Primary backend language] | [Scale & Reliability, Intelligence Layer] |
| [e.g., TypeScript] | [Frontend and tooling] | [Developer Experience, Experiment Velocity] |
| [e.g., Python] | [Data pipelines, ML] | [Intelligence Layer, Frontier] |
| [e.g., Terraform] | [Infrastructure as code] | [Scale & Reliability] |

---

## CI/CD

- **Pipeline tool:** [GitHub Actions / GitLab CI / Jenkins / CircleCI]
- **Deployment tool:** [ArgoCD / Flux / Spinnaker / direct deploy]
- **Artifact registry:** [ECR / GCR / Artifactory / GitHub Packages]
- **Environment strategy:** [dev / staging / prod / preview environments]
- **Deployment frequency target:** [Current frequency -> Phase 3 target]

---

## Observability

- **Metrics:** [Datadog / Grafana / Prometheus / CloudWatch]
- **Logging:** [Datadog / ELK / Splunk / CloudWatch Logs]
- **Tracing:** [Datadog APM / Jaeger / Honeycomb / X-Ray]
- **Alerting:** [PagerDuty / OpsGenie / Datadog Alerts]
- **SLO framework:** [Defined / In progress / Not started]

---

## Data Infrastructure

- **Data warehouse:** [BigQuery / Snowflake / Redshift / Databricks]
- **Data transformation:** [dbt / Spark / Airflow / custom]
- **Metric storage:** [Where HIO metrics will be aggregated]
- **Dashboard tool:** [Grafana / Looker / Tableau / Mode]

---

## Communication

- **Primary chat:** [Slack / Microsoft Teams]
- **Documentation:** [Confluence / Notion / Google Docs]
- **Video:** [Zoom / Google Meet / Teams]
- **Async updates:** [Slack channels / email / Loom]

---

## AI Agent Configuration

### Tool Access

| AI Tool | Status | License Count | Security Review |
|---------|--------|--------------|-----------------|
| Claude Code | [Provisioned / Pending / Not started] | [Number of seats] | [Approved / In review / Not started] |
| GitHub Copilot | [Provisioned / Pending / Not started] | [Number of seats] | [Approved / In review / Not started] |
| Gemini Enterprise | [Provisioned / Pending / Not started] | [Number of seats] | [Approved / In review / Not started] |
| Glean | [Provisioned / Pending / Not started] | [Number of seats] | [Approved / In review / Not started] |

### MCP Server Configuration

| MCP Server | Target System | Status | Configuration Location |
|-----------|---------------|--------|----------------------|
| git-mcp | [GitHub / GitLab] | [Configured / Pending] | [Path to config] |
| jira-mcp | [Jira / Linear] | [Configured / Pending] | [Path to config] |
| confluence-mcp | [Confluence / Notion] | [Configured / Pending] | [Path to config] |
| slack-mcp | [Slack / Teams] | [Configured / Pending] | [Path to config] |
| datadog-mcp | [Datadog / Grafana] | [Configured / Pending] | [Path to config] |

### Agent-to-Tool Mapping

| Agent | Primary Tools | MCP Servers Required |
|-------|--------------|---------------------|
| Analysis Partner | Claude Code, Gemini Enterprise, Glean | git-mcp, jira-mcp, datadog-mcp |
| Code Co-Creator | Claude Code, GitHub Copilot | git-mcp |
| Architecture Explorer | Claude Code, Gemini Enterprise | git-mcp, confluence-mcp |
| Quality Analyst | Claude Code | git-mcp, datadog-mcp |
| Metrics Monitor | Claude Code | jira-mcp, datadog-mcp, slack-mcp |
| Documentation & Knowledge | Claude Code, Glean | confluence-mcp, slack-mcp |

---

## Environment Access

| Environment | Agent Access Level | Human Approval Required |
|-------------|-------------------|------------------------|
| Development | [Read-write / Read-only / None] | [No / Yes] |
| Staging | [Read-write / Read-only / None] | [No / Yes] |
| Production | [Read-only / None] | [Always] |
| Data warehouse | [Read-only / None] | [No / Yes] |

---

### Organization Extension Point

> Complete all sections above during Phase 0. Review MCP server configurations with your security team before enabling agent access. Update this document as tools are provisioned and configurations change.
>
> See `config/` for MCP server definition files and `org/policies.md` for agent access guardrails.
