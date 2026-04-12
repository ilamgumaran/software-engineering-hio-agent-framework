# Platform Engineering Glossary

Essential terminology for platform engineering teams working within the HIO framework. Terms are ordered alphabetically.

---

| Term | Definition |
|------|-----------|
| API Gateway | A service that acts as a single entry point for API requests, providing routing, authentication, rate limiting, and observability. |
| Backstage | An open-source developer portal framework originally created by Spotify, used to build internal developer portals with a plugin-based architecture. |
| Blue-Green Deployment | A deployment strategy that runs two identical production environments, switching traffic from the current (blue) to the new (green) version to enable zero-downtime releases. |
| Canary Release | A deployment strategy that routes a small percentage of traffic to a new version before gradually rolling it out, allowing early detection of issues. |
| Cell-Based Architecture | An architectural pattern that isolates workloads into independent cells to limit blast radius and improve fault containment. |
| Chaos Engineering | The discipline of experimenting on a system to build confidence in its ability to withstand turbulent conditions in production. |
| CI/CD Pipeline | A series of automated steps that build, test, and deploy code changes, forming the backbone of continuous integration and continuous delivery. |
| Container Orchestration | The automated management of containerized workloads including scheduling, scaling, networking, and health monitoring, typically using Kubernetes. |
| Developer Portal | A centralized web interface where downstream teams discover platform capabilities, read documentation, and access self-service tools. |
| Error Budget | The acceptable amount of unreliability for a service, calculated as 1 minus the SLO target. When the error budget is exhausted, teams prioritize reliability over features. |
| Feature Flag | A mechanism that allows enabling or disabling features at runtime without deploying new code, supporting canary releases, A/B testing, and kill switches. |
| GitOps | An operational framework that takes DevOps best practices and applies them to infrastructure automation, using Git as the single source of truth for declarative infrastructure and applications. |
| Golden Path | An opinionated and supported path for performing a common task on the platform, designed to reduce cognitive load and accelerate delivery. |
| Helm Chart | A package format for Kubernetes applications that bundles templates, default values, and dependencies into a versioned, reusable artifact. |
| Infrastructure as Code (IaC) | The practice of managing and provisioning infrastructure through machine-readable definition files rather than manual processes or interactive tools. |
| Internal Developer Platform (IDP) | A self-service layer built on top of infrastructure and tooling that provides downstream teams with curated capabilities for building, deploying, and operating software. |
| Kubernetes | An open-source container orchestration platform that automates deployment, scaling, and management of containerized workloads. |
| Observability | The ability to understand the internal state of a system by examining its external outputs: logs, metrics, and traces. |
| Platform as Product | The practice of treating an internal developer platform as a product, with downstream teams as customers, requiring user research, roadmaps, and satisfaction measurement. |
| Platform Team | A team that builds and maintains the internal developer platform, organized as cognitive units in the HIO framework. |
| Self-Service | The ability for downstream teams to provision resources, deploy services, and manage configurations without submitting tickets or waiting for another team. |
| Service Catalog | A registry of available platform services, their owners, documentation links, and operational status, typically accessible through the developer portal. |
| Service Level Agreement (SLA) | A formal contract between a service provider and consumer that defines the expected level of service, including consequences for violations. |
| Service Level Indicator (SLI) | A quantitative measure of some aspect of the level of service being provided, such as request latency, availability, or error rate. |
| Service Level Objective (SLO) | A target value or range for a service level indicator that defines the acceptable level of reliability for a service. |
| Service Mesh | A dedicated infrastructure layer for handling service-to-service communication, providing features like mTLS, retries, circuit breaking, and observability. |
| Terraform | An open-source infrastructure as code tool that enables defining and provisioning infrastructure across multiple cloud providers using a declarative configuration language. |
| Toil | Repetitive, manual, automatable, tactical, and devoid-of-long-term-value work that scales linearly with service growth. A key target for platform automation. |

---

*Reference: [overview.md](overview.md) | [skills.md](skills.md)*
