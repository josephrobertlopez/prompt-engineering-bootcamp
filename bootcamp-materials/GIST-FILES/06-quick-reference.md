# Prompt Engineering Quick Reference Card

**Cheat sheet for daily use** - Keep this handy!

---

## 🟢🟡🟠 Maturity Tiers (Evaluate ANY tool/pattern)

| Tier | Age | Evidence | Action |
|------|-----|----------|--------|
| 🟢 Tier 1 | 10+ years | Microsoft/AWS/Google use | Adopt now |
| 🟡 Tier 2 | 1-3 years | Growing adoption, 1000s users | Adopt with monitoring |
| 🟠 Tier 3 | Months | Experimental, expert concerns | Experiment cautiously |

---

## 📚 Pattern Quick Selector

### "I need AI to act like an expert"
→ **Persona Pattern**
```
You are an expert [role].
```

### "I have examples to show"
→ **Few-shot Pattern**
```
Example 1: Input → Output
Example 2: Input → Output
Now: [your input]
```

### "I need specific output format"
→ **Template Pattern**
```
Format as:
## Section
- Item 1
- Item 2
```

### "I need to see the reasoning"
→ **Chain-of-Thought**
```
Solve step-by-step:
1. First, [step]
2. Then, [step]
3. Finally, [step]
```

### "I have multi-phase work with dependencies"
→ **ReAct Pattern**
```
Phase 1:
THINK: [reasoning]
ACT: [tasks]
OBSERVE: [validation]

Phase 2:
[repeat]
```

### "I need to compare multiple approaches"
→ **Tree of Thoughts**
```
BRANCH A: [option] - Pros/Cons/Fit
BRANCH B: [option] - Pros/Cons/Fit
Decision: [choice with rationale]
```

---

## ⚡ Pattern Combinations (Copy-Paste Ready)

### Basic: Persona + Few-shot
```markdown
You are an expert [role].

Transform using these examples:
- Before: [example]
- After: [example]

Now transform: [input]
```

### Intermediate: Add Template
```markdown
You are an expert [role].

Examples:
- Before: [example] → After: [example]

Format output as:
## Changes
- [ ] Item 1
- [ ] Item 2

Now transform: [input]
```

### Advanced: Full Orchestration
```markdown
You are an expert [role]. (Persona)

Rules:
- Example: [before] → [after] (Few-shot)

Execute in phases: (ReAct)
Phase 1: THINK → ACT → OBSERVE
Phase 2: THINK → ACT → OBSERVE

For decisions, evaluate: (Tree of Thoughts)
- Option A: [description]
- Option B: [description]

Format as: (Template)
## Phase 1 Results
## Phase 2 Results
## Decision: [choice]
```

---

## 🚀 Three Approaches (When to Use Which)

### Simple Task
→ **ADRs + Prompt**
```
Following ADR 0001, [task].
```
- Time: 5 min
- Files: 0 (reuse ADR)
- Maturity: 🟢 Tier 1

### Complex Task
→ **Structured Files**
```
Load file-1 through file-5
Generate code
```
- Time: 45 min setup
- Files: 5
- Maturity: 🟠 Tier 3 (learning)

### Team Workflow
→ **Config + Tool**
```
.cursorrules + Copilot
```
- Time: 1 hr setup, 5 min daily
- Files: 1 (.cursorrules)
- Maturity: 🟡 Tier 2

---

## 📋 Pre-Prompt Checklist

Before writing a prompt, check:

- [ ] Would a role help? → Add **Persona**
- [ ] Can I show examples? → Add **Few-shot**
- [ ] Does format matter? → Add **Template**
- [ ] Is reasoning complex? → Add **Chain-of-Thought**
- [ ] Multiple phases? → Add **ReAct**
- [ ] Real decisions? → Add **Tree of Thoughts**

**Use only patterns that add value for your task.**

---

## 🎯 Common Tasks (Copy-Paste)

### Debug Code
```markdown
You are an expert debugger.

Analyze this error step-by-step:
1. Identify root cause
2. Suggest fix
3. Explain why it works

Error: [paste error]
Code: [paste code]
```

### Code Review
```markdown
Review this code using these criteria:

Example good: [code snippet with explanation]
Example bad: [code snippet with explanation]

Provide feedback as:
## Strengths
- Item 1

## Issues
- Item 1: [severity] [suggestion]

Code to review: [paste]
```

