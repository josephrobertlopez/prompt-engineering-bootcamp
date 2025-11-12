# Feature Specification: Presentation Timing Restructure

**Created**: 2025-11-12
**Status**: Draft
**Target**: SESSION-1 and SESSION-2 presentation materials

## Clarifications

### Session 2025-11-12

- Q: For SESSION 1's 20 minutes, should the flow emphasize comparative experiment or foundational concepts? → A: Option B - Foundational concepts first, then tease comparative experiment for hands-on
- Q: For SESSION 2's presentation, should orchestration be demonstrated through live walkthrough or conceptual diagrams? → A: Option C - Split: 10 min concepts, 10 min live demo

## REQUIRED

### Functional Requirements

**SESSION 1 (90 minutes total):**
- [ ] 30 min slides: Learning concepts (prompting templates, tool evaluation, ad-hoc vs structured workflows, ADR evolution)
- [ ] 40 min: Spring Boot demo hands-on
  - [ ] 20 min: Freestyle experimentation (participants try ad-hoc approach)
  - [ ] 10 min: Show guided templated solution
  - [ ] 10 min: Participants apply templates themselves
- [ ] 20 min: Review, discussion, wrap-up

**SESSION 2 (90 minutes total):**
- [ ] 30 min slides: Learning concepts (orchestration, ReAct, Tree of Thoughts, ADR vs spec-kit comparison)
- [ ] 40 min: Spring Boot demo hands-on
  - [ ] 20 min: Freestyle with basic prompt file (participants experiment)
  - [ ] 10 min: Show proper spec-kit prompt files for migration
  - [ ] 10 min: Participants apply spec-kit approach themselves
- [ ] 20 min: Review, discussion, wrap-up

### Acceptance Criteria

**SESSION 1:**
- [ ] Foundational concepts slide deck covers all required topics in 20 minutes
- [ ] Freestyle exercise has clear success criteria (specific task on Java codebase)
- [ ] Templated solution demo shows measurable speed/quality improvement vs freestyle
- [ ] Participants can apply templates to migration task within 40 min time box

**SESSION 2:**
- [ ] Orchestration concepts clearly explain ReAct (Think→Act→Observe) and Tree of Thoughts patterns
- [ ] ADR vs spec-kit comparison shows concrete examples from both approaches
- [ ] Live demo demonstrates end-to-end code generation with both strategies
- [ ] Cadence matches SESSION 1 structure (20 min slides, demonstration phase, application phase)
- [ ] Common Pitfalls slide prevents frequently observed mistakes
- [ ] Participants can complete end-to-end migration using spec-kit prompt files

**Cross-Session:**
- [ ] Total time per session = 90 minutes (no overtime)
- [ ] Similar pedagogical cadence between sessions
- [ ] Clear progression: SESSION 1 (individual patterns) → SESSION 2 (orchestration)

## RECOMMENDED

### User Story

**As a** workshop facilitator
**I want** restructured presentation timing for both sessions
**So that** participants experience both freestyle and templated approaches with adequate time for hands-on application

### Session Flow Design

**SESSION 1 Flow (Comparison-Focused):**

```
0-30 min:   Slides (Learning Concepts)
            ├─ Prompting templates overview (8 min)
            ├─ Tool evaluation (Copilot, Cursor, Windsurf) (7 min)
            ├─ Ad-hoc vs structured workflows (8 min)
            └─ Evolution: ADRs → Specs (7 min)

30-50 min:  Freestyle Experimentation (Active)
            └─ Task: Migrate UserController using ad-hoc prompts
            └─ Participants experiment with own approach
            └─ Instructor provides hints/help

50-60 min:  Show Guided Solution (Demonstration)
            ├─ Load 5-file template structure (3 min)
            ├─ Execute same task with templates (4 min)
            └─ Compare: freestyle vs templated results (3 min)

60-70 min:  Apply Templates (Active)
            └─ Participants apply templates to controller migration
            └─ Quick validation of results

70-90 min:  Review & Discussion
            ├─ What worked? What didn't? (10 min)
            ├─ Q&A (8 min)
            └─ Preview SESSION 2 (2 min)
```

