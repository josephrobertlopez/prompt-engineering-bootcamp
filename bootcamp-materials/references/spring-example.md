# Complete Example: Spring Boot Migration with All Patterns

**Scenario:** Migrate UserController from Spring Boot 2.7 to 3.2

**This example demonstrates:** All patterns working together in real workflow

---

## Context

**Task:** Migrate UserController.java
**From:** Spring Boot 2.7 (javax imports, verbose annotations)
**To:** Spring Boot 3.2 (jakarta imports, modern patterns)
**Endpoints:** 7 REST endpoints (GET, POST, PUT, DELETE operations)

---

## Approach: Structured Files (All Patterns)

We'll use 5-file workflow to explicitly show each pattern. In production, ADRs + simple prompt often simpler.

---

## File 1: System Prompt (Persona + Few-shot)

```markdown
# System Prompt: Spring Boot 3 Migration Specialist

## Role (Persona Pattern)
You are an expert Spring Boot migration specialist with 10+ years experience upgrading enterprise Java applications.

Your expertise includes:
- Package migration (javax → jakarta namespace)
- Spring Security 6.x patterns
- Modern annotation usage (@GetMapping over @RequestMapping)
- Spring Boot 3.2.x best practices

## Transformation Examples (Few-shot Pattern)

### Example 1: Package Updates
BEFORE: import javax.validation.Valid;
AFTER:  import jakarta.validation.Valid;

### Example 2: Annotation Modernization
BEFORE: @RequestMapping(value = "/users", method = RequestMethod.GET)
AFTER:  @GetMapping("/users")

### Example 3: Dependency Injection
BEFORE:
```java
@Autowired
private UserService userService;
```

AFTER:
```java
@RequiredArgsConstructor
private final UserService userService;
```

## Quality Standards
- ✅ Must compile with Spring Boot 3.2.x
- ✅ All unit tests must pass
- ✅ No @Deprecated warnings
- ✅ API contracts unchanged (same URLs)
- ✅ Business logic preserved exactly
```

**Pattern used:** Persona + Few-shot
**Reusability:** 100% reusable across all Spring migrations
**Alternative:** This could be .github/copilot-instructions.md or ADR

---

## File 2: Task Specification (Template Pattern)

```markdown
# Task Specification: UserController Migration

## File Target
**Path:** src/main/java/com/example/demo/controller/UserController.java
**Current:** Spring Boot 2.7 with javax imports
**Goal:** Spring Boot 3.2 compatible with jakarta imports

## Required Changes (Structured Checklist)

### Imports
- [ ] javax.validation.Valid → jakarta.validation.Valid
- [ ] Verify no javax.* imports remain

### Annotations
- [ ] @RequestMapping(method=GET) → @GetMapping
- [ ] @RequestMapping(method=POST) → @PostMapping
- [ ] @RequestMapping(method=PUT) → @PutMapping
- [ ] @RequestMapping(method=DELETE) → @DeleteMapping

### Dependency Injection
- [ ] @RequiredArgsConstructor present
- [ ] UserService is final field
- [ ] No @Autowired on constructor

### API Endpoints (Must Preserve)
1. GET /api/users - List all users
2. GET /api/users/active - List active users
3. GET /api/users/{id} - Get by ID
4. GET /api/users/username/{username} - Get by username
5. POST /api/users - Create user
6. PUT /api/users/{id} - Update user
7. DELETE /api/users/{id} - Delete user

## Success Criteria
✓ Compiles with Spring Boot 3.2
✓ All 7 endpoints unchanged (same URLs)
✓ All tests pass
✓ No deprecated warnings
```

**Pattern used:** Template (structured checklist)
**Reusability:** Template reusable, customize per file
**Alternative:** Could be GitHub issue or Jira ticket

---

## File 3: Execution Plan (ReAct Pattern)

