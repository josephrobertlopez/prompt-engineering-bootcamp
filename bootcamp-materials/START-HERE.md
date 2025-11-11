# START HERE - Prompt Engineering Workshop

**Updated:** November 2025
**Duration:** 2 sessions × 90 minutes = 180 minutes total
**Target:** Jr/Mid Software Developers
**Grounded In:** Industry-standard patterns (White et al. 2023, Yao et al. 2022/2023)

---

## 🎯 What You'll Learn

### Session 1: Industry Standards & Practical Application (90 min)
✅ **Tier 1/2/3 maturity framework** - Evaluate tools/patterns by maturity level
✅ **Foundational patterns** - Few-shot, Chain-of-Thought, Persona, Template (White et al. 2023)
✅ **Configuration standards** - .cursorrules, .github/copilot-instructions.md
✅ **Decision documentation** - ADRs (industry standard since 2011)
✅ **Practical application** - 5-file workflow example using Spring Boot migration

### Session 2: Advanced Patterns & Workflows (90 min)
✅ **Advanced patterns** - ReAct (Yao et al. 2022), Tree of Thoughts (Yao et al. 2023)
✅ **Workflow orchestration** - Combining multiple patterns for complex tasks
✅ **Approach comparison** - ADR-driven vs file-based vs tool-assisted
✅ **Complete example** - End-to-end Spring migration with pattern orchestration

**Key Insight:** This workshop teaches patterns FIRST, then shows ONE practical application. ADRs + .cursorrules is simpler and equally valid for most teams.

---

## 🚀 Quick Navigation

### "I want to understand the approach" → [README.md](README.md)
- Workshop philosophy
- 3-tier maturity framework
- Multiple valid approaches
- Research backing

### "I'm ready to start Session 1" → [SESSION-1-industry-standards.md](02-SESSION-GUIDES/SESSION-1-industry-standards.md)
- 15 min presentation (industry standards overview)
- 60 min hands-on (apply patterns to Spring migration)
- 15 min review (compare alternatives)

### "I'm ready for Session 2" → [SESSION-2-advanced-patterns.md](02-SESSION-GUIDES/SESSION-2-advanced-patterns.md)
- 15 min presentation (ReAct, Tree of Thoughts)
- 60 min hands-on (orchestrate patterns)
- 15 min review (map to production practices)

### "I need templates NOW" → [templates/prompts/](templates/prompts/)
- System prompt template
- Task specification template
- ReAct plan template
- Decision documentation template
- Code generation template

### "What changed from old materials?" → [MIGRATION-GUIDE.md](MIGRATION-GUIDE.md)
- Terminology updates (non-standard → research-backed)
- Old "5 Modes" → New "5-File Workflow Example"
- Added 3-tier framework and alternative approaches

---

## 🟢🟡🟠 Understanding Maturity Tiers

**Why this matters:** Not all tools/patterns have equal track records.

### 🟢 Tier 1: Proven (10+ years, production-ready)
**Patterns:** Few-shot, Chain-of-Thought, Persona, Template
**Practices:** ADRs, RFC Process
**Used by:** Microsoft, AWS, Google, Spotify, Netflix
**Your action:** Adopt without hesitation

### 🟡 Tier 2: Emerging (1-3 years, growing adoption)
**Tools:** .cursorrules, .github/copilot-instructions.md
**Evidence:** 3,000+ forks of awesome-cursorrules
**Status:** Official Microsoft/GitHub standard for Copilot
**Your action:** Adopt with monitoring

### 🟠 Tier 3: Experimental (months to 1-2 years)
**Tools:** GitHub Spec-Kit (Sept 2024, ~14 months old)
**Status:** Interesting experiment, growing understanding
**Concerns:** Not yet proven at scale (Martin Fowler analysis)
**Your action:** Experiment cautiously, don't bet critical work

**This workshop:** Teaches Tier 1 patterns, shows Tier 2 tools, demonstrates Tier 3 application.

---

## 📚 Three Valid Approaches (Choose What Fits)

### Option A: ADRs + Config Files ⭐ (Recommended for most teams)

