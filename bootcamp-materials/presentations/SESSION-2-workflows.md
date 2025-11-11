# SESSION 2: WORKFLOWS AND ORCHESTRATION
## Orchestrate All 5 Prompt Modes for Complete Migration Workflow

**Duration:** 90 minutes
**Format:** 15-min presentation + 60-min hands-on + 15-min review
**Prerequisites:**
- Completed Session 1 (understand Constitution and Specification modes)
- spring-migration-demo repository cloned
- AI tool (Copilot/Claude/Windsurf) configured
- Basic understanding of prompt file structure

**Learning Objectives:**
- Create Planning mode file (Mode 3) for structured execution
- Create ABCD mode file (Mode 4) for decision documentation
- Create Implementation mode file (Mode 5) to synthesize all modes
- Execute complete 5-mode workflow for controller migration
- Understand how to orchestrate modes for any coding task

---

## PART 1: PRESENTATION (0-15 minutes)

### Slide 1: From Individual Modes to Complete Workflows (3 min)

**Session 1 Recap:**
- You created Constitution (Mode 1) - Reusable rules
- You created Specification (Mode 2) - File-specific targets
- You saw these work with UserController

**Today's Goal:**
- Add Planning (Mode 3) - Execution steps
- Add ABCD (Mode 4) - Decision documentation
- Add Implementation (Mode 5) - Synthesis and generation
- **Execute complete 5-mode workflow**

**The Shift:**
- Session 1: Individual prompt files (2 modes)
- Session 2: Orchestrated workflow (all 5 modes together)

---

### Slide 2: The 3 Missing Modes Quick Overview (4 min)

**Mode 3: Planning** - Break work into ordered steps
- **Example:** "Phase 1: Imports (2 min), Phase 2: Annotations (5 min), Phase 3: Testing (5 min)"
- **Time:** 5 min to write, reusable for similar files
- **Uses:** ReAct technique (Think → Act → Observe)

**Mode 4: ABCD Clarification** - Document decisions
- **Example:** "Exception handling: Option A (simple) vs B (ProblemDetail) vs C (RFC 7807) vs D (keep current)"
- **Time:** 5 min when ambiguous, skip if obvious
- **Uses:** Tree of Thoughts technique (explore alternatives)

**Mode 5: Implementation** - Pull everything together
- **Example:** "Context loaded: Constitution ✓, Specification ✓, Planning ✓, ABCD ✓ → Generate code"
- **Time:** 2 min to write, AI generates immediately
- **Uses:** All techniques combined

**Key Insight:** Modes 1-4 provide context, Mode 5 triggers generation

---

### Slide 3: How Planning Mode Structures Execution (3 min)

**Without Planning:**
```
AI: "I'll migrate your controller"
[Makes random changes, unclear order]
```

**With Planning:**
```markdown
## Phase 1: Package Updates (Est: 2 min)
Why first: Must compile before other changes
- javax.servlet → jakarta.servlet
- Validation: Code compiles

## Phase 2: Annotations (Est: 5 min)
Why second: Build on updated imports
- @RequestMapping → @GetMapping
- Validation: Endpoints correct

## Phase 3: Testing (Est: 5 min)
Why last: Validate everything works
- Run unit tests
- Validation: All tests green
```

**Benefits:**
- ✅ Logical order (dependencies clear)
- ✅ Small tasks (easy to debug)
- ✅ Validation checkpoints
- ✅ Time estimates (manage scope)

---

### Slide 4: How ABCD Mode Documents Decisions (3 min)

**When to Use ABCD:**
- Multiple valid approaches exist
- Tradeoffs matter for your context
- Team needs to understand why you chose X

**Example Decision:**
```markdown
---
Clarification Question: Exception Handling

UserController currently uses try-catch with ResponseEntity.
How should we handle exceptions in Spring 3?

Recommended: Option B - ProblemDetail

Reasoning: API clients need detailed error messages.
Option B provides structure while using Spring 3 standards.

| Option | Description |
|--------|-------------|
| A | Simple String messages (too basic) |
| B | ProblemDetail with details (recommended) |
| C | Full RFC 7807 (over-engineered) |
| D | Keep current pattern (not modernized) |
---
```