```markdown
# ReAct Execution Plan: Phased Migration

## Phase 1: Package Import Updates

### THINK (Reasoning)
**Question:** What dependencies must be satisfied before other changes?
**Answer:** Imports must compile first. Annotations depend on correct imports.
**Conclusion:** Start with javax → jakarta package updates.

### ACT (Action Items)
- Task 1.1: Replace javax.validation.Valid with jakarta.validation.Valid
- Task 1.2: Replace any javax.servlet.* with jakarta.servlet.*
- Task 1.3: Search for remaining javax.* imports

### OBSERVE (Validation)
**Checkpoint:** Run `mvn compile`
**Success criteria:** Code compiles without import errors
**If failure:** Check Spring 3 compatibility docs
**Dependencies:** None (this is first phase)

---

## Phase 2: Annotation Modernization

### THINK (Reasoning)
**Question:** Can annotations be safely updated now?
**Answer:** Yes, imports validated (Phase 1 complete). Annotations now compile correctly.
**Conclusion:** Modernize HTTP method annotations to Spring 3 style.

### ACT (Action Items)
- Task 2.1: Identify all @RequestMapping annotations
- Task 2.2: Replace @RequestMapping(method=GET) with @GetMapping
- Task 2.3: Replace @RequestMapping(method=POST) with @PostMapping
- Task 2.4: Replace @RequestMapping(method=PUT) with @PutMapping
- Task 2.5: Replace @RequestMapping(method=DELETE) with @DeleteMapping

### OBSERVE (Validation)
**Checkpoint:** Check for @Deprecated warnings in IDE
**Success criteria:** No deprecated warnings, code compiles cleanly
**If failure:** Review Spring 3 annotation reference
**Dependencies:** Phase 1 complete (imports updated)

---

## Phase 3: Dependency Injection Verification

### THINK (Reasoning)
**Question:** Is dependency injection following Spring 3 best practices?
**Answer:** Check if @RequiredArgsConstructor is used (no @Autowired).
**Conclusion:** Verify pattern, make minimal changes only if needed.

### ACT (Action Items)
- Task 3.1: Verify @RequiredArgsConstructor annotation present
- Task 3.2: Confirm no @Autowired on constructor
- Task 3.3: Verify UserService is final field
- Task 3.4: If needed, add final keyword and @RequiredArgsConstructor

### OBSERVE (Validation)
**Checkpoint:** Run application, check Spring logs
**Success criteria:** Application starts, no injection warnings
**If failure:** Review Spring dependency injection docs
**Dependencies:** Phase 2 complete (annotations modernized)

---

## Total Estimated Time: 15 minutes

## Rollback Strategy
Because we validated at each phase:
- Phase 3 fails → Review Phase 2 changes
- Phase 2 fails → Review Phase 1 changes
- Phase 1 fails → Check Spring 3 compatibility

Clear checkpoint boundaries enable precise debugging.
```

**Pattern used:** ReAct (THINK → ACT → OBSERVE cycles)
**Reusability:** Reusable for similar migrations
**Alternative:** Brief implementation notes in ADR
**When to skip:** Simple tasks with obvious order

---

## File 4: Decisions (Tree of Thoughts Pattern)

