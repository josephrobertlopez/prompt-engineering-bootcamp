# 3-Tier Maturity Framework for Prompt Engineering

**Problem:** New tools/patterns emerge constantly. How do you evaluate them?

**Solution:** 3-tier framework based on track record and adoption.

---

## 🟢 Tier 1: Proven (10+ years, production-ready)

### Prompt Patterns
**Few-shot Prompting** (Brown et al., 2020)
- Provide example inputs/outputs in prompt
- GPT-3 paper established this as foundational
- Universal adoption across all LLMs

**Chain-of-Thought** (Wei et al., 2022)
- Ask AI to show reasoning steps
- "Let's think step by step"
- Dramatically improves complex reasoning

**Persona Pattern** (White et al., 2023)
- Assign AI a role/identity
- "You are an expert Spring Boot developer..."
- Catalog of 16+ patterns in research paper

**Template Pattern** (White et al., 2023)
- Provide structured output format
- Checklists, tables, specific formats
- Ensures consistent AI responses

### Decision Documentation
**Architecture Decision Records (ADRs)**
- Since: 2011 (Michael Nygard)
- Used by: Microsoft (Azure), AWS, Google Cloud, Spotify, Netflix
- Format: Lightweight markdown in `docs/adr/`
- Evidence: Mature tooling ecosystem (adr-tools, log4brains, MADR)

**RFC Process**
- Since: 1969 (IETF), adapted by tech companies
- Used by: Google, Amazon, Uber, Airbnb, LinkedIn, Rust Language
- Format: Structured design documents
- Best for: Large changes requiring coordination

### Configuration Management
**(Moving to Tier 2 - see below)**

---

## 🟡 Tier 2: Emerging Standards (1-3 years, growing adoption)

### Tool Configuration Files

**`.github/copilot-instructions.md`** (GitHub Copilot) ⭐ **RECOMMENDED**
- Evidence: Official Microsoft/GitHub standard
- Format: Markdown with YAML frontmatter for path-specific rules
- Usage: Supported across VS Code, Visual Studio, JetBrains, Neovim, Xcode
- Status: Official documentation, auto-referenced by Copilot
- **Primary choice for most teams** - cross-IDE compatibility

**`.windsurfrules`** (Windsurf by Codeium)
- Evidence: Official Windsurf/Codeium standard
- Format: Plaintext/Markdown with natural language rules
- Usage: Windsurf IDE (VSCode-based) with Cascade AI
- Status: Growing adoption in 2024-2025
- **Good choice for VSCode users wanting integrated AI**

**Alternative: `.cursorrules`** (Cursor AI - IDE-specific)
- Evidence: 3,000+ forks of awesome-cursorrules repository
- Format: Plaintext/Markdown with natural language rules
- Usage: Cursor IDE only (VSCode fork)
- **Note:** IDE lock-in concern - prefer cross-IDE standards above

**YAML Frontmatter Metadata**
- Standard: Emerging practice for prompt versioning
- Format: model, temperature, version, author fields
- Tools: PromptLayer, LangSmith, Langfuse

### Prompt Versioning
**Platform-managed versioning**
- Tools: PromptLayer, LangSmith, Langfuse
- Features: Visual CMS, auto-versioning, labels (production/staging/latest)
- Cost: $50-500/month for teams

---

## 🟠 Tier 3: Experimental (months to 1-2 years, unproven at scale)

### AI-Assisted Development Tools

**GitHub Spec-Kit**
- Released: September 2024 (~14 months old as of Nov 2025)
- Stars: 28,000+ on GitHub
- Workflow: Constitution → Specify → Plan → Tasks → Implement
- Concerns: Martin Fowler warns of "waterfall" patterns, verbose overhead for small tasks
- Status: Interesting experiment, not yet proven in production

**OpenSpec, Kiro** (Even newer alternatives)
- Status: Early experimentation
- Evidence: Limited production adoption

**Tessl Framework** ("spec-as-source")
- Concept: Specs become primary artifact, code fully generated
- Parallel: Failed Model-Driven Development from 2000s
- Status: Unproven approach

