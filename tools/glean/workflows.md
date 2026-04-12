# Glean -- HIO Workflows

Three workflows where Glean's enterprise search capabilities support HIO activities. These complement the Claude Code workflows in `tools/claude-code/workflows.md`.

---

## 1. Prior Art Search for Sprint Kickoff

Discovering existing knowledge, decisions, and implementations relevant to upcoming sprint work.

**Trigger:** Sprint Kickoff preparation, after backlog items are identified but before the kickoff ceremony.

**Flow:**

1. For each sprint backlog item, extract key terms: technologies, patterns, system names, problem descriptions
2. Search Glean across all connected sources for: prior implementations of similar features, past design decisions on the same system, related Slack or email discussions, relevant Confluence pages or Google Docs
3. For each result, assess: relevance to the current item, currency (is it still accurate?), and applicability (same system or analogous?)
4. Compile a "prior art brief" per backlog item with links to relevant sources
5. Feed the prior art brief into the Sprint Kickoff pre-analysis package (`tools/claude-code/workflows.md`)

**Key Features Used:** Cross-system search, relevance ranking, source linking.

**Expected Outcome:** Each sprint backlog item arrives at the kickoff ceremony with known prior art attached, preventing teams from rediscovering what the organization already knows.

---

## 2. Knowledge Synthesis for Onboarding

Accelerating new team member onboarding by surfacing relevant organizational knowledge.

**Trigger:** New team member joins a cognitive unit, or an existing member rotates into a new area.

**Flow:**

1. Identify the cognitive unit and domain area the person is joining (see `cognitive-units/` and `domains/`)
2. Search Glean for: architecture decision records (ADRs), system design documents, onboarding guides, key Slack channels and their pinned messages, recent retrospective notes
3. Organize results by topic: system overview, key decisions and their rationale, current initiatives, team norms, and known pitfalls
4. Create a curated reading list ordered from foundational to advanced
5. Share the list with the new member as a starting point, supplemented by `org/working-agreements.md` and the relevant cognitive unit definition

**Key Features Used:** Topical search, source aggregation, cross-tool indexing.

**Expected Outcome:** A curated knowledge package that reduces onboarding time from weeks to days by surfacing the right documents from across the organization's scattered tools.

---

## 3. Institutional Memory Search

Finding historical context for current decisions, supporting the Documentation & Knowledge agent and the Harmonization Retrospective.

**Trigger:** A team faces a decision that "feels familiar," a retrospective surfaces a recurring issue, or someone asks "have we tried this before?"

**Flow:**

1. Formulate the search as a question: "When did we last evaluate X?", "What happened when we tried Y?", "Why did we choose Z over the alternatives?"
2. Search Glean with multiple query variations to catch different phrasings across tools
3. Review results for: original decision context, the options considered, the rationale for the choice, and any follow-up outcomes
4. Synthesize findings into a brief timeline: when decisions were made, what was decided, and what resulted
5. Present to the team during the relevant ceremony (retrospective, sprint kickoff, or architecture review)

**Key Features Used:** Natural language search, historical indexing, cross-tool context assembly.

**Expected Outcome:** Decisions informed by organizational history, avoiding the pattern of repeatedly revisiting settled questions or repeating past mistakes without awareness.
