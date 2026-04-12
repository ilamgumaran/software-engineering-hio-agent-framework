# GitHub Copilot -- HIO Workflows

Four workflows where GitHub Copilot supports HIO activities at the IDE level. These complement the Claude Code workflows in `tools/claude-code/workflows.md`.

---

## 1. Code Generation During Deep Work

Real-time coding assistance during Deep Work Collaboration blocks (`workflows/deep-work-collaboration.md`).

**Trigger:** Engineer enters a deep work block for implementation tasks.

**Flow:**

1. Open the target files in your IDE with Copilot enabled
2. Write a descriptive comment for the function or module you are building
3. Let Copilot generate the initial implementation inline
4. Review, accept, or modify suggestions as you go
5. Use Copilot Chat for quick questions about syntax, patterns, or library usage
6. Continue building with Copilot handling boilerplate while you focus on logic

**Key Features Used:** Inline completion, Copilot Chat, multi-line suggestions.

**Expected Outcome:** Faster implementation during deep work blocks with reduced context-switching for syntax and boilerplate questions.

---

## 2. Test Writing Assistance

Generating test scaffolding and test cases for new or modified code.

**Trigger:** Implementation complete, tests needed before code review.

**Flow:**

1. Open the implementation file alongside the test file
2. Write a comment describing the test scenario (e.g., "Test that rate limiter rejects requests above threshold")
3. Let Copilot generate the test structure: arrange, act, assert
4. Review generated assertions for correctness -- Copilot may suggest plausible but incorrect expected values
5. Add edge cases by writing descriptive test names and letting Copilot fill in the body
6. Run tests to verify before submitting for review

**Key Features Used:** Inline completion, context from implementation file, test pattern recognition.

**Expected Outcome:** Test scaffolding generated quickly, with the engineer focusing on test design and edge case identification rather than test syntax.

---

## 3. Code Review Suggestions

Using Copilot during manual code review to understand and evaluate changes.

**Trigger:** Reviewing a pull request or changeset (complementary to the Claude Code agent-assisted review).

**Flow:**

1. Open the changed files in your IDE
2. Use Copilot Chat to ask about unfamiliar patterns: "What does this function do?" or "Why would you use this approach?"
3. Ask Copilot to suggest alternative implementations if you suspect a better approach exists
4. Use inline completion to draft review comments with suggested fixes
5. Cross-reference with the Claude Code Quality Analyst review for comprehensive coverage

**Key Features Used:** Copilot Chat, inline suggestions for review comments.

**Expected Outcome:** More informed code reviews, especially when reviewing code in unfamiliar areas of the codebase.

---

## 4. Documentation Inline Comments

Adding inline documentation to code during or after implementation.

**Trigger:** Code written without sufficient inline documentation, or documentation sprint.

**Flow:**

1. Position cursor above a function, class, or complex block
2. Type the documentation comment prefix for your language (e.g., `/**`, `"""`, `///`)
3. Let Copilot generate the docstring with parameter descriptions, return values, and usage examples
4. Review for accuracy -- Copilot infers intent from code structure but may miss nuance
5. Add context that only the author would know (why, not just what)

**Key Features Used:** Inline completion, docstring pattern recognition.

**Expected Outcome:** Consistent inline documentation that supports the Documentation & Knowledge agent's broader knowledge synthesis efforts.
