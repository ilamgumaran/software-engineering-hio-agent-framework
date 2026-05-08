---
description: >
  Runs SBOM generation, software composition analysis (SCA), and
  vulnerability scans on dependencies. Use during PR review for any
  dependency change, and as a scheduled job on main.
---

## Dependency Security Scan

### Components
- **SBOM (Software Bill of Materials):** A manifest of every direct + transitive
  dependency. Format: CycloneDX or SPDX.
- **SCA (Software Composition Analysis):** Cross-references the SBOM against
  known vulnerability databases (NVD, GHSA, OSV).
- **License compliance:** Confirms licenses fit org policy.
- **Secrets scan:** Detects accidentally committed secrets.

### Tooling Choices (pick one per category)
- **SBOM:** Syft, CycloneDX CLI, or build-tool plugins (gradle-cyclonedx, pip-audit).
- **SCA:** GitHub Advanced Security, Snyk, Trivy, Grype, OSV-Scanner.
- **Secrets:** GitHub secret scanning (free), Trufflehog, Gitleaks.
- **License:** FOSSA, scancode, license-checker.

### CI Gates
- **PR check:**
  - SBOM regenerated.
  - SCA fails the build on Critical or High severity (with no fix available)
    UNLESS an exception is filed and approved (see below).
  - License check fails on disallowed licenses (e.g., GPL in proprietary code).
  - Secrets scan fails on any positive hit.
- **Main / nightly:**
  - Full scan; alerts to on-call channel for new findings.
  - SBOM published as build artifact (regulatory requirement in many orgs).

### Exception Process
A Critical / High vulnerability with no immediate fix happens. Don't block
shipping forever. Document:
- Why the issue is mitigated (not exposed to user input, behind WAF, etc.).
- Owner + expiration date for the exception.
- Tracking ticket for permanent fix.
- Auto-revoke after expiration.

### Allow-List Policy (Licenses)
Maintain an org-level list:
- **Allow:** MIT, Apache-2.0, BSD-2-Clause, BSD-3-Clause, ISC, MPL-2.0,
  LGPL-3.0 (with caveats).
- **Review:** GPL-3.0, AGPL-3.0, EPL.
- **Deny:** SSPL, BUSL-1.1 (depending on usage).

### Container Images
- Scan every image push (Trivy / Grype).
- Use distroless or minimal bases to shrink CVE surface.
- Pin by digest, not tag.
- Re-scan periodically — today's clean image is tomorrow's vulnerable image.

### Anti-patterns
- Snoozing all warnings to clear the dashboard.
- Long-lived exceptions with no expiration.
- Disabling Dependabot / Renovate to avoid noise.
- Treating SCA findings as advisory only.

### Verification
- SBOM artifact exists in build pipeline.
- SCA results visible per PR.
- Exceptions list reviewed monthly.
- Container images re-scanned weekly.

### Reference
- `.claude/rules/security.md` for the broader security guardrails.

### Model Tier
Default: Sonnet. Escalate to Opus when responding to a zero-day or
designing the org's exception policy.