```markdown
# Tree of Thoughts: Exception Handling Decision

## Decision Point: Exception Handling Strategy

### Context
UserController currently uses try-catch with ResponseEntity.badRequest() and ResponseEntity.notFound().
Spring Boot 3 introduced ProblemDetail (RFC 7807) for structured error responses.

### Question
Should we adopt ProblemDetail or keep current approach?

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

**Evaluation:**
- Pros:
  - ✅ Minimal code changes (lowest risk)
  - ✅ Existing API clients unaffected (no breaking changes)
  - ✅ Clear and readable
  - ✅ Fast migration (no additional testing)
- Cons:
  - ❌ Not using Spring 3 ProblemDetail feature
  - ❌ Error responses are minimal (just HTTP status)
- Context fit: ✅ **EXCELLENT** for migration-focused work
- Effort: 0 hours (no changes)
- Risk: Very low

---

**BRANCH B: Adopt ProblemDetail Pattern**
```java
try {
    User user = userService.createUser(user);
    return ResponseEntity.status(HttpStatus.CREATED).body(user);
} catch (IllegalArgumentException e) {
    ProblemDetail pd = ProblemDetail.forStatusAndDetail(
        HttpStatus.BAD_REQUEST,
        e.getMessage()
    );
    pd.setProperty("timestamp", Instant.now());
    return ResponseEntity.badRequest().body(pd);
}
```

**Evaluation:**
- Pros:
  - ✅ Modern Spring 3 pattern
  - ✅ Structured error responses
  - ✅ Can include additional context
- Cons:
  - ❌ API response format changes (may break clients)
  - ❌ Requires more testing
  - ❌ Scope creep (feature enhancement, not just migration)
- Context fit: ⚠️ **GOOD** for greenfield or enhancement work
- Effort: 4-6 hours (implementation + testing)
- Risk: Medium (API contract changes)

---

**BRANCH C: Full RFC 7807 Implementation**
[Details of comprehensive error catalog with @ControllerAdvice]

**Evaluation:**
- Pros: Enterprise-grade, comprehensive
- Cons: Over-engineered for simple CRUD API
- Context fit: ❌ **POOR** for current scope
- Effort: 16-24 hours
- Risk: High (large scope change)

---

### Tree Evaluation Matrix

| Branch | Context Fit | Effort | Risk | Quality | Recommendation |
|--------|-------------|--------|------|---------|----------------|
| A: Keep Current | ✅ Excellent | 0h | Very Low | Good | ⭐ **RECOMMENDED** |
| B: ProblemDetail | ⚠️ Good | 4-6h | Medium | Excellent | Consider for v2 |
| C: Full RFC 7807 | ❌ Poor | 16-24h | High | Excellent | Future work |

### Decision: Branch A (Keep Current Pattern)

**Rationale:**
This migration focuses on framework upgrade (Spring 2.7 → 3.2), not feature enhancements. Branch A:
- Minimizes risk (no API contract changes)
- Reduces testing scope (existing behavior unchanged)
- Maintains clear separation: migration work vs enhancement work
- Enables faster completion and deployment

**Future Work:**
Branch B (ProblemDetail) is a good candidate for separate enhancement work after migration is stable.
Could be tracked as separate ADR or user story.
```

**Pattern used:** Tree of Thoughts (branch exploration)
**Reusability:** Decision-specific, not reusable
**Alternative:** ADR "Alternatives Considered" section
**When to skip:** Only one reasonable approach, no real decision

---

## File 5: Code Generation (Meta-prompting)

```markdown
# Code Generation: Complete Pattern Synthesis

## Context Synthesis (Meta-prompting)

This generation orchestrates all previous patterns:

**From System Prompt (file-1):**
✓ Persona Pattern: AI role as Spring migration specialist
✓ Few-shot Pattern: Transformation examples loaded
  - javax → jakarta rules
  - @RequestMapping → @GetMapping rules
  - Dependency injection patterns
✓ Quality standards defined

**From Task Specification (file-2):**
✓ Template Pattern: Structured checklist
  - 7 API endpoints documented
  - Success criteria defined
  - All required changes listed

**From ReAct Execution Plan (file-3):**
✓ ReAct Pattern: Phased execution
  - Phase 1: Imports first
  - Phase 2: Annotations second
  - Phase 3: Injection verification third
✓ Validation checkpoints at each phase

**From Tree of Thoughts Decisions (file-4):**
✓ Tree of Thoughts: Branch exploration complete
  - Decision: Keep current exception handling (Branch A)
  - Rationale: Migration-focused, minimal changes
  - Future: Branch B for enhancement later

## Generation Instructions

Generate Spring Boot 3.2 compatible code using this multi-pattern approach:

### Step 1: Apply Few-shot Transformations
- Update imports using examples from file-1
- Modernize annotations using examples from file-1
- Verify injection patterns from file-1

### Step 2: Follow ReAct Phases
- Phase 1: Package updates (validate compilation)
- Phase 2: Annotation modernization (validate no deprecations)
- Phase 3: Injection verification (validate patterns)

### Step 3: Implement Tree Decisions
- Exception handling: Keep current pattern (Branch A decision)
- Do NOT adopt ProblemDetail (decision rationale: future work)

### Step 4: Validate Template Checklist
- All 7 endpoints preserved (same URLs)
- All checklist items complete
- Success criteria met

## Expected Output

Complete UserController.java that:
1. ✅ Uses jakarta.validation.Valid (not javax)
2. ✅ Uses @GetMapping, @PostMapping, @PutMapping, @DeleteMapping
3. ✅ Uses @RequiredArgsConstructor (no @Autowired)
4. ✅ Maintains all 7 endpoints with same URLs
5. ✅ Preserves exception handling exactly as-is (Branch A decision)
6. ✅ Compiles with Spring Boot 3.2
7. ✅ No deprecated warnings

**Generate the complete migrated UserController.java now.**
```

