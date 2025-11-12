# Alternative Teaching Approaches

This directory contains alternative pedagogical approaches for the Prompt Engineering Bootcamp. These are **complete alternatives** to the main presentations, not supplementary materials.

**Default:** Use main presentations in `presentations/` directory (industry standards approach).

**Use alternatives when:** Teaching specific audiences or contexts where different pedagogies are more appropriate.

---

## 5-Mode Pedagogy

**Location:** [5-mode-pedagogy/](5-mode-pedagogy/)

**Files:**
- `SESSION-1-prompt-files.md` - Modes 0-1 (Constitution, Specification)
- `SESSION-2-workflows.md` - Modes 2-4 (Planning, ABCD, Implementation)

### Approach

Numbered progression (Mode 0 → Mode 5) with file-based workflow metaphor:

| Mode | File Name | Purpose |
|------|-----------|---------|
| 0 | Constitution | Project-wide rules (reusable) |
| 1 | Specification | What to build (this task) |
| 2 | Planning | How to build (execution phases) |
| 3 | ABCD | Decision documentation (alternatives) |
| 4 | Implementation | Synthesis and code generation |

### Best For

- **Beginner developers** new to AI tools
- **Structured learners** who prefer sequential steps
- **File-as-artifact** mindset (prompts saved as .md files)
- **Workshops** emphasizing workflow documentation

### Tradeoffs

**Pros:**
- Clear numeric sequencing (Mode 0 → 5)
- Explicit file-based workflow
- Easy to follow for beginners

**Cons:**
- Non-standard terminology (Constitution, Specification, ABCD)
- Less transferable to other contexts (can't google "Mode 3")
- Requires maintaining parallel materials
- Lower industry recognition (vs ADRs, copilot-instructions)

### When to Use

✅ **Use 5-mode pedagogy when:**
- Teaching absolute beginners to AI-assisted development
- Audience prefers numbered frameworks
- Workshop focuses on "workflow as documentation"
- Team culture values explicit sequential processes

❌ **Use main presentations when:**
- Teaching professional developers
- Want industry-transferable terminology
- Emphasizing ADRs and configuration standards
- Career development is a learning objective

---

## Maintenance Strategy

**Priority:** Main presentations (`presentations/`) are actively maintained.

**Alternatives:** Updated when significant demo repo changes occur, but lower priority.

**Philosophy:** Alternatives are "archived but usable" rather than "actively maintained in parallel."

---

## Contributing Alternative Pedagogies

If you develop alternative teaching approaches:

1. Create new directory: `alternatives/your-approach-name/`
2. Include complete session materials (SESSION-1, SESSION-2)
3. Document pedagogy, audience, and tradeoffs in this README
4. Reference same demo repo: [spring-migration-demo](https://github.com/josephrobertlopez/spring-migration-demo)

**Keep:**
- Same 180-minute format (2 × 90-minute sessions)
- Same learning objectives (Spring Boot 2→3 migration)
- Same hands-on focus (60 min per session)

**Vary:**
- Terminology and metaphors
- Progression structure
- Target audience level
