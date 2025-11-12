# spec/ Folder Workflow Guide

**Complete guide to spec-driven development using the spec/ folder structure.**

**Quick Start:** Create folder → Fill templates → Execute workflow

---

## Overview

**Never waste implementation time on misunderstood requirements. Read 3 docs first, build second.**

### The Three Required Files

```
spec/
├── knowledge-base.md        # Domain context (reusable)
├── specification.md         # Requirements (this feature)
└── implementation-plan.md   # Technical approach (this feature)
```

**Philosophy:**
- knowledge-base.md: Write once, use forever (project-level)
- specification.md: New file per feature (feature-level)
- implementation-plan.md: Generated from specification (execution-level)

---

## Part 1: Folder Setup

### Quick Setup

```bash
# Create folder + files
mkdir -p spec
cp knowledge-base-template.md spec/knowledge-base.md
cp specification-template.md spec/specification.md
```

### What Goes Where?

| File | Scope | Content |
|------|-------|---------|
| **knowledge-base.md** | Project | Domain terms, architecture patterns, constraints, past decisions |
| **specification.md** | Feature | Requirements, acceptance criteria, API contracts, edge cases |
| **implementation-plan.md** | Feature | Phases, tasks, dependencies, testing strategy, timeline |

**Workflow:**
1. Fill `knowledge-base.md` once per project
2. Create new `specification.md` per feature
3. Generate `implementation-plan.md` using Planning Mode
4. Build using Spec-Driven Mode

---

## Part 2: Spec-Driven Mode (Execution)

**Workflow: Read docs → Verify understanding → Implement phase-by-phase**

### Step 1: Document Discovery

Search for the three required files. Report what you find:

```
Found: knowledge-base.md, specification.md
Missing: implementation-plan.md
```

### Step 2: Read and Extract

**From knowledge-base.md:**
- Domain concepts (terminology, definitions)
- Architectural decisions (patterns, rationale)
- Constraints (technical, regulatory, organizational)

**From specification.md:**
- Requirements (functional, non-functional)
- Acceptance criteria (how to verify)
- Edge cases (boundary conditions)

**From implementation-plan.md:**
- Current phase (execution order)
- Dependencies (what must complete first)
- Testing approach (validation strategy)

### Step 3: Synthesize and Clarify

Summarize understanding:

```
Domain uses [terminology] to mean [definition]
Architecture follows [pattern] because [rationale]
Critical constraint: [constraint]

This feature requires: [requirement]
Must handle edge case: [case]
Acceptance criteria: [criteria]

This is Phase [N], depends on: [dependencies]
```

Identify gaps/conflicts, ask clarifying questions.

### Step 4: Get Approval

Present plan before implementation. Wait for explicit approval.

### Step 5: Execute Phase-by-Phase

Implement according to plan, validate between phases.

### Step 6: Update Documentation

After implementation, update knowledge-base.md with decisions and lessons learned.

### Handling Missing Documents

- **Missing knowledge-base.md**: Proceed, document decisions as you go
- **Missing specification.md**: CRITICAL - Create it first based on user description
- **Missing implementation-plan.md**: Offer to create using Planning Mode

### Critical Rules

✅ Read all documentation before starting
✅ Create missing specification.md
✅ Verify understanding before implementation
✅ Update documentation after implementation
❌ Never implement without specification
❌ Never skip acceptance criteria verification

---

## Part 3: Planning Mode (Create implementation-plan.md)

**Plan first, build second. 5 minutes planning saves 5 hours debugging.**

### Core Philosophy

Prevents: Wasted effort, misunderstood requirements, missing edge cases, technical dead-ends, scope creep.

### Workflow

**Phase 1: Discovery**

1. Read request carefully - what's the end goal?
2. Identify ambiguities - ask clarifying questions upfront
3. State assumptions explicitly
4. Identify constraints (technical, resource, business, quality)

**Phase 2: Create Plan**

Generate structured plan using implementation-plan-template.md:

**Plan Structure:**
1. Objective (goal, success criteria, out of scope)
2. Approach (strategy, key decisions, alternatives)
3. Implementation Phases (tasks, dependencies, risks, verification)
4. Testing Strategy (unit, integration, edge cases, acceptance)
5. Rollout (deployment steps, rollback, monitoring)
6. Open Questions
7. Timeline

**Phase 3: Approval**

