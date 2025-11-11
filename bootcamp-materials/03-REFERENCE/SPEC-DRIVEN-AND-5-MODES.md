# SPEC-DRIVEN DEVELOPMENT + 5 PROMPT MODES
## How Artifacts and Modes Work Together

---

## 🎯 THE CONNECTION

You now have TWO powerful frameworks:

**Spec-Driven Development Artifacts** (from your document)
- mainspec.md, implementation_plan.md, knowledge_bank.md, research.md, notes.md
- Structured approach to feature development
- Living documents that preserve context

**5 Prompt Modes** (custom teaching framework, see [GLOSSARY.md](../01-OVERVIEW/GLOSSARY.md))
- Constitution, Specification, Planning, ABCD, Implementation
- AI collaboration framework mapped to industry-standard patterns
- Systematic prompt orchestration

**They complement each other perfectly:**
- **Artifacts = Project-level structure** (what you build)
- **5 Modes = Task-level execution** (how AI helps you build it)

---

## 🔗 MAPPING: ARTIFACTS → MODES

### **Artifact: mainspec.md**
**Maps to:** Mode 2 (Specification)

**What it does:**
- Human-written requirements
- Acceptance criteria
- Technical approach

**When to use:**
- Beginning of feature work
- Source of truth for WHAT to build

**Connection to Mode 2:**
```markdown
# Mode 2: Specification (from mainspec.md)

## Current State:
[What exists today]

## Target State: 
[From mainspec.md Requirements section]

## Success Criteria:
[From mainspec.md Acceptance Criteria]

## Before Code:
[Current implementation if modifying existing code]
```

---

### **Artifact: implementation_plan.md**
**Maps to:** Mode 3 (Planning)

**What it does:**
- AI-generated checklist
- Phases, tasks, dependencies
- Risk assessment

**When to use:**
- After mainspec is written
- Before coding starts

**Connection to Mode 3:**
```markdown
# Mode 3: Planning (from implementation_plan.md)

## Phase 1: [From implementation_plan phases]
- Task 1.1: [From implementation_plan tasks]
  - Files: [affected files]
  - Dependencies: [prerequisites]
  - Risk: [assessment]

## Validation:
[From implementation_plan Definition of Done]
```

---

### **Artifact: knowledge_bank.md**
**Maps to:** Context for ALL modes

**What it does:**
- Session logs
- Key decisions
- Context preservation

**When to use:**
- Continuously throughout development
- Before/after each session

**Connection to Modes:**
- **Mode 1 (Constitution):** Decisions become rules for future work
- **Mode 4 (ABCD):** Documents which option was chosen and why
- **Mode 5 (Implementation):** Provides historical context

**Example:**
```markdown
# knowledge_bank.md logs ABCD decisions

## Key Decisions

### Security Config Approach (from Mode 4 ABCD)
- **Context**: Migrating Spring 2→3 security
- **Options Considered**: A, B, C, D (from ABCD Mode)
- **Decision**: Option B - Custom SecurityFilterChain
- **Rationale**: Preserves custom auth logic while modernizing
- **Trade-offs**: More complex than default, but necessary
- **Validation**: Tests passing, no security regressions

[This decision informs future SecurityFilterChain migrations]
```

---

### **Artifact: research.md**
**Maps to:** Mode 1 (Constitution) input

**What it does:**
- Codebase analysis
- Existing patterns
- Integration points

**When to use:**
- Discovery phase
- Before writing constitution

**Connection to Mode 1:**
```markdown
# Research findings become Constitution rules

## research.md findings:
- Existing pattern: All controllers use constructor injection
- Integration point: SecurityConfig uses lambda DSL
- Constraint: Must maintain API contracts

## Mode 1 Constitution rules (extracted from research):
- Rule: Use constructor injection (existing pattern)
- Rule: Use lambda DSL for security (existing pattern)
- Constraint: Maintain API contracts (from research)
```

---

