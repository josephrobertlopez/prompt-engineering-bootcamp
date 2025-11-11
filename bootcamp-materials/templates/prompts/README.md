# Structured Prompt Workflow Templates

**Industry Context:** These templates demonstrate ONE way to structure AI interactions using proven prompt engineering patterns. ADRs + `.cursorrules` is simpler and equally valid.

**Patterns Applied:**
- Persona Pattern (file-1)
- Template Pattern (file-2)
- ReAct Pattern (file-3)
- Tree of Thoughts (file-4)
- Meta-prompting (file-5)

**Grounded In:** White et al. (2023) prompt patterns, Yao et al. (2022/2023) advanced patterns

---

## When to Use This Approach

✅ **Use structured files when:**
- Task is complex (multiple dependencies, decisions)
- Learning prompt engineering patterns
- Need audit trail of reasoning
- Multiple team members need to understand approach

❌ **Skip structured files when:**
- Simple task (single file, obvious approach)
- Team has good ADRs and `.cursorrules` already
- Developer judgment is sufficient

**Rule of thumb:** Start with ADR + simple prompt. Add structure only if complexity demands it.

---

## Usage

1. Copy relevant files to your project (not all 5 required!)
2. Fill in templates with your specific context
3. Load files into AI tool in order
4. AI generates solutions with full context

**Minimum viable:** Just file-1 (system prompt) + file-5 (generation)
**Full workflow:** All 5 files for complex tasks

---

## Files & Pattern Mapping

### file-1-system-prompt.md - Reusable Rules
**Patterns:** Persona + Few-shot
**Maps to:** `.cursorrules`, `.github/copilot-instructions.md`
**Alternative:** ADR documenting project standards
**Reusability:** 100% reusable across project
**When to skip:** Never (always need basic rules)

### file-2-task-spec.md - What to Build
**Patterns:** Template Pattern (structured checklist)
**Maps to:** GitHub issue, Jira ticket, ADR requirements section
**Alternative:** Inline comments, ticket acceptance criteria
**Reusability:** Template reusable, customize per component
**When to skip:** Obvious requirements, well-understood task

### file-3-react-plan.md - How to Build It (Optional)
**Patterns:** ReAct (THINK → ACT → OBSERVE)
**Maps to:** Migration runbook, ADR implementation notes
**Alternative:** Developer judgment, brief implementation notes
**Reusability:** Reusable for similar components
**When to skip:** Simple tasks, obvious execution order

### file-4-tree-decisions.md - Explore Alternatives (Optional)
**Patterns:** Tree of Thoughts (branch exploration)
**Maps to:** ADR "Alternatives Considered" section
**Alternative:** Write as proper ADR instead
**Reusability:** Decision-specific, not reusable
**When to skip:** No real decisions, only one approach

### file-5-synthesize.md - Generate Solution
**Patterns:** Meta-prompting (orchestrates all patterns)
**Maps to:** Inline code comments, PR description
**Alternative:** Simple "generate following ADR" prompt
**Reusability:** Template constant, references others
**When to skip:** Never (this triggers generation)

---

## Comparison to Industry Practices

| This Workflow | Industry Standard | When to Use Which |
|---------------|-------------------|-------------------|
| file-1-system-prompt.md | .cursorrules, Copilot instructions | Structured files: learning; Config files: production |
| file-2-task-spec.md | GitHub issue, Jira ticket | Structured files: complex; Tickets: simple |
| file-3-react-plan.md | ADR implementation notes | Structured files: multi-phase; ADR: brief notes |
| file-4-tree-decisions.md | ADR alternatives section | Structured files: AI consumption; ADR: team docs |
| file-5-synthesize.md | Simple prompt + ADR reference | Structured files: complex; Simple: straightforward |

**Key Insight:** These files TEACH the patterns. Once learned, you can apply patterns through simpler formats (ADRs, config files, prompts).

---

## Reusability Matrix

| File | Reusability | Customize Frequency |
|------|-------------|---------------------|
| file-1 | 100% across project | Once per project |
| file-2 | Template reusable | Per component/file |
| file-3 | For similar tasks | When execution is complex |
| file-4 | Decision-specific | When alternatives exist |
| file-5 | Template constant | Every generation (references others) |

---

## Alternative Approaches

**Option A: ADRs + Config Files** (Recommended for most teams)
```
.cursorrules (system prompt equivalent)
docs/adr/0001-standards.md (decisions)
Simple prompt: "Migrate this following ADR"
```

**Option B: IDE-Native**
```
.cursorrules or Copilot instructions
Inline comments referencing standards
Use IDE suggestions
```

**Option C: Structured Files** (This template set)
```
Explicit pattern application
Good for learning and complex tasks
```

**Choose based on team maturity and task complexity.**

---

## References

**Prompt Engineering Patterns:**
- White et al. (2023): "A Prompt Pattern Catalog" (arXiv 2302.11382)
- Yao et al. (2022): "ReAct: Synergizing Reasoning and Acting"
- Yao et al. (2023): "Tree of Thoughts"

**Industry Standards:**
- ADRs: https://github.com/adr
- Configuration: awesome-cursorrules, GitHub Copilot docs

**When in doubt:** Start simple (ADRs + config), add structure only if needed.
