# SESSION 1: PROMPT FILES AND CONFIGURATION
## Create Your First Prompt Files for Spring Migration

**Duration:** 90 minutes
**Format:** 15-min presentation + 60-min hands-on + 15-min review
**Prerequisites:**
- Java development environment set up
- AI tool (Copilot/Claude/Windsurf) configured
- spring-migration-demo repository cloned
- Basic Java/Spring knowledge (can read code)

**Learning Objectives:**
- Create Constitution prompt file with Spring migration rules
- Create Specification prompt file for UserController
- Use prompt files with AI to generate Spring Boot 3 code
- Understand how to structure reusable prompt templates

---

## PART 1: PRESENTATION (0-15 minutes)

### Slide 1: From Individual Techniques to Organized Modes (3 min)

**You already know the 4 core techniques:**

| Technique | What It Does |
|-----------|--------------|
| **Chain of Thought** | "Let's think step by step" - Forces reasoning |
| **ReAct** | "Think → Act → Observe" - Iterative problem-solving |
| **Tree of Thoughts** | "Try multiple approaches" - Explores alternatives |
| **Structured Prompts** | Templates that always work - Consistent output |

**The Problem:**
- Great building blocks, but how do you ORGANIZE them?
- How do you make them REUSABLE across your team?
- How do you avoid rewriting prompts every time?

**Today's Answer: Prompt Files**
- Files you create ONCE
- Use FOREVER for similar tasks
- Share with your TEAM

---

### Slide 2: The 5 Prompt Modes Quick Overview (4 min)

**Mode 1: Constitution** - Project rules that apply everywhere
- **Example:** "javax → jakarta, @RequestMapping → @GetMapping"
- **Time:** Write once (15 min), use forever
- **Uses:** Structured Prompts technique

**Mode 2: Specification** - Describe WHAT to build in THIS file
- **Example:** "Migrate UserController: current state → target state"
- **Time:** 5 min per file
- **Uses:** Chain of Thought technique

**Mode 3: Planning** - HOW to execute step-by-step
- **Example:** "Phase 1: Imports, Phase 2: Annotations, Phase 3: Security"
- **Time:** 5 min per pattern
- **Uses:** ReAct technique

**Mode 4: ABCD Clarification** - Handle decision points
- **Example:** "Security config: Option A vs B vs C vs D"
- **Time:** 5 min when ambiguous
- **Uses:** Tree of Thoughts technique

**Mode 5: Implementation** - Combine all modes and generate
- **Example:** "Generate migrated code following all rules"
- **Time:** 2 min per file
- **Uses:** All 4 techniques together

**Key Insight:** Modes 1-4 = THINKING. Mode 5 = DOING.

---

### Slide 3: Spring Migration Example - Before & After (3 min)

**Bad Prompt:**
```
"Migrate this controller to Spring 3"
```
**Result:** Generic changes, might miss important patterns

**Good Prompt:**
```
"Migrate UserController from Spring 2.7 to 3.2.
Update javax → jakarta imports.
Change @RequestMapping to @GetMapping/@PostMapping.
Use constructor injection without @Autowired.
Use ProblemDetail for error handling."
```
**Result:** Specific, correct migration

**Even Better - Prompt Files Approach:**
```
Constitution file (reusable):
  - javax → jakarta rules
  - Annotation modernization rules
  - Dependency injection rules

Specification file (per controller):
  - Current: UserController.java (Spring 2.7)
  - Target: Spring 3.2 compatible
  - Before code → After patterns
```
**Result:** Systematic, reusable, documented approach

---

### Slide 4: Time Investment vs Payoff (3 min)

| Activity | First Time | Second Time | Third+ Time |
|----------|-----------|-------------|-------------|
| Manual coding | 45 min | 45 min | 45 min |
| With Prompt Files | 30 min | 5 min | 5 min |
| **Savings** | 15 min | 40 min | 40 min |

**Compound effect:** After 5 migrations, you've saved 3+ hours