### **Artifact: notes.md**
**Maps to:** Scratchpad for ALL modes

**What it does:**
- Stream-of-consciousness capture
- Quick decisions
- Context notes

**When to use:**
- During active development
- Quick thoughts that get promoted to knowledge_bank

**Connection to Modes:**
- **Temporary storage** for decisions before formalizing in knowledge_bank
- **Quick captures** during Mode 5 (Implementation) execution
- **Context notes** that inform Mode 4 (ABCD) decisions

---

## 🏗️ COMBINED WORKFLOW

Here's how to use BOTH frameworks together:

### **Phase 1: Discovery & Setup**

**1. Create Spec-Driven Artifacts**
```bash
mkdir -p specs/spring-migration/
touch specs/spring-migration/mainspec.md
touch specs/spring-migration/research.md
```

**2. Research Codebase**
- Analyze before/after branches
- Document in research.md
- Identify patterns and constraints

**3. Write mainspec.md**
- Requirements
- Acceptance criteria
- Technical approach

---

### **Phase 2: Planning with AI**

**4. Create 5-Mode Workflow**
```bash
mkdir -p prompt-workflows/spring-migration/
```

**5. Extract Constitution from research.md**
- research.md findings → file-0-constitution.md (Mode 1)
- Patterns become rules
- Constraints become constraints

**6. Write Specification from mainspec.md**
- mainspec requirements → file-1-specification.md (Mode 2)
- Acceptance criteria → Success criteria
- Technical approach → Target state

**7. Generate implementation_plan.md**
- Use AI with mainspec + constitution
- Create phased approach
- Document as file-2-planning.md (Mode 3)

---

### **Phase 3: Execution**

**8. Identify Decisions (ABCD Mode)**
- Review implementation_plan risks
- Create file-3-abcd.md (Mode 4)
- Document decision points

**9. Implement with Context**
- Load all modes (file-0 through file-3)
- Create file-4-implementation.md (Mode 5)
- Generate code with full context

**10. Document in knowledge_bank.md**
- Log session
- Record decisions made (from Mode 4)
- Update status

---

### **Phase 4: Iteration**

**11. Update artifacts as you learn**
- notes.md → Capture quick thoughts during coding
- knowledge_bank.md → Promote important notes
- implementation_plan.md → Check off completed tasks

**12. Reuse modes for next file**
- Constitution (Mode 1): Reuse as-is
- Specification (Mode 2): Update for new file
- Planning (Mode 3): Reuse similar pattern
- ABCD (Mode 4): Reference past decisions from knowledge_bank
- Implementation (Mode 5): Execute quickly

---

## 📁 DIRECTORY STRUCTURE

Your project now has BOTH:

```
your-project/
├── specs/                          # Spec-Driven Artifacts
│   └── spring-migration/
│       ├── mainspec.md            # Requirements (human-written)
│       ├── implementation_plan.md  # Phased tasks (AI-generated)
│       ├── knowledge_bank.md      # Living context (continuously updated)
│       ├── research.md            # Codebase analysis
│       └── notes.md               # Quick captures
│
├── prompt-workflows/               # 5-Mode Workflows
│   └── spring-migration/
│       ├── file-0-constitution.md  # Rules (from research.md)
│       ├── file-1-specification.md # What to build (from mainspec.md)
│       ├── file-2-planning.md     # How to build (from implementation_plan.md)
│       ├── file-3-abcd.md         # Decision points
│       └── file-4-implementation.md # Code generation
│
└── src/                           # Your actual code
    └── main/java/...
```

---

## 💡 WHEN TO USE WHAT

### **Use Spec-Driven Artifacts When:**
- ✅ Starting new feature
- ✅ Need to preserve context across sessions
- ✅ Multiple people working on same feature
- ✅ Complex feature with many decisions
- ✅ Want to document "why" for future reference