**Benefits:**
- ✅ Documents WHY you chose approach X
- ✅ Team understands tradeoffs
- ✅ Can revisit decision later with context

---

### Slide 5: Complete 5-Mode Workflow (2 min)

**Today's Hands-On Plan:**

```
Step 1: Create Planning File (15 min)
  • Break UserController migration into phases
        ↓
Step 2: Create ABCD File (10 min)
  • Document exception handling decision
        ↓
Step 3: Create Implementation File (10 min)
  • Reference all 5 modes
        ↓
Step 4: Execute Workflow (15 min)
  • Load all modes into AI
  • Generate complete migrated code
        ↓
Step 5: Validate & Document (10 min)
  • Compare with feature branch
  • Update knowledge bank
```

**You'll walk away with:**
- ✅ Complete 5-mode workflow example
- ✅ Understanding of mode orchestration
- ✅ Templates for your own workflows

---

## PART 2: HANDS-ON EXERCISE (15-75 minutes)

### Exercise Step 1: Create Planning File (Duration: 15 min)

**Goal:** Create structured execution plan for UserController migration

**Instructions:**
1. Create new file: `bootcamp-materials/demos/spring-boot-migration/file-2-planning.md`
2. Think about migration order: What must happen before what?
   - Imports must compile first
   - Annotations build on imports
   - Testing validates everything
3. Fill in the template below
4. Add time estimates for each phase

**Example:**
```markdown
# MODE 3: PLANNING - UserController Migration Execution Plan

## Phase 1: Package Updates (Est: 2 min)

**Why first:** Imports must compile before changing annotations

**Tasks:**
- Task 1.1: Replace javax.servlet.* with jakarta.servlet.*
- Task 1.2: Replace javax.validation.* with jakarta.validation.*

**Validation:** Code compiles without import errors

**Dependencies:** None (this is first phase)

---

## Phase 2: Annotation Modernization (Est: 5 min)

**Why second:** Annotations build on updated imports

**Tasks:**
- Task 2.1: Identify all @RequestMapping annotations
- Task 2.2: Replace @RequestMapping(method=GET) with @GetMapping
- Task 2.3: Replace @RequestMapping(method=POST) with @PostMapping
- Task 2.4: Replace @RequestMapping(method=PUT) with @PutMapping
- Task 2.5: Replace @RequestMapping(method=DELETE) with @DeleteMapping

**Validation:** All HTTP method annotations are specific, code compiles

**Dependencies:** Phase 1 complete (imports updated)

---

## Phase 3: Dependency Injection (Est: 3 min)

**Why third:** Clean up after framework changes

**Tasks:**
- Task 3.1: Verify @RequiredArgsConstructor is present
- Task 3.2: Confirm no @Autowired annotations on constructor
- Task 3.3: Ensure all dependencies are final fields

**Validation:** Constructor injection working, no @Autowired warnings

**Dependencies:** Phase 2 complete (annotations modernized)

---

## Phase 4: Exception Handling Enhancement (Est: 5 min)

**Why fourth:** Depends on updated Spring framework patterns

**Tasks:**
- Task 4.1: Identify exception handling in createUser method
- Task 4.2: Identify exception handling in updateUser method
- Task 4.3: Identify exception handling in deleteUser method
- Task 4.4: (Optional) Consider ProblemDetail pattern for enhanced errors

**Validation:** Exception handling appropriate for Spring 3, errors handled gracefully

**Dependencies:** Phase 3 complete (injection updated)

---

## Phase 5: Testing & Validation (Est: 5 min)

**Why last:** Validates all changes work together

**Tasks:**
- Task 5.1: Review code for compilation errors
- Task 5.2: Check for @Deprecated warnings
- Task 5.3: Compare with spring-migration-demo feature branch
- Task 5.4: Verify API endpoints unchanged

**Validation:** Code compiles, patterns match target, APIs unchanged

**Dependencies:** All previous phases complete

---

## Total Estimated Time: 20 minutes

## Rollback Strategy
If any phase fails:
1. Identify which task in the phase failed
2. Review Constitution rules for that area
3. Check Specification success criteria
4. Fix issue before proceeding to next phase

## Notes
- Keep tasks small (1-2 changes per task)
- Validate after each phase
- Don't skip phases (dependencies matter)
```

