# Foundational Skills

## The 8-Stage Problem-Solving Journey

Every significant engineering challenge moves through these stages. HIO agents support each stage differently, but the human drives the journey.

| Stage | Description | Key Cognitive Functions | Agent Support |
|-------|-------------|----------------------|---------------|
| 1. **Notice** | Sense that something needs attention | Resonance Sensor, Fresh-Eyes Observer | Analysis Partner surfaces signals from metrics and logs |
| 2. **Frame** | Shape the ambiguity into a solvable problem | Problem Framer | Analysis Partner provides data; human reframes the question |
| 3. **Explore** | Generate options without premature commitment | Solution Architect, Pattern Integrator | Architecture Explorer generates alternatives |
| 4. **Choose** | Select a path with clear trade-off awareness | Solution Architect, Stakeholder Harmonizer | Architecture Explorer quantifies trade-offs |
| 5. **Build** | Translate the decision into working systems | Builder, Quality Guardian | Code Co-Creator collaborates on implementation |
| 6. **Verify** | Confirm that what was built solves what was framed | Quality Guardian, Fresh-Eyes Observer | Quality Analyst runs multi-dimensional assessment |
| 7. **Learn** | Extract transferable knowledge from the experience | Learner, Growth Catalyst | Documentation & Knowledge captures decisions and lessons |
| 8. **Share** | Distribute learning to amplify organizational capability | Growth Catalyst, Stakeholder Harmonizer | Documentation & Knowledge synthesizes and publishes |

The journey is not strictly linear. Most real work oscillates between stages -- framing leads to exploration, which reframes the problem, which opens new options. HIO embraces this oscillation rather than forcing linear progression.

---

## 7 HIO Meta-Capabilities

These meta-capabilities distinguish HIO practitioners from traditional engineers. Each one can be developed deliberately and each one is supported by AI agents.

### 1. Oscillation Recognition

**Description:** Seeing the natural back-and-forth between states -- analysis and action, focus and diffusion, confidence and doubt -- as productive rather than wasteful.

**How AI agents support it:** The Metrics Monitor tracks patterns of oscillation in team behavior (e.g., cycles between exploration and execution). The Analysis Partner surfaces data showing when oscillation produced better outcomes than forced linearity.

**Anti-pattern:** Treating oscillation as indecision. Forcing premature convergence to "stop going back and forth."

---

### 2. Grip Awareness

**Description:** Noticing when identity attachment limits options. "I'm a backend engineer" becomes a grip that prevents someone from contributing as a Problem Framer or Resonance Sensor.

**How AI agents support it:** The Documentation & Knowledge agent tracks which cognitive functions each person has exercised. The Metrics Monitor flags when someone has operated exclusively in one function for multiple sprints.

**Anti-pattern:** Confusing expertise with identity. Expertise is portable; identity grip is not.

---

### 3. Bandwidth Expansion

**Description:** Deliberately growing capacity for new cognitive functions. A Builder who develops Pattern Integrator capabilities sees code differently -- not just "does it work?" but "what does this pattern mean?"

**How AI agents support it:** The Code Co-Creator and other agents can temporarily carry more of a person's primary function load, creating space to practice a developing function. The Documentation & Knowledge agent provides learning paths.

**Anti-pattern:** Bandwidth hoarding -- only doing what you are already good at because it feels productive.

---

### 4. Position-Free Observation

**Description:** Seeing situations without attachment to a particular viewpoint. Observing a system design debate without needing your preferred architecture to win.

**How AI agents support it:** The Architecture Explorer generates multiple design options without preference, modeling the view from each position. The Analysis Partner provides data that no single viewpoint owns.

**Anti-pattern:** Advocacy disguised as analysis. Presenting data selectively to support a pre-chosen position.

---

### 5. Resonance Sensitivity

**Description:** Reading the "frequency" of a situation and matching it. A team in crisis needs a different cognitive approach than a team in exploration mode.

**How AI agents support it:** The Metrics Monitor tracks fulfillment scores and engagement signals. The Analysis Partner synthesizes retrospective themes and Slack sentiment to surface the team's current frequency.

**Anti-pattern:** One-mode operation. Applying the same energy and approach regardless of context -- e.g., optimizing during a crisis or firefighting during calm.

---

### 6. Non-Resistance to Fluctuation

**Description:** Accepting that energy and productivity naturally fluctuate. Some sprints produce breakthroughs; others produce foundations that make future breakthroughs possible.

**How AI agents support it:** The Metrics Monitor shows productivity patterns over time, normalizing fluctuation as healthy. The Documentation & Knowledge agent captures value from "quiet" sprints that traditional metrics would dismiss.

**Anti-pattern:** Treating every low-output sprint as a problem to solve. Demanding constant peak performance.

---

### 7. Scale Sensitivity

**Description:** Recognizing when to zoom in (detail) vs. zoom out (pattern). A bug fix requires detail focus; understanding why bugs keep appearing in the same module requires pattern focus.

**How AI agents support it:** The Analysis Partner operates at multiple scales -- it can analyze a single function or trace patterns across the entire codebase. The Architecture Explorer shifts between component-level and system-level views on demand.

**Anti-pattern:** Scale lock -- staying zoomed in on implementation details when the real issue is architectural, or staying zoomed out on strategy when the team needs concrete next steps.

---

## Developing These Skills

Each meta-capability develops through practice, not instruction. The recommended approach:

| Capability | Practice Method | Frequency |
|-----------|----------------|-----------|
| Oscillation Recognition | Retrospective reflection on productive oscillation | Every sprint retro |
| Grip Awareness | Quarterly cognitive function rotation | Every quarter |
| Bandwidth Expansion | Pair with someone strong in your developing function | Weekly |
| Position-Free Observation | Facilitate a design discussion without advocating | Monthly |
| Resonance Sensitivity | Open each sprint kickoff with a "frequency check" | Every sprint |
| Non-Resistance to Fluctuation | Review 6-sprint metric trends, not single sprints | Every phase gate |
| Scale Sensitivity | Practice deliberate zoom-in/zoom-out during analysis | Weekly |

See `cognitive-functions/` for the 10 cognitive function definitions and `workflows/` for how these skills integrate into harmonized sprints.
