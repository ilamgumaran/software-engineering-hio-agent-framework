# Capabilities

## Agent Capabilities

### Analysis Partner

| Agent | Capability | Description | Tools Used |
|-------|-----------|-------------|------------|
| Analysis Partner | **Problem decomposition** | Breaks ambiguous situations into structured problem statements | Claude Code, Gemini Enterprise |
| Analysis Partner | **Codebase pattern analysis** | Scans repositories for architectural patterns, anti-patterns, and drift | Claude Code, Glean |
| Analysis Partner | **Incident correlation** | Connects signals across logs, metrics, and alerts to surface root causes | Datadog/Grafana, Claude Code |
| Analysis Partner | **Stakeholder sentiment synthesis** | Aggregates feedback from retros, surveys, and Slack to detect organizational currents | Glean, Slack API |
| Analysis Partner | **Dependency mapping** | Traces service dependencies and identifies coupling risks | Claude Code, GitHub |
| Analysis Partner | **Impact forecasting** | Models the downstream effects of proposed changes before implementation | Claude Code, Gemini Enterprise |

### Code Co-Creator

| Agent | Capability | Description | Tools Used |
|-------|-----------|-------------|------------|
| Code Co-Creator | **Collaborative code authoring** | Pair-programs with humans, generating code that reflects shared intent | Claude Code, GitHub Copilot |
| Code Co-Creator | **Test generation** | Creates unit, integration, and property-based tests aligned to quality standards | Claude Code, GitHub Copilot |
| Code Co-Creator | **Refactoring assistance** | Proposes and executes refactoring with pattern awareness across the codebase | Claude Code, GitHub Copilot |
| Code Co-Creator | **Code review** | Reviews PRs for correctness, readability, security, and pattern consistency | Claude Code, GitHub |
| Code Co-Creator | **Migration support** | Assists large-scale code migrations with pattern-preserving transformations | Claude Code, Gemini Enterprise |
| Code Co-Creator | **Boilerplate reduction** | Generates scaffolding, configuration, and repetitive code from intent descriptions | Claude Code, GitHub Copilot |

### Architecture Explorer

| Agent | Capability | Description | Tools Used |
|-------|-----------|-------------|------------|
| Architecture Explorer | **Design option evaluation** | Generates and compares architectural alternatives with trade-off matrices | Claude Code, Gemini Enterprise |
| Architecture Explorer | **System boundary mapping** | Identifies service boundaries, API contracts, and integration seams | Claude Code, Glean |
| Architecture Explorer | **Scalability modeling** | Evaluates how designs behave under load, growth, and failure scenarios | Claude Code, Gemini Enterprise |
| Architecture Explorer | **ADR generation** | Drafts architecture decision records from discussion context | Claude Code, Confluence |
| Architecture Explorer | **Tech debt quantification** | Maps technical debt to business impact and prioritizes remediation paths | Claude Code, Jira |
| Architecture Explorer | **Migration path planning** | Designs incremental migration strategies that maintain delivery continuity | Claude Code, Gemini Enterprise |

### Quality Analyst

| Agent | Capability | Description | Tools Used |
|-------|-----------|-------------|------------|
| Quality Analyst | **Multi-dimensional quality assessment** | Evaluates code health across reliability, security, performance, and maintainability | Claude Code, SonarQube |
| Quality Analyst | **Regression risk analysis** | Identifies areas most likely to break given a proposed change | Claude Code, GitHub |
| Quality Analyst | **Observability gap detection** | Finds blind spots in monitoring, logging, and alerting coverage | Datadog/Grafana, Claude Code |
| Quality Analyst | **Security vulnerability scanning** | Detects security issues and suggests remediations with context | Claude Code, Snyk |
| Quality Analyst | **Fresh-eyes review** | Examines established patterns and assumptions others have stopped questioning | Claude Code, Gemini Enterprise |
| Quality Analyst | **Test coverage optimization** | Identifies the highest-value tests to add based on risk and change frequency | Claude Code, GitHub |

### Metrics Monitor

| Agent | Capability | Description | Tools Used |
|-------|-----------|-------------|------------|
| Metrics Monitor | **DORA metric tracking** | Continuously measures deployment frequency, lead time, CFR, and MTTR | GitHub Actions, Datadog |
| Metrics Monitor | **SPACE/DX survey automation** | Administers and analyzes developer experience surveys on cadence | Slack, Claude Code |
| Metrics Monitor | **Anomaly detection** | Flags unexpected metric shifts across all 9 categories | Claude Code, Datadog |
| Metrics Monitor | **Trend correlation** | Connects metric movements across categories to reveal systemic patterns | Claude Code, BigQuery |
| Metrics Monitor | **Fulfillment tracking** | Monitors human fulfillment scores and triggers conversations when below threshold | Claude Code, Slack |
| Metrics Monitor | **Dashboard generation** | Creates and maintains metric dashboards for each cognitive unit | Grafana, Claude Code |

### Documentation & Knowledge

| Agent | Capability | Description | Tools Used |
|-------|-----------|-------------|------------|
| Documentation & Knowledge | **Decision capture** | Records decisions, context, and rationale as they happen in workflow | Claude Code, Confluence |
| Documentation & Knowledge | **Knowledge synthesis** | Connects scattered documentation into coherent knowledge graphs | Glean, Claude Code |
| Documentation & Knowledge | **Onboarding acceleration** | Generates personalized onboarding paths based on cognitive profile and unit assignment | Claude Code, Glean |
| Documentation & Knowledge | **Runbook generation** | Creates and maintains operational runbooks from incident learnings | Claude Code, Confluence |
| Documentation & Knowledge | **Learning extraction** | Distills transferable lessons from retrospectives, incidents, and experiments | Claude Code, Gemini Enterprise |
| Documentation & Knowledge | **Knowledge gap identification** | Detects areas where documentation is missing, stale, or contradictory | Glean, Claude Code |