### Write Tests
```markdown
You are a test engineer.

Generate tests following this pattern:
```
test('should [behavior]', () => {
  // Arrange
  // Act
  // Assert
});
```

Code to test: [paste]

Format as:
## Test Cases
- [ ] Test 1: [description]
- [ ] Test 2: [description]

## Implementation
[test code]
```

### Migration Task
```markdown
You are an expert [technology] engineer.

Transform code using these rules:
- Old pattern: [example] → New pattern: [example]
- Old pattern: [example] → New pattern: [example]

Execute in phases:
Phase 1: [what] - Validate: [how]
Phase 2: [what] - Validate: [how]

Code: [paste]
```

### Make Technical Decision
```markdown
Choose between [option A] and [option B] for [use case].

Evaluate each option:

OPTION A: [description]
- Pros: [list]
- Cons: [list]
- Effort: [hours]
- Risk: [Low/Medium/High]

OPTION B: [description]
- Pros: [list]
- Cons: [list]
- Effort: [hours]
- Risk: [Low/Medium/High]

Recommend best option with rationale.
```

---

## 🚨 Common Mistakes & Fixes

### ❌ Vague prompt
```
Fix this code
```

### ✅ Specific prompt
```
You are a Python expert.
This code has a KeyError on line 10.
Explain root cause and suggest fix.
Code: [paste]
```

---

### ❌ No examples
```
Modernize these annotations
```

### ✅ With examples (Few-shot)
```
Modernize annotations using these examples:
- @RequestMapping(method=GET) → @GetMapping
- @RequestMapping(method=POST) → @PostMapping
Code: [paste]
```

---

### ❌ No validation
```
Do A then B
```

### ✅ With validation (ReAct)
```
Phase 1: Do A
Validate: Check X passes

Phase 2: Do B
Validate: Check Y passes
```

---

## ⏱️ Time-Saving Tricks

### 1. Build a Prompt Library
Save your best prompts with names:
```
~/prompts/
  debug-python.md
  review-java.md
  test-typescript.md
```

### 2. Use Variables
```markdown
You are an expert [LANGUAGE] engineer.
[TASK] this code using [PATTERN].
```
Replace [CAPS] for each use.

### 3. Chain Multiple Prompts
```
Prompt 1: Analyze → Save output
Prompt 2: Using analysis above, suggest fixes
Prompt 3: Using fixes above, generate code
```

### 4. Keep a Win Log
Track what worked:
```
Date: 2025-11-11
Task: Debug Kafka consumer
Pattern: Chain-of-Thought
Time saved: 30 min
What worked: Step-by-step revealed offset issue
```

---

## 📊 Measuring Impact

### Track Weekly
```
Week of [date]:
- Prompts used: 10
- Time saved: 3 hours
- Best pattern: ReAct (debugging)
- Improvement: Added examples to prompts
```

### For Performance Reviews
```
Accomplishment: Used prompt engineering for 15 tasks
Impact: Saved 40 hours, delivered 3 features faster
Evidence: Win log shows consistent 30-40% time reduction
```

---

## 🔗 Quick Links

**Research:**
- White et al. (2023): arXiv 2302.11382 (pattern catalog)
- Yao et al. (2022): ReAct paper
- Yao et al. (2023): Tree of Thoughts paper

**Industry Standards:**
- ADRs: github.com/adr
- .cursorrules: github.com/PatrickJS/awesome-cursorrules
- Copilot: docs.github.com/copilot

**Tools:**
- Spec-Kit: github.com/github/spec-kit (🟠 Tier 3)
- Cursor: cursor.sh (🟡 Tier 2)

---

## 💡 Pro Tips

1. **Start simple** - One pattern at a time
2. **Add examples** - Few-shot improves everything
3. **Validate checkpoints** - Use ReAct for complex tasks
4. **Document decisions** - Use Tree of Thoughts or ADRs
5. **Track wins** - Evidence for performance reviews
6. **Share prompts** - Build team library
7. **Iterate** - Refine prompts based on results
8. **Know tiers** - Evaluate new tools with framework

---

## 🎯 Today's Action Item

**Pick ONE:**

- [ ] Try Persona + Few-shot on real task (15 min)
- [ ] Create .cursorrules for project (30 min)
- [ ] Write first ADR documenting decision (20 min)
- [ ] Build prompt library folder (10 min)
- [ ] Track one win in log (5 min)

**Measure:** How much time did you save?

---

**Print this card** - Keep it visible while coding!

**Last Updated:** November 2025
**Full workshop:** See 00-README.md in this gist
