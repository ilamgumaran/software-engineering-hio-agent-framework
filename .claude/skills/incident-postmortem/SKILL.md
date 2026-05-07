---
description: >
  Drafts a post-incident review (blameless postmortem) following the org
  template. Use after an incident is resolved to capture timeline, root
  cause, contributing factors, and follow-up actions.
---

## Incident Postmortem

### Sections
1. **Summary** — 1–2 sentences. What happened, blast radius, duration.
2. **Impact** — customers affected, revenue impact, SLA breach.
3. **Timeline** — UTC timestamps, key events, who acted.
4. **Root cause** — the proximate cause and the systemic cause.
5. **What went well** / **What went poorly** — process observations.
6. **Action items** — owner + due date for each. No “be more careful” items.
7. **Detection / response gaps** — alerts that didn’t fire, runbooks that
   were missing or wrong.

### Rules
- Blameless. Describe systems and decisions, not individuals.
- Action items must be concrete (“Add alert on X queue depth >Y”), not vague.
- Link to relevant dashboards, logs, runbooks.

### Model Tier
Default: Opus (high stakes, full-context reasoning).