**Success Criteria:**
- file-2-planning.md exists in bootcamp-materials/demos/spring-boot-migration/
- File contains 4-5 phases
- Each phase has clear "Why" explanation
- Each phase has validation criteria
- Time estimates sum to realistic total (15-25 minutes)

**Common Pitfalls:**
- Don't make phases too large ("Update everything" is too vague)
- Don't skip "Why" explanations (helps debugging)
- Don't forget validation criteria (how do you know phase is done?)

---

### Exercise Step 2: Create ABCD File (Duration: 10 min)

**Goal:** Document decision about exception handling approach

**Instructions:**
1. Create new file: `bootcamp-materials/demos/spring-boot-migration/file-3-abcd.md`
2. Think about UserController exception handling: Currently uses try-catch with ResponseEntity.badRequest() or notFound()
3. Consider: Should we enhance this with ProblemDetail pattern?
4. Present options and make recommendation

**Example:**
```markdown
# MODE 4: ABCD CLARIFICATION - Decision Points for UserController

## Decision Documentation

This file documents decision points encountered during UserController migration where multiple valid approaches exist.

---

### Clarification Question 1: Exception Handling Approach

**Context:**
UserController currently uses try-catch blocks with ResponseEntity.badRequest() and ResponseEntity.notFound() for error handling. Spring 3 introduces ProblemDetail (RFC 7807) for structured error responses.

**Question:**
How should we handle exceptions in the migrated UserController?

**Recommended:** Option B - Keep Current Pattern (Simple ResponseEntity)

**Reasoning:**
- Current error handling is clear and functional
- API clients may not need detailed error structures
- Keeps changes minimal (safer migration)
- Can enhance later if requirements change

**Options:**

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| A | Simple String messages | Very simple, minimal code | Not structured, hard to parse |
| B | Keep current ResponseEntity pattern (recommended) | Already working, minimal changes, clear logic | Not using Spring 3 ProblemDetail feature |
| C | ProblemDetail with custom details | Modern Spring 3 pattern, structured errors | More verbose, API response format changes |
| D | Full RFC 7807 with error catalog | Enterprise-grade, comprehensive | Over-engineered for simple CRUD API |

**Your Decision:** Reply with option letter (A/B/C/D) or "recommended"

---

### Clarification Question 2: Validation Enhancement

**Context:**
UserController uses @Valid annotation for request validation. Current validation is basic.

**Question:**
Should we enhance validation with custom validators?

**Recommended:** Option A - Keep Current @Valid Pattern

**Reasoning:**
- Current validation works
- Focus this migration on framework upgrade, not business logic changes
- Can add custom validators in separate feature work

**Options:**

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| A | Keep current @Valid (recommended) | Maintains scope, minimal changes | No validation enhancements |
| B | Add custom validators | Better validation, catches edge cases | Scope creep, more testing needed |
| C | Use Spring Validation groups | Flexible validation rules | Complex, requires more changes |
| D | Remove validation (use service layer) | Cleaner controller | Less immediate feedback |

**Your Decision:** Reply with option letter (A/B/C/D) or "recommended"

---

## Decision Summary

- **Exception Handling:** Option B (Keep current ResponseEntity pattern)
- **Validation:** Option A (Keep current @Valid)

**Rationale for Conservative Approach:**
This migration focuses on Spring framework upgrade (Spring 2.7 → 3.2), not feature enhancements. Keeping current patterns minimizes risk and testing burden. Future work can enhance error handling and validation after migration is stable.

---

## Notes

- ABCD files are optional if no real decisions exist
- Don't force decisions that aren't ambiguous
- Document WHY you recommend an option, not just what options exist
- Conservative choices (minimal changes) are often best for migrations
```

