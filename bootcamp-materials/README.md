# Prompt Engineering Workshop Materials

**Practical Training**: 2-Session Workshop (180 minutes total)
**Target Audience**: Jr/Mid Software Developers
**Last Updated**: 2025-11-11

**Grounded In**: Industry-standard prompt engineering patterns (White et al. 2023, Yao et al. 2022/2023)

---

## 🚀 Quick Start

**New here?** Start with [START-HERE.md](START-HERE.md) or [WORKSHOP-OVERVIEW.md](01-OVERVIEW/WORKSHOP-OVERVIEW.md)

**Session 1 (90 min):** [Industry Standards & Practical Application](02-SESSION-GUIDES/SESSION-1-industry-standards.md)
- Learn industry-standard patterns: Few-shot, Chain-of-Thought, Persona, Template
- Explore configuration standards: .cursorrules, .github/copilot-instructions.md
- Compare decision documentation: ADRs vs structured prompts
- Apply patterns through practical 5-file workflow example

**Session 2 (90 min):** [Advanced Patterns & Workflows](02-SESSION-GUIDES/SESSION-2-advanced-patterns.md)
- Learn advanced patterns: ReAct (Reason + Act), Tree of Thoughts
- Orchestrate multiple patterns for complex tasks
- Compare workflow strategies: ADR-driven, file-based, tool-assisted
- Execute complete end-to-end migration example

**Updated materials?** See [MIGRATION-GUIDE.md](MIGRATION-GUIDE.md) for terminology changes

---

## 📁 Repository Structure

### Primary Materials

- **[02-SESSION-GUIDES/](02-SESSION-GUIDES/)** - Workshop session content (START HERE)
  - SESSION-1-industry-standards.md (teaches patterns first)
  - SESSION-2-advanced-patterns.md (advanced orchestration)
  - PowerPoint slides for presentations

- **[06-SPRING-WORKFLOW/](06-SPRING-WORKFLOW/)** - Complete working example
  - file-1-system-prompt.md (Persona + Few-shot patterns)
  - file-2-task-spec.md (Template pattern)
  - file-3-react-plan.md (ReAct pattern - optional)
  - file-4-tree-decisions.md (Tree of Thoughts - optional)
  - file-5-synthesize.md (Meta-prompting orchestration)

### Supporting Materials

- **[00-RESEARCH/](00-RESEARCH/)** - Research backing workshop content
  - prompt-engineering-workshop-research.md (comprehensive industry research)

- **[01-OVERVIEW/](01-OVERVIEW/)** - Workshop orientation
  - WORKSHOP-OVERVIEW.md (format, prerequisites, outcomes)
  - GLOSSARY.md (terminology and maturity tiers)

- **[03-REFERENCE/](03-REFERENCE/)** - Quick references
  - QUICK-REFERENCE-CARD.md (cheat sheet)
  - templates-quick-reference.md (pattern comparison)

- **[04-MODES/](04-MODES/)** - Pattern deep dives
  - Individual pattern explanations and examples

- **[05-TEMPLATES/](05-TEMPLATES/)** - Reusable templates
  - Copy-paste ready prompt templates
  - README with usage guidance

- **[07-CONFIG-EXAMPLES/](07-CONFIG-EXAMPLES/)** - Tool configuration
  - .cursorrules examples
  - .github/copilot-instructions.md examples

---

## 🟢🟡🟠 Maturity Framework

Materials use a 3-tier framework to set expectations:

**🟢 Tier 1: Proven Patterns (10+ years, production-ready)**
- Architecture Decision Records (ADRs)
- RFC Process
- Few-shot, Chain-of-Thought, Persona, Template patterns
- Examples: Used by Microsoft, AWS, Google, Spotify, Netflix

**🟡 Tier 2: Emerging Standards (1-3 years, growing adoption)**
- .cursorrules (3,000+ forks of awesome-cursorrules)
- .github/copilot-instructions.md (official Microsoft/GitHub standard)
- Configuration management patterns