Present plan, get explicit approval before implementation.

**Phase 4: Execution**

Implement phase-by-phase, validate after each phase.

### Critical Rules

✅ Plan before building
✅ State assumptions explicitly
✅ Get approval before execution
✅ Validate between phases
❌ Never skip planning for complex tasks
❌ Never assume - verify interpretations

---

## Part 4: ABCD Clarification Mode (Handle Ambiguities)

**Work autonomously but stop at ambiguities to present 4 options.**

**Note**: ABCD decisions get recorded in spec/specification.md under "Design Decisions"

### Core Behavior

1. Work autonomously on clear requirements
2. Stop immediately when encountering:
   - Ambiguous requirements (multiple interpretations)
   - Technical decisions (multiple valid approaches)
   - Tradeoffs (speed vs quality, simple vs flexible)
   - Design choices affecting UX/architecture
   - Edge cases needing handling decisions
3. Present exactly 4 options (A, B, C, D)
4. Make recommendation with reasoning
5. Wait for user input before proceeding

### ABCD Presentation Format

```
---
Clarification Question [N]: [State the ambiguity clearly]

Recommended: Option [X] - [One-line summary]

Reasoning: [2-3 sentences explaining why given context, constraints, best practices, tradeoffs]

| Option | Description |
|--------|-------------|
| A | [Conservative/safe/traditional approach] |
| B | [Balanced/pragmatic approach] |
| C | [Alternative/creative approach] |
| D | [Edge case/contrarian/different philosophy] |

Reply with: option letter (e.g., "B"), "yes"/"recommended", or your own answer.
---
```

### User Response Handling

- **Letter (A/B/C/D)**: Use that choice, continue
- **"yes"/"recommended"**: Use recommended option, continue
- **Custom answer**: Integrate their guidance, continue
- **"skip"/"decide for me"**: Use recommended option, continue

### When to Trigger ABCD

**DO trigger for**:
- Implementation choices (REST vs GraphQL, SQL vs NoSQL)
- Error handling strategies (fail fast vs graceful degradation)
- Architecture patterns (monolith vs microservices)

**DON'T trigger for**:
- Obvious best practices (input validation, password hashing)
- Minor formatting/style (spacing, naming)
- Decisions already in requirements

### Option Design Guidelines

**Option A**: Lowest risk, most proven, may sacrifice innovation
**Option B**: Balanced, industry standard (usually recommended)
**Option C**: Alternative approach, may be better for specific contexts
**Option D**: Unconventional, addresses specific edge cases

### Critical Rules

✅ Make recommendations based on context
✅ Provide clear reasoning
✅ Present genuinely different options
✅ Wait for user input
✅ Keep working between clarifications
❌ Don't clarify obvious/trivial decisions
❌ Don't make all options equal (have real recommendation)
❌ Don't over-clarify (balance momentum with quality)

---

## Appendix: File Templates

### specification.md Template

```markdown
# Feature Specification

**Location**: spec/specification.md
**Related**: knowledge-base.md (domain context), implementation-plan.md (how to build)
**Created**: [Date]
**Last Updated**: [Date]

**Small feature?** Just fill: Functional Requirements + Acceptance Criteria + Edge Cases
**API feature?** Add: API Contract + Business Rules
**Data feature?** Add: Data Model

---

## REQUIRED (Always fill these)

### Functional Requirements

- [ ] Requirement 1
- [ ] Requirement 2
- [ ] Requirement 3

### Acceptance Criteria

**MUST VERIFY** - How do we know we're done?

- [ ] Criterion 1 (testable)
- [ ] Criterion 2 (testable)
- [ ] Criterion 3 (testable)

---

## RECOMMENDED (Fill if applicable)

### User Story

**As a** [role]
**I want** [feature]
**So that** [benefit]

### API Contract

Document all endpoints this feature touches. Include:
- HTTP method + path
- Request body schema
- Response codes + bodies
- Authentication requirements

### Business Rules

- Rule 1: [Description]
- Rule 2: [Description]

---

## OPTIONAL (Add as needed)

### Data Model

- Entity: [Name]
  - field1: [type] [description]
  - field2: [type] [description]

### Edge Cases

- Case 1: [How to handle empty input]
- Case 2: [How to handle duplicate entries]

### Non-Functional Requirements

- Performance: [API response time < 200ms]
- Security: [All passwords hashed with bcrypt]
- Scalability: [Support 10k concurrent users]

---

## Design Decisions

Record ABCD clarification decisions here:

- [Decision point]: Chose [option] because [reasoning]
- [Decision point]: Chose [option] because [reasoning]
```

