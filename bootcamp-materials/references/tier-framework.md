# Evaluating Prompt Engineering Tools

**Challenge:** New AI tools emerge constantly. How do you evaluate them?

**This document:** Observable facts about tool maturity. You decide what to adopt.

---

## Tool Evaluation Data

We organize by age + adoption. Draw your own conclusions.

---

## 🟢 Category: 10+ Years in Production

**What this means:** Long track record, multiple companies, mature tooling.

### Prompt Patterns

**Few-shot Prompting**
- First documented: Brown et al., 2020 (GPT-3 paper)
- Used in: All major LLM applications
- Evidence: Universal practice across OpenAI, Anthropic, Google, etc.

**Chain-of-Thought**
- First documented: Wei et al., 2022
- Research: Multiple papers showing accuracy improvements
- Used in: Common practice for complex reasoning tasks

**Persona Pattern**
- First documented: White et al., 2023 (16+ patterns cataloged)
- Format: "You are an expert [role]..."
- Usage: Widespread in ChatGPT, Claude, and other LLM interactions

**Template Pattern**
- First documented: White et al., 2023
- Format: Structured output specifications
- Usage: Common in production LLM applications

### Decision Documentation

**Architecture Decision Records (ADRs)**
- Created: 2011 (Michael Nygard)
- Used by: Microsoft Azure, AWS, Google Cloud, Spotify, Netflix
- Format: Markdown in docs/adr/
- Tooling: adr-tools, log4brains, MADR (mature ecosystems)
- Community: Active, established patterns

**RFC Process**
- Adapted from: IETF (1969)
- Used by: Google, Amazon, Uber, Airbnb, LinkedIn, Rust Language
- Format: Structured design documents
- Use case: Large changes requiring coordination

---

## 🟡 Category: 1-3 Years, Growing Adoption

**What this means:** Emerging standards, growing but not universal adoption.

### Tool Configuration Files

**`.github/copilot-instructions.md`** (GitHub Copilot)
- Released: ~2022-2023
- Created by: Microsoft/GitHub (official)
- Supported: VS Code, Visual Studio, JetBrains, Neovim, Xcode
- Adoption: Growing with Copilot user base
- Documentation: Official Microsoft docs
- Cross-IDE: Yes

**`.windsurfrules`** (Windsurf)
- Released: 2024
- Created by: Codeium (official)
- Supported: Windsurf IDE (VSCode-based)
- Adoption: Growing in 2024-2025
- Cross-IDE: No (Windsurf only)

**`.cursorrules`** (Cursor)
- Released: ~2023
- Created by: Community (not official Cursor standard)
- Repository: awesome-cursorrules (3,000+ forks)
- Supported: Cursor IDE only
- Cross-IDE: No (Cursor only)

### Prompt Management

**PromptLayer, LangSmith, Langfuse**
- Released: 2022-2023
- Features: Version control, CMS, analytics for prompts
- Cost: $50-500/month for teams
- Adoption: Startups, some enterprises

---

## 🟠 Category: <2 Years, Limited Production Evidence

**What this means:** New tools, limited track record outside creators.

### AI-Assisted Development

**GitHub Spec-Kit**
- Released: September 2024 (~14 months as of Nov 2025)
- Created by: GitHub (official)
- GitHub Stars: 28,000+
- Workflow: Constitution → Specify → Plan → Tasks → Implement
- Production adoption: Limited evidence outside GitHub
- Criticism: Martin Fowler warns of "waterfall" patterns
- Status: Experiment by GitHub team

**OpenSpec, Kiro**
- Released: 2024
- Status: Very new
- Production adoption: Minimal documented cases

**Structured File Workflows (5-file pattern)**
- Source: This workshop
- Age: Teaching example
- Production adoption: Unknown
- Purpose: Explicit demonstration of patterns
- Alternative: ADRs (simpler, more widely used)

---

## How to Use This Data

**Questions to ask:**

1. **How old?** Longer track record = more learning from failures
2. **Who uses it?** Multiple companies or just creator?
3. **Cross-platform?** Works with multiple tools or locked to one?
4. **What problem?** Does it solve your actual need?
5. **What's the cost?** Time to learn, vendor lock-in, actual $$$

**Example evaluation:**

**ADRs (10+ years, Microsoft/AWS/Netflix):**
- Age: 14 years (2011-2025)
- Multi-company: Yes (hundreds)
- Cross-platform: Yes (just markdown)
- Cost: Low (text files, free tools)
→ Your decision: Low risk to try

**Spec-Kit (14 months, GitHub):**
- Age: 14 months (Sept 2024-Nov 2025)
- Multi-company: Unknown (no public data)
- Cross-platform: Yes (CLI tool)
- Cost: Learning curve, workflow changes
→ Your decision: Higher risk, might change

---

## Our Recommendations

We show our thinking, you decide:

**For most teams starting out:**
- ADRs for decisions (long track record)
- `.github/copilot-instructions.md` for AI config (official standard)
- Few-shot, Chain-of-Thought, Persona patterns (universal)

**Why these?**
- Long track records (reduced risk of abandonment)
- Multi-company adoption (not vendor-specific)
- Free/low cost
- Cross-platform where applicable

**For experimentation:**
- Spec-Kit (if you want structured workflows)
- Prompt management platforms (if you need versioning at scale)

**Why experiment?**
- Learn new patterns
- Might become tomorrow's standards
- Can abandon if doesn't fit

**What we avoid recommending:**
- Single-vendor-only tools for critical workflows (lock-in risk)
- Very new tools (<6 months) for production
- Tools with no external adoption data

---

## Observable Trends (Nov 2025)

**Growing:**
- `.github/copilot-instructions.md` (official Microsoft standard)
- Prompt management platforms (LangSmith, etc.)
- Chain-of-Thought prompting

**Stable:**
- ADRs (mature, not growing but not shrinking)
- Few-shot prompting (universal practice)

**Uncertain:**
- Spec-Kit (too new to call)
- `.cursorrules` (community-driven, IDE-specific)

---

## References

[1] Brown, T. et al. (2020). "Language Models are Few-Shot Learners" - https://arxiv.org/abs/2005.14165

[2] Wei, J. et al. (2022). "Chain-of-Thought Prompting Elicits Reasoning in Large Language Models" - https://arxiv.org/abs/2201.11903

[3] White, J. et al. (2023). "A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT" - https://arxiv.org/abs/2302.11382

[4] Nygard, M. (2011). "Documenting Architecture Decisions" - https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions

[5] GitHub Copilot Documentation - https://docs.github.com/en/copilot

[6] GitHub Spec-Kit - https://github.com/github/spec-kit
