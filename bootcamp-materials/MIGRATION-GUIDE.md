# Migration Guide: Terminology Updates (November 2025)

**What changed:** Bootcamp materials updated to align with industry-standard prompt engineering terminology and research-backed practices.

**Why:** Research (White et al. 2023, Yao et al. 2022/2023) shows established patterns with proven track records. Original terminology was non-standard and could confuse practitioners.

**Impact:** Content is stronger, grounded in authoritative sources, and maps clearly to production practices.

---

## Terminology Changes

### Core Concept Reframing

| Old Term | New Term | Industry Grounding |
|----------|----------|-------------------|
| "5 Modes" | "5-File Workflow Example" | One practical application, not the only approach |
| "Mode 1: Constitution" | "File 1: System Prompt" | Maps to .cursorrules, Persona Pattern (White et al.) |
| "Mode 2: Specification" | "File 2: Task Specification" | Template Pattern (White et al.) |
| "Mode 3: Planning" | "File 3: Execution Plan" | ReAct Pattern (Yao et al. 2022) |
| "Mode 4: ABCD" | "File 4: Decision Documentation" | Tree of Thoughts (Yao et al. 2023) |
| "Mode 5: Implementation" | "File 5: Code Generation" | Meta-prompting (orchestration) |

### Pattern Names

| Old (Non-Standard) | New (Industry Standard) | Source |
|-------------------|------------------------|--------|
| "Constitution Pattern" | Persona + Few-shot Pattern | White et al. (2023) |
| "Specification Pattern" | Template Pattern | White et al. (2023) |
| "Planning Pattern" | ReAct (Reason + Act) | Yao et al. (2022) |
| "ABCD Pattern" | Tree of Thoughts | Yao et al. (2023) |
| "5-Mode Workflow" | Structured File Workflow (one option) | Multiple valid approaches |

---

## Framework Changes

### Old Framework: Implied Single Approach
```
The 5 Modes are the way to structure AI prompts
Mode 1 → Mode 2 → Mode 3 → Mode 4 → Mode 5
This is how to do prompt engineering
```

### New Framework: Industry Context + Options
```
Tier 1: Proven Patterns (10+ years)
- ADRs, RFCs, Few-shot, Chain-of-Thought, Persona, Template

Tier 2: Emerging Standards (1-3 years)
- .cursorrules, .github/copilot-instructions.md

Tier 3: Experimental (months to 1-2 years)
- GitHub Spec-Kit, structured file workflows

Multiple valid approaches:
A) ADRs + Config Files (recommended for most teams)
B) Structured Files (today's example, good for learning)
C) Tool-Assisted (Spec-Kit, Copilot Workspace)
```

---

## File Mapping Changes

### Session Guides

| Old File | New File | Key Changes |
|----------|----------|-------------|
| SESSION-1-prompt-files.md | SESSION-1-industry-standards.md | Teaches standards first, shows example second |
| SESSION-2-workflows.md | SESSION-2-advanced-patterns.md | Grounded in ReAct/Tree of Thoughts research |

### Workflow Example Files (06-SPRING-WORKFLOW/)

| Old Naming | New Naming | Pattern Mapping Added |
|------------|------------|----------------------|
| file-0-constitution.md | file-1-system-prompt.md | → Persona + Few-shot (White et al.) |
| file-1-specification.md | file-2-task-spec.md | → Template Pattern (White et al.) |
| file-2-planning.md | file-3-react-plan.md | → ReAct Pattern (Yao et al. 2022) |
| file-3-abcd.md | file-4-tree-decisions.md | → Tree of Thoughts (Yao et al. 2023) |
| file-4-implementation.md | file-5-synthesize.md | → Meta-prompting (orchestration) |

**Note:** Old file-0-constitution.md kept for backwards compatibility, but new materials use file-1-system-prompt.md

### PowerPoint Slides

| Old Slide Deck | New Slide Deck | Key Changes |
|----------------|----------------|-------------|
| SESSION-1-Prompt-Files.pptx | SESSION-1-Industry-Standards.pptx | 3-tier framework, ADRs prominent |
| SESSION-2-Workflows.pptx | SESSION-2-Advanced-Patterns.pptx | ReAct/Tree of Thoughts patterns |

---

## Content Changes

### Added Throughout Materials

✅ **3-Tier Maturity Framework**
- Tier 1: 10+ years (ADRs, RFCs, foundational patterns)
- Tier 2: 1-3 years (.cursorrules, Copilot instructions)
- Tier 3: Months to 1-2 years (Spec-Kit, experimental tools)

✅ **Alternative Approaches**
- ADRs + .cursorrules presented as simpler and equally valid
- Multiple workflow strategies compared side-by-side
- Clear guidance on when to use which approach

✅ **Research Citations**
- White et al. (2023): Prompt pattern catalog
- Yao et al. (2022): ReAct pattern
- Yao et al. (2023): Tree of Thoughts
- Brown et al. (2020): Few-shot prompting

✅ **Production Mapping**
- Workshop files map to real-world tools (.cursorrules, GitHub issues, ADRs)
- Explicit "Alternative Formats" sections in each file
- Comparison tables showing options

✅ **Spec-Kit Context**
- Released September 2024 (~14 months old as of Nov 2025)
- Labeled as "experimental, growing understanding, not yet proven at scale"
- Positioned as interesting experiment, not required standard

### Removed from Materials

