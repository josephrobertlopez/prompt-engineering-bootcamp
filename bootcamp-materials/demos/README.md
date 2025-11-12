# Workshop Demo Materials

Demo materials are now housed in the actual Spring Boot migration repository for better grounding and hands-on practice.

## 📍 Demo Locations

All Spring Boot migration demos live in: **[spring-migration-demo](https://github.com/josephrobertlopez/spring-migration-demo)**

### Session 1: Industry Standards (Day 1)

**Location:** `demos/session-1-industry-standards/`
**Link:** https://github.com/josephrobertlopez/spring-migration-demo/tree/main/demos/session-1-industry-standards

**Contains:**
- ADR example (0001-migration-strategy.md)
- 5-file workflow demonstrating foundational patterns
- `.github/copilot-instructions.md`
- Session 1 README with usage instructions

**Patterns:** Persona, Few-shot, Template, ReAct, Tree of Thoughts, Chain-of-Thought

### Session 2: Advanced Patterns (Day 2)

**Location:** `demos/session-2-advanced-patterns/`
**Link:** https://github.com/josephrobertlopez/spring-migration-demo/tree/main/demos/session-2-advanced-patterns

**Contains:**
- spec/ folder workflow (knowledge-base.md, specification.md, implementation-plan.md)
- `.github/copilot-instructions.md` (unified version)
- Session 2 README with usage instructions

**Patterns:** Meta-prompting, ReAct, Tree of Thoughts, Iterative refinement

## 🎯 Why Separate Repo?

- **Grounded in real code:** Demos reference actual Java files, tests, and migrations
- **Hands-on practice:** Workshop participants clone and work with actual codebase
- **No duplication:** Single source of truth for Spring Boot migration demos
- **Folder organization:** Day 1 and Day 2 materials in separate demo folders (main branch)

## 📂 What's Here

This demos/ folder contains:

### config-files/

Generic AI configuration examples (cross-IDE):
- `.github/copilot-instructions.md` (GitHub Copilot - recommended)
- `.windsurfrules` (Windsurf IDE)
- `.cursorrules` (Cursor IDE - reference only)
- Comparison matrix and usage guide

These are **generic examples** not tied to Spring Boot migration.

## 🚀 Getting Started

**For workshop participants:**

1. Clone the Spring migration repo:
   ```bash
   git clone https://github.com/josephrobertlopez/spring-migration-demo.git
   cd spring-migration-demo
   ```

2. **Day 1:** Navigate to session 1 materials
   ```bash
   cd demos/session-1-industry-standards/
   cat README.md
   ```

3. **Day 2:** Navigate to session 2 materials
   ```bash
   cd demos/session-2-advanced-patterns/
   cat README.md
   ```

**All materials are on the main branch** - no branch switching required!

## 📚 Related Materials

- **Presentations:** See `presentations/` folder in this repo
- **Reference docs:** See `references/` folder in this repo
- **Spring migration repo:** https://github.com/josephrobertlopez/spring-migration-demo
- **Workshop repo:** https://github.com/josephrobertlopez/prompt-engineering-bootcamp

## 💡 Quick Links

| Session | Location | Materials | Live Code |
|---------|----------|-----------|-----------|
| Day 1 | [session-1-industry-standards](https://github.com/josephrobertlopez/spring-migration-demo/tree/main/demos/session-1-industry-standards) | 5-file workflow + ADR | Spring Boot 3 |
| Day 2 | [session-2-advanced-patterns](https://github.com/josephrobertlopez/spring-migration-demo/tree/main/demos/session-2-advanced-patterns) | spec/ folder workflow | Spring Boot 3 |

---

**Note:** All Spring Boot migration demo files have been moved to the spring-migration-demo repository to provide better hands-on experience with actual code.