---

### Slide 5: Today's Hands-On Plan (2 min)

**In the next 60 minutes, you'll:**

1. **Create Constitution File** (15 min)
   - Spring 2→3 migration rules that apply to ALL controllers

2. **Create Specification File** (15 min)
   - UserController-specific migration details

3. **Test with AI** (20 min)
   - Load both files into AI tool
   - Generate migrated Spring 3 code

4. **Validate Output** (10 min)
   - Compare with spring-migration-demo "after" branch
   - Verify patterns match

**You'll walk away with:**
- ✅ 2 working prompt files (Constitution + Specification)
- ✅ Generated Spring 3 code
- ✅ Templates for your own migrations

---

## PART 2: HANDS-ON EXERCISE (15-75 minutes)

### Exercise Step 1: Setup Repository (Duration: 5 min)

**Goal:** Verify spring-migration-demo repository is ready for exercises

**Instructions:**
1. Open terminal in spring-migration-demo directory
2. Run `git branch -a` to verify branches exist
3. Run `git checkout main` to see "before" state
4. Open `src/main/java/com/example/demo/controller/UserController.java` in editor
5. Verify you see `javax.servlet` imports (Spring Boot 2.7 code)

**Success Criteria:**
- You can see UserController.java with Spring 2.7 code
- You can see `javax.servlet` imports (not `jakarta`)
- You have AI tool (Copilot/Claude/Windsurf) ready

**Common Pitfalls:**
- If repository not cloned: Run `git clone https://github.com/josephrobertlopez/spring-migration-demo`
- If on wrong branch: Run `git checkout main`

---

### Exercise Step 2: Create Constitution File (Duration: 15 min)

**Goal:** Create reusable Constitution file with Spring 2→3 migration rules

