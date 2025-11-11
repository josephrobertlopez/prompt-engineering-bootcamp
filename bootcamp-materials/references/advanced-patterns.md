# Advanced Prompt Engineering Patterns (Research-Backed)

**Sources:**
- Yao et al. (2022): "ReAct: Synergizing Reasoning and Acting in Language Models"
- Yao et al. (2023): "Tree of Thoughts: Deliberate Problem Solving with Large Language Models"

**Status:** 🟢 Tier 1 - Research-backed, proven effective

These advanced patterns build on foundational patterns for complex, multi-step tasks.

---

## Pattern 1: ReAct (Reason + Act)

**Source:** Yao et al. (2022)
**Use case:** Multi-step tasks with dependencies, need validation checkpoints

### What It Is
Structured cycles of reasoning, action, and observation.

**Pattern:** THINK → ACT → OBSERVE → THINK → ACT → OBSERVE...

### Why It Works
- Catches errors early (validation checkpoints)
- Makes dependencies explicit
- Enables precise debugging
- Clear rollback points

### Template
```markdown
## Phase [N]: [Name]

### THINK (Reasoning)
Question: [What must be considered?]
Answer: [Analysis]
Conclusion: [What to do]

### ACT (Action Items)
- Task 1: [specific action]
- Task 2: [specific action]

### OBSERVE (Validation)
Checkpoint: [How to verify]
Success criteria: [What success looks like]
If failure: [What to do]
Dependencies: [What must be complete first]
```

### Example: Spring Migration
```markdown
## Phase 1: Import Updates

### THINK
Question: What dependencies must be satisfied first?
Answer: Imports must compile before annotations can be updated.
Conclusion: Start with javax → jakarta package updates.

### ACT
- Task 1.1: Replace javax.validation.* with jakarta.validation.*
- Task 1.2: Replace javax.servlet.* with jakarta.servlet.*

### OBSERVE
Checkpoint: Run `mvn compile`
Success criteria: Code compiles without import errors
If failure: Review Spring 3 compatibility docs
Dependencies: None (this is first phase)

---

## Phase 2: Annotation Modernization

### THINK
Question: Can annotations be safely updated now?
Answer: Yes, imports validated (Phase 1 complete).
Conclusion: Modernize HTTP method annotations.

### ACT
- Task 2.1: Replace @RequestMapping(method=GET) with @GetMapping
- Task 2.2: Replace @RequestMapping(method=POST) with @PostMapping

### OBSERVE
Checkpoint: Check for @Deprecated warnings
Success criteria: No deprecated warnings, code compiles
If failure: Review Spring 3 annotation docs
Dependencies: Phase 1 complete (imports updated)
```

### When to Use
✅ Multi-phase migrations
✅ Tasks with clear dependencies
✅ Need early error detection
✅ Want clear rollback points

### When to Skip
❌ Single-step tasks
❌ No dependencies between steps
❌ Obvious execution order

---

## Pattern 2: Tree of Thoughts

**Source:** Yao et al. (2023)
**Use case:** Decisions with multiple valid approaches, tradeoffs matter

### What It Is
Explore multiple solution branches, evaluate each, choose best fit.

**Pattern:** Generate Branches → Evaluate Each → Select Best

### Why It Works
- Considers alternatives systematically
- Makes tradeoffs explicit
- Documents reasoning for future reference
- Prevents premature optimization

### Template
```markdown
## Decision Point: [Question]

### Context
[Background and constraints]

### Tree of Thoughts: Generate Branches

**BRANCH A: [Option A]**
```[code or description]```

Evaluation:
- Pros: [benefits]
- Cons: [drawbacks]
- Context fit: [Excellent/Good/Fair/Poor]
- Effort: [hours]
- Risk: [Low/Medium/High]

**BRANCH B: [Option B]**
[same structure]

**BRANCH C: [Option C]**
[same structure]

### Tree Evaluation

| Branch | Context Fit | Effort | Risk | Quality | Recommendation |
|--------|-------------|--------|------|---------|----------------|
| A | ✅ Excellent | 0h | Very Low | Good | ⭐ RECOMMENDED |
| B | ⚠️ Good | 4h | Medium | Excellent | Consider for v2 |
| C | ❌ Poor | 16h | High | Excellent | Future work |

### Decision: Branch A

Rationale: [Why this choice is best for context]

Future Work: [What other branches might be worth revisiting]
```