### **Use 5-Mode Workflows When:**
- ✅ Ready to execute specific task
- ✅ Need AI to generate code
- ✅ Migrating similar files repeatedly
- ✅ Want systematic AI collaboration
- ✅ Reusing patterns across files

### **Use BOTH When:**
- ✅ Feature is complex enough to need project-level structure
- ✅ Individual tasks within feature need AI assistance
- ✅ Team needs both "why we're doing this" and "how to do it"
- ✅ Want maximum reusability and context preservation

---

## 🎯 EXAMPLE: SPRING MIGRATION

### **Step 1: Create Spec Artifacts**

**specs/spring-migration/mainspec.md:**
```markdown
# Feature Specification: Spring 2→3 Migration

## Overview
Migrate 50+ controllers from Spring Boot 2.7 to 3.2

## Requirements
- [ ] Update all javax → jakarta imports
- [ ] Modernize @RequestMapping annotations
- [ ] Update security configuration
- [ ] Maintain API contracts

## Acceptance Criteria
- [ ] All files compile with Spring 3.2
- [ ] All tests pass
- [ ] No deprecated warnings
- [ ] API endpoints unchanged
```

**specs/spring-migration/research.md:**
```markdown
# Research: Spring 2→3 Migration

## Codebase Analysis
- 50 controllers in src/main/java/com/example/controllers/
- All use @RequestMapping (verbose style)
- SecurityConfig extends WebSecurityConfigurerAdapter (deprecated)
- Test coverage: 85%

## Existing Patterns
- Constructor injection (good, keep this)
- Standard exception handling
- Consistent API structure

## Integration Points
- Security filter chain
- Global exception handler
- CORS configuration
```

---

### **Step 2: Create 5-Mode Workflow**

**prompt-workflows/spring-migration/file-0-constitution.md:**
```markdown
# Constitution: Spring 2→3 Migration

[Extract rules from research.md findings]

## Rules:
- javax.* → jakarta.*
- @RequestMapping(method=GET) → @GetMapping
- Keep constructor injection (existing pattern)
- Maintain API contracts

[Full constitution as shown earlier]
```

**prompt-workflows/spring-migration/file-1-specification.md:**
```markdown
# Specification: Migrate UserController

[From mainspec.md requirements, specific to this controller]

## Current State: UserController (Spring 2.7)
[Code from before branch]

## Target State: UserController (Spring 3.2)
[From mainspec acceptance criteria]

## Success Criteria:
[From mainspec, applied to UserController specifically]
```

---

### **Step 3: Execute with AI**

**Load modes in AI tool:**
1. file-0-constitution.md → AI learns rules
2. file-1-specification.md → AI knows target
3. file-2-planning.md → AI has approach
4. file-3-abcd.md → Make security config decision
5. file-4-implementation.md → AI generates code

**Document in knowledge_bank.md:**
```markdown
## Session 2025-11-11 14:00

### Completed
- Migrated UserController using 5-mode workflow
- Chose Option B for security config (custom SecurityFilterChain)
- All tests passing

### Key Decision: Security Config
[From Mode 4 ABCD]
- Context: WebSecurityConfigurerAdapter deprecated
- Options: A (default), B (custom), C (deprecated), D (multiple)
- Chose: B (custom SecurityFilterChain)
- Rationale: Preserves custom auth logic, follows Spring 3 patterns
- Validation: Tests pass, no security regressions

### Next Steps
- Migrate OrderController (reuse same workflow)
- Update implementation_plan.md task checklist
```

---

### **Step 4: Iterate**

**For next controller (OrderController):**

1. ✅ Constitution: Reuse file-0 (same rules)
2. ⚡ Specification: Update file-1 (change controller name)
3. ✅ Planning: Reuse file-2 (same approach)
4. ✅ ABCD: Reference knowledge_bank decision (already made)
5. ⚡ Implementation: Run file-4 (fast!)

**Result:** 30 min first controller → 5 min every controller after

---

## 📊 BENEFITS OF COMBINED APPROACH