**Instructions:**
1. **Reference:** [file-0-constitution.md](https://github.com/josephrobertlopez/spring-migration-demo/blob/main/demos/session-2-advanced-patterns/prompts/file-0-constitution.md) in spring-migration-demo (main branch)
2. Copy the template below
3. Read each rule and understand what it does
4. Save the file

**Example:**
```markdown
# MODE 1: CONSTITUTION - Spring 2→3 Migration Rules

## Non-Negotiable Rules

### Package Migration Rules
- javax.servlet.* → jakarta.servlet.*
- javax.persistence.* → jakarta.persistence.*
- javax.validation.* → jakarta.validation.*
- javax.transaction.* → jakarta.transaction.*

### Annotation Rules
- @RequestMapping(method=RequestMethod.GET) → @GetMapping
- @RequestMapping(method=RequestMethod.POST) → @PostMapping
- @RequestMapping(method=RequestMethod.PUT) → @PutMapping
- @RequestMapping(method=RequestMethod.DELETE) → @DeleteMapping
- Remove @Autowired on constructor injection

### Exception Handling Rules
- Use ProblemDetail for REST error responses
- @ExceptionHandler should return ProblemDetail
- Include status, title, detail in ProblemDetail

### Security Rules
- WebSecurityConfigurerAdapter → SecurityFilterChain
- authorizeRequests() → authorizeHttpRequests()
- Use lambda DSL (no .and() chaining)

## Constraints
- Maintain API contracts (same endpoints, same responses)
- Preserve business logic (only change framework code)
- Java 17+ required
- Spring Boot 3.2+ target

## Quality Standards
Code must:
- ✅ Compile with Spring Boot 3.2.x
- ✅ Pass all existing tests
- ✅ Use modern Spring patterns
- ✅ Have no @Deprecated warnings

Code must NOT:
- ❌ Change API endpoints or responses
- ❌ Modify business logic
- ❌ Break backward compatibility
```

**Success Criteria:**
- file-0-constitution.md [available in spring-migration-demo repo](https://github.com/josephrobertlopez/spring-migration-demo/blob/main/demos/session-2-advanced-patterns/prompts/file-0-constitution.md)
- File contains at least 5 package migration rules
- File contains at least 4 annotation rules
- File specifies Spring Boot 3.2+ as target

**Common Pitfalls:**
- Don't make rules too vague (be specific: "javax.servlet → jakarta.servlet", not "update imports")
- Don't forget constraints (API compatibility, Java 17+)

---

### Exercise Step 3: Create Specification File (Duration: 15 min)

**Goal:** Create Specification file describing UserController migration

**Instructions:**
1. Open UserController.java from spring-migration-demo (main branch)
2. Copy the entire class code
3. **Reference:** [file-1-specification.md](https://github.com/josephrobertlopez/spring-migration-demo/blob/main/demos/session-2-advanced-patterns/prompts/file-1-specification.md) in spring-migration-demo (main branch)
4. Fill in template below with UserController code

**Example:**
```markdown
# MODE 2: SPECIFICATION - Migrate UserController

## Current State (Spring 2.7)
File: spring-migration-demo/src/main/java/com/example/demo/controller/UserController.java

Current implementation:
- Uses javax.servlet imports
- @RequestMapping for all endpoints
- @Autowired dependency injection
- Generic exception handling

## Target State (Spring 3.2)
- jakarta.servlet imports
- @GetMapping, @PostMapping, @PutMapping, @DeleteMapping
- Constructor injection (no @Autowired)
- ProblemDetail exception handling

## Success Criteria
✓ Compiles with Spring Boot 3.2.x
✓ All unit tests pass
✓ API endpoints unchanged (same URLs, same request/response formats)
✓ No deprecated warnings

## Before Code
```java
[Paste entire UserController.java from main branch here]
```
```

**Success Criteria:**
- file-1-specification.md [available in spring-migration-demo repo](https://github.com/josephrobertlopez/spring-migration-demo/blob/main/demos/session-2-advanced-patterns/prompts/file-1-specification.md)
- File includes current state description
- File includes target state description
- File includes complete UserController.java code from main branch

**Common Pitfalls:**
- Don't paste code from feature branch (use main branch - the "before" state)
- Don't forget success criteria section
- Make sure code formatting is preserved (use triple backticks)

**Reference:**
- UserController.java location: `spring-migration-demo/src/main/java/com/example/demo/controller/UserController.java`

---

### Exercise Step 4: Test Prompt Files with AI (Duration: 20 min)

**Goal:** Use Constitution + Specification files with AI to generate migrated code

**Instructions:**
1. Open your AI tool (Copilot Chat, Claude, or Windsurf)
2. Start new conversation
3. Copy entire content of file-0-constitution.md and paste into AI
4. Wait for AI to acknowledge (e.g., "I understand the Spring migration rules")
5. Copy entire content of file-1-specification.md and paste into AI
6. Wait for AI to acknowledge
7. Type: "Generate the migrated UserController following all Constitution rules and meeting Specification criteria"
8. Copy the generated code from AI
9. Save generated code to a temporary file (e.g., `UserController-migrated.java`)

**Success Criteria:**
- AI generates code with jakarta imports (not javax)
- AI uses @GetMapping, @PostMapping instead of @RequestMapping
- AI uses constructor injection (no @Autowired visible)
- Generated code compiles (no obvious syntax errors)

**Common Pitfalls:**
- Don't skip loading Constitution first - AI needs those rules
- Don't edit AI output yet - save exactly what AI generates
- If AI output is incomplete, ask: "Please provide the complete class with all methods"

**Example AI Interaction:**
```
You: [Paste file-0-constitution.md]
AI: "I understand the Spring 2→3 migration rules..."

You: [Paste file-1-specification.md]
AI: "I understand the UserController migration target..."

You: "Generate the migrated UserController following all Constitution rules and meeting Specification criteria"
AI: [Generates migrated code]
```

---

### Exercise Step 5: Validate Generated Code (Duration: 10 min)

**Goal:** Compare AI-generated code with target implementation from after branch

**Instructions:**
1. Checkout feature branch: `git checkout feature/spring-boot-3-migration`
2. Open UserController.java from feature branch
3. Compare with your AI-generated code from Exercise Step 4
4. Look for these patterns:
   - ✓ Imports: `jakarta.servlet` (not `javax.servlet`)
   - ✓ Annotations: `@GetMapping` (not `@RequestMapping(method=GET)`)
   - ✓ Constructor: No `@Autowired` annotation
   - ✓ Error handling: Uses `ProblemDetail` or similar Spring 3 patterns
5. Note differences between AI output and target branch

**Success Criteria:**
- AI-generated code uses jakarta imports
- AI-generated code uses specific HTTP method annotations (@GetMapping, @PostMapping)
- Key patterns match feature branch (even if exact code differs)

**Common Pitfalls:**
- Don't expect exact match - variable names, formatting may differ
- Focus on patterns, not exact code
- Both AI output and feature branch can be correct

**Discussion Questions:**
- What patterns match between AI output and feature branch?
- What's different? Why might that be?
- Is your AI output correct even if different from feature branch?

---

## PART 3: REVIEW & WRAP-UP (75-90 minutes)

### What You Learned (5 min)

**Today you created:**
- ✅ Constitution file (file-0-constitution.md) - Spring migration rules
- ✅ Specification file (file-1-specification.md) - UserController specifics
- ✅ Generated Spring 3 code using prompt files

**Key concepts:**
- Constitution = Reusable rules (write once, use forever)
- Specification = File-specific details (write once per controller)
- Prompt files = Structured way to guide AI

**Time savings:**
- First migration with prompt files: ~30 min
- Second migration (reuse Constitution): ~5 min
- **Savings: 40 min per controller after initial setup**

---

### Common Questions & Answers (5 min)

**Q: Do I need to create Constitution file for every controller?**
A: No! Constitution is written ONCE and reused for ALL controllers. Only Specification changes per file.

**Q: What if AI output doesn't match the feature branch exactly?**
A: That's okay! Focus on patterns (imports, annotations, injection). Both can be correct.

**Q: Can I use these prompt files with different AI tools?**
A: Yes! Constitution and Specification files work with Copilot, Claude, Windsurf, ChatGPT, etc.

**Q: How do I share these with my team?**
A: Commit prompt files to your repository. Team members load same files, get consistent results.

---

### Next Steps (5 min)

**For Session 2 (Tomorrow):**
- You'll create Planning and ABCD files (Modes 3 & 4)
- You'll execute a complete 5-mode workflow
- You'll see how all modes work together

**To prepare:**
- Review your file-0-constitution.md and file-1-specification.md
- Think about what other files you might want to migrate
- (Optional) Try creating a Specification file for OrderController

**For your daily work:**
- Use Constitution file for any Spring migration tasks
- Create Specification files for each controller you migrate
- Track time saved and document for performance reviews

---

## Deliverables

By the end of this session, you will have created:

- [ ] file-0-constitution.md (Spring migration rules)
- [ ] file-1-specification.md (UserController specifics)
- [ ] AI-generated Spring 3 code
- [ ] Understanding of how to structure reusable prompts

---

## Troubleshooting

**Issue: Repository not found**
- Solution: Clone repository: `git clone https://github.com/josephrobertlopez/spring-migration-demo`

**Issue: AI doesn't understand Constitution file**
- Solution: Make sure you pasted the ENTIRE file, including markdown headers

**Issue: AI generates incomplete code**
- Solution: Ask: "Please provide the complete UserController class with all methods"

**Issue: Can't find UserController.java**
- Solution: Verify you're on main branch: `git checkout main`
- Path: `src/main/java/com/example/demo/controller/UserController.java`

---

**Session Status:** Ready for delivery
**Duration:** 90 minutes (15 presentation + 60 hands-on + 15 review)
**Next Session:** Session 2 - Workflows (Using All 5 Modes Together)
**Repository:** https://github.com/josephrobertlopez/spring-migration-demo