### Example: Exception Handling
```markdown
## Decision Point: Exception Handling Strategy

### Context
UserController uses try-catch with ResponseEntity. Spring 3 offers ProblemDetail (RFC 7807) for structured errors.

### Tree of Thoughts: Generate Branches

**BRANCH A: Keep Current ResponseEntity Pattern**
```java
try {
    User user = userService.createUser(user);
    return ResponseEntity.status(HttpStatus.CREATED).body(user);
} catch (IllegalArgumentException e) {
    return ResponseEntity.badRequest().build();
}
```

Evaluation:
- Pros:
  - ✅ Minimal changes (lowest risk)
  - ✅ Existing clients unaffected
  - ✅ Fast migration
- Cons:
  - ❌ Not using Spring 3 ProblemDetail feature
  - ❌ Error responses are minimal
- Context fit: ✅ Excellent for migration-focused work
- Effort: 0 hours
- Risk: Very low

**BRANCH B: Adopt ProblemDetail**
```java
try {
    User user = userService.createUser(user);
    return ResponseEntity.status(HttpStatus.CREATED).body(user);
} catch (IllegalArgumentException e) {
    ProblemDetail pd = ProblemDetail.forStatusAndDetail(
        HttpStatus.BAD_REQUEST, e.getMessage()
    );
    return ResponseEntity.badRequest().body(pd);
}
```

Evaluation:
- Pros:
  - ✅ Modern Spring 3 pattern
  - ✅ Structured error responses
- Cons:
  - ❌ API contract changes (may break clients)
  - ❌ Requires more testing
  - ❌ Scope creep (feature enhancement)
- Context fit: ⚠️ Good for greenfield work
- Effort: 4-6 hours
- Risk: Medium

**BRANCH C: Full RFC 7807 with Error Catalog**
[Implementation with @ControllerAdvice, error codes, etc.]

Evaluation:
- Pros:
  - ✅ Enterprise-grade
  - ✅ Comprehensive error catalog
- Cons:
  - ❌ Over-engineered for simple CRUD API
  - ❌ Requires extensive documentation
- Context fit: ❌ Poor for current scope
- Effort: 16-24 hours
- Risk: High

### Tree Evaluation

| Branch | Context Fit | Effort | Risk | Quality | Recommendation |
|--------|-------------|--------|------|---------|----------------|
| A | ✅ Excellent | 0h | Very Low | Good | ⭐ RECOMMENDED |
| B | ⚠️ Good | 4-6h | Medium | Excellent | Consider for v2 |
| C | ❌ Poor | 16-24h | High | Excellent | Future work |

### Decision: Branch A (Keep Current Pattern)

Rationale: This migration focuses on framework upgrade, not feature enhancements. Branch A minimizes risk, reduces testing scope, and enables faster deployment. Branch B is a good candidate for separate enhancement work after migration is stable.
```

### When to Use
✅ Multiple valid technical approaches exist
✅ Tradeoffs depend on specific context
✅ Team needs to understand decision rationale
✅ Future developers will ask "why X over Y?"

### When to Skip
❌ Only one reasonable approach
❌ Decision is obvious
❌ Simple "best practice" applies

---

## Pattern 3: Meta-prompting (Orchestration)

**Use case:** Complex tasks requiring multiple patterns combined

### What It Is
A prompt that orchestrates other prompts/patterns.

**Pattern:** Synthesize context from multiple sources → Generate using all

### Why It Works
- Combines strengths of different patterns
- Ensures all context considered
- Creates reproducible workflows

### Template
```markdown
# [Task]: Complete Pattern Synthesis

## Context Synthesis (Meta-prompting)

**From [Source 1] (Pattern X):**
✓ [Key information extracted]
✓ [Constraints/rules applied]

**From [Source 2] (Pattern Y):**
✓ [Decisions made]
✓ [Approach chosen]

**From [Source 3] (Pattern Z):**
✓ [Execution order established]
✓ [Validation checkpoints defined]

## Generation Instructions

Using all context above:
1. [Step combining patterns]
2. [Step showing orchestration]
3. [Step validating result]

Generate [desired output].
```

### Example: Complete Migration
```markdown
# Code Generation: Complete Pattern Synthesis

## Context Synthesis

**From System Prompt (Persona + Few-shot):**
✓ Role: Spring Boot migration specialist
✓ Transformation rules: javax → jakarta examples provided
✓ Quality standards: Must compile, pass tests

**From Task Specification (Template):**
✓ File: UserController.java
✓ Required changes: 7 endpoints, modern annotations
✓ Success criteria: Compiles, tests pass, APIs unchanged

**From ReAct Execution Plan:**
✓ Phase 1: Update imports first
✓ Phase 2: Modernize annotations second
✓ Phase 3: Verify injection third

**From Tree of Thoughts Decisions:**
✓ Exception handling: Keep current pattern (Branch A)
✓ Validation: Keep current @Valid (Branch A)

## Generation Instructions

Generate Spring Boot 3.2 code following this orchestration:

1. **Phase 1 (from ReAct):** Update imports using few-shot rules
2. **Phase 2 (from ReAct):** Modernize annotations per system prompt
3. **Phase 3 (from ReAct):** Verify injection patterns
4. **Decision implementation (from Tree):** Keep exception handling unchanged

Validate against success criteria from task specification.

Please generate the complete migrated UserController.java.
```