**SESSION 2 Flow (Orchestration-Focused):**

```
0-30 min:   Slides (Learning Concepts)
            ├─ Prompt orchestration overview (7 min)
            ├─ ReAct pattern (Think→Act→Observe) (6 min)
            ├─ Tree of Thoughts (alternatives evaluation) (6 min)
            ├─ ADR vs spec-kit comparison (6 min)
            └─ Use case matrix: when to use each (5 min)

30-50 min:  Freestyle with Basic Prompt (Active)
            └─ Task: End-to-end migration with basic prompt file
            └─ Participants experiment with minimal structure
            └─ Observe where they struggle

50-60 min:  Show Proper Spec-Kit Files (Demonstration)
            ├─ Load spec/ folder (knowledge-base, spec, plan) (3 min)
            ├─ Execute orchestrated workflow (4 min)
            └─ Compare: basic vs spec-kit approach (3 min)

60-70 min:  Apply Spec-Kit Approach (Active)
            └─ Participants use spec/ folder for migration
            └─ Validate against acceptance criteria

70-90 min:  Review & Discussion
            ├─ Lessons learned (10 min)
            ├─ When to use which approach (5 min)
            ├─ Q&A (5 min)
```

### Business Rules

- Slide content must be self-contained (no external dependencies during presentation)
- Hands-on exercises must reference spring-migration-demo repository
- Demonstration phases use real code execution (not mockups)
- Timing allows 5-10 min buffer for questions
- Participants can choose their AI tool (Copilot/Claude/Cursor/Windsurf)

## OPTIONAL

### Data Model

**Presentation Assets:**
- SESSION-1-industry-standards.md (existing, needs restructure)
- SESSION-2-advanced-patterns.md (existing, needs restructure)
- spring-migration-demo/demos/session-1-*/prompts/ (5-file pattern)
- spring-migration-demo/demos/session-2-*/spec/ (spec folder pattern)

### Edge Cases

**Case 1: Participants finish hands-on early**
- Provide extension exercise: Apply patterns to SecurityConfig migration
- Direct to reference materials for self-study

**Case 2: Participants struggle with freestyle phase (SESSION 1)**
- Instructor provides scaffolding prompts
- Show example of ad-hoc prompt that "works but isn't reusable"

**Case 3: Live demo encounters technical issues (SESSION 2)**
- Have pre-recorded backup video ready
- Provide written transcript of expected AI responses

**Case 4: Time overruns during demonstration phases**
- Skip detailed explanation of anti-patterns slide (optional content)
- Reduce wrap-up to 2 minutes with resource handout

### Non-Functional Requirements

- **Clarity**: Slide content understandable without presenter narration
- **Reproducibility**: All demos must work with provided repository state
- **Accessibility**: Code examples use high-contrast syntax highlighting
- **Pacing**: No single slide exceeds 3 minutes of content

## Design Decisions

### Decision 1: Session Structure - Identical 30/40/20 Split

**Chosen: 30 min slides / 40 min demo (20 freestyle + 10 show + 10 apply) / 20 min review**

**Reasoning (from user requirement)**: Both sessions must have identical cadence to establish predictable rhythm. Participants learn the structure in SESSION 1 and can focus on content (not structure) in SESSION 2.

**Debate Findings:**
- Original proposal: SESSION 1 (20/50/20), SESSION 2 (15/70/5) = inconsistent
- Risk: Different pacing between sessions confuses participants
- Fix: Standardize to 30/40/20 for both sessions

**Alternatives Considered:**

