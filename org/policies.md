# Policies

> Configure agent guardrails and operational boundaries for your organization.

---

## Data Policies

### What Agents Can Access

- [ ] Source code repositories
- [ ] CI/CD pipeline logs and metrics
- [ ] Issue tracker (Jira/Linear)
- [ ] Documentation (Confluence/Notion)
- [ ] Observability data (logs, metrics, traces)
- [ ] Production databases (read-only)

### What Agents Cannot Access

- [ ] Customer PII without explicit approval
- [ ] Financial systems
- [ ] HR/personnel records
- [ ] Security credentials and secrets
- [ ] [Your organization-specific restrictions]

---

## Code Policies

### Review Requirements

- **AI-generated code:** [Requires human review before merge / Auto-merge with tests passing / ...]
- **Architecture changes:** [Requires Architecture Explorer analysis + human approval]
- **Security-sensitive code:** [Requires Quality Analyst scan + human security review]

### Testing Standards

- **Minimum coverage:** [e.g., 80% for new code]
- **Required test types:** [Unit, Integration, E2E for critical paths]
- **AI-generated tests:** [Accepted as-is / Requires human review]

---

## Workflow Policies

### Decision Spectrum

| Decision Type | Agent Authority | Human Role |
|---------------|----------------|------------|
| Reversible (feature flag, config change) | Agent decides, human informed | Review async |
| Semi-reversible (code merge, dependency update) | Agent recommends, human approves | Approve before action |
| Irreversible (production deploy, data migration) | Agent analyzes, human decides | Must explicitly approve |

### Escalation Rules

- **Agent confidence below [70%]:** Escalate to human
- **Cross-unit impact detected:** Notify affected unit leads
- **Security vulnerability found:** Immediate escalation to security team
- **Fulfillment score below 6:** Escalate to HIO coach

---

## Quality Gates

| Gate | Required For | Enforcement |
|------|-------------|-------------|
| Unit tests pass | All merges | Automated (CI) |
| Integration tests pass | Release candidates | Automated (CI) |
| Security scan clean | All merges | Automated (Quality Analyst) |
| Code review approved | All merges | Human + AI |
| Performance regression check | Performance-critical paths | Quality Analyst |

---

## HIO-Specific Policies

### Fulfillment Data Privacy

- Individual fulfillment scores are **private** -- only aggregates shared beyond the unit
- Fulfillment data never used in performance reviews
- Individuals own their cognitive profile data

### Emergence Logging Requirements

- All units log emergence events weekly
- Emergence events are shared in sprint outcome reviews
- No pressure to "produce" emergence -- it is observed, not manufactured

### Identity Grip Observation Guidelines

- Identity grip observations are **descriptive, not judgmental**
- Observations stay within the retrospective context
- Never used to evaluate individuals

### Cognitive Function Boundaries

- No one is required to operate outside their primary functions
- Bandwidth expansion is **invitational** -- growth goals are self-set
- Function rotation happens quarterly, by choice

---

### Organization Extension Point

> **YOUR_ORG:** Configure all checkboxes and [bracketed] values for your security and compliance requirements.
