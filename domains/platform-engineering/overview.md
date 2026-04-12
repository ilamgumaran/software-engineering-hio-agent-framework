# Domain: Platform Engineering

## What Is Platform Engineering

Platform engineering designs and builds toolchains and workflows that enable self-service capabilities for software engineering organizations. A platform engineering team builds the **Internal Developer Platform (IDP)** that downstream teams use to provision infrastructure, deploy services, observe systems, and manage the full software lifecycle without filing tickets or waiting on other teams.

Platform engineering treats the platform as a product. Downstream engineering teams are the customers. Success is measured by adoption, self-service rates, and developer satisfaction rather than by tickets closed or infrastructure provisioned.

---

## Key Concepts

| Concept | Definition | HIO Connection |
|---------|-----------|----------------|
| Internal Developer Platform (IDP) | Self-service layer over infrastructure and tooling | Core product of cognitive units |
| Golden Paths | Opinionated, supported workflows for common tasks | Designed by **Developer Experience** unit |
| Self-Service | Downstream teams operate independently without tickets | Key metric (>70% target) |
| Platform as Product | Treating the platform as a product with users and feedback loops | **Problem Framer** function drives this mindset |
| Service Level Indicators (SLIs) | Quantitative measures of service quality | Tracked by **Metrics Monitor** agent |
| Service Level Objectives (SLOs) | Target reliability values for platform services | Managed by **Scale & Reliability** unit |
| Developer Portal | Centralized hub for platform capabilities and documentation | Built by **Developer Experience** unit |
| GitOps | Git as single source of truth for infrastructure state | Enforced by **Code Co-Creator** agent |
| Service Catalog | Registry of available platform services and their owners | Maintained by **Documentation & Knowledge** agent |
| Infrastructure Abstraction | Hiding infrastructure complexity behind simple interfaces | Core **Architecture Explorer** output |

---

## Business Impact

Platform engineering delivers measurable business value across four dimensions:

**Developer Productivity** -- Reduce time developers spend on infrastructure tasks by 40-60% through self-service capabilities and golden paths.

**Reduced Cognitive Load** -- Abstract away infrastructure complexity so downstream teams focus on business logic rather than operational concerns.

**Standardized Practices** -- Enforce security, compliance, and operational best practices through platform defaults rather than review gates.

**Accelerated Time-to-Market** -- Cut time-to-first-deploy for new services from weeks to hours through templated workflows and automated provisioning.

---

## Primary Cognitive Functions and Agents

| Platform Activity | Primary Function | Primary Agent |
|-------------------|-----------------|---------------|
| Design infrastructure abstractions | **Solution Architect** | **Architecture Explorer** |
| Build CI/CD pipelines | **Builder** | **Code Co-Creator** |
| Research developer pain points | **Problem Framer** | **Analysis Partner** |
| Monitor platform reliability | **Quality Guardian** | **Quality Analyst** |
| Track platform adoption metrics | **Pattern Integrator** | **Metrics Monitor** |
| Onboard downstream teams | **Growth Catalyst** | **Documentation & Knowledge** |
| Resolve platform incidents | **Builder** + **Quality Guardian** | **Code Co-Creator** + **Quality Analyst** |
| Evaluate new technologies | **Fresh-Eyes Observer** | **Architecture Explorer** |
| Harmonize cross-team standards | **Stakeholder Harmonizer** | **Analysis Partner** |
| Capture platform knowledge | **Learner** | **Documentation & Knowledge** |

---

## Multi-Agent Execution Example

**Scenario:** A downstream team requests the ability to run A/B tests on their service.

1. **Analysis Partner** (Problem Framer): Gathers requirements from the requesting team. Analyzes how other teams have solved A/B testing. Identifies three approaches: feature flags, traffic splitting at the mesh layer, and dedicated experimentation infrastructure.

2. **Architecture Explorer** (Solution Architect): Evaluates the three approaches against platform constraints. Produces a tradeoff matrix comparing build effort, operational complexity, and reuse potential. Recommends traffic splitting with feature flag integration.

3. **Code Co-Creator** (Builder): Implements the chosen approach. Creates Terraform modules for traffic splitting rules, extends the service mesh configuration, and builds a CLI command for downstream teams to create experiments.

4. **Quality Analyst** (Quality Guardian): Validates the implementation against platform reliability standards. Runs chaos tests to confirm A/B routing does not degrade latency beyond SLO thresholds. Verifies rollback behavior.

5. **Documentation & Knowledge** (Learner): Generates a golden path guide for A/B testing. Creates API documentation for the new CLI commands. Updates the service catalog with the new capability.

6. **Metrics Monitor** (Pattern Integrator): Configures adoption tracking for the new capability. Sets up dashboards showing how many teams are using A/B testing, experiment duration distributions, and statistical significance rates.

---

*Reference: [cognitive-functions/](../../cognitive-functions/) | [agents/](../../agents/) | [cognitive-units/](../../cognitive-units/)*