---

## Cognitive Function Capabilities

| Function | Capability | How AI Agents Support |
|----------|-----------|----------------------|
| **Builder** | Translate intent to working code | Code Co-Creator generates code; human Builder validates intent alignment |
| **Builder** | Infrastructure provisioning | Code Co-Creator scaffolds IaC; human Builder makes deployment decisions |
| **Builder** | Pipeline construction | Code Co-Creator templates CI/CD; human Builder tunes flow and gates |
| **Problem Framer** | Ambiguity structuring | Analysis Partner surfaces data; human Problem Framer shapes the question |
| **Problem Framer** | Constraint identification | Architecture Explorer maps constraints; human Problem Framer prioritizes |
| **Problem Framer** | Scope definition | Analysis Partner models impact; human Problem Framer draws boundaries |
| **Pattern Integrator** | Cross-domain connection | All agents surface patterns; human Pattern Integrator synthesizes meaning |
| **Pattern Integrator** | Systemic insight | Metrics Monitor correlates signals; human Pattern Integrator interprets |
| **Pattern Integrator** | Trend recognition | Metrics Monitor detects anomalies; human Pattern Integrator judges significance |
| **Resonance Sensor** | Organizational pulse reading | Analysis Partner aggregates signals; human Resonance Sensor feels the current |
| **Resonance Sensor** | Tension detection | Metrics Monitor flags fulfillment dips; human Resonance Sensor investigates |
| **Resonance Sensor** | Energy assessment | Analysis Partner summarizes retro themes; human Resonance Sensor acts |
| **Quality Guardian** | Standards enforcement | Quality Analyst automates checks; human Quality Guardian sets the bar |
| **Quality Guardian** | Craft advocacy | Quality Analyst flags shortcuts; human Quality Guardian holds the line |
| **Quality Guardian** | Risk assessment | Quality Analyst scans for vulnerabilities; human Quality Guardian decides tolerance |
| **Growth Catalyst** | Learning opportunity creation | Documentation & Knowledge identifies gaps; human Growth Catalyst designs experiences |
| **Growth Catalyst** | Capability development | Documentation & Knowledge personalizes paths; human Growth Catalyst mentors |
| **Growth Catalyst** | Psychological safety | Metrics Monitor tracks fulfillment; human Growth Catalyst creates conditions |
| **Solution Architect** | System design | Architecture Explorer generates options; human Solution Architect chooses |
| **Solution Architect** | Trade-off navigation | Architecture Explorer quantifies trade-offs; human Solution Architect balances |
| **Solution Architect** | Evolutionary architecture | Architecture Explorer maps migration paths; human Solution Architect sequences |
| **Stakeholder Harmonizer** | Interest alignment | Analysis Partner maps stakeholder needs; human Stakeholder Harmonizer mediates |
| **Stakeholder Harmonizer** | Communication bridging | Documentation & Knowledge synthesizes context; human Stakeholder Harmonizer translates |
| **Stakeholder Harmonizer** | Conflict resolution | Metrics Monitor provides objective data; human Stakeholder Harmonizer facilitates |
| **Fresh-Eyes Observer** | Assumption challenging | Quality Analyst flags established patterns; human Fresh-Eyes Observer questions them |
| **Fresh-Eyes Observer** | Blind spot detection | Analysis Partner maps coverage gaps; human Fresh-Eyes Observer looks where others don't |
| **Fresh-Eyes Observer** | Convention questioning | Quality Analyst compares to external practices; human Fresh-Eyes Observer decides relevance |
| **Learner** | Knowledge extraction | Documentation & Knowledge captures decisions; human Learner distills lessons |
| **Learner** | Experience synthesis | Documentation & Knowledge connects incidents; human Learner builds mental models |
| **Learner** | Transfer facilitation | Documentation & Knowledge generates guides; human Learner teaches others |

---

## Combined Capability Patterns

| Task Pattern | Agent Combination | Human Functions Needed |
|-------------|-------------------|----------------------|
| **Incident response** | Analysis Partner + Quality Analyst + Metrics Monitor | Problem Framer + Builder + Resonance Sensor |
| **Feature design** | Architecture Explorer + Code Co-Creator + Documentation & Knowledge | Solution Architect + Builder + Stakeholder Harmonizer |
| **Tech debt remediation** | Architecture Explorer + Quality Analyst + Code Co-Creator | Quality Guardian + Builder + Pattern Integrator |
| **Platform migration** | Architecture Explorer + Code Co-Creator + Analysis Partner | Solution Architect + Builder + Problem Framer |
| **New team onboarding** | Documentation & Knowledge + Analysis Partner | Growth Catalyst + Learner + Resonance Sensor |
| **Performance optimization** | Quality Analyst + Metrics Monitor + Code Co-Creator | Pattern Integrator + Builder + Quality Guardian |
| **Retrospective synthesis** | Analysis Partner + Documentation & Knowledge + Metrics Monitor | Resonance Sensor + Learner + Fresh-Eyes Observer |
| **Security hardening** | Quality Analyst + Code Co-Creator + Architecture Explorer | Quality Guardian + Builder + Solution Architect |
| **Metric framework setup** | Metrics Monitor + Analysis Partner + Documentation & Knowledge | Pattern Integrator + Problem Framer + Learner |
| **Emergence exploration** | Analysis Partner + Architecture Explorer + Documentation & Knowledge | Fresh-Eyes Observer + Pattern Integrator + Growth Catalyst |

See `agents/` for agent implementation details and `cognitive-functions/` for function definitions.
