# Foundational Prompt Engineering Patterns (Tier 1)

**Source:** White et al. (2023), "A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT" - arXiv 2302.11382

**Status:** 🟢 Tier 1 - Proven, production-ready, universal adoption

These patterns are research-backed, proven over years of use, and form the foundation of effective prompt engineering.

---

## Pattern 1: Persona Pattern

### What It Is
Assign the AI a specific role, identity, or expertise level.

### Why It Works
- Sets context for responses
- Activates relevant knowledge domains
- Establishes appropriate tone/style

### Template
```
You are [role/identity with expertise].

Your responsibilities include [key activities].
Your knowledge covers [domains].

[Task/question]
```

### Example: Spring Migration
```markdown
You are an expert Spring Boot migration specialist with 10+ years experience upgrading enterprise applications.

Your expertise includes:
- Package migration (javax → jakarta namespace)
- Spring Security 6.x patterns
- Modern annotation usage
- Spring Boot 3.2.x best practices

Task: Review this controller and suggest Spring 3 upgrades.
```

### When to Use
- ✅ Complex domains requiring specific expertise
- ✅ Need consistent tone across multiple prompts
- ✅ Want to activate specialized knowledge

### When to Skip
- ❌ Simple, obvious tasks
- ❌ General questions not requiring expertise

---

## Pattern 2: Few-shot Pattern

### What It Is
Provide example input/output pairs to demonstrate desired behavior.

### Why It Works
- Shows rather than tells
- Establishes format expectations
- Reduces ambiguity

### Template
```
Transform inputs using these examples:

Example 1:
Input: [example input 1]
Output: [example output 1]

Example 2:
Input: [example input 2]
Output: [example output 2]

Now transform:
Input: [actual input]
Output: ?
```

### Example: Package Updates
```markdown
Transform Java imports using these examples:

Example 1:
Input: import javax.validation.Valid;
Output: import jakarta.validation.Valid;

Example 2:
Input: import javax.servlet.http.HttpServletRequest;
Output: import jakarta.servlet.http.HttpServletRequest;

Now transform:
Input: import javax.persistence.Entity;
Output: ?
```

### When to Use
- ✅ Pattern-based transformations
- ✅ Consistent formatting needed
- ✅ Complex rules hard to describe

### When to Skip
- ❌ One-off unique tasks
- ❌ Rules are simple and obvious

---

## Pattern 3: Template Pattern

### What It Is
Provide a structured format for AI output.

### Why It Works
- Ensures consistency
- Makes responses parseable
- Easier to validate

### Template
```
Please provide your response in this format:

## Section 1: [Name]
- Item 1: [description]
- Item 2: [description]

## Section 2: [Name]
| Column A | Column B |
|----------|----------|
| Value    | Value    |

## Section 3: [Name]
[specific format]
```

### Example: Migration Checklist
```markdown
Please analyze this code and provide a migration checklist in this format:

## Required Changes
- [ ] Change 1: [description]
- [ ] Change 2: [description]

## Validation Steps
1. [step with expected outcome]
2. [step with expected outcome]

## Success Criteria
✓ Criterion 1
✓ Criterion 2
```

### When to Use
- ✅ Need consistent output format
- ✅ Output will be parsed/processed
- ✅ Multiple people using same prompt

### When to Skip
- ❌ Exploratory questions
- ❌ Format doesn't matter

---

## Pattern 4: Chain-of-Thought

### What It Is
Ask AI to show its reasoning process step-by-step.

### Why It Works
- Improves accuracy on complex reasoning
- Makes errors debuggable
- Helps you learn from AI logic

### Template
```
Solve this problem step by step:

1. First, analyze [aspect 1]
2. Then, consider [aspect 2]
3. Next, evaluate [aspect 3]
4. Finally, conclude [result]

Show your reasoning for each step.
```

### Example: Debugging
```markdown
Debug this Kafka consumer issue step by step:

1. First, check the consumer configuration
2. Then, verify the topic exists and has messages
3. Next, examine the consumer group state
4. Then, review offset management
5. Finally, check for serialization issues

Show your reasoning and findings for each step.
```

### When to Use
- ✅ Complex debugging
- ✅ Multi-step reasoning needed
- ✅ Want to understand AI's logic

### When to Skip
- ❌ Simple factual questions
- ❌ Just need final answer

---

## Combining Patterns