---

### knowledge-base.md Template

```markdown
# Project Knowledge Base

**Location**: spec/knowledge-base.md
**Created**: [Date]
**Last Updated**: [Date]

**First time?** Start with:
1. **Constraints** - What can't we change? (databases, APIs, compliance)
2. **Domain Concepts** - What jargon needs defining?
3. **Architectural Principles** - What patterns do we follow?

**Small project?** Start with just Constraints + Domain Concepts. Add sections as needed.

---

## Domain Concepts

Business terms that might confuse developers. Define once, reference everywhere.

- [Term]: [Definition]
- [Term]: [Definition]

## Architectural Principles

Patterns we follow and why. Helps AI stay consistent with project style.

- Pattern: [Name and rationale]
- Anti-patterns: [What to avoid]

## System Context

External systems and infrastructure we integrate with.

- Infrastructure: [Description]
- Integrations: [List]

## Past Decisions

Previous technical decisions and their rationale (ADR-style).

- [Decision]: [Rationale] (Date: [When])
- [Decision]: [Rationale] (Date: [When])

## Constraints

**MUST-FOLLOW** limitations. Most critical section.

- Technical: [Database version, language version, APIs we must use]
- Regulatory: [GDPR, HIPAA, SOC2 requirements]
- Organizational: [Team size, timeline, budget]

## Lessons Learned

What we learned from previous projects or iterations.

- [What we learned and how it affects this project]
- [What we learned and how it affects this project]
```

---

### implementation-plan.md Template

```markdown
# Implementation Plan: [Project Name]

## 1. Objective

**Goal**: [What are we building/solving in one clear sentence]

**Success Criteria**:
- [ ] Criterion 1 (measurable/testable)
- [ ] Criterion 2 (measurable/testable)
- [ ] Criterion 3 (measurable/testable)

**Out of Scope**:
- Item 1
- Item 2

## 2. Approach

**High-Level Strategy**: [2-3 sentences on overall approach]

**Key Technical Decisions**:
- Decision 1: [Choice made] - Rationale: [Why]
- Decision 2: [Choice made] - Rationale: [Why]

**Alternatives Considered**: [What approaches we rejected and why]

## 3. Implementation Phases

### Phase 1: [Phase Name]

**Goal**: [What this phase achieves]

**Tasks**:
1. Task 1 - [Description]
2. Task 2 - [Description]

**Input**: [What's needed to start this phase]
**Output**: [What gets produced]
**Dependencies**: [None / Must complete Phase X first]
**Estimated Effort**: [Time estimate]

**Risks**:
- Risk 1 - Mitigation: [How to handle]

**Verification**:
- [ ] How to test/verify this phase worked

---

### Phase 2: [Phase Name]

[Same structure as Phase 1]

## 4. Testing Strategy

**Unit Testing**: [Approach for testing individual components]

**Integration Testing**: [Approach for testing components together]

**Edge Cases to Test**:
- Edge case 1
- Edge case 2

**Acceptance Testing**: [How to verify against success criteria]

## 5. Rollout/Deployment

**Deployment Steps**:
1. Step 1
2. Step 2

**Rollback Plan**: [How to undo if things break]

**Monitoring**: [What to watch after deployment]

## 6. Open Questions

- [ ] Question 1 that needs answering
- [ ] Question 2 that needs answering

## 7. Timeline

| Phase | Duration | Dependencies |
|-------|----------|--------------|
| Phase 1 | [Time] | None |
| Phase 2 | [Time] | Phase 1 |
| **Total** | **[Time]** | |
```

---

## Quick Reference

**To start a new feature:**
1. Check if `spec/knowledge-base.md` exists (create if first feature)
2. Create `spec/specification.md` for this feature
3. Use Planning Mode to generate `spec/implementation-plan.md`
4. Use Spec-Driven Mode to execute
5. Use ABCD Mode when hitting ambiguities

**Integration with other workflows:**
- Works with ADRs (knowledge-base.md records decisions ADR-style)
- Works with copilot-instructions.md (architectural principles → config file)
- Works with alternatives/5-mode-pedagogy (same content, different names)
