---
marp: true
theme: accenture-theme
paginate: true
headingDivider: 2
---

<script type="module">
import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
mermaid.initialize({ startOnLoad: true, theme: 'base' });
</script>

<!-- _class: hero -->

# Test Presentation

**Accenture Marp Theme**
Sample slide deck for testing

---

## Content Slide Test

This is a **regular content slide** with:

- Bullet points
- *Italic text*
- Purple accents on **bold text**

---

## Framework Overview

### The 3-Question Pattern

1. **What stays constant?** → knowledge-base.md
2. **What's unique?** → specification.md
3. **How to execute?** → implementation-plan.md

---

<!-- _class: exercise -->

## Exercise: Build Your First File

**Time**: 15 minutes

**Task**: Create knowledge-base.md from source materials

**Validation**: Instructor will review 2-3 examples

---

## Testing Complete

Theme elements verified:
✓ Hero slide
✓ Content slides
✓ Exercise styling
✓ Purple accents
✓ Clean layout

**Next**: Add Mermaid diagrams

---

## Mermaid Test: 3-Question Framework

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