❌ "5 Modes is THE way" - Now presented as ONE example
❌ Implied maturity for experimental tools - Now properly tiered
❌ Non-standard pattern names - Now use research-backed terms

---

## Migration Path for Existing Users

### If You Already Use the Old "5 Modes" Approach

**Good news:** The underlying patterns and structure remain solid. Only terminology changed.

**Update your files:**
1. Rename "Constitution" → "System Prompt" in docs/comments
2. Rename "Specification" → "Task Specification"
3. Rename "Planning" → "Execution Plan" or "ReAct Plan"
4. Rename "ABCD" → "Decision Documentation" or "Tree of Thoughts"
5. Rename "Implementation" → "Code Generation" or "Synthesis"

**Consider simplifying:**
- For simple tasks: Switch to ADR + simple prompt
- For team workflows: Adopt .cursorrules + Copilot instructions
- For complex tasks: Keep structured files but acknowledge alternatives

### If You're Starting Fresh

**Recommended path:**
1. **Session 1:** Learn industry standards (ADRs, .cursorrules, foundational patterns)
2. **Session 2:** Learn advanced patterns (ReAct, Tree of Thoughts)
3. **Apply:** Choose approach that fits your team:
   - Simple: ADRs + .cursorrules
   - Learning: Structured 5-file workflow
   - Tool-native: Copilot Workspace, Spec-Kit

### If You Teach This Material

**Key messaging changes:**
- Teach patterns FIRST (Few-shot, Chain-of-Thought, ReAct, Tree of Thoughts)
- Show 5-file workflow as practical APPLICATION of patterns
- Present ADRs as equally valid (often simpler) alternative
- Use 3-tier framework to set expectations about maturity
- Cite authoritative sources (White et al., Yao et al., GitHub docs)

---

## Backwards Compatibility

### Old Files Still Work

All old file names and content still valid for learning purposes:
- `file-0-constitution.md` demonstrates same concepts as `file-1-system-prompt.md`
- Old "MODE 1" headings still convey same structure
- Patterns applied are identical, only names changed

### Gradual Migration Recommended

No need to update everything at once:
1. Use new terminology for new materials
2. Update old materials as you touch them
3. Keep old files for reference during transition
4. Point users to this migration guide

### Cross-References Maintained

Workshop materials include both old and new terminology during transition:
- "(Previously called MODE 1: CONSTITUTION)"
- "This maps to .cursorrules (industry standard)"
- "Alternative: Write as ADR instead"

---

## Resources

### Research Papers (Authoritative Sources)

**Prompt Engineering Foundations:**
- White et al. (2023): "A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT" - arXiv 2302.11382
- Brown et al. (2020): "Language Models are Few-Shot Learners" (GPT-3 paper)
- Wei et al. (2022): "Chain-of-Thought Prompting Elicits Reasoning"

**Advanced Patterns:**
- Yao et al. (2022): "ReAct: Synergizing Reasoning and Acting in Language Models"
- Yao et al. (2023): "Tree of Thoughts: Deliberate Problem Solving with Large Language Models"
- Wang et al. (2022): "Self-Consistency Improves Chain of Thought Reasoning"

### Industry Standards

**Configuration Management:**
- GitHub Copilot Official Docs: https://docs.github.com/copilot/customizing-copilot
- awesome-cursorrules: https://github.com/PatrickJS/awesome-cursorrules (3,000+ forks)
- VS Code Copilot Customization: https://code.visualstudio.com/docs/copilot

**Decision Documentation:**
- ADR GitHub Organization: https://github.com/adr
- Michael Nygard's ADR blog post (2011 - original)
- Rust Language RFCs: https://github.com/rust-lang/rfcs

**Experimental Tools:**
- GitHub Spec-Kit: https://github.com/github/spec-kit (Sept 2024 release)
- Martin Fowler's Analysis: "Exploring Gen AI: Spec-Driven Development"

---

## Questions?

**Q: Are the old materials wrong?**
A: No! The underlying patterns and structure were sound. Only the terminology was non-standard. Content is now stronger with research grounding.

**Q: Do I need to rewrite everything I've done?**
A: No. Old approach still works. Update terminology gradually as convenient.

**Q: Is the 5-file workflow still valid?**
A: Yes! It's a solid application of proven patterns. Now positioned as ONE option alongside ADRs and other approaches.

**Q: Should I use ADRs or structured files?**
A: For most teams: Start with ADRs + .cursorrules (simpler, proven). Use structured files for complex tasks or when learning patterns.

**Q: What about Spec-Kit?**
A: Interesting experimental tool (Sept 2024). Growing understanding, not yet proven at scale. Fine for experimentation, not required.

---

## Summary

**What didn't change:**
- ✅ Core patterns remain solid (Persona, Few-shot, Template, Task Decomposition)
- ✅ Workflow structure still effective
- ✅ Spring migration example still excellent
- ✅ Hands-on exercises remain valuable

**What improved:**
- ✅ Terminology now matches industry standards
- ✅ Grounded in research (White et al., Yao et al.)
- ✅ Multiple approaches presented (not just one way)
- ✅ Proper maturity context (Tier 1/2/3)
- ✅ Maps to production practices (ADRs, .cursorrules)

**Net result:** Materials are now stronger, more credible, and more practical for real-world application.

---

**Last Updated:** November 2025
**Research Source:** prompt-engineering-workshop-research.md
**Questions:** See updated session guides for detailed explanations
