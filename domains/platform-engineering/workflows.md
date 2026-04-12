# Platform Engineering Workflows

Multi-agent workflows for common platform engineering activities. Each workflow identifies the primary agent and cognitive function at every step.

---

## Workflow 1: Diagnose a Platform Reliability Problem

**Trigger:** SLO breach detected or incident reported by downstream team.

**Outcome:** Root cause identified, fix deployed, runbook updated.

1. **Metrics Monitor** (Pattern Integrator): Surface anomaly data. Identify which SLIs are breaching, since when, and the magnitude of deviation. Correlate with other metric categories to narrow the blast radius.

2. **Analysis Partner** (Problem Framer): Correlate the anomaly with recent changes. Check deployment logs, configuration changes, dependency updates, and upstream service modifications. Produce a ranked list of probable causes.

3. **Code Co-Creator** (Builder): Trace execution paths in the suspect components. Instrument additional logging if needed. Identify the root cause at the code or configuration level. Implement the fix.

4. **Quality Analyst** (Quality Guardian): Verify the fix in staging. Confirm no regression in related platform services. Validate that SLO dashboards return to green. Run targeted chaos tests against the fixed component.

5. **Documentation & Knowledge** (Learner): Update the runbook with the new failure mode and resolution steps. Add the incident to the knowledge base. Tag with relevant service names and failure categories for future retrieval.

---

## Workflow 2: Onboard a New Team onto the Platform

**Trigger:** New team requests platform access, or existing team migrates from legacy infrastructure.

**Outcome:** Team completes first deployment within 4 hours of starting onboarding.

1. **Analysis Partner** (Problem Framer): Assess the team's current technology stack, deployment model, and operational maturity. Identify integration points with the platform. Estimate migration effort and flag potential blockers.

2. **Documentation & Knowledge** (Growth Catalyst): Generate a customized onboarding guide based on the team's stack and needs. Select the appropriate golden paths. Create a checklist of platform capabilities the team should adopt first.

3. **Code Co-Creator** (Builder): Create starter templates for the team's service type. Bootstrap repositories with CI/CD configuration, Dockerfile, Helm charts, and observability instrumentation. Configure namespace and access controls.

4. **Quality Analyst** (Quality Guardian): Validate the onboarding path meets security compliance requirements. Verify that the bootstrapped configuration passes all platform policy checks. Confirm testing standards are met.

5. **Metrics Monitor** (Pattern Integrator): Track time-to-first-deploy for the onboarding team. Surface friction points where the team deviates from the golden path or spends unexpected time. Feed findings back to the **Developer Experience** unit.

---

## Workflow 3: Build a New Platform Capability

**Trigger:** Multiple downstream teams request a capability, or strategic decision to expand the platform.

**Outcome:** New capability launched with documentation, metrics, and adoption tracking.

1. **Analysis Partner** (Problem Framer): Conduct pre-analysis. Research prior art in the organization and in the platform engineering community. Consolidate downstream team requests. Analyze competitive platforms and open-source alternatives.

2. **Architecture Explorer** (Solution Architect): Generate 3 or more architecture options. Produce a tradeoff matrix comparing build effort, operational complexity, scalability, and reuse potential. Recommend an approach with rationale.

3. **Code Co-Creator** (Builder): Implement the chosen approach. Write comprehensive tests including unit, integration, and contract tests. Follow platform coding standards and create reusable modules where possible.

4. **Quality Analyst** (Quality Guardian): Provide continuous quality monitoring during development. Run security scans, dependency checks, and performance benchmarks. Validate that the new capability does not degrade existing platform services.

5. **Metrics Monitor** (Pattern Integrator): Configure adoption tracking dashboards for the new capability. Define success metrics (adoption rate, usage frequency, error rate). Track metrics from launch through the first 30 days.

6. **Documentation & Knowledge** (Learner): Generate API documentation, runbooks, and troubleshooting guides. Create an onboarding tutorial for the new capability. Update the service catalog and developer portal.

---

## Workflow 4: Run a Platform Health Evaluation

**Trigger:** End of sprint, monthly review, or phase gate assessment.

**Outcome:** Comprehensive health report across all 9 metric categories with actionable recommendations.

1. **Metrics Monitor** (Pattern Integrator): Generate a full 9-category metrics snapshot. Pull data from all configured sources. Compute trends, identify anomalies, and flag metrics that are off-target.

2. **Quality Analyst** (Quality Guardian): Run automated platform health checks. Assess security posture, dependency freshness, test coverage, and compliance status. Produce a quality scorecard for each platform service.

3. **Analysis Partner** (Problem Framer): Analyze metric trends across the evaluation period. Flag emerging risks before they become incidents. Identify improvement opportunities ranked by effort and impact. Highlight connections between metric categories.

4. **Documentation & Knowledge** (Learner): Compile the health report for stakeholders. Format findings using the evaluation report template (see `templates/confluence/evaluation-report.md.j2`). Archive the report in the knowledge base for trend analysis.

---

## Workflow Execution Guidelines

- Every workflow step names the **agent** and **cognitive function** responsible.
- Steps execute sequentially by default. Steps 3 and 4 in Workflow 3 may overlap.
- Each workflow produces artifacts that feed into the next step.
- The **Resonance Sensor** function monitors team energy throughout all workflows. If fulfillment drops below 7, the workflow pauses for a check-in.
- Workflows should be adapted to your organization's cadence and tooling.

---

## Organization Extension Point

> **YOUR_ORG:** Customize these workflows to match your platform's architecture and team structure. Add workflows for your most common platform activities. Ensure every step has an explicit agent and function label.

---

*Reference: [agents/](../../agents/) | [workflows/](../../workflows/) | [evaluation.md](evaluation.md)*
