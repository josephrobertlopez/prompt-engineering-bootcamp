# Prompt Engineering Bootcamp

Industry-standard workshop materials for teaching prompt engineering to developers.

**Based on research:** White et al. (2023), Yao et al. (2022/2023)

---

## Quick Start

1. **Presentations** - Run the workshop
   - [SESSION-1-industry-standards.md](presentations/SESSION-1-industry-standards.md) - Foundational patterns (90 min)
   - [SESSION-2-advanced-patterns.md](presentations/SESSION-2-advanced-patterns.md) - Advanced patterns (90 min)
   - PDF + PPTX slides included

2. **Demos** - Try the examples
   - [config-files/](demos/config-files/) - GitHub Copilot + Windsurf configuration examples
   - [spring-boot-migration/](demos/spring-boot-migration/) - Complete 5-file workflow example

3. **References** - Learn the patterns
   - [tier-framework.md](references/tier-framework.md) - How to evaluate tools (Tier 1/2/3)
   - [foundational-patterns.md](references/foundational-patterns.md) - Persona, Few-shot, Template, Chain-of-Thought
   - [advanced-patterns.md](references/advanced-patterns.md) - ReAct, Tree of Thoughts, Meta-prompting
   - [three-approaches.md](references/three-approaches.md) - ADRs vs Files vs Tools
   - [quick-reference.md](references/quick-reference.md) - Cheat sheet

---

## Repository Structure

```
bootcamp-materials/
├── presentations/     Workshop slides + session guides
├── demos/            Working examples (Spring Boot, config files)
├── references/       Learning materials + gist-ready files
└── README.md         This file
```

---

## Workshop Format

**Session 1 (90 minutes):** Industry Standards
- Tier 1/2/3 maturity framework
- Foundational patterns (Persona, Few-shot, Template, Chain-of-Thought)
- Configuration files (.github/copilot-instructions.md, .windsurfrules)
- ADRs vs structured prompts

**Session 2 (90 minutes):** Advanced Patterns
- ReAct pattern (Reason → Act → Observe)
- Tree of Thoughts (branch exploration)
- Meta-prompting (orchestration)
- Complete Spring Boot migration example

---

## Key Philosophy

**Multiple approaches are valid:**
- ADRs + config files (recommended for most teams)
- Structured files (good for learning/complex tasks)
- Tool-assisted (platform-specific)

Choose based on team needs, not dogma.

---

## References

**Research:**
- White et al. (2023) - "A Prompt Pattern Catalog" (arXiv 2302.11382)
- Yao et al. (2022) - "ReAct: Synergizing Reasoning and Acting"
- Yao et al. (2023) - "Tree of Thoughts"

**Standards:**
- ADRs: github.com/adr
- GitHub Copilot: docs.github.com/copilot

---

**License:** Open source - use freely for workshops and training

**Last Updated:** November 2025
