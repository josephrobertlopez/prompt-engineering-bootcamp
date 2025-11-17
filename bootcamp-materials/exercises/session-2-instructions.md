# SESSION 2: Specification + Implementation - Exercise Instructions

**Duration**: 90 minutes total
**Prerequisites**: SESSION 1 completed (knowledge-base.md built)
**Materials Needed**: Your knowledge-base.md from SESSION 1, blank markdown editor

---

## Overview

In SESSION 2, you'll complete your prompt file system by building specification.md and implementation-plan.md. You already know the 3-Question Framework—now you'll apply it with deeper complexity.

**SESSION 1 Recap**:
- ✓ Q1: What stays constant? → knowledge-base.md (you built this!)
- ➜ Q2: What's unique? → specification.md (today)
- ➜ Q3: How to execute? → implementation-plan.md (today)

---

## Exercise 1: Build specification.md (25 minutes)

### Goal
Document YOUR specific FY26 priorities instance in a specification.md file that references (not duplicates) your knowledge-base.md.

### Materials
- Your completed `knowledge-base.md` from SESSION 1
- `FY26_Accenture_Priorities_Guide.txt` (for your specific data)
- Blank file named `specification.md`

### Instructions

1. **Review your knowledge-base.md** (2 min)
   - Remind yourself what's in there
   - This is your source of truth for "what stays constant"

2. **Extract YOUR instance data** from the guide (5 min):
   - Your name, role, team
   - Your 4 chosen priorities (from which categories?)
   - Your selected metrics (1-3 per priority)
   - Your timeline (Q1/Q2/etc.)

3. **Document in specification.md** using this structure:

   ```markdown
   # Specification: [Your Name]'s FY26 Priorities

   ## Instance Metadata
   - Employee: [Your name]
   - Role: [Your title/level]
   - Team: [Your practice/group]
   - Review Period: Q1 FY26 (Oct-Dec 2025)
   - Manager: [Name]

   ## Scope Definition
   This specification covers my individual FY26 priorities. It references
   the strategic framework from knowledge-base.md and applies it to my
   specific role and goals.

   ## Selected Priorities
   Using the 4 Strategic Categories from knowledge-base.md Section 2:

   1. **Category**: Client Value
      - **My Priority**: Increase NPS for Financial Services clients by 10 points
      - **Rationale**: Aligns with practice focus on customer retention

   2. **Category**: AI Enablement
      - **My Priority**: [Your specific goal]
      - **Rationale**: [Why this matters for your role]

   [Continue for all 4 priorities]

   ## Selected Metrics
   From knowledge-base.md Section 3 (28 available metrics):

   **Priority 1 Metrics**:
   - Client satisfaction (NPS) - Target: +10 points
   - Revenue retention (%) - Target: 95%

   **Priority 2 Metrics**:
   [Your selected metrics with targets]

   [Continue for all 4 priorities, 1-3 metrics each]

   ## Constraints
   - Timeline: Must complete by Dec 31, 2025
   - Resources: [Budget, team size, tools available]
   - Dependencies: [Relies on X team, Y system, etc.]

   ## Success Criteria
   This specification is successful if:
   1. All 4 priorities are measurable via selected metrics
   2. Priorities align with both personal development goals and team objectives
   3. Manager approves in review meeting
   4. Metrics are trackable in Workday system
   ```

4. **Key principle**: REFERENCE, don't REPEAT
   - ✓ Good: "Using categories from knowledge-base.md Section 2..."
   - ✗ Bad: Copying the entire category list into specification.md

### Anti-Patterns to Avoid

**❌ Mistake #1**: Duplicating knowledge-base content
```markdown
# specification.md (DON'T DO THIS)
## Strategic Categories
1. Client Value - focuses on customer outcomes...
```

**✓ Fix**: Reference, don't repeat
```markdown
## Selected Priorities
Using categories from knowledge-base.md:
- Priority 1: Client Value → [specific goal]
```

**❌ Mistake #2**: Being too vague
```markdown
Selected metrics: Some customer satisfaction stuff
```

**✓ Fix**: Be specific with targets
```markdown
Selected metrics from KB Section 3:
- Client satisfaction (NPS) - Target: +10 points from Q4 FY25 baseline
```

### Validation Checkpoint (minute 23)

**Pair review**:
1. Exchange specification.md files with a partner
2. Partner checks:
   - ✓ Does it reference knowledge-base.md (not duplicate)?
   - ✓ Are priorities specific (not generic)?
   - ✓ Are metrics measurable with clear targets?
   - ✓ Could I understand the goals without asking clarifying questions?

3. **Feedback**: 2 stars + 1 wish (2 min each direction)

---

## Exercise 2: Build implementation-plan.md (30 minutes)

### Goal
Create a step-by-step execution plan that transforms your specification into reality. Anyone with your 3 files should be able to execute this plan.

### Materials
- Your `knowledge-base.md`
- Your `specification.md` (from Exercise 1)
- Blank file named `implementation-plan.md`