**What:** Lightweight decision docs + team config files
**Files:** `docs/adr/0001-standards.md` + `.cursorrules`
**When:** Production teams, established workflows
**Effort:** Low (simple markdown)
**Maturity:** Tier 1 (10+ years proven)

**Example workflow:**
```
1. Write ADR documenting decision
2. Add rules to .cursorrules
3. Use AI with "follow ADR 0001"
4. Validate against ADR success criteria
```

---

### Option B: Structured Files 📚 (This workshop's example)

**What:** 5-file workflow explicitly mapping to patterns
**Files:** system-prompt.md, task-spec.md, react-plan.md, tree-decisions.md, synthesize.md
**When:** Complex tasks, learning patterns, need auditability
**Effort:** Medium (more files, more explicit)
**Maturity:** Tier 3 (experimental approach)

**Example workflow:**
```
1. System prompt (Persona + Few-shot)
2. Task spec (Template pattern)
3. Execution plan (ReAct - optional)
4. Decisions (Tree of Thoughts - optional)
5. Generate (Meta-prompting orchestration)
```

---

### Option C: Tool-Assisted 🔧 (Platform-specific)

**What:** Built-in workflow tools
**Tools:** Spec-Kit, GitHub Copilot Workspace, Cursor Composer
**When:** Team committed to specific IDE/platform
**Effort:** Low (built into tool)
**Maturity:** Varies (Tier 2-3 depending on tool)

**Example workflow:**
```
Spec-Kit: constitution → specify → plan → tasks → implement
Copilot Workspace: task list → plan → review
Cursor Composer: multi-file context → generation
```

---

**Key Insight:** All three apply the same underlying patterns. Format differs, principles stay constant.

---

## 🎓 Recommended Learning Path

### Day 1: Session 1 (90 minutes)
**Goal:** Understand industry standards, apply through one example

1. **Presentation (15 min)** - 3-tier framework, foundational patterns
2. **Hands-on (60 min)** - Create system prompt, task spec, optional planning/decisions
3. **Review (15 min)** - Compare to ADRs, discuss when to use which approach

**Outcome:** Can explain Tier 1/2/3 framework, apply foundational patterns

---

### Day 2: Session 2 (90 minutes)
**Goal:** Learn advanced patterns, orchestrate complete workflow

1. **Presentation (15 min)** - ReAct, Tree of Thoughts, workflow strategies
2. **Hands-on (60 min)** - Create ReAct plan, Tree decisions, synthesize patterns
3. **Review (15 min)** - Map to production practices, choose team approach

**Outcome:** Can orchestrate multiple patterns, choose appropriate workflow

---

### Week 1: Apply to Real Work
**Goal:** Use patterns on actual tasks

- Try ADR + simple prompt for straightforward tasks
- Use structured files for one complex task
- Measure time saved
- Share wins with team

**Outcome:** Confidence with patterns, measurable impact

---

### Month 1: Establish Team Standards
**Goal:** Standardize approach for your team

- Choose primary workflow (ADR? Files? Tool?)
- Create .cursorrules or equivalent
- Build template library
- Track cumulative time saved

**Outcome:** Team using consistent patterns, templates reusable

---

## 📊 What Success Looks Like

### After Session 1:
✅ Can explain 3-tier maturity framework
✅ Know when to use ADRs vs structured files
✅ Created working system prompt + task spec
✅ Understand foundational patterns (Few-shot, Chain-of-Thought, Persona, Template)

### After Session 2:
✅ Can apply ReAct pattern for phased execution
✅ Can use Tree of Thoughts for decision exploration
✅ Orchestrated complete workflow end-to-end
✅ Mapped workshop files to production practices

### After Week 1:
✅ Used patterns on 2-3 real tasks
✅ Saved 2-4 hours cumulatively
✅ One "aha moment" with immediate impact

### After Month 1:
✅ Team has chosen standard approach
✅ .cursorrules or equivalent in place
✅ 5+ templates in team library
✅ Measurable ROI for performance reviews

---

## 🔗 Key Resources

