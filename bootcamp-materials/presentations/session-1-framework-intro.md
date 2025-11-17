---
marp: true
theme: accenture-theme
paginate: true
headingDivider: 2
html: true
---

<!-- _class: hero -->

# First-Principles Prompt Engineering

**SESSION 1**: Building Your Framework from Scratch

*Discovery-based learning for complex AI workflows*

---

## Today's Journey

**Duration**: 90 minutes (with 2 micro-breaks)

**Goal**: Build a complete prompt file system from raw materials

**Method**: Discovery → Construction → Validation

---

## What You'll Learn

By the end of this session, you will:

1. **Extract** structure from unstructured content
2. **Apply** the 3-Question Framework to any domain
3. **Build** knowledge-base.md from real requirements
4. **Validate** your work through peer review

---

## The Problem We're Solving

Traditional prompt engineering:
- Copy template files blindly
- Miss critical domain context
- Struggle when requirements change

**Our approach:**
- Build from first principles
- Understand *why* structure emerges
- Adapt to any domain automatically

---

<!-- _class: exercise -->

## Exercise Setup (5 min)

**Materials Needed:**
1. FY26 Priorities Guide (PDF)
2. Interview questions (TXT)
3. Blank markdown files
4. Your curiosity

**Outcome**: Ready workspace for discovery

---

## The 3-Question Framework

Every complex system answers three questions:

```mermaid
flowchart LR
    A[Raw Materials] --> B{What stays constant?}
    A --> C{What's unique?}
    A --> D{How to execute?}

    B --> E[knowledge-base.md]
    C --> F[specification.md]
    D --> G[implementation-plan.md]

    style E fill:#A100FF,stroke:#A100FF,color:#fff
    style F fill:#4A90E2,stroke:#4A90E2,color:#fff
    style G fill:#7ED321,stroke:#7ED321,color:#fff
```

---

## Question 1: What Stays Constant?

**Definition**: Information that applies to *every* instance

**Examples from FY26 Priorities:**
- 4 strategic categories (always the same)
- ABCD reflection framework (never changes)
- 28 metric types (fixed list)

**Output**: `knowledge-base.md` - your system's DNA

---

## Question 2: What's Unique?

**Definition**: Information specific to *this* instance

**Examples from FY26 Priorities:**
- Your 4 personal priorities (different for each person)
- Selected metrics (1-3 per priority)
- Individual accomplishments

**Output**: `specification.md` - this execution's blueprint

---

## Question 3: How to Execute?

**Definition**: Steps to transform inputs → outputs

**Examples from FY26 Priorities:**
- Category selection workflow
- Metric assignment process
- Review cycle timeline

**Output**: `implementation-plan.md` - actionable steps

---

<!-- _class: break -->

# Micro-Break

**2 minutes**: Stand, stretch, hydrate

*Return ready for live deconstruction demo*

---

## Live Demo: Deconstructing FY26 Guide

**Instructor will demonstrate:**

1. Opening PDF with "beginner's mind"
2. Identifying constant vs. unique elements
3. Mapping content to 3 questions
4. Creating knowledge-base.md structure

**Watch for**: Decision points when categorizing information

---

## Demo Insights (Key Takeaways)

**Pattern Recognition:**
- Lists with fixed items → knowledge-base
- Fields requiring user input → specification
- Sequences of actions → implementation-plan

**Edge Cases:**
- Hybrid content (e.g., "select from these options")
- Conditional logic (if/then rules)
- Metadata vs. content

---

<!-- _class: exercise -->

## Your Turn: Extract Constants (30 min)

**Task**: Create knowledge-base.md from FY26 guide

**Success Criteria:**
- 4 strategic categories documented
- 28 metric types captured
- ABCD framework explained
- No user-specific data included

**Validation**: Pair review at 25-minute mark

---

## Validation Checkpoint

**Pair Review Questions:**

1. Can another person use this knowledge-base for *their* priorities?
2. Is anything user-specific mixed in?
3. Are all 28 metrics documented?
4. Does ABCD framework have clear definitions?

**Feedback**: 2 stars (strengths) + 1 wish (improvement)

---

## Common Mistakes (Lessons Learned)

**Mistake #1**: Including example data in knowledge-base
- ❌ "John's priority: Client Value - Increase satisfaction 15%"
- ✅ "Client Value category focuses on customer outcomes"

**Mistake #2**: Omitting framework explanations
- ❌ "ABCD framework exists"
- ✅ "A=Accomplishments (what), B=Business impact (why), C=Challenges (obstacles), D=Development (growth)"

**Mistake #3**: Missing metric constraints
- ❌ "28 metrics available"
- ✅ "1-3 metrics per priority, 28 options: [list]"

---

<!-- _class: break -->

# Micro-Break

**2 minutes**: Brain reset before final synthesis

*Return for wrap-up and Session 2 preview*

---

## Session 1 Recap

**You've accomplished:**

✓ Learned the 3-Question Framework
✓ Distinguished constant vs. unique information
✓ Built knowledge-base.md from raw materials
✓ Validated through peer review

**Next session**: specification.md + implementation-plan.md

---

## Homework (Optional)

**Practice the framework** on a different domain:

- Recipe (constant: cooking techniques | unique: ingredients | execute: steps)
- API docs (constant: endpoints | unique: parameters | execute: request flow)
- Training manual (constant: concepts | unique: scenarios | execute: exercises)

**Goal**: Pattern recognition across domains

---

## Questions & Reflection

**Open floor for:**

- Clarification questions
- Insights discovered
- Challenges faced
- Connections to your work

**Instructor note**: Capture themes for Session 2 adjustments

---

<!-- _class: hero -->

# See You Next Session

**Coming up**: Specification.md + Implementation-plan.md

*Keep your knowledge-base.md handy!*

<script type="module">
import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
mermaid.initialize({ startOnLoad: true, theme: 'base' });
</script>