### Instructions

1. **Map the end-to-end workflow** (5 min):
   - What's the first action?
   - What happens next?
   - What's the final deliverable?
   - What could go wrong?

2. **Write steps with clear structure**:

   ```markdown
   # Implementation Plan: FY26 Priorities Execution

   ## Prerequisites
   - [ ] knowledge-base.md reviewed and understood
   - [ ] specification.md complete with all 4 priorities
   - [ ] Workday system access confirmed
   - [ ] Manager review meeting scheduled

   ## Execution Steps

   ### Phase 1: Priority Selection

   #### Step 1: Review Strategic Categories
   **Input**: knowledge-base.md Section 2 (4 Strategic Categories)
   **Action**:
   1. Read descriptions of Client Value, AI Enablement, Great Place to Work, Financial Performance
   2. Identify which categories align with my role and team goals
   3. Select 1-2 priorities per category (total 4)

   **Output**: Draft list of 4 priorities with category mappings
   **Validation**: Each priority clearly belongs to one category
   **Time estimate**: 15 minutes

   #### Step 2: Map Priorities to Metrics
   **Input**:
   - Draft priorities from Step 1
   - knowledge-base.md Section 3 (28 available metrics)

   **Action**:
   1. For each priority, identify 1-3 measurable metrics
   2. Ensure metrics are trackable in Workday
   3. Set specific target values (not "improve" but "+10 points")

   **Output**: Metric assignments for all 4 priorities
   **Validation**:
   - Total metrics: 4-12 (1-3 per priority)
   - Each metric has a target value
   - All metrics exist in knowledge-base.md list

   **Time estimate**: 20 minutes

   ### Phase 2: System Documentation

   #### Step 3: Enter Priorities in Workday
   **Input**: Completed priorities and metrics from Steps 1-2

   **Action**:
   1. Log into Workday → Navigate to "Performance" tab
   2. Click "My Goals" → "Add New Goal"
   3. For each priority:
      a. Enter goal title and description
      b. Select strategic category from dropdown
      c. Add metrics with target values
      d. Set timeline (review period)
   4. Save each priority

   **Output**: 4 priorities visible in Workday "My Goals" section
   **Validation**:
   - All 4 priorities appear in system
   - Metrics display correctly
   - Manager has visibility (check sharing settings)

   **Time estimate**: 30 minutes

   #### Step 4: Document ABCD Reflections
   **Input**: knowledge-base.md Section 2.2 (ABCD Framework definitions)

   **Action**:
   For each priority, write:
   - **A**ccomplishments: What did you achieve?
   - **B**usiness Impact: Why does it matter?
   - **C**hallenges: What obstacles did you face?
   - **D**evelopment: How did you grow?

   **Output**: ABCD entries for all 4 priorities in Workday
   **Validation**: Each section has 2-3 bullet points minimum
   **Time estimate**: 45 minutes

   ### Phase 3: Manager Review

   #### Step 5: Prepare Review Meeting
   **Input**: Completed Workday entries from Steps 3-4

   **Action**:
   1. Export priorities summary from Workday (PDF)
   2. Prepare 3 talking points per priority:
      - Why this priority matters
      - How you'll measure success
      - What support you need from manager
   3. Send meeting invite with summary PDF attached

   **Output**: Scheduled review meeting with prepared materials
   **Validation**: Manager confirms meeting, receives PDF in advance
   **Time estimate**: 15 minutes

   #### Step 6: Conduct Review & Finalize
   **Input**: Manager feedback from review meeting

   **Action**:
   1. Present priorities using ABCD framework
   2. Collect manager feedback and suggestions
   3. Adjust metrics or targets if needed
   4. Get manager approval signature in Workday

   **Output**: Approved FY26 priorities locked in system
   **Validation**: Status = "Approved" in Workday
   **Time estimate**: 30-minute meeting

   ## Rollback Plan

   **If Step 3 fails** (Workday system error):
   - Save priorities in local spreadsheet as backup
   - Contact IT support for Workday access
   - Use backup spreadsheet for manager review if system down

   **If Step 6 fails** (manager requests major changes):
   - Return to Step 1 with manager's guidance
   - Re-select priorities based on feedback
   - Re-run Steps 2-5 with adjusted priorities

   ## Success Criteria
   - [ ] All 4 priorities documented in Workday
   - [ ] ABCD reflections complete for each priority
   - [ ] Manager approval obtained
   - [ ] Review meeting completed
   - [ ] Total time: ≤ 3 hours (across all steps)
   ```

3. **Best practices for implementation plans**:
   - ✓ One action per step (not "review and update")
   - ✓ Observable outcomes (not vague "understand")
   - ✓ Clear dependencies (Step 3 requires output of Step 2)
   - ✓ Validation criteria (how to know step succeeded)
   - ✓ Time estimates (helps with planning)

### Validation Checkpoint (minute 28)