**Success Criteria:**
- file-3-abcd.md exists in bootcamp-materials/demos/spring-boot-migration/
- File contains 1-2 real decision points
- Each decision has 4 options (A, B, C, D)
- Recommendation is explained with reasoning
- Clear table format for options

**Common Pitfalls:**
- Don't create fake decisions just to have ABCD file
- Don't make all options equally good (recommend one)
- Don't forget to explain reasoning for recommendation

---

### Exercise Step 3: Create Implementation File (Duration: 10 min)

**Goal:** Synthesize all modes and prepare for code generation

**Instructions:**
1. Create new file: `bootcamp-materials/demos/spring-boot-migration/file-4-implementation.md`
2. Reference all previous modes (file-0 through file-3)
3. Include the "before" code from UserController
4. Provide clear generation instructions

**Example:**
```markdown
# MODE 5: IMPLEMENTATION - Generate Migrated UserController

## Context Loaded

This file synthesizes all previous modes to generate Spring 3.2 compatible code.

### From Constitution (file-0):
✓ Package rules: javax.* → jakarta.*
✓ Annotation rules: @RequestMapping → specific HTTP methods (@GetMapping, @PostMapping, etc.)
✓ Dependency injection: Constructor injection with @RequiredArgsConstructor (no @Autowired)
✓ Quality standards: Must compile with Spring 3.2, pass tests, maintain API contracts

### From Specification (file-1):
✓ File: UserController.java
✓ Target: Spring Boot 3.2 compatible
✓ Success criteria: Compiles, tests pass, APIs unchanged, no deprecated warnings
✓ Endpoints: /api/users (GET, POST), /api/users/{id} (GET, PUT, DELETE), /api/users/active (GET), /api/users/username/{username} (GET)

### From Planning (file-2):
✓ Phase 1: Package updates (javax → jakarta)
✓ Phase 2: Annotation modernization (@RequestMapping → @GetMapping/@PostMapping/@PutMapping/@DeleteMapping)
✓ Phase 3: Dependency injection (verify @RequiredArgsConstructor, no @Autowired)
✓ Phase 4: Exception handling (keep current pattern per ABCD decision)
✓ Phase 5: Testing and validation

### From ABCD Decisions (file-3):
✓ Exception handling: Keep current ResponseEntity pattern (Option B)
✓ Validation: Keep current @Valid pattern (Option A)
✓ Approach: Conservative migration focusing on framework upgrade, minimal business logic changes

---

## Input Code (Spring 2.7 - Hypothetical Before State)

**Note:** The spring-migration-demo repository main branch already uses jakarta imports. For learning purposes, imagine the "before" state as shown below with javax imports:

```java
package com.example.demo.controller;

import com.example.demo.model.User;
import com.example.demo.service.UserService;
import lombok.RequiredArgsConstructor;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import javax.validation.Valid;  // Before: javax
import java.util.List;

@RestController
@RequestMapping("/api/users")
@RequiredArgsConstructor
public class UserController {

    private final UserService userService;

    @RequestMapping(method = RequestMethod.GET)  // Before: verbose @RequestMapping
    public ResponseEntity<List<User>> getAllUsers() {
        List<User> users = userService.getAllUsers();
        return ResponseEntity.ok(users);
    }

    @RequestMapping(value = "/active", method = RequestMethod.GET)
    public ResponseEntity<List<User>> getActiveUsers() {
        List<User> users = userService.getActiveUsers();
        return ResponseEntity.ok(users);
    }

    @RequestMapping(value = "/{id}", method = RequestMethod.GET)
    public ResponseEntity<User> getUserById(@PathVariable Long id) {
        return userService.getUserById(id)
            .map(ResponseEntity::ok)
            .orElse(ResponseEntity.notFound().build());
    }

    @RequestMapping(value = "/username/{username}", method = RequestMethod.GET)
    public ResponseEntity<User> getUserByUsername(@PathVariable String username) {
        return userService.getUserByUsername(username)
            .map(ResponseEntity::ok)
            .orElse(ResponseEntity.notFound().build());
    }

