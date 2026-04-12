# Metrics: Code Health

## Purpose

Code quality and maintenance burden metrics. These measure the structural health of the codebase itself -- the foundation that all other engineering outcomes rest on. Poor code health creates a drag on every other metric category.

Code Health sits in Layer 2 (Outcome) because healthy code is an outcome of good engineering practices, not just a process input.

---

## KPIs

| KPI | What It Measures | How to Capture | Target Direction | Frequency |
|---|---|---|---|---|
| Rework Rate | % of code changed within 2 weeks of initial merge | Git log analysis (commits modifying recently merged code) | Lower (25%+ reduction) | Weekly |
| Defect Escape Rate | Ratio of defects found in production vs. pre-production | Bug tracker labels (production vs. caught in review/test) | Lower (20%+ reduction) | Monthly |
| Technical Debt Ratio | Estimated debt remediation time / total development time | Static analysis tools (SonarQube, CodeClimate) + team estimates | Lower (trending down) | Monthly |
| Test Coverage Trend | % change in meaningful test coverage over time | CI test coverage reports (track direction, not absolute %) | Higher (trending up) | Weekly |
| Build/Pipeline Duration | Time from commit to deployable artifact | CI/CD pipeline timing data | Lower (trending down) | Daily |
| Dependency Health | % of dependencies current + % with known vulnerabilities | Dependency scanning tools (Dependabot, Snyk, Renovate) | Higher currency, lower vulnerabilities | Weekly |

---

## Baseline Capture

To establish your Code Health baseline:

1. Run git log analysis to calculate rework rate for the last 4 weeks. Count files modified within 14 days of their initial merge.
2. Classify the last quarter of bugs by where they were caught: code review, automated test, staging, or production.
3. Run static analysis across all active repositories to generate a technical debt estimate.
4. Pull current test coverage numbers from CI. Record the starting point for trend tracking.
5. Measure average pipeline duration across all active CI pipelines.
6. Run dependency audit across all repositories. Record currency and vulnerability counts.

---

## Interpretation Guide

- **Rework Rate** above 20% suggests code is being merged before it is ready. Investigate whether the cause is insufficient review, unclear requirements, time pressure, or inadequate testing. AI-assisted code review (see [../agents/](../agents/)) can help catch issues earlier.
- **Defect Escape Rate** is the most consequential code health metric. Defects that reach production cost 10-100x more to fix than those caught in review. Track this as a ratio, not an absolute count -- as deployment frequency increases, total defects may rise while the escape rate drops.
- **Technical Debt Ratio** above 15% means the team is spending more than 1 day per sprint on debt. This is manageable. Above 30% signals that debt is actively slowing feature delivery and requires dedicated remediation.
- **Test Coverage Trend** matters more than absolute coverage. A team going from 40% to 55% is healthier than a team stable at 80% with flaky tests. Focus on meaningful coverage -- tests that catch real bugs, not tests that exercise trivial paths.
- **Build/Pipeline Duration** above 15 minutes breaks developer flow. Optimize build caching, test parallelization, and dependency resolution before asking developers to tolerate slow feedback loops.
- **Dependency Health** vulnerabilities above 0 critical and 0 high are non-negotiable to address. Currency (keeping dependencies up to date) prevents vulnerability accumulation.

---

## Connection to Other Categories

**Feeds:**
- DORA -- test coverage and low rework rates directly reduce change failure rate. Fast pipelines reduce lead time.
- SPACE/DX -- fast builds and clean code reduce developer friction
- Platform Outcomes -- code health drives platform reliability and downstream trust

**Fed by:**
- AI Utilization -- AI code review and automated refactoring improve rework and defect rates
- Current/Legacy -- merge rate and velocity patterns signal where code health pressure exists
- Harmonization -- cross-function collaboration brings diverse perspectives to code quality

---

## Organization Extension Point

> **YOUR_ORG:** Map your existing code quality tools (linters, static analyzers, coverage reporters) to the KPIs above. If you use SonarQube, CodeClimate, or similar platforms, configure dashboards to track these specific metrics. Add any org-specific code health indicators (e.g., API backward compatibility rate, documentation coverage) that matter for your platform consumers.
