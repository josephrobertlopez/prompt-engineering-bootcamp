# Prompt Engineering Workshop - Industry Standards & Patterns

**Research-Backed Training** | Nov 2025 | 180 minutes total

Ground your prompt engineering in industry standards. This workshop teaches proven patterns (White et al. 2023, Yao et al. 2022/2023), not made-up terminology.

---

## 🎯 What This Is

**Workshop teaching:** Foundational patterns → Advanced patterns → Practical application

**NOT:** "The one true way" or proprietary methodology

**Based on:**
- White et al. (2023): "A Prompt Pattern Catalog" (arXiv 2302.11382)
- Yao et al. (2022): "ReAct: Synergizing Reasoning and Acting"
- Yao et al. (2023): "Tree of Thoughts"
- Industry standards: ADRs (2011+), .cursorrules, GitHub Copilot docs

---

## 📁 Files in This Gist

1. **00-README.md** (this file) - Overview and navigation
2. **01-tier-framework.md** - 3-tier maturity framework for evaluating tools
3. **02-foundational-patterns.md** - Few-shot, Chain-of-Thought, Persona, Template
4. **03-advanced-patterns.md** - ReAct, Tree of Thoughts, Meta-prompting
5. **04-three-approaches.md** - ADRs vs Structured Files vs Tool-Assisted
6. **05-spring-example.md** - Complete working example (Spring Boot migration)
7. **06-quick-reference.md** - Cheat sheet for daily use

---

## 🟢🟡🟠 Core Concept: Maturity Tiers

**Not all patterns/tools have equal track records.**

### 🟢 Tier 1: Proven (10+ years)
- Few-shot, Chain-of-Thought, Persona, Template patterns
- ADRs, RFC Process
- Used by: Microsoft, AWS, Google, Spotify, Netflix
- **Your action:** Adopt without hesitation

### 🟡 Tier 2: Emerging (1-3 years)
- .cursorrules (3,000+ forks)
- .github/copilot-instructions.md (official Microsoft standard)
- **Your action:** Adopt with monitoring

### 🟠 Tier 3: Experimental (months to 1-2 years)
- GitHub Spec-Kit (Sept 2024, ~14 months old)
- Structured file workflows
- **Your action:** Experiment cautiously

**See:** `01-tier-framework.md` for full details

---

## 🎓 Two Learning Paths

### Path A: Quick Start (30 min)
1. Read `02-foundational-patterns.md` (10 min)
2. Review `06-quick-reference.md` (5 min)
3. Try one pattern on real work (15 min)

### Path B: Complete Workshop (3 hours)
1. Session 1 (90 min): Foundational patterns + application
2. Session 2 (90 min): Advanced patterns + orchestration
3. Apply to real work (60 min)

---

## 🚀 Three Valid Approaches

**Choose based on team maturity and task complexity:**

### Option A: ADRs + Config Files ⭐ (Recommended)
- **Maturity:** Tier 1 (10+ years proven)
- **When:** Production teams, straightforward tasks
- **Files:** `docs/adr/0001.md` + `.cursorrules`

### Option B: Structured Files 📚 (This workshop's example)
- **Maturity:** Tier 3 (experimental)
- **When:** Complex tasks, learning, auditability
- **Files:** system-prompt.md, task-spec.md, react-plan.md, tree-decisions.md, synthesize.md

### Option C: Tool-Assisted 🔧 (Platform-specific)
- **Maturity:** Varies (Tier 2-3)
- **When:** Team committed to specific IDE
- **Tools:** Spec-Kit, Copilot Workspace, Cursor Composer

**See:** `04-three-approaches.md` for detailed comparison

---

## 📚 Pattern Reference

### Foundational (Tier 1)
- **Persona Pattern:** Assign AI a role/identity
- **Few-shot Pattern:** Provide example transformations
- **Template Pattern:** Structured output format
- **Chain-of-Thought:** Show reasoning steps

**See:** `02-foundational-patterns.md`

### Advanced (Research-backed)
- **ReAct (Yao 2022):** THINK → ACT → OBSERVE cycles
- **Tree of Thoughts (Yao 2023):** Branch exploration for decisions
- **Meta-prompting:** Orchestrate multiple patterns

**See:** `03-advanced-patterns.md`

---

## 💡 Key Insights

### Pattern > Format
The prompt engineering patterns matter. The file format doesn't.

Apply Few-shot, Chain-of-Thought, ReAct through:
- ADRs + simple prompts (simpler)
- Structured files (explicit)
- IDE tools (built-in)
- Custom format (team-specific)

### Start Simple
Don't over-engineer:
- Simple task → ADR + prompt
- Complex task → Structured files
- Team workflow → Config files

### Multiple Valid Approaches
ADRs are proven (Tier 1). Structured files are experimental (Tier 3). **Both are valid.**

---

## 🔗 Full Workshop Materials

This gist is a quick reference. Full materials include:
- Complete session guides (15+60+15 format)
- PowerPoint slides
- Templates
- Spring Boot migration example
- Comprehensive research document

**Repository:** github.com/josephrobertlopez/spring-migration-demo

---

## 📊 Quick Comparison

| Approach | Maturity | Effort | Best For |
|----------|----------|--------|----------|
| ADRs + Config | 🟢 Tier 1 | Low | Most teams |
| Structured Files | 🟠 Tier 3 | Medium | Learning, complex tasks |
| Tool-Assisted | 🟡🟠 Tier 2-3 | Low | IDE-committed teams |

---

## 🎯 Next Steps

**If you have 5 minutes:**
- Read `01-tier-framework.md`
- Understand how to evaluate tools/patterns

**If you have 30 minutes:**
- Read `02-foundational-patterns.md`
- Read `06-quick-reference.md`
- Try one pattern on real work

**If you have 3 hours:**
- Complete workshop (Session 1 + Session 2)
- Apply to real project
- Measure time saved

---

## 📞 Questions?

**Q: Is this the only way?**
A: No! ADRs + .cursorrules is simpler and often better. This teaches patterns through one example.

**Q: Do I need all the files?**
A: No. Start with ADR + simple prompt. Add structure only when complexity demands it.

**Q: What about Spec-Kit?**
A: Experimental (Sept 2024, 14 months old). Growing understanding, not yet proven at scale.

**Q: How do I convince my team?**
A: Start solo. Measure time saved. Share win. Repeat. Let results drive adoption.

---

## 🏆 Credits

**Workshop Author:** Joseph Lopez
**Research Backing:**
- White et al. (2023): "A Prompt Pattern Catalog"
- Yao et al. (2022): "ReAct: Synergizing Reasoning and Acting"
- Yao et al. (2023): "Tree of Thoughts: Deliberate Problem Solving"

**Industry Standards:**
- ADR GitHub Organization: github.com/adr
- awesome-cursorrules: github.com/PatrickJS/awesome-cursorrules
- GitHub Copilot: docs.github.com/copilot

---

**Last Updated:** November 2025
**Status:** Production-ready
**License:** MIT

**Start here:** `06-quick-reference.md` for immediate use
**Deep dive:** Full workshop materials in repository
