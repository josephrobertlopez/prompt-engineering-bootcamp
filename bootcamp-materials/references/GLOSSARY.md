# Glossary: Prompt Engineering Terms

**Purpose**: Maps custom bootcamp terminology to industry-standard prompt engineering patterns
**Last Updated**: 2025-11-11

This glossary bridges the "5 Prompt Modes" framework taught in the bootcamp to established industry patterns documented in academic research and official documentation.

---

## How to Use This Glossary

- **Custom Term**: The term used in bootcamp materials
- **Standard Pattern(s)**: Industry-recognized equivalent(s)
- **Source**: Academic paper or official documentation
- **Tier**: Maturity classification (🟢 Tier 1 / 🟡 Tier 2 / 🟠 Tier 3)

---

## Term Mappings

| Custom Term | Standard Pattern(s) | Source | Tier |
|-------------|---------------------|--------|------|
| Constitution | System prompt with guidelines, Persona Pattern | [White et al. 2023](https://arxiv.org/abs/2302.11382 "A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT") | 🟢 Tier 1 |
| Specification | Template Pattern, Structured output prompting | [White et al. 2023](https://arxiv.org/abs/2302.11382 "A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT") | 🟢 Tier 1 |
| Planning | ReAct pattern, Task decomposition, Chain-of-Thought | [Yao et al. 2022](https://arxiv.org/abs/2210.03629 "ReAct: Synergizing Reasoning and Acting in Language Models") | 🟢 Tier 1 |
| ABCD | Tree of Thoughts, Decision prompting | [Yao et al. 2023](https://arxiv.org/abs/2305.10601 "Tree of Thoughts: Deliberate Problem Solving with Large Language Models") | 🟢 Tier 1 |
| Implementation | Code generation prompting, Few-shot prompting | [Brown et al. 2020](https://arxiv.org/abs/2005.14165 "Language Models are Few-Shot Learners") | 🟢 Tier 1 |

---

## Maturity Tier Definitions

### 🟢 Tier 1: Industry Standard (10+ years)
**Timeline**: Proven in production for over a decade
**Risk Level**: Low
**Recommendation**: Safe for all production environments
**Examples**: ADRs, RFCs, Few-shot prompting, Chain-of-Thought

### 🟡 Tier 2: Emerging Practice (1-3 years)
**Timeline**: Growing adoption over 1-3 years
**Risk Level**: Medium
**Recommendation**: Good for modern projects, monitor for breaking changes
**Examples**: .cursorrules, .github/copilot-instructions.md, prompt versioning platforms

### 🟠 Tier 3: Experimental (months old)
**Timeline**: Recently released, limited production validation
**Risk Level**: High
**Recommendation**: Learning/exploration only, not mission-critical production
**Examples**: Spec-Kit (Sept 2024), AI-assisted spec-as-source frameworks

**Source**: See [prompt-engineering-workshop-research.md](../00-RESEARCH/prompt-engineering-workshop-research.md) for comprehensive analysis

---

## Quick Reference

Need to understand a term quickly? Use your browser's find function (Ctrl+F / Cmd+F) to search this page.

**Most Common Lookups**:
- [Constitution](#constitution) - System-level guidance patterns
- [Specification](#specification) - Structured output formats
- [Planning](#planning) - Task decomposition and reasoning