    @RequestMapping(method = RequestMethod.POST)
    public ResponseEntity<User> createUser(@Valid @RequestBody User user) {
        try {
            User createdUser = userService.createUser(user);
            return ResponseEntity.status(HttpStatus.CREATED).body(createdUser);
        } catch (IllegalArgumentException e) {
            return ResponseEntity.badRequest().build();
        }
    }

    @RequestMapping(value = "/{id}", method = RequestMethod.PUT)
    public ResponseEntity<User> updateUser(@PathVariable Long id, @Valid @RequestBody User user) {
        try {
            User updatedUser = userService.updateUser(id, user);
            return ResponseEntity.ok(updatedUser);
        } catch (IllegalArgumentException e) {
            return ResponseEntity.notFound().build();
        }
    }

    @RequestMapping(value = "/{id}", method = RequestMethod.DELETE)
    public ResponseEntity<Void> deleteUser(@PathVariable Long id) {
        try {
            userService.deleteUser(id);
            return ResponseEntity.noContent().build();
        } catch (IllegalArgumentException e) {
            return ResponseEntity.notFound().build();
        }
    }
}
```

---

## Instructions

Generate Spring Boot 3.2 compatible code for UserController following these requirements:

1. **Apply all Constitution rules:**
   - Update javax.validation.* → jakarta.validation.*
   - Replace all @RequestMapping annotations with specific HTTP method annotations
   - Verify constructor injection with @RequiredArgsConstructor (no @Autowired needed)

2. **Meet all Specification criteria:**
   - Target: Spring Boot 3.2.x compatibility
   - Preserve all 7 API endpoints with same URLs
   - Maintain request/response formats
   - Ensure code compiles without errors or warnings

3. **Follow the Planning phases:**
   - Phase 1: Package updates first
   - Phase 2: Annotation modernization second
   - Phase 3: Verify dependency injection third
   - Phase 4: Maintain current exception handling (per ABCD decision)
   - Phase 5: Ensure validation and testing readiness

4. **Implement ABCD decisions:**
   - Keep current exception handling pattern (try-catch with ResponseEntity)
   - Keep current validation pattern (@Valid annotation)
   - Focus on framework upgrade, not feature enhancements

5. **Generate complete, working code:**
   - Include all imports
   - Include all methods
   - Include all annotations
   - Ensure proper formatting
   - Add brief comments where Spring 3 patterns differ significantly

---

## Expected Output

Complete UserController.java class that:
- ✅ Compiles with Spring Boot 3.2.x
- ✅ Uses jakarta.validation.Valid (not javax)
- ✅ Uses @GetMapping, @PostMapping, @PutMapping, @DeleteMapping
- ✅ Uses @RequiredArgsConstructor for dependency injection
- ✅ Maintains all 7 endpoints with same behavior
- ✅ Has no @Deprecated warnings
- ✅ Follows modern Spring 3 patterns

**Please generate the complete migrated code now.**
```

**Success Criteria:**
- file-4-implementation.md exists in bootcamp-materials/demos/spring-boot-migration/
- File references all 4 previous modes (Constitution, Specification, Planning, ABCD)
- File includes complete "before" code
- File has clear generation instructions
- File specifies expected output characteristics

**Common Pitfalls:**
- Don't forget to reference all modes (AI needs full context)
- Don't omit the "before" code (AI needs to see starting point)
- Don't be vague in instructions (be specific about what to generate)

---

### Exercise Step 4: Execute Complete Workflow (Duration: 15 min)

**Goal:** Load all 5 modes into AI and generate migrated code

**Instructions:**
1. Open your AI tool (Copilot Chat, Claude, or Windsurf)
2. Start new conversation
3. Load modes in order (file-0 through file-4)
4. Generate code
5. Save AI output

**Step-by-Step:**