### Persona + Few-shot
```markdown
You are an expert Spring Boot developer.

Transform annotations using these examples:

Example: @RequestMapping(method=GET) → @GetMapping
Example: @RequestMapping(method=POST) → @PostMapping

Now transform this controller...
```

**Effect:** Role-specific transformations with clear examples

### Template + Chain-of-Thought
```markdown
Debug this issue step-by-step and format as:

## Step 1: [Name]
Reasoning: [your analysis]
Finding: [what you discovered]

## Step 2: [Name]
Reasoning: [your analysis]
Finding: [what you discovered]

[etc.]
```

**Effect:** Structured reasoning output

### All Four Together
```markdown
You are an expert database performance engineer. (Persona)

Optimize SQL queries using this pattern: (Few-shot)
Before: SELECT * FROM users WHERE active=true
After: SELECT id, name FROM users WHERE active=true

Analyze this query step-by-step: (Chain-of-Thought)
1. Identify performance issues
2. Suggest optimizations
3. Estimate impact

Format your response as: (Template)
## Analysis
[findings]

## Optimizations
- [ ] Change 1
- [ ] Change 2

## Expected Impact
[metrics]
```

**Effect:** Maximum structure and clarity

---

## 📚 Pattern Catalog

**White et al. (2023) documents 16+ patterns. The 4 above are most foundational.**

### Other Notable Patterns:

**Cognitive Verifier Pattern**
- Break complex questions into sub-questions
- Verify answers across multiple dimensions

**Recipe Pattern**
- Complete missing steps in sequences
- Fill gaps in procedures

**Fact Check List Pattern**
- Generate verifiable facts from AI output
- Enable human validation

**Meta Language Creation Pattern**
- Create shorthand for complex concepts
- Build team-specific vocabulary

**Full catalog:** arXiv:2302.11382

---

## 🎯 Quick Decision Guide

**Use Persona when:** You need specialized expertise or consistent tone

**Use Few-shot when:** Showing examples is clearer than explaining rules

**Use Template when:** Output format matters for processing/consistency

**Use Chain-of-Thought when:** Reasoning process is important, not just answer

---

## 💡 Pro Tips

### Start Simple
Begin with one pattern. Add others only if needed.

```markdown
# Simple (just Persona)
You are a Spring expert. Migrate this controller.

# Adding Few-shot
You are a Spring expert.
Example: javax → jakarta
Now migrate this controller.

# Adding Template
You are a Spring expert.
Example: javax → jakarta
Format as: [checklist]
Now migrate this controller.
```

### Test Pattern Effectiveness
Track which patterns save the most time for your use cases.

### Build Team Library
Document which pattern combinations work best for common tasks.

---

## 🚨 Common Mistakes

### ❌ Over-explaining
**Bad:**
```
You are an expert who knows about Spring Boot and Java and has worked with
enterprise applications for many years and understands migration patterns...
```

**Good:**
```
You are an expert Spring Boot migration specialist.
```

### ❌ Too many examples
**Bad:** 10 examples when 2-3 would suffice

**Good:** 2-3 representative examples covering edge cases

### ❌ Vague templates
**Bad:**
```
Please format nicely.
```

**Good:**
```
Format as:
## Section
- Item 1
- Item 2
```

---

## 📊 Pattern Effectiveness

| Pattern | Time to Learn | Accuracy Improvement | Consistency Improvement |
|---------|--------------|---------------------|------------------------|
| Persona | 5 min | +15% | +30% |
| Few-shot | 10 min | +25% | +40% |
| Template | 5 min | +10% | +50% |
| Chain-of-Thought | 15 min | +30% | +20% |

*(Approximate based on research and workshop feedback)*

---

## 🎓 Learning Path

### Day 1: Persona + Few-shot
- Apply to 2-3 tasks
- Measure time saved
- Notice quality improvement

### Week 1: Add Template
- Use for recurring tasks
- Build template library
- Share with team

### Month 1: Master Chain-of-Thought
- Apply to complex debugging
- Understand when overhead worth it
- Combine all four patterns

---

## ✅ Quick Checklist

Before writing a prompt, ask:

- [ ] Would a role/expertise help? → **Persona**
- [ ] Can I show examples? → **Few-shot**
- [ ] Does output format matter? → **Template**
- [ ] Is reasoning complex? → **Chain-of-Thought**

Use only the patterns that add value for your specific task.

---

**Key Takeaway:** These 4 patterns form the foundation. Master them before moving to advanced patterns (ReAct, Tree of Thoughts). They're proven, simple, and immediately valuable.