| Option | SESSION 1 | SESSION 2 | Pros | Cons |
|--------|-----------|-----------|------|------|
| **A** | **30/40/20** | **30/40/20** | **Consistent, predictable** | **Tight on demo time** |
| B | 20/50/20 | 20/50/20 | More demo time | Less concept coverage |
| C | 25/45/20 | 25/45/20 | Balanced | No clear advantage |
| D | Variable | Variable | Flexible per session | Confusing for participants |

**Impact**: Cadence consistency > individual optimization per session

---

### Decision 2: Freestyle Time Allocation Within Demo

**Chosen: 20 minutes freestyle (out of 40 min demo block)**

**Reasoning (from user requirement + debate)**: 20 min allows meaningful struggle without excessive frustration. Debate identified that original 10 min was too short to experience ad-hoc limitations. 20 min provides:

**Alternatives Considered:**

| Option | Duration | Pros | Cons |
|--------|----------|------|------|
| A | 20 min | More exploration time | Risk of frustration, hard to recover schedule |
| **B** | **15 min** | **Balanced, keeps schedule** | **Less exploration depth** |
| C | 10 min | Very tight schedule | Too rushed, won't see ad-hoc struggles |
| D | 25 min | Deep exploration | Cuts into template application time |

**Impact**: Tighter pacing in freestyle phase, more time for explaining templated solution benefits

---

### Decision 2: Live Demo Categorization

**Chosen: Part of hands-on demonstration phase (25 min)**

**Reasoning (from debate)**: While participants observe passively, the demo is interactive (instructor fielding questions, showing real execution). Categorizing as "demonstration" rather than "slides" sets correct expectations. Reduced from 30 to 25 min to add wrap-up buffer.

**Alternatives Considered:**

| Option | Category | Duration | Pros | Cons |
|--------|----------|----------|------|------|
| **A** | **Demonstration** | **25 min** | **Accurate categorization** | **Long passive phase** |
| B | Slides | 30 min | Keeps "slides" block together | Misleading (not static slides) |
| C | Split demo | 15+15 min | Breaks up passive time | Disrupts narrative flow |
| D | Shorter demo | 15 min | More hands-on time | Too rushed, misses key patterns |

**Impact**: SESSION 2 has longer demonstration phase than SESSION 1 (25 vs 15 min) but justified by complexity

---

### Decision 3: Missing 5 Minutes Content

**Chosen: Common Pitfalls & Anti-Patterns slide**

**Reasoning (from debate)**: Addresses frequently observed workshop mistakes. Prevents participants from repeating known failure modes during hands-on. Complements orchestration concepts with practical guardrails.

**Alternatives Considered:**

| Option | Content | Pros | Cons |
|--------|---------|------|------|
| **A** | **Common Pitfalls** | **Immediately actionable** | **Slightly negative framing** |
| B | Extended Q&A | Interactive | Hard to time accurately |
| C | Tool comparison matrix | Detailed evaluation | May cause tool debates |
| D | Success stories | Inspiring | Less actionable |

**Impact**: Reduces hands-on errors, provides preventive guidance

---

### Overall Restructure Strategy

**Approach: Debate-Validated Timing with Pedagogical Balance**

This restructure uses step-by-step reasoning (debate with Judge, Skeptic, Advocate, Evidence Gatherer agents) to validate timing feasibility. Key principles:
- Foundational before advanced (SESSION 1 → SESSION 2 progression)
- Demonstrate before apply (show solution → participants try)
- Balance passive and active time (max 25 min demonstration phases)
- Build in schedule buffers (wrap-up time, optional content)

**Cadence Consistency:**
- Both sessions: 20 min slides → demonstration → hands-on → wrap
- SESSION 1: Emphasizes comparison (freestyle vs templated)
- SESSION 2: Emphasizes orchestration (multiple patterns coordinated)

**Risk Mitigation:**
- Pre-recorded backup demos for technical failures
- Extension exercises for fast finishers
- Scaffolding prompts for strugglers
- Optional content (anti-patterns) can be cut if time overruns
