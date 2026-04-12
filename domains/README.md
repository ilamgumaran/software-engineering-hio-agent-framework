# Domains

## What Is a Domain

A domain is a specialization layer that applies the HIO framework to a specific engineering discipline. Each domain defines how the 10 cognitive functions, 6 AI agents, and 5 cognitive units manifest in the context of a particular engineering practice.

A domain does not change the core framework. It interprets and extends it, providing domain-specific skills, evaluation methods, workflows, and terminology that make the abstract framework concrete and actionable.

---

## Reference Domain: Platform Engineering

The `platform-engineering/` directory is the reference implementation. It demonstrates how to apply HIO to a platform engineering organization that builds Internal Developer Platforms (IDPs) for downstream engineering teams.

Use this domain as a model when creating domains for other specialties such as data engineering, machine learning, mobile development, or security engineering.

---

## Domain Structure

Every domain directory contains 5 files:

| File | Purpose |
|------|---------|
| `overview.md` | Key concepts, business impact, role mapping to cognitive functions and agents |
| `skills.md` | Domain-specific skills organized by cognitive function |
| `evaluation.md` | Domain-specific metrics and evaluation methods using the three-layer model |
| `workflows.md` | Domain-specific multi-agent workflows with explicit agent labels |
| `glossary.md` | Domain terminology with 25+ terms defined |

---

## Creating a New Domain

Follow these 5 steps to create a domain for your engineering specialty:

### Step 1: Create Directory

Create a new directory under `domains/` named after your specialty (e.g., `domains/data-engineering/`).

### Step 2: Write Overview

Define the key concepts of your domain and map them to HIO constructs. Identify which cognitive functions are most prominent and which agents perform which domain activities.

### Step 3: Define Skills

Organize domain-specific technical skills by cognitive function. Each function should have 3-5 skills that represent how that function manifests in your domain.

### Step 4: Define Evaluation

Map the three-layer evaluation model to your domain. Layer 1 captures current operational metrics. Layer 2 captures outcome metrics. Layer 3 captures HIO-specific metrics like fulfillment and emergence.

### Step 5: Create Workflows and Glossary

Define 3-5 multi-agent workflows that represent common domain activities. Compile a glossary of 25+ domain terms that team members need to share vocabulary around.

---

## Organization Extension Point

> **YOUR_ORG:** Create a domain directory for your engineering specialty. Copy the `platform-engineering/` structure and replace the content with your domain-specific concepts, skills, metrics, workflows, and terminology. Reference `domains/platform-engineering/` as a model.
