# Grounding Prompt Engineering Workshop Materials in Real Industry Practices

## Executive Summary

This research reveals a **critical divide between established patterns (proven over 10+ years) and experimental AI-assisted approaches (months old)**. Key findings: dotfiles like `.cursorrules` and `.github/copilot-instructions.md` are widespread industry standards, **"[redacted reference]" does not exist**, and terms like "Constitution/Specification/Planning patterns" are not recognized prompt engineering terminology. Workshop materials should focus on proven patterns while clearly labeling experimental approaches.

## 1. Dotfiles and Configuration Management: What Actually Exists

### Widespread Industry Standards (Production-Ready)

**`.cursorrules` (Cursor AI)** is the most prevalent pattern with **thousands of public repositories** using it. [Rafferty Uy](https://raffertyuy.com/raztype/ghcp-custom-prompts-structure/) Developers place plaintext/Markdown files in project roots containing natural language instructions for AI code generation. [GitHub](https://github.com/PatrickJS/awesome-cursorrules) [GitHub](https://github.com/JhonMA82/awesome-clinerules) The PatrickJS/awesome-cursorrules repository has 3,000+ forks with 150+ categorized examples covering React, Next.js, Python, Django, and more. [github +2](https://github.com/PatrickJS/awesome-cursorrules) These files typically include tech stack specifications, coding standards (DRY, KISS, YAGNI), framework-specific guidelines, and explicit "DO NOT use" lists. [github +2](https://gist.github.com/artsparkAI/d34cfcce2bc8eff4773502476deb32d3)

**`.github/copilot-instructions.md` (GitHub Copilot)** represents the **official Microsoft standard** supported across VS Code, Visual Studio, JetBrains IDEs, Xcode, and GitHub.com. [GitHub](https://docs.github.com/copilot/customizing-copilot/adding-custom-instructions-for-github-copilot) This pattern includes repository-wide instructions at `.github/copilot-instructions.md` and path-specific instructions using `.github/instructions/*.instructions.md` with YAML frontmatter. [raffertyuy +2](https://raffertyuy.com/raztype/ghcp-custom-prompts-structure/) GitHub's official documentation confirms this is automatically referenced by Copilot and version-controlled alongside code. [raffertyuy](https://raffertyuy.com/raztype/ghcp-custom-prompts-structure/) [GitHub](https://docs.github.com/copilot/customizing-copilot/adding-custom-instructions-for-github-copilot)

**`.windsurfrules` (Windsurf AI IDE)** is a growing pattern similar to Cursor, with curated collections emerging. [GitHub](https://github.com/kinopeee/windsurfrules) [GitHub](https://github.com/balqaasem/awesome-windsurfrules) Many projects now maintain both `.cursorrules` AND `.windsurfrules` with identical or nearly identical content, demonstrating cross-tool compatibility as a common practice. [GitHub](https://github.com/grapeot/devin.cursorrules)

### What Does NOT Exist

**`.promptrc` and `.specrc`** have no evidence of real-world usage. The only mention of `.promptrc` appears in a proposed feature request for Amazon Q CLI (not yet implemented). [GitHub](https://github.com/aws/amazon-q-developer-cli/issues/1122) These should not be presented as established patterns in workshop materials.

### Standard File Organization Pattern

The most common structure observed across thousands of repositories:
```
project/
├── .cursorrules                      # Cursor instructions
├── .github/
│   ├── copilot-instructions.md       # Base Copilot instructions
│   └── instructions/
│       └── *.instructions.md         # Path-specific instructions
├── .windsurfrules                    # Windsurf instructions
└── src/
```

Content patterns consistently include: technology stack declarations, clean code principles (DRY, KISS, YAGNI), framework-specific guidelines, project structure documentation, and explicit exclusion lists. [GitHub](https://github.com/obviousworks/vibe-coding-ai-rules/blob/main/.windsurfrules)

## 2. Prompt Engineering File Structures: Established vs Emerging

### Established Pattern: GitHub Copilot Standard

The **`.github/` folder structure** has emerged as the de facto standard for team-shared prompts. This includes `.github/prompts/*.prompt.md` for reusable prompts and `.github/prompt-snippets/` for referenced components. [raffertyuy](https://raffertyuy.com/raztype/ghcp-custom-prompts-structure/) [github](https://github.com/github/awesome-copilot) Naming conventions use semantic prefixes: `agent.{use-case}.prompt.md` for agent mode and `fetch.{use-case}.prompt.md` for external URLs. [raffertyuy](https://raffertyuy.com/raztype/ghcp-custom-prompts-structure/) [Rafferty Uy](https://raffertyuy.com/raztype/ghcp-custom-prompts-structure/)

### Versioning: Three Proven Approaches

**Semantic Versioning (X.Y.Z)** is widely adopted, with major versions for breaking changes, minor for new features, and patch for fixes. [Latitude Blog](https://latitude-blog.ghost.io/blog/prompt-versioning-best-practices/) Implementation varies from JSON-based with UUID timestamps to Git-native versioning using commit SHAs and tags. [James' Coffee Blog](https://jamesg.blog/2023/04/01/llm-prompt-versioning)

**Platform-managed versioning** through tools like PromptLayer, LangSmith, and Langfuse provides visual CMS interfaces with auto-versioning and label systems (`production`, `staging`, `latest`). [PromptLayer](https://www.promptlayer.com/) [PromptLayer](https://blog.promptlayer.com/5-best-tools-for-prompt-versioning/)

**YAML Frontmatter Metadata** is becoming standard practice:
```yaml
---
model: gpt-4o
temperature: 0.7
version: 1.2.0
author: team-ai
last_updated: 2025-11-11
---
```

### Production Patterns by Use Case

**For individual developers:** Start with `.github/prompts/` folder + Git versioning (free, familiar workflow).

**For small teams (2-10):** Use `.github/` structure + shared repo with code reviews for prompt changes.

**For production LLM applications:** Implement CMS + Git hybrid (PromptLayer, LangSmith, or Langfuse) with evaluation pipelines and A/B testing ($50-500/month).

**For enterprise:** Deploy LangSmith Enterprise or Humanloop with multi-environment governance, access controls, and audit logs (custom pricing).

### Critical Success Factors

Research of production systems reveals eight essential practices: decouple prompts from code to enable non-engineer edits, always version prompts, test before production using evaluation datasets, enable one-click rollback capability, document why changes were made not just what changed, monitor versions in production, use labels not branches for environment management, and evaluate systematically rather than relying on intuition. [Agenta](https://agenta.ai/blog/the-definitive-guide-to-prompt-management-systems) [LaunchDarkly](https://launchdarkly.com/blog/prompt-versioning-and-management/)

## 3. Spec-Driven Development: The Critical Distinction

### Established Practices (10+ Years, Proven at Scale)

**Architecture Decision Records (ADRs)** represent mature, widely-adopted practice since 2011. Featured in Azure Well-Architected Framework, AWS Prescriptive Guidance, and Google Cloud Architecture Center, ADRs are used by Microsoft, AWS, Google Cloud, Spotify, and countless others. Multiple tools exist: adr-tools, log4brains, MADR. Files live in `docs/adr/` with numbered naming like `0001-use-postgresql.md` and remain immutable once accepted. [GitHub](https://github.com/npryce/adr-tools)

**RFC/Design Doc Process** is widespread at scale, adapted from IETF standards (1969). Used by Google, Amazon (PR/FAQs), Uber, Airbnb, LinkedIn, Spotify, Netflix, and Stripe. The Rust Language RFCs repository provides an exemplary open-source implementation. [GitHub](https://github.com/rust-lang/rfcs) This process excels for asynchronous collaboration, reducing rework, and building consensus across distributed teams. [Ebury LABS](https://labs.ebury.rocks/2022/02/08/rfc-driven-development/)

### Experimental AI-Assisted Patterns (Months Old, Unproven)

**GitHub Spec-Kit** (released September 2024) is an experimental open-source toolkit with 28,000+ stars but limited production adoption. [GitHub](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/) [Ainativedev](https://ainativedev.io/news/a-look-at-spec-kit-githubs-spec-driven-software-development-toolkit) It implements a four-phase workflow: Constitution → Specify → Plan → Tasks → Implement. [GitHub](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/) Files live in `.specify/` directory with `memory/constitution.md` and numbered spec folders. [github +2](https://github.com/github/spec-kit)

Martin Fowler's analysis highlights concerns: verbose markdown files to review, unclear problem size fit, agents don't always follow elaborate specs despite large context windows, and heavy overhead for small tasks. The key question remains: "Is this too much like waterfall for AI?" [martinfowler](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html) [Martin Fowler](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)

**OpenSpec** and **Kiro** are even newer lightweight alternatives, while **Tessl Framework** attempts "spec-as-source" where specs become the primary maintained artifact and code is fully generated. This parallels failed Model-Driven Development approaches from the 2000s. [martinfowler](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html) [Martin Fowler](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)

### Critical Distinction for Workshop Materials

**Proven:** ADRs and RFCs for documenting decisions and designs (lightweight, valuable regardless of AI tools).

**Experimental:** AI-assisted spec-as-source tools like Spec-Kit (interesting experiments but not proven for production use).

The most successful "spec-driven" practices are actually **decision-driven** and **design-driven** - capturing the why and architecture, not trying to make specs the source of truth for all code.

## 4. [redacted reference] and Spec-Kit: Separating Fact from Fiction

### [redacted reference]: Does NOT Exist

**Zero evidence found.** Extensive searches across GitHub, Reddit, developer blogs, and general web returned no results. No events, communities, projects, or frameworks exist with this specific name. This should not be referenced in workshop materials as an established methodology.

### Vibe Coding (General): Real but Controversial

**"Vibe coding"** (without "Thursday") is a real methodology coined by **Andrej Karpathy** (OpenAI co-founder) in February 2025. Named Collins Dictionary's Word of the Year for 2025 and listed in Merriam-Webster as trending slang, it describes AI-assisted development where developers accept AI-generated code without reviewing it. [Wikipedia +3](https://en.wikipedia.org/wiki/Vibe_coding)

**Industry adoption:** Y Combinator reported 25% of Winter 2025 startups had codebases that were 95% AI-generated. [Wikipedia](https://en.wikipedia.org/wiki/Vibe_coding) Microsoft CEO stated 30% of Microsoft's code is AI-written. [Wikipedia](https://en.wikipedia.org/wiki/Vibe_coding) [CNBC](https://www.cnbc.com/2025/05/08/i-took-a-2-day-vibe-coding-class-and-successfully-built-a-product.html)

**Critical warning:** September 2025 Fast Company reported "vibe coding hangover" with engineers citing "development hell." Karpathy himself recommends it only for "throwaway weekend projects." Security concerns about unreviewed AI-generated code make it unsuitable for production or mission-critical applications. [Wikipedia +2](https://en.wikipedia.org/wiki/Vibe_coding)

### Spec-Kit: Real, Established Framework

**GitHub Spec-Kit is a legitimate framework** released September 2024 with official GitHub backing. [GitHub](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/) [Ainativedev](https://ainativedev.io/news/a-look-at-spec-kit-githubs-spec-driven-software-development-toolkit) It explicitly positions itself **as an antidote to vibe coding chaos**, emphasizing structured specifications, multi-step refinement with human checkpoints, and maintainable production-ready code. [github +2](https://github.com/github/spec-kit)

The framework creates organizational "opinionated stacks" through `constitution.md` files and systematic workflows. [Microsoft Developer](https://developer.microsoft.com/blog/spec-driven-development-spec-kit) However, it remains experimental with acknowledged limitations: can feel excessive for small bugs, requires discipline and process adherence, and has a learning curve. [github +2](https://github.com/github/spec-kit)

**The irony:** Spec-Kit exists specifically to solve problems created by vibe coding, making them philosophical opposites in the AI-assisted development ecosystem.

## 5. Constitution/Specification/Planning: Non-Standard Terminology

### The Verdict: NOT Established Prompt Engineering Patterns

Extensive research of academic papers, OpenAI documentation, Anthropic research, and community resources definitively shows: **"Constitution," "Specification," and "Planning" are not recognized prompt engineering pattern names** in industry-standard terminology.

### What Actually Exists

**Constitutional AI** is a specific training methodology from Anthropic (Bai et al., 2022), not a general prompting pattern. It's a training technique using a "constitution" (set of principles) during model training - not something practitioners use as a prompt pattern. [Anthropic](https://www.anthropic.com/research/constitutional-ai-harmlessness-from-ai-feedback) [Anthropic](https://www.anthropic.com/news/claudes-constitution)

### Established Terminology Practitioners Actually Use

The most comprehensive academic catalog (White et al., 2023) documents 16+ recognized patterns:
- **Persona Pattern**: Assigning a role/identity to the AI
- **Template Pattern**: Providing structured output formats
- **Cognitive Verifier Pattern**: Breaking questions into sub-questions
- **Recipe Pattern**: Completing missing steps in sequences
- **Fact Check List Pattern**: Generating verifiable facts from output [arXiv +4](https://arxiv.org/abs/2302.11382)

**Core foundational patterns** with universal recognition:
- Zero-shot, few-shot, one-shot prompting (Brown et al., 2020)
- Chain-of-Thought (CoT) prompting (Wei et al., 2022)
- ReAct for agents (Yao et al., 2022) [Prompt Engineering Guide +2](https://www.promptingguide.ai/techniques/fewshot)

### How Practitioners Describe Prompts

**Common terminology:** System prompt (sets overall behavior), user prompt (the actual query), few-shot examples (sample inputs/outputs), instruction prompts (direct task specification), role-playing/persona prompts (assigning identity), structured prompts (using templates/formats), meta prompts (prompts that generate prompts), agentic prompts (for tool-using agents).

**NOT common:** "Constitution prompts," "specification prompts," "planning prompts" (except for narrow agentic contexts).

### Correct Alternative Terminology

**Instead of "Constitution Pattern":** Use "System prompt with guidelines" or reference Anthropic's Constitutional AI training methodology.

**Instead of "Specification Pattern":** Use "Template Pattern" or "Structured output prompting."

**Instead of "Planning Pattern":** Use "ReAct pattern," "Multi-step reasoning," or "Task decomposition."

## 6. Recommendations for Workshop Materials

### Use These Proven Patterns (High Confidence)

**Configuration Management:**
- `.cursorrules` and `.github/copilot-instructions.md` as industry standards
- Cross-tool compatibility practices (maintaining multiple config files) [GitHub](https://github.com/grapeot/devin.cursorrules)
- Natural language instructions with XML-like tags for organization [github +2](https://gist.github.com/artsparkAI/d34cfcce2bc8eff4773502476deb32d3)

**File Organization:**
- `.github/` folder structure for team prompts [github](https://github.com/github/awesome-copilot)
- Semantic naming: `agent.{use-case}.prompt.md`, `fetch.{source}.prompt.md`
- YAML frontmatter for metadata (model, temperature, version, author) [GitHub](https://microsoft.github.io/promptflow/how-to-guides/develop-a-prompty/index.html)

**Specification Practices:**
- ADRs for architectural decisions (lightweight, proven)
- RFC process for large changes requiring coordination
- Numbered markdown files in `docs/adr/` or `docs/rfcs/`

**Prompt Engineering:**
- Zero-shot, few-shot, one-shot patterns [GitHub](https://github.com/promptslab/Awesome-Prompt-Engineering) [GitHub](https://github.com/NirDiamant/Prompt_Engineering)
- Chain-of-Thought prompting [GitHub](https://github.com/promptslab/Awesome-Prompt-Engineering)
- Persona/Template patterns from White et al. catalog [GitHub](https://github.com/NirDiamant/Prompt_Engineering) [vanderbilt](https://www.vanderbilt.edu/generative-ai/prompt-patterns/)
- System/User/Assistant message role structure

### Label These Experimental (Proceed with Caution)

**Emerging AI-Assisted Approaches:**
- GitHub Spec-Kit (clearly state: released September 2024, experimental) [GitHub](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/) [Ainativedev](https://ainativedev.io/news/a-look-at-spec-kit-githubs-spec-driven-software-development-toolkit)
- Explicitly note concerns from Martin Fowler's analysis
- Position as "interesting experiment to watch" not "proven best practice"
- Recommend for greenfield projects willing to experiment, not production-critical code

**Vibe Coding:**
- Acknowledge as real industry term (Word of the Year 2025) [Wikipedia](https://en.wikipedia.org/wiki/Vibe_coding)
- Include strong warnings: recommended only for throwaway projects [Wikipedia](https://en.wikipedia.org/wiki/Vibe_coding) [GitHub](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/)
- Reference September 2025 "vibe coding hangover" reports [Wikipedia](https://en.wikipedia.org/wiki/Vibe_coding) [GitHub](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/)
- Not suitable for production or mission-critical applications

### Do NOT Reference

**Non-existent frameworks:**
- [redacted reference] (zero evidence of existence)
- .promptrc, .specrc as established patterns (only proposed, not real)
- "Constitution/Specification/Planning patterns" as standard prompt engineering terminology

### Framework for Presenting Information

**Three-tier classification system:**

**Tier 1 - Industry Standard (10+ years):** ADRs, RFCs, Few-shot prompting, Chain-of-Thought
- Label: "Proven, widely adopted across industry"
- Confidence: High, recommend without reservation

**Tier 2 - Emerging Practice (1-3 years):** `.cursorrules`, `.github/copilot-instructions.md`, Prompt versioning platforms
- Label: "Growing adoption, community momentum"
- Confidence: Medium, recommend with monitoring

**Tier 3 - Experimental (months old):** Spec-Kit, OpenSpec, AI-assisted spec-as-source
- Label: "Experimental, unproven, rapidly evolving"
- Confidence: Low, recommend only for experimentation

## 7. Key Insights for Workshop Design

### The Maturity Spectrum

Industry practices exist on a spectrum from mature patterns with decades of validation to bleeding-edge experiments mere months old. **The most common error in workshop materials is conflating these categories** - presenting experimental approaches as established best practices or inventing terminology that doesn't exist in the field.

### Terminology Precision Matters

Using non-standard terms like "Constitution Pattern" when the field uses "System prompt with guidelines" or "Persona Pattern" erodes credibility. **Ground all terminology in authoritative sources**: White et al.'s prompt pattern catalog, OpenAI's official documentation, Anthropic's research papers, or GitHub's official standards. [arXiv](https://arxiv.org/abs/2302.11382) [arXiv](https://arxiv.org/abs/2406.06608)

### Real Examples Trump Theory

Every pattern discussed should include actual GitHub repository links, production system examples, or documentation from major companies. Avoid theoretical frameworks without implementation evidence. The research revealed clear examples: PatrickJS/awesome-cursorrules (3,000+ forks), [github +2](https://github.com/PatrickJS/awesome-cursorrules) Rust Language RFCs (gold standard), adr-tools (mature ecosystem).

### Distinguish Personal Frameworks

Be explicit when something is "a personal methodology I've tested" versus "an industry-standard practice." [redacted reference] appeared to be a misremembered or hypothetical term. Spec-Kit, while real, is an official GitHub experiment, not a proven production standard. [GitHub](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/) [Ainativedev](https://ainativedev.io/news/a-look-at-spec-kit-githubs-spec-driven-software-development-toolkit) This distinction helps participants make informed decisions about adoption risk.

### The AI Assistant Context

Current AI-assisted development practices span from chaotic (vibe coding - accept everything) to highly structured (Spec-Kit - systematic refinement). [MIT Technology Review](https://www.technologyreview.com/2025/04/16/1115135/what-is-vibe-coding-exactly/) [Simon Willison](https://simonwillison.net/2025/Mar/19/vibe-coding/) Most production teams fall somewhere in the middle, adapting traditional patterns (ADRs, RFCs) with modern tooling (Copilot instructions, prompt versioning platforms). Workshop materials should reflect this pragmatic middle ground rather than extremes.

## Authoritative Sources for Citation

### Configuration Management
- GitHub Copilot Official Documentation: https://docs.github.com/copilot/customizing-copilot
- PatrickJS/awesome-cursorrules: https://github.com/PatrickJS/awesome-cursorrules
- VS Code Copilot Customization Guide: https://code.visualstudio.com/docs/copilot

### Prompt Engineering
- White et al. (2023): "A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT" (arXiv 2302.11382) [arXiv](https://arxiv.org/abs/2302.11382)
- Schulhoff et al. (2024): "The Prompt Report: A Systematic Survey" (arXiv 2406.06608) - 58 techniques cataloged
- OpenAI Platform Documentation & Best Practices Guide
- Anthropic Constitutional AI papers (Bai et al., 2022)

### Spec-Driven Development
- GitHub Spec-Kit: https://github.com/github/spec-kit
- Martin Fowler analysis: Blog post on spec-driven development with AI
- ADR GitHub organization: https://github.com/adr
- Rust Language RFCs: https://github.com/rust-lang/rfcs

### Production Systems
- PromptLayer: https://www.promptlayer.com/
- LangSmith: https://www.langchain.com/langsmith
- Langfuse: https://langfuse.com/
- OpenAI Cookbook: https://cookbook.openai.com/

## Final Recommendations

**Ground workshop materials in the three-tier framework**: clearly distinguish industry-standard practices (ADRs, RFCs, established prompt patterns) from emerging patterns (.cursorrules, Copilot instructions) and experimental approaches (Spec-Kit). Avoid referencing non-existent frameworks like [redacted reference] or using non-standard terminology like "Constitution Pattern."

**Focus on proven patterns first**: Start with ADRs for decisions, RFC process for large changes, `.github/copilot-instructions.md` for team prompts, [GitHub](https://docs.github.com/copilot/customizing-copilot/adding-custom-instructions-for-github-copilot) and established prompt engineering patterns (few-shot, Chain-of-Thought, Persona/Template patterns). These have track records and wide adoption.

**Be honest about experimental status**: When covering Spec-Kit or similar tools, explicitly label them as "experimental, released [date], not yet proven in production." [GitHub](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/) [Ainativedev](https://ainativedev.io/news/a-look-at-spec-kit-githubs-spec-driven-software-development-toolkit) Include practitioner concerns and acknowledge open questions about their fit and sustainability.

**Use correct industry terminology**: Reference authoritative sources like White et al.'s pattern catalog, OpenAI documentation, and GitHub standards. Replace personal frameworks with recognized terms unless explicitly labeled as "a tested personal approach."

**Provide real examples throughout**: Every pattern should link to actual GitHub repositories, production implementations, or official documentation. Theory without evidence undermines workshop credibility and participant ability to implement practices effectively.