### Structured File Workflows
**5-File Workflow** (this workshop's example)
- Pattern: System prompt → Task spec → Execution plan → Decisions → Generate
- Status: Teaching tool, not industry standard
- Use case: Learning prompt patterns, complex tasks requiring auditability
- Alternative: ADRs are simpler and proven

---

## 📊 Evaluation Criteria

### What Makes Tier 1?
✅ 10+ years of use
✅ Adopted by major companies (Microsoft, AWS, Google)
✅ Mature tooling ecosystem
✅ Documented in academic research
✅ Proven at scale

### What Makes Tier 2?
✅ 1-3 years of growing adoption
✅ Official company backing OR strong community momentum
✅ Thousands of users
✅ Clear evidence of value
⚠️ Not yet universally established

### What Makes Tier 3?
⚠️ Months to 1-2 years old
⚠️ Experimental status
⚠️ Limited production evidence
⚠️ Concerns from industry experts
⚠️ Unclear long-term viability

---

## 🎯 Decision Framework

### When to adopt Tier 1:
**Answer: Always.** These are proven, low-risk, high-value patterns.

**Action:**
- Use ADRs for decision documentation
- Apply Few-shot, Chain-of-Thought, Persona, Template patterns
- No hesitation needed

### When to adopt Tier 2:
**Answer: With monitoring.** Growing standards with momentum.

**Action:**
- Create `.cursorrules` or `.github/copilot-instructions.md`
- Monitor community evolution
- Be prepared to adapt format

**Risk:** Format may evolve, but core concept (team config files) is solid

### When to adopt Tier 3:
**Answer: Experiment cautiously.** Don't bet critical work.

**Action:**
- Try on non-critical projects
- Compare to Tier 1 alternatives (ADRs)
- Measure overhead vs value
- Be prepared to abandon

**Risk:** May not stand test of time, could be wasted investment

---

## 💡 Applying the Framework

### Example 1: Team wants to adopt "5-Mode Workflow"

**Analysis:**
- 5-Mode Workflow = Tier 3 (experimental, this workshop's teaching example)
- Underlying patterns (Few-shot, ReAct, Tree of Thoughts) = Tier 1
- Alternative (ADRs) = Tier 1

**Recommendation:**
- Learn the patterns through 5-file example
- Apply patterns via ADRs + simple prompts (Tier 1)
- Use structured files only for complex tasks where overhead justified

### Example 2: Team wants to adopt Spec-Kit

**Analysis:**
- Spec-Kit = Tier 3 (Sept 2024, 14 months old)
- Concerns: Martin Fowler analysis points to potential issues
- Alternative: ADRs + manual implementation = Tier 1

**Recommendation:**
- Experiment on 1-2 non-critical projects
- Compare time/value vs ADR approach
- Don't commit entire team workflow until proven
- Track overhead vs benefits

### Example 3: Team wants to create .cursorrules

**Analysis:**
- .cursorrules = Tier 2 (1-3 years, growing adoption)
- Evidence: 3,000+ forks, widespread community use
- Risk: Format may evolve, but concept is solid

**Recommendation:**
- Adopt! Create team .cursorrules
- Keep it simple (tech stack, coding standards, patterns)
- Review/update quarterly
- Low risk, high value

---

## 🚨 Red Flags for Tier 3

Watch for these warning signs:
- ❌ No evidence of production use at scale
- ❌ Released < 1 year ago
- ❌ Expert concerns (Martin Fowler, etc.)
- ❌ Feels like previous failed approaches (Model-Driven Development)
- ❌ Heavy overhead for simple tasks
- ❌ No clear path from experiment to production

**If 3+ red flags:** Proceed very cautiously or wait for maturity.

---

## ✅ Green Lights for Tier 1

Look for these indicators:
- ✅ 10+ years of use
- ✅ Used by Microsoft, AWS, Google, Netflix, Spotify
- ✅ Documented in research papers (White et al., Yao et al.)
- ✅ Mature tooling (multiple implementations)
- ✅ Clear success stories
- ✅ Low overhead, high value

**If 4+ green lights:** Adopt without hesitation.

---

## 📈 Tier Progression

**How things move between tiers:**

Tier 3 → Tier 2 (1-3 years):
- Growing adoption evidence
- Official company backing OR strong community
- Tooling matures
- Success stories emerge

Tier 2 → Tier 1 (5-10 years):
- Universal adoption
- Academic research backing
- Multiple implementations
- Taught in computer science

**Rare:** Tier 3 → Obsolete (failed experiment)
- No adoption growth
- Better alternatives emerge
- Fundamental flaws discovered

---

## 🎓 Teaching Strategy

### For Teams:
1. **Teach Tier 1 first** - Foundational, proven patterns
2. **Show Tier 2 tools** - Growing standards with momentum
3. **Demo Tier 3 application** - Experimental, but shows patterns in action

### For Individuals:
1. **Use Tier 1 daily** - ADRs, Few-shot, Chain-of-Thought
2. **Adopt Tier 2 when ready** - .cursorrules, config files
3. **Experiment with Tier 3** - Learn patterns, but don't bet career on unproven tools

---

## 📚 Sources

**Tier 1 Research:**
- White et al. (2023): "A Prompt Pattern Catalog" - arXiv 2302.11382
- Wei et al. (2022): "Chain-of-Thought Prompting Elicits Reasoning"
- Brown et al. (2020): "Language Models are Few-Shot Learners"
- Nygard (2011): Original ADR blog post
- ADR GitHub Organization: github.com/adr

**Tier 2 Evidence:**
- PatrickJS/awesome-cursorrules: 3,000+ forks
- GitHub Copilot Official Docs: docs.github.com/copilot
- PromptLayer, LangSmith, Langfuse documentation

**Tier 3 Analysis:**
- GitHub Spec-Kit: github.com/github/spec-kit (Sept 2024)
- Martin Fowler: "Exploring Gen AI: Spec-Driven Development"
- Fowler concerns: Verbose, unclear fit, potential waterfall anti-pattern

---

**Key Takeaway:** Use this framework to evaluate ANY new prompt engineering tool/pattern. Favor Tier 1, adopt Tier 2 with monitoring, experiment cautiously with Tier 3.