```
Step 1: Load Constitution
------
Copy entire content of file-0-constitution.md
Paste into AI tool
Wait for AI to acknowledge: "I understand the Spring migration rules"

Step 2: Load Specification
------
Copy entire content of file-1-specification.md
Paste into AI tool (same conversation)
Wait for AI to acknowledge: "I understand the UserController migration target"

Step 3: Load Planning
------
Copy entire content of file-2-planning.md
Paste into AI tool (same conversation)
Wait for AI to acknowledge migration plan understanding

Step 4: Load ABCD (if you have decisions)
------
Copy entire content of file-3-abcd.md
Paste into AI tool (same conversation)
AI will present decision options
Reply: "recommended" or specific option letter (B, A)
Wait for AI to acknowledge decisions

Step 5: Load Implementation and Generate
------
Copy entire content of file-4-implementation.md (with code)
Paste into AI tool (same conversation)
AI will generate complete migrated UserController code
Copy AI output
Save to temporary file: UserController-generated.java
```

**Success Criteria:**
- AI generates complete UserController class
- Generated code uses jakarta imports (not javax)
- Generated code uses @GetMapping, @PostMapping, @PutMapping, @DeleteMapping
- Generated code has all 7 methods
- No obvious syntax errors

**Common Pitfalls:**
- Don't skip modes (load all 5 in order)
- Don't start new conversation between modes (keep same session)
- If AI output is incomplete, ask: "Please provide the complete class with all 7 methods"

---

### Exercise Step 5: Validate Generated Code (Duration: 10 min)

**Goal:** Compare AI-generated code with spring-migration-demo feature branch

**Instructions:**
1. Open AI-generated UserController code (from Exercise Step 4)
2. Checkout feature branch: `git checkout feature/spring-boot-3-migration`
3. Open UserController.java from feature branch
4. Compare implementations

**Comparison Checklist:**

```markdown
## Import Statements
- [ ] AI uses jakarta.validation.Valid (not javax)
- [ ] AI imports match or are equivalent to feature branch

## Class Annotation
- [ ] @RestController present
- [ ] @RequestMapping("/api/users") present
- [ ] @RequiredArgsConstructor present

## Dependency Injection
- [ ] UserService is final field
- [ ] No @Autowired annotation (implicit with @RequiredArgsConstructor)

## HTTP Method Annotations
- [ ] getAllUsers uses @GetMapping (not @RequestMapping)
- [ ] getActiveUsers uses @GetMapping("/active")
- [ ] getUserById uses @GetMapping("/{id}")
- [ ] getUserByUsername uses @GetMapping("/username/{username}")
- [ ] createUser uses @PostMapping
- [ ] updateUser uses @PutMapping("/{id}")
- [ ] deleteUser uses @DeleteMapping("/{id}")

## Exception Handling
- [ ] createUser has try-catch with ResponseEntity.badRequest()
- [ ] updateUser has try-catch with ResponseEntity.notFound()
- [ ] deleteUser has try-catch with ResponseEntity.notFound()

## Overall Assessment
- [ ] Code compiles (no syntax errors)
- [ ] All 7 methods present
- [ ] Logic preserved (no business logic changes)
- [ ] Patterns match Spring 3 style
```

**Discussion:**
- What differences did you find?
- Are the differences acceptable? (variable names, formatting OK)
- Is AI output correct even if different from feature branch?
- Which approach is better? Why?

**Success Criteria:**
- AI output uses jakarta imports
- AI output uses specific HTTP annotations
- Key patterns match feature branch (even if exact code differs)
- No critical errors or missing functionality

---

## PART 3: REVIEW & WRAP-UP (75-90 minutes)

### What You Learned Today (5 min)

**Today you created:**
- ✅ Planning file (file-2-planning.md) - Structured execution
- ✅ ABCD file (file-3-abcd.md) - Decision documentation
- ✅ Implementation file (file-4-implementation.md) - Synthesis
- ✅ Complete 5-mode workflow for UserController

**Key concepts:**
- Planning = Break work into logical phases
- ABCD = Document decisions with tradeoffs
- Implementation = Synthesize all context for generation
- Orchestration = Modes work together, not in isolation

**Workflow value:**
- First time (learning): ~60 min total (Session 1 + Session 2)
- Second migration: ~10 min (reuse Constitution, Planning, ABCD)
- Third+ migrations: ~5 min (only update Specification)

---

### Complete 5-Mode Pattern (5 min)

**The Universal Pattern:**