**Triangle Test** (handoff simulation):

1. **Find a partner** who didn't see your spec before
2. **Give them your 3 files**:
   - knowledge-base.md
   - specification.md
   - implementation-plan.md

3. **Partner reads silently** (3 min) and answers:
   - "Could I execute this plan without asking you questions?"
   - "What's unclear or missing?"

4. **Discuss feedback** (2 min), then **swap roles**

**This simulates real-world handoff**: Can someone else use your documentation?

---

## Exercise 3: Peer Review Circle (20 minutes)

### Goal
Get feedback from multiple perspectives, identify integration issues between your 3 files.

### Format
Groups of 3 people, rotating presenter role.

### Instructions

1. **Form groups of 3** (instructor will assign)

2. **Assign roles**:
   - Person A: Presents first
   - Person B: Presents second
   - Person C: Presents third

3. **Round 1: Person A presents** (6 minutes)
   - Min 1-3: Share screen, walk through your 3-file system
   - Min 4-5: B and C ask clarifying questions
   - Min 6: B and C each give feedback (2 stars + 1 wish)

4. **Round 2: Person B presents** (6 minutes, same format)

5. **Round 3: Person C presents** (6 minutes, same format)

6. **Return to main room** (2 min)

### Review Questions to Ask

**For knowledge-base.md**:
- Is anything user-specific mixed in?
- Are definitions clear enough for a new team member?
- Are all framework components documented?

**For specification.md**:
- Does it reference (not duplicate) knowledge-base?
- Are priorities specific and measurable?
- Is the scope clearly bounded?

**For implementation-plan.md**:
- Are steps actionable (not vague)?
- Is every step validated?
- Could I execute this without domain expertise?

### Common Integration Issues

**Issue #1**: Orphaned specifications
- Spec references "metric types" but knowledge-base doesn't define them
- **Fix**: Audit all references, ensure knowledge-base completeness

**Issue #2**: Implementation assumes knowledge
- Steps skip crucial context
- **Fix**: Every step should cite knowledge-base or specification source

**Issue #3**: Circular references
- "See implementation for details" in spec
- **Fix**: Clear hierarchy: KB → Spec → Implementation

---

## Session Wrap-Up

### What You've Accomplished
✓ Built specification.md from your instance data
✓ Created implementation-plan.md with actionable steps
✓ Validated through Triangle Test and peer review
✓ Completed a full 3-file prompt system

**Time comparison**: Did you complete exercises faster than SESSION 1?
(Expected: Yes, due to skill transfer and framework familiarity)

### Real-World Applications

Apply this 3-file system to:
- Client project documentation
- API integration guides
- Training program design
- Process improvement initiatives
- Personal knowledge management

**Key**: Start with raw materials, extract structure using the framework.

### Reflection Questions (Individual, 5 minutes)

1. **Biggest insight** from this workshop?
2. **Immediate application** you'll try this week?
3. **Challenge** you anticipate?
4. **One question** still unanswered?

Optional: Share with group if comfortable.

---

## Homework & Next Steps

**Practice challenge**:
Pick 1 work project this week and apply the 3-Question Framework:
1. Identify source materials (docs, specs, emails)
2. Build knowledge-base.md (constants)
3. Build specification.md (your instance)
4. Build implementation-plan.md (execution)

**Share results** with your team or bring to follow-up session.

### Resources to Keep

- Your completed 3-file system (reference example)
- FY26 Priorities Guide (example domain)
- 3-Question Framework diagram (mental model)
- These exercise instructions (reusable pattern)

---

## Instructor Notes

**Timing Breakdown**:
- Exercise 1: 25 min (23 min work + 2 min validation)
- Exercise 2: 30 min (28 min work + 2 min Triangle Test)
- Exercise 3: 20 min (18 min peer review + 2 min debrief)
- Total: 75 minutes of exercises (15 minutes remaining for slides/reflection)

**Circulation Tips**:
- Minutes 0-15: Silent work on specification.md
- Minutes 15-25: Answer questions, help with referencing pattern
- Minute 23: Call time for pair review
- Minutes 30-55: Circulate during implementation-plan work
- Visit each peer review group briefly (in-person) or join breakout rooms (virtual)

**Expected Completion Rates**:
- 90%+ complete specification.md in 25 min (faster than SESSION 1 due to familiarity)
- 80%+ complete implementation-plan.md core steps (full plan may extend beyond session)
- 100% participate in peer review

**Common Blockers**:
- "Should I copy this from knowledge-base?" → No, reference it
- "How detailed should implementation steps be?" → Detailed enough that someone else could execute
- "What if my plan is different from others?" → Good! Plans should be instance-specific

**Advanced Patterns** (for fast finishers):
- Add conditional logic to implementation (IF priority type = X, THEN use workflow Y)
- Create specification-template.md for your team (fill-in-the-blanks version)
- Add validation rules from knowledge-base to implementation (automated checks)
