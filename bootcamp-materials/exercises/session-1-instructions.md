# SESSION 1: Framework Introduction - Exercise Instructions

**Duration**: 90 minutes total
**Materials Needed**: FY26_Accenture_Priorities_Guide.txt, blank markdown editor

---

## Overview

In this session, you'll learn to build prompt file systems from first principles using the **3-Question Framework**. You will NOT receive pre-filled templates—instead, you'll extract structure directly from source materials.

**The 3-Question Framework**:
1. **What stays constant?** → `knowledge-base.md`
2. **What's unique?** → `specification.md`
3. **How to execute?** → `implementation-plan.md`

---

## Exercise 1: Build knowledge-base.md (30 minutes)

### Goal
Extract "what stays constant" from the FY26 Priorities Guide and document it as a knowledge-base.md file.

### Materials
- `FY26_Accenture_Priorities_Guide.txt`
- Blank markdown file named `knowledge-base.md`

### Instructions

1. **Open the FY26 guide** with a "beginner's mind" - pretend you know nothing about Accenture priorities

2. **Ask yourself**: What information applies to EVERY employee's priorities (not just mine)?

3. **Look for patterns**:
   - Fixed lists (categories, metric types, frameworks)
   - Definitions that don't change per person
   - Rules or constraints that apply universally

4. **Extract and document** the following (minimum requirements):
   - 4 strategic categories (Client Value, AI Enablement, etc.)
   - ABCD reflection framework definitions
   - 28 metric types available for selection
   - Any rules about how many priorities, metrics per priority, etc.

5. **Structure your knowledge-base.md**:
   ```markdown
   # Knowledge Base: FY26 Accenture Priorities System

   ## Strategic Categories
   [List the 4 categories with brief descriptions]

   ## ABCD Reflection Framework
   [Define A, B, C, D components]

   ## Available Metrics
   [List all 28 metric types]

   ## System Rules & Constraints
   [Document selection rules, limits, requirements]
   ```

### Validation Checkpoint (minute 25)

**Pair with a neighbor** and review each other's knowledge-base using these questions:

1. ✓ Can another person use this knowledge-base for THEIR priorities?
2. ✓ Is anything user-specific mixed in? (if yes, remove it)
3. ✓ Are all 28 metrics documented?
4. ✓ Does ABCD framework have clear definitions?

**Feedback format**: 2 stars (strengths) + 1 wish (improvement)

### Common Mistakes to Avoid

❌ **Mistake #1**: Including example data
- Bad: "John's priority: Client Value - Increase satisfaction 15%"
- Good: "Client Value category focuses on customer outcomes"

❌ **Mistake #2**: Omitting framework explanations
- Bad: "ABCD framework exists"
- Good: "A=Accomplishments (what), B=Business impact (why), C=Challenges (obstacles), D=Development (growth)"

❌ **Mistake #3**: Missing metric constraints
- Bad: "28 metrics available"
- Good: "1-3 metrics per priority, 28 options: [detailed list]"

---

## Exercise 2: Build specification.md (15 minutes)

### Goal
Document YOUR specific FY26 priorities (the "what's unique" part) in a specification.md file.

### Materials
- Your completed `knowledge-base.md`
- Blank file named `specification.md`
- FY26 guide (for reference)

### Instructions