**Pattern used:** Meta-prompting (orchestrates all patterns)
**Maps to:** This would be your final prompt to AI
**Alternative:** Simple "migrate following ADR 0001" if using ADR approach

---

## Execution: Load All Files into AI

**Step 1:** Copy file-1 contents → Paste into AI tool
**Step 2:** Copy file-2 contents → Paste (same conversation)
**Step 3:** Copy file-3 contents → Paste (same conversation)
**Step 4:** Copy file-4 contents → Paste (same conversation)
**Step 5:** Copy file-5 contents → Paste (same conversation)

**Result:** AI generates complete migrated UserController with all patterns applied

---

## Alternative: ADR Approach (Simpler)

Instead of 5 files, you could achieve same result with:

**File: docs/adr/0001-spring-migration-standards.md**
```markdown
# ADR 0001: Spring Boot 3 Migration Standards

## Decision
- javax → jakarta transformations
- @RequestMapping → specific HTTP method annotations
- Keep current exception handling

## Implementation Notes
Phase 1: Imports
Phase 2: Annotations
Phase 3: Verification
```

**File: .github/copilot-instructions.md**
```markdown
# Spring Boot 3 Migration Rules
- javax.* → jakarta.*
- @RequestMapping(method=X) → @XMapping
```

**Prompt:**
```
Following ADR 0001 and .github/copilot-instructions.md, migrate UserController.java
```

**Same patterns, simpler format!**

---

## Key Insights from This Example

### Pattern Application
- **Persona:** Establishes AI expertise (Spring specialist)
- **Few-shot:** Shows transformations (javax→jakarta examples)
- **Template:** Structures output (checklist format)
- **ReAct:** Phases with validation (imports→annotations→verify)
- **Tree of Thoughts:** Evaluates alternatives (exception handling)
- **Meta-prompting:** Synthesizes all patterns

### When Structured Files Add Value
✅ Complex task (7 endpoints, multiple concerns)
✅ Learning tool (shows all patterns explicitly)
✅ Audit trail (full reasoning documented)
✅ Teaching others (explicit pattern application)

### When ADRs Simpler
✅ Team experienced with patterns
✅ Production workflow (proven approach)
✅ Low maintenance (fewer files)
✅ Simple to medium complexity

---

## Measuring Success

**Time investment (first time):**
- Create 5 files: 30 minutes
- Load into AI: 5 minutes
- Review/validate output: 10 minutes
- **Total: 45 minutes**

**Time investment (second migration):**
- Reuse file-1 (system prompt): 0 minutes
- Update file-2 (task spec): 5 minutes
- Reuse/adapt file-3 (ReAct plan): 2 minutes
- Skip file-4 if no decisions: 0 minutes
- Update file-5 (generation): 2 minutes
- **Total: 9 minutes**

**ROI:** First migration teaches patterns (investment), subsequent migrations fast (payoff)

---

## Next Steps

**If this example resonates:**
1. Try structured files on complex task
2. Measure time saved vs manual approach
3. Compare to ADR + simple prompt
4. Choose approach that fits your team

**If this feels like overhead:**
1. Use ADRs + .github/copilot-instructions.md (simpler, cross-IDE)
2. Apply patterns implicitly (no explicit files)
3. Reserve structured files for very complex tasks

**Both are valid!** Choose based on context, not dogma.

---

**Key Takeaway:** This example shows maximum structure for teaching. Production often uses simpler formats (ADRs, config files, simple prompts) that apply same underlying patterns. The patterns matter. The format doesn't.