### Workshop Materials
- [README.md](README.md) - Complete overview, philosophy, research backing
- [SESSION-1-industry-standards.md](02-SESSION-GUIDES/SESSION-1-industry-standards.md) - Session 1 guide
- [SESSION-2-advanced-patterns.md](02-SESSION-GUIDES/SESSION-2-advanced-patterns.md) - Session 2 guide
- [06-SPRING-WORKFLOW/](06-SPRING-WORKFLOW/) - Complete working example
- [templates/prompts/](templates/prompts/) - Reusable templates

### Research Backing
- [00-RESEARCH/prompt-engineering-workshop-research.md](00-RESEARCH/prompt-engineering-workshop-research.md) - Comprehensive industry research
- White et al. (2023): "A Prompt Pattern Catalog" - arXiv 2302.11382
- Yao et al. (2022): "ReAct: Synergizing Reasoning and Acting"
- Yao et al. (2023): "Tree of Thoughts: Deliberate Problem Solving"

### Industry Standards
- ADR GitHub Organization: https://github.com/adr
- awesome-cursorrules: https://github.com/PatrickJS/awesome-cursorrules
- GitHub Copilot Docs: https://docs.github.com/copilot/customizing-copilot

---

## 💡 Key Insights

### Pattern > Format
**The prompt engineering patterns matter. The file format doesn't.**

You can apply Few-shot, Chain-of-Thought, ReAct, Tree of Thoughts through:
- ADRs + simple prompts
- Structured 5-file workflow
- IDE-native tools
- Custom team format

Choose format based on team maturity and task complexity.

---

### Start Simple, Add Structure When Needed
**Don't over-engineer simple tasks.**

- Simple task → ADR + prompt
- Complex task → Structured files
- Team workflow → Config files + standards

The workshop shows maximum structure for learning. Production uses minimum necessary.

---

### Multiple Valid Approaches
**There is no "one true way."**

ADRs are proven (Tier 1). Structured files are experimental (Tier 3). Both are valid.

The workshop teaches patterns through one example, not prescribing the only approach.

---

## ❓ Common Questions

**Q: Is this the only way to structure prompts?**
A: No! ADRs + .cursorrules is simpler and often better. This workshop demonstrates patterns through one structured example.

**Q: Do I need all 5 files every time?**
A: No. For simple tasks, just system prompt + simple "generate" request. Use full structure for complex work.

**Q: Should I use ADRs or structured files?**
A: For most teams: Start with ADRs + .cursorrules (simpler, proven). Use structured files for learning or complex tasks.

**Q: What about Spec-Kit?**
A: Interesting experimental tool (Sept 2024, ~14 months old). Growing understanding, not yet proven at scale. Fine for experimentation.

**Q: How do I convince my team to adopt this?**
A: Start with one person (you), one task, measure time saved. Share win. Repeat. Let results drive adoption.

---

## 🚦 Ready to Start?

### If you have 5 minutes:
Read the [3-tier framework](#-understanding-maturity-tiers) section above

### If you have 30 minutes:
Read [README.md](README.md) to understand workshop philosophy

### If you have 90 minutes:
Start [Session 1](02-SESSION-GUIDES/SESSION-1-industry-standards.md) right now

### If you have 3 hours:
Complete both sessions back-to-back, apply to real work immediately

---

## 📞 Need Help?

**Understanding terms:** → [GLOSSARY.md](01-OVERVIEW/GLOSSARY.md)
**Choosing approaches:** → Comparison tables in session guides
**Migration questions:** → [MIGRATION-GUIDE.md](MIGRATION-GUIDE.md)
**Quick reference:** → [QUICK-REFERENCE-CARD.md](03-REFERENCE/QUICK-REFERENCE-CARD.md)

---

**Next Step:** Open [SESSION-1-industry-standards.md](02-SESSION-GUIDES/SESSION-1-industry-standards.md) and begin!

---

**Last Updated:** November 2025
**Research Backing:** White et al. (2023), Yao et al. (2022/2023)
**Workshop Duration:** 180 minutes (2 × 90-minute sessions)
**Status:** Ready for delivery