```
Mode 1: Constitution
↓ "What rules apply EVERYWHERE?"

Mode 2: Specification
↓ "What needs to happen in THIS file?"

Mode 3: Planning
↓ "What ORDER should work happen?"

Mode 4: ABCD
↓ "What DECISIONS need documenting?"

Mode 5: Implementation
↓ "GENERATE using all context"
```

**This pattern works for ANY coding task:**
- API integrations
- Data transformations
- Test automation
- Infrastructure as code
- Refactoring projects

---

### Next Steps for Your Work (3 min)

**This Week:**
- Apply 5-mode workflow to 1-2 more controllers
- Refine your templates based on what works
- Track time saved (compare with manual migration estimates)

**Next Week:**
- Share your templates with team
- Help teammate create their first workflow
- Start building team template library

**This Month:**
- Use workflows for 5+ similar tasks
- Document time savings for performance reviews
- Identify other tasks that could use this pattern

**For Performance Reviews:**
- Quantify: "Saved 40 min per file × 10 files = 6.7 hours"
- Quality: "Generated code matches target patterns, passes all tests"
- Team impact: "Shared templates, 3 teammates now using workflow"
- Innovation: "Created reusable process for Spring migrations"

---

### Common Questions & Answers (2 min)

**Q: Do I need to create ABCD file for every migration?**
A: No! Only create ABCD when you have real decisions with tradeoffs. Skip if choices are obvious.

**Q: Can I reuse Planning file across controllers?**
A: Yes! Planning phases are often the same for similar files (imports → annotations → testing).

**Q: What if AI doesn't follow my Planning phases?**
A: AI might optimize the order. Check if the output is still correct. Planning guides AI but doesn't force strict ordering.

**Q: How do I know if my workflow is good?**
A: Test it: Does it work for a second file with minimal changes? If yes, you built it well!

---

## Deliverables

By the end of this session, you will have created:

- [ ] file-2-planning.md (Migration execution plan)
- [ ] file-3-abcd.md (Decision documentation)
- [ ] file-4-implementation.md (Synthesis for generation)
- [ ] Complete 5-mode workflow example
- [ ] AI-generated Spring 3 code
- [ ] Understanding of mode orchestration

---

## Troubleshooting

**Issue: AI generates code that doesn't follow Planning phases**
- Solution: AI might optimize. Check if output is correct even if order differs. Planning guides but doesn't force exact sequence.

**Issue: ABCD decisions feel forced**
- Solution: ABCD is optional! Skip if no real ambiguity exists. Don't create fake decisions.

**Issue: Implementation file too long**
- Solution: That's OK! Implementation synthesizes everything. Long is fine if all context is needed.

**Issue: Generated code differs from feature branch**
- Solution: Different doesn't mean wrong. Focus on patterns (imports, annotations, injection) not exact matches.

---

## Taking This Beyond Spring Migration

**This 5-mode pattern works for:**

**Data Engineering:**
- Constitution: Data quality rules, transformation standards
- Specification: Transform dataset X from format A to format B
- Planning: Extract → Validate → Transform → Load
- ABCD: Decide on deduplication strategy
- Implementation: Generate ETL pipeline code

**API Integration:**
- Constitution: Error handling patterns, retry logic
- Specification: Connect to Confluence API, extract page data
- Planning: Authenticate → Search → Extract → Format
- ABCD: Decide on rate limiting approach
- Implementation: Generate integration script

**Test Automation:**
- Constitution: Test naming conventions, assertion patterns
- Specification: Test UserService create/update/delete methods
- Planning: Setup → Execute → Assert → Teardown
- ABCD: Decide on mocking strategy
- Implementation: Generate test cases

**The pattern is universal: Rules → Target → Plan → Decide → Generate**

---

**Session Status:** Ready for delivery
**Duration:** 90 minutes (15 presentation + 60 hands-on + 15 review)
**Previous Session:** Session 1 - Prompt Files and Configuration
**Repository:** https://github.com/josephrobertlopez/spring-migration-demo
**Outcome:** Complete 5-mode workflow understanding and working templates