1. **Reference (don't duplicate) your knowledge-base**
   - Link to sections instead of copying content
   - Example: "Using categories from knowledge-base.md Section 2..."

2. **Document YOUR instance-specific data**:
   - Your name and role
   - Your 4 chosen priorities (which categories?)
   - Selected metrics (1-3 per priority from the 28 options)
   - Timeline for this review cycle
   - Any role-specific context

3. **Structure your specification.md**:
   ```markdown
   # Specification: [Your Name]'s FY26 Priorities

   ## Instance Metadata
   - Name: [Your name]
   - Role: [Your title]
   - Timeline: Q1 FY26 (Oct 2025 - Dec 2025)

   ## Selected Priorities
   From knowledge-base.md Strategic Categories:
   1. [Category] → [Your specific priority goal]
   2. [Category] → [Your specific priority goal]
   3. [Category] → [Your specific priority goal]
   4. [Category] → [Your specific priority goal]

   ## Selected Metrics
   Priority 1: [Metric name from KB] - [target value]
   Priority 2: [Metric names] - [targets]
   ...

   ## Success Criteria
   [What does success look like for YOUR priorities?]
   ```

### Validation Checkpoint (minute 13)

**Self-check**:
1. ✓ Did I reference knowledge-base instead of duplicating it?
2. ✓ Is this specific to MY priorities (not generic)?
3. ✓ Could someone understand my goals without additional explanation?

---

## Exercise 3: Build implementation-plan.md (20 minutes)

### Goal
Create step-by-step execution instructions for completing YOUR FY26 priorities workflow.

### Materials
- Your `knowledge-base.md`
- Your `specification.md`
- Blank file named `implementation-plan.md`

### Instructions

1. **Map the workflow** from selection to completion:
   - How do you select priorities?
   - How do you assign metrics?
   - How do you document in Workday?
   - How do you prepare for manager review?

2. **Write actionable steps** (not vague descriptions):
   - ✓ Good: "Open Workday → Navigate to 'My Priorities' → Click 'Add Priority'"
   - ✗ Bad: "Review and update priorities"

3. **Include validation** for each step:
   - Input: What you need before starting
   - Output: What you produce
   - Validation: How you know it succeeded

4. **Structure your implementation-plan.md**:
   ```markdown
   # Implementation Plan: FY26 Priorities Setup

   ## Prerequisites
   - knowledge-base.md reviewed
   - specification.md complete
   - Workday access confirmed

   ## Execution Steps

   ### Step 1: Select Priorities from Knowledge-Base
   **Input**: FY26 Strategic Categories (KB Section 2)
   **Action**: Choose 4 priorities (1-2 per category)
   **Output**: List of 4 priorities mapped to categories
   **Validation**: Each priority aligns with one of the 4 categories

   ### Step 2: Assign Metrics
   **Input**: 28 available metrics (KB Section 3)
   **Action**: Select 1-3 metrics per priority
   **Output**: Metric assignments for all 4 priorities
   **Validation**: Total metrics ≤ 12, each priority has 1-3 metrics

   ### Step 3: Document in Workday
   **Input**: Priorities + metrics from Steps 1-2
   **Action**: [Specific Workday navigation steps]
   **Output**: Workday priorities page populated
   **Validation**: All 4 priorities visible in system

   ### Step 4: Prepare for Manager Review
   **Input**: Completed Workday entries
   **Action**: [Review preparation steps]
   **Output**: Review meeting scheduled
   **Validation**: Manager has visibility to priorities

   ## Rollback Plan
   If Step X fails → [recovery action]
   ```

### Validation Checkpoint (minute 18)

**Triangle Test** (pair exercise):
1. Give your 3 files (knowledge-base, spec, implementation) to a partner
2. Partner reads silently for 2 minutes
3. Partner answers: "Could I execute this? What's missing?"
4. Swap roles

---

## Session Wrap-Up

### Key Takeaways
✓ You built a complete 3-file system from scratch (no templates!)
✓ You learned to distinguish constant vs. unique information
✓ You practiced extraction-based discovery learning

### Next Session Preview
In SESSION 2, you'll:
- Build specification.md and implementation-plan.md for a new domain
- Apply the same framework to different source materials
- Complete exercises faster (skill transfer!)

### Homework (Optional)
Apply the 3-Question Framework to a different domain:
- **Recipe**: constant=cooking techniques | unique=ingredients | execute=steps
- **API docs**: constant=endpoints | unique=parameters | execute=request flow
- **Training manual**: constant=concepts | unique=scenarios | execute=exercises

Bring your examples to SESSION 2 for a 2-minute show-and-tell!

---

## Instructor Notes

**Timing Breakdown**:
- Exercise 1: 30 min (25 min work + 5 min validation)
- Exercise 2: 15 min (13 min work + 2 min self-check)
- Exercise 3: 20 min (18 min work + 2 min Triangle Test)
- Total: 65 minutes of exercises (25 minutes remaining for slides/breaks)

**Circulation Tips**:
- Minutes 0-10: Silent work (don't interrupt)
- Minutes 10-20: Answer questions, coach individuals
- Minute 25: Call time for validation checkpoint

**Common Blockers**:
- "I don't know where to start" → Point to Table of Contents in guide
- "Is this too detailed?" → "If it helps someone NEW understand, include it"
- "What if something is both constant AND unique?" → "If it applies to ALL instances, it's constant"

**Expected Outcomes**:
- 80%+ participants complete Exercise 1 in allocated time
- 90%+ correctly distinguish constant vs unique in validation
- All participants have at least partial knowledge-base.md by end of session
