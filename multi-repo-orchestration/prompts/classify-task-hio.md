# Prompt: Classify Task as OI / II / Interactive

Use this whenever a task arrives and routing is not obvious. Routing is the first decision; everything else follows.

---

## Inputs

- **Task description:** `[what the user wants done]`
- **Starting repo:** `[owner/name]`
- **Sibling repos likely touched:** `[list]`

---

## Prompt

```
Classify this task as OI (Organic Intelligence), II (Inorganic Intelligence),
or Interactive Collaboration.

Task: [task description]
Starting repo: [owner/name]
Sibling repos likely touched: [list]

Procedure:
1. Identify the task signal -- map it to a row in
   multi-repo-orchestration/hio-collaboration/matrix.md. If no row matches,
   default to Interactive and note that a new row should be proposed.

2. For each repo touched, read the per-repo override in
   hio-collaboration/per-repo-routing.md.

3. Take the most restrictive routing across central and overrides.

4. Check stop conditions: irreversible? security-sensitive? child-safety adjacent?
   identity-level? ambiguous-by-design? Any "yes" forces OI.

5. Output:
   - Classification: OI | II | Interactive
   - Rationale: one line
   - Cited matrix row(s)
   - Stop conditions triggered (or "none")
   - Recommended next step

If the task is OI, do not propose any code or content changes. Produce an
analysis only and hand off to a human.
```

---

## When this prompt is unnecessary

- The starting repo's `AGENTS.md` already routes this exact task signal explicitly
- The task is a trivial typo fix that obviously routes II
