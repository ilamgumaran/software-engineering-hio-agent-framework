# Glean -- HIO Tool Guide

## What It Does

Glean is an enterprise knowledge search platform that indexes content across your organization's tools -- code repositories, documentation wikis, chat messages, email, ticketing systems, and more. Within HIO, it supports the **Documentation & Knowledge** agent type by providing searchable access to institutional memory.

---

## Role in HIO

Glean is the **enterprise knowledge layer**. Where other tools create and analyze content, Glean finds what already exists. It answers the question: "Has someone in this organization already solved this problem or made this decision?"

| HIO Activity | Glean Role |
|---|---|
| Sprint Kickoff | Find prior art, past decisions, related implementations |
| Architecture decisions | Surface historical context and previous evaluations |
| Onboarding | Locate relevant documentation across scattered systems |
| Retrospectives | Find patterns across past retrospective notes and decisions |

---

## Best For

- **Finding institutional knowledge** -- decisions, discussions, and context spread across tools
- **Searching across systems** -- unified search over Confluence, Slack, GitHub, Jira, Google Docs, email
- **Prior art discovery** -- locating existing implementations, designs, or decisions relevant to current work
- **Onboarding support** -- quickly surfacing relevant documentation for new team members or new project areas

---

## HIO Integration

- Feeds the **Documentation & Knowledge** agent (`agents/documentation-knowledge.md`) with organizational context
- Supports the **Learner** cognitive function (`cognitive-functions/learner.md`) during rapid knowledge acquisition
- Supports the **Analysis Partner** agent during sprint kickoff prior art research
- Complements Gemini Enterprise's deep analysis with broad institutional search

---

## Setup and Configuration

1. **Deploy Glean** following your organization's enterprise software process
2. **Connect data sources** -- code repos, wikis, chat, ticketing, email, and document stores
3. **Configure access controls** to respect existing permissions across connected systems
4. **Index HIO framework files** so team members can search for framework guidance alongside other documentation
5. **Review policies** in `org/policies.md` for search scope and data access boundaries

---

## Limitations

- Search quality depends on the breadth and freshness of indexed sources
- Cannot create, modify, or analyze content -- it only finds existing content
- Results require human judgment to assess relevance and currency
- Access controls from source systems must be properly mapped

---

## Related Files

- Documentation & Knowledge agent: `agents/documentation-knowledge.md`
- Learner function: `cognitive-functions/learner.md`
- Glean workflows: `tools/glean/workflows.md`
- AI policies: `org/policies.md`