### When to Use
✅ Complex tasks with multiple concerns
✅ Combining system prompts, task specs, plans, decisions
✅ Need reproducible workflow
✅ Teaching how patterns work together

### When to Skip
❌ Simple tasks
❌ Single pattern sufficient
❌ Ad-hoc one-off work

---

## Combining All Patterns

### Foundation → Advanced Pipeline

**Step 1: Foundational Patterns (Setup)**
- Persona: Establish expertise
- Few-shot: Provide transformation examples
- Template: Define output format

**Step 2: Advanced Patterns (Execution)**
- ReAct: Structure multi-phase execution
- Tree of Thoughts: Make key decisions
- Meta-prompting: Synthesize everything

**Result:** Complete, orchestrated workflow

---

## 📊 Pattern Comparison

| Pattern | Complexity | Time to Learn | Best For |
|---------|-----------|--------------|----------|
| Persona | Low | 5 min | Setting context |
| Few-shot | Low | 10 min | Pattern transformations |
| Template | Low | 5 min | Structured output |
| Chain-of-Thought | Medium | 15 min | Complex reasoning |
| ReAct | Medium | 30 min | Multi-phase execution |
| Tree of Thoughts | Medium | 30 min | Decision exploration |
| Meta-prompting | High | 45 min | Full workflow orchestration |

---

## 🎯 When to Use Which

### Simple Task (5-15 min)
**Use:** Persona + Few-shot
**Skip:** ReAct, Tree of Thoughts, Meta-prompting

### Medium Task (30-60 min)
**Use:** Persona + Few-shot + Template + Chain-of-Thought
**Optional:** ReAct if phases clear

### Complex Task (multiple hours)
**Use:** All patterns orchestrated
- Persona + Few-shot (setup)
- Template (output format)
- ReAct (phased execution)
- Tree of Thoughts (key decisions)
- Meta-prompting (orchestration)

---

## Mapping to Production Practices

### ReAct Pattern Maps To:
- Phased rollout plans
- Migration runbooks
- ADR implementation notes
- CI/CD pipeline stages

### Tree of Thoughts Maps To:
- ADR "Alternatives Considered" section
- Decision matrices
- RFC comparison tables
- Architecture review documents

### Meta-prompting Maps To:
- Pull request descriptions (synthesizing multiple concerns)
- Implementation plans (combining specifications + decisions)
- Code review checklists (all context in one place)

---

## 💡 Pro Tips

### Start with Foundation
Master Persona, Few-shot, Template, Chain-of-Thought before attempting advanced patterns.

### ReAct for Dependencies
If steps have dependencies, use ReAct. Otherwise, simple list fine.

### Tree of Thoughts for Real Decisions
Don't force Tree of Thoughts if decision is obvious. Use only when alternatives genuinely exist.

### Meta-prompting for Learning
Meta-prompting shows how patterns work together. Once learned, can apply patterns through simpler formats (ADRs, config files).

---

## 🚨 Common Mistakes

### ❌ Using advanced patterns for simple tasks
Overhead not justified. Stick to foundational patterns.

### ❌ Creating fake branches in Tree of Thoughts
If only one reasonable approach exists, don't manufacture alternatives.

### ❌ ReAct phases without real dependencies
If steps are independent, simple list better than elaborate ReAct structure.

### ❌ Meta-prompting everything
Once patterns learned, apply through simpler formats (ADRs, prompts, config).

---

## ✅ Success Criteria

You've mastered advanced patterns when:

- ✅ Can identify when ReAct adds value vs overhead
- ✅ Use Tree of Thoughts for genuine decisions, not fake ones
- ✅ Can orchestrate patterns without explicit meta-prompt
- ✅ Know when simpler approach (ADR + prompt) is better

---

**Key Takeaway:** Advanced patterns are powerful for complex tasks. But foundation patterns (Persona, Few-shot, Template, Chain-of-Thought) solve 80% of needs. Use advanced patterns only when complexity justifies overhead.