### **Spec-Driven Artifacts Give You:**
- 📝 Project-level documentation
- 🧠 Context preservation across sessions
- 👥 Team knowledge sharing
- 📈 Progress tracking
- ❓ "Why" documentation

### **5-Mode Workflows Give You:**
- ⚡ Fast AI-powered execution
- 🔄 Reusability across similar tasks
- 🎯 Systematic AI collaboration
- 🧪 Consistent code quality
- 🚀 Productivity gains

### **Together They Give You:**
- 🏗️ **Structure + Speed** - Organized at project level, fast at task level
- 🧠 **Context + Execution** - Know why + how to do it
- 👥 **Team + Individual** - Team sees artifacts, individual uses modes
- 📚 **Documentation + Automation** - Human-readable docs, AI-readable prompts
- 🔄 **Reusability + Traceability** - Reuse modes, trace decisions in artifacts

---

## 🎓 TRAINING INTEGRATION

### **Add to Day 1 Workshop:**

**After teaching 5 modes, add:**
"These 5 modes work great with spec-driven development artifacts. If you're starting a complex feature:
1. Create mainspec.md (requirements)
2. Run research.md (analyze codebase)
3. Extract constitution from research findings
4. Build 5-mode workflow
5. Execute, document in knowledge_bank"

---

### **Add to Day 2 Workshop:**

**After writing workflows, add:**
"Your workflow can be part of spec-driven development:
1. specs/feature/ has mainspec, implementation_plan, knowledge_bank
2. prompt-workflows/feature/ has your 5 modes
3. Artifacts preserve 'why', modes execute 'how'
4. Both live in Git, both evolve with project"

---

## ✅ QUICK REFERENCE

### **When starting NEW feature:**
```bash
# 1. Create spec artifacts
mkdir -p specs/feature-name/
create mainspec.md        # Human writes requirements
create research.md        # Analyze codebase

# 2. Create 5-mode workflow
mkdir -p prompt-workflows/feature-name/
extract file-0 from research.md    # Constitution
write file-1 from mainspec.md      # Specification
generate file-2 with AI            # Planning
identify file-3 decision points    # ABCD
create file-4 template             # Implementation

# 3. Execute
load modes → generate code → update knowledge_bank
```

### **When resuming existing feature:**
```bash
# 1. Read context
read knowledge_bank.md    # Where were we?
read implementation_plan.md  # What's next?

# 2. Load modes
reuse file-0 (constitution)
update file-1 (specification for current task)
reuse file-2 (planning)
reference file-3 (past decisions)
run file-4 (implementation)

# 3. Update artifacts
append to knowledge_bank.md
check off implementation_plan.md tasks
note any new decisions
```

---

## 🎉 SUMMARY

**You now have TWO complementary frameworks:**

**Spec-Driven Development Artifacts:**
- mainspec.md → WHAT to build (requirements)
- implementation_plan.md → Tasks and phases
- knowledge_bank.md → Context and decisions
- research.md → Codebase analysis
- notes.md → Quick captures

**5 Prompt Modes:**
- Mode 1 (Constitution) → Rules (from research.md)
- Mode 2 (Specification) → Target (from mainspec.md)
- Mode 3 (Planning) → Approach (from implementation_plan.md)
- Mode 4 (ABCD) → Decisions (logged in knowledge_bank.md)
- Mode 5 (Implementation) → Code generation

**Use them together:**
- Artifacts for project structure and context
- Modes for task execution and AI collaboration
- Both in Git for version control
- Both evolve throughout development

**Result:** 
- Organized project documentation
- Fast AI-assisted execution
- Context preserved across sessions
- Team knowledge sharing
- Measurable productivity gains

---

**Document Status:** Integration Guide  
**Created:** 2025-11-11  
**Purpose:** Bridge Spec-Driven Development and 5 Prompt Modes  
**Maintainer:** Joseph Lopez