**🟠 Tier 3: Experimental (months to 1-2 years, unproven at scale)**
- GitHub Spec-Kit (released Sept 2024, ~14 months old)
- AI-assisted spec-as-source tools
- Structured file workflows (this workshop's example)

**Key Insight:** Workshop teaches Tier 1 patterns, shows Tier 2 tools, demonstrates Tier 3 application. Choose what fits your team's maturity and risk tolerance.

See [GLOSSARY.md](01-OVERVIEW/GLOSSARY.md) for complete definitions.

---

## 🎯 Workshop Philosophy

### Teach Patterns First, Show Application Second

**Session 1:** Industry-standard patterns (Persona, Few-shot, Template, Chain-of-Thought)
**Then:** One practical application through 5-file workflow example
**Always:** Multiple valid approaches presented (ADRs, config files, structured files)

### Multiple Valid Approaches

**Option A: ADRs + Config Files** (Recommended for most teams)
- Proven, lightweight, widely understood
- Example: docs/adr/ + .cursorrules + simple prompts

**Option B: Structured Files** (This workshop's example)
- Explicit pattern application, good for learning
- Example: 5-file workflow demonstrated in Session 2

**Option C: Tool-Assisted** (Platform-specific)
- Built-in guardrails, varying maturity
- Example: Spec-Kit, GitHub Copilot Workspace, Cursor Composer

**Choose based on team maturity and task complexity.**

---

## 📚 Research Backing

This workshop is grounded in authoritative research:

**Prompt Engineering Foundations:**
- White et al. (2023): "A Prompt Pattern Catalog" - arXiv 2302.11382 (16+ patterns cataloged)
- Brown et al. (2020): "Language Models are Few-Shot Learners" (foundational GPT-3 paper)
- Wei et al. (2022): "Chain-of-Thought Prompting Elicits Reasoning"

**Advanced Patterns:**
- Yao et al. (2022): "ReAct: Synergizing Reasoning and Acting" (agents, multi-step tasks)
- Yao et al. (2023): "Tree of Thoughts: Deliberate Problem Solving" (decision exploration)

**Industry Standards:**
- GitHub Copilot Documentation (configuration standards)
- ADR GitHub Organization (decision documentation)
- awesome-cursorrules repository (community patterns)

**Full bibliography:** See [00-RESEARCH/prompt-engineering-workshop-research.md](00-RESEARCH/prompt-engineering-workshop-research.md)

---

## 🎓 Workshop Format

Each session follows a 15+60+15 structure:
- **15 minutes**: Focused presentation with research backing
- **60 minutes**: Hands-on exercises using real code (spring-migration-demo)
- **15 minutes**: Review, comparison to alternatives, next steps

**Hands-on focus:** 80% practice, 20% theory. Learn by doing with immediate application.

---

## 🔄 Recent Updates (November 2025)

**Major terminology update:** Materials aligned with industry-standard prompt engineering terminology.

**Key changes:**
- ❌ "5 Modes" → ✅ "5-File Workflow Example (one approach)"
- ❌ "Constitution Pattern" → ✅ "Persona + Few-shot Pattern"
- ❌ Non-standard terms → ✅ Research-backed pattern names
- ✅ Added 3-tier maturity framework
- ✅ ADRs presented as equally valid alternative
- ✅ Citations added throughout (White et al., Yao et al.)

**See [MIGRATION-GUIDE.md](MIGRATION-GUIDE.md) for complete details.**

---

## 🚦 Getting Started

**1. Review Prerequisites**
- AI tool installed (GitHub Copilot, Claude, Cursor, or Windsurf)
- spring-migration-demo repository cloned
- Basic understanding of Spring Boot (for hands-on example)

**2. Choose Your Path**

**Path A: Full Workshop** (Recommended for learning)
1. Read [WORKSHOP-OVERVIEW.md](01-OVERVIEW/WORKSHOP-OVERVIEW.md)
2. Complete Session 1 (90 min)
3. Complete Session 2 (90 min)
4. Apply to your own project

**Path B: Quick Reference** (Experienced practitioners)
1. Review [QUICK-REFERENCE-CARD.md](03-REFERENCE/QUICK-REFERENCE-CARD.md)
2. Copy templates from [05-TEMPLATES/](05-TEMPLATES/)
3. Adapt to your workflow

**Path C: Research Deep Dive**
1. Read [prompt-engineering-workshop-research.md](00-RESEARCH/prompt-engineering-workshop-research.md)
2. Review authoritative sources (White et al., Yao et al.)
3. Implement patterns in your context

**3. Apply to Real Work**
- Start simple: Try ADRs + .cursorrules
- For complex tasks: Use structured files
- Measure impact: Track time saved for performance reviews

---

## 📞 Need Help?

**Understanding concepts:** Review [GLOSSARY.md](01-OVERVIEW/GLOSSARY.md)
**Choosing approaches:** See comparison tables in session guides
**Technical questions:** Check [03-REFERENCE/](03-REFERENCE/) materials
**Migration questions:** Read [MIGRATION-GUIDE.md](MIGRATION-GUIDE.md)

---

## 🎯 Learning Outcomes

By completing this workshop, you will:

✅ Understand industry-standard prompt engineering patterns
✅ Know when to use ADRs vs structured files vs tool-assisted approaches
✅ Apply Tier 1/2/3 framework to evaluate new tools
✅ Create reusable prompt templates for your team
✅ Measure and communicate time savings for performance reviews
✅ Ground practices in authoritative research (White et al., Yao et al.)

**Ready to start?** Open [START-HERE.md](START-HERE.md) or jump directly to [Session 1](02-SESSION-GUIDES/SESSION-1-industry-standards.md)!

---

**Last Updated:** November 2025
**Research Version:** prompt-engineering-workshop-research.md (November 2025)
**License:** MIT (if applicable) or see project root
