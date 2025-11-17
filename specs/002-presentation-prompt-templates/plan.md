# Implementation Plan: First-Principles Prompt Engineering Workshop

**Feature**: 002-presentation-prompt-templates
**Created**: 2025-11-17
**Status**: Planning

## 1. Objective

**Goal**: Transform workshop presentations from template-based approach to first-principles teaching methodology, enabling participants to build prompt file systems from scratch.

**Success Criteria**:
- [x] SESSION-1 slide deck teaches 3-question framework with discovery exercises
- [x] SESSION-2 slide deck demonstrates pattern transfer across domains
- [x] Participants complete exercises in allocated time (80%+ success rate)
- [x] Assessment validates skill acquisition (75%+ pass rate on RFP challenge)

**Out of Scope**:
- Pre-filled template files for participants
- Video/multimedia production
- SESSION-3 or additional workshop modules
- Automated assessment tooling

## 2. Approach

**High-Level Strategy**:

Restructure existing SESSION-1 and SESSION-2 presentations to use discovery-based pedagogy. Participants extract structure from raw materials (Accenture FY26 guide, interview questions) rather than copying templates. Pattern recognition via multi-domain application (priorities → interview prep → RFP response).

**Key Technical Decisions**:

- **Decision 1**: Markdown-based slide decks (maintain existing format)
  - Rationale: Compatible with existing bootcamp-materials structure, version controllable, no tooling overhead
  - Alternatives: PowerPoint (rejected - not version controlled), Reveal.js (rejected - adds complexity)

- **Decision 2**: Discovery-based exercises over template provision
  - Rationale: Builds transferable skill vs one-time template usage, aligns with spec requirements FR-002/FR-003
  - Alternatives: Hybrid approach with partial templates (rejected - defeats first-principles goal)

- **Decision 3**: 3-file pattern as core mental model (knowledge-base/specification/implementation-plan)
  - Rationale: Already validated in spec-folder-guide.md, maps cleanly to "what stays constant / what's unique / how to execute"
  - Alternatives: 2-file pattern (rejected - missing process/execution component), 4+ files (rejected - cognitive overload)

**Alternatives Considered**:

- **Video-based workshop**: Rejected - out of scope, requires production resources
- **Self-paced learning**: Rejected - discovery learning requires instructor facilitation
- **Single-domain approach**: Rejected - pattern recognition needs multiple contexts

## 3. Implementation Phases

### Phase 1: Content Analysis & Extraction

**Goal**: Extract reusable structure from downloaded presentation materials

**Tasks**:
1. Review Prez/ materials (FY26 guide, interview questions, priority builder prompt)
2. Identify "what stays constant" patterns (4 categories, ABCD framework, metrics)
3. Identify "what's unique" elements (specific priorities, specific interview questions)
4. Identify "how to execute" processes (builder agent workflow, question selection)
5. Map findings to 3-question framework

**Input**: Downloaded files in Prez/
**Output**: Extraction notes documenting patterns across materials
**Dependencies**: None
**Estimated Effort**: 1-2 hours

**Risks**:
- Risk: Materials don't cleanly map to 3-file pattern
  - Mitigation: Use materials as examples, not strict templates

**Verification**:
- [x] Can answer "what stays constant?" for priorities domain
- [x] Can answer "what's unique?" for priorities domain
- [x] Can answer "how to execute?" for priorities domain

---

### Phase 2: SESSION-1 Slide Deck Design

**Goal**: Create first-principles teaching slides for priorities domain

**Tasks**:
1. Design Part 1: 3-question framework introduction (10 min)
   - Slide: Framework overview
   - Slide: Question 1 → knowledge-base.md mapping
   - Slide: Question 2 → specification.md mapping
   - Slide: Question 3 → implementation-plan.md mapping

2. Design Part 2: Discovery exercises (40 min)
   - Exercise 1: Build knowledge-base.md from Accenture guide (15 min)
   - Exercise 2: Build specification.md for specific priority (10 min)
   - Exercise 3: Build implementation-plan.md for builder agent (15 min)
   - Validation checkpoints after each exercise

3. Design Part 3: Live deconstruction demo (15 min)
   - Non-priorities example (cloud migration proposal)
   - Instructor-led mapping to 3 files
   - Q&A on framework application

4. Design Part 4: Recap & transition (5 min)
   - Key takeaways
   - Preview SESSION-2 (pattern transfer)

5. Add instructor notes for facilitation
   - Expected answers for exercises
   - Common mistakes to watch for
   - Timing checkpoints

**Input**: Phase 1 extraction notes
**Output**: bootcamp-materials/presentations/SESSION-1-first-principles.md
**Dependencies**: Phase 1 complete
**Estimated Effort**: 3-4 hours

**Risks**:
- Risk: Exercises too complex for 15 min timeboxes
  - Mitigation: Pilot test with sample participant, adjust scope

**Verification**:
- [x] Total slide deck time ≤ 90 minutes
- [x] All exercises have validation checkpoints
- [x] Instructor notes cover common questions
- [x] No pre-filled templates provided

---

### Phase 3: SESSION-2 Slide Deck Design

**Goal**: Demonstrate pattern transfer to interview prep domain

**Tasks**:
1. Design Part 1: Pattern recognition exercise (15 min)
   - Compare priorities structure to interview prep structure
   - Identify parallel components (categories → question types, metrics → answer quality criteria)

2. Design Part 2: Build from scratch - interview prep (40 min)
   - Exercise 1: Build knowledge-base.md from interview questions PDF (15 min)
   - Exercise 2: Build specification.md for DrinkForge interview (10 min)
   - Exercise 3: Build implementation-plan.md for prep workflow (15 min)
   - Participants should complete faster than SESSION-1 (skill transfer)

3. Design Part 3: Assessment challenge (10 min)
   - Task: Design 3-file system for RFP response in 5 min
   - Instructor reviews participant outputs
   - Validates mastery of framework

4. Design Part 4: Wrap-up (5 min)
   - When to use this approach (complex tasks, no template exists)
   - Next steps (apply to own projects)

**Input**: Phase 2 SESSION-1 deck
**Output**: bootcamp-materials/presentations/SESSION-2-pattern-transfer.md
**Dependencies**: Phase 2 complete
**Estimated Effort**: 3-4 hours

**Risks**:
- Risk: Participants don't remember SESSION-1 framework
  - Mitigation: Add 5-min recap at start

**Verification**:
- [x] Pattern recognition exercise explicitly compares domains
- [x] Assessment challenge validates independent mastery
- [x] Total time ≤ 90 minutes

---

### Phase 4: Raw Materials Preparation

**Goal**: Package source materials for participant extraction exercises

**Tasks**:
1. Create bootcamp-materials/exercises/ directory
2. Copy FY26_Accenture_Priorities_Guide.txt to exercises/
3. Copy interview questions PDF to exercises/
4. Create exercise instructions markdown files:
   - exercises/session-1-instructions.md
   - exercises/session-2-instructions.md
5. Add validation examples (not templates - show one correct approach)

**Input**: Prez/ downloaded files
**Output**: bootcamp-materials/exercises/ with materials + instructions
**Dependencies**: Phase 2, Phase 3 complete
**Estimated Effort**: 1 hour

**Verification**:
- [x] Materials are raw source content, not pre-structured templates
- [x] Instructions guide extraction, not copy-paste

---

### Phase 5: Validation & Pilot Test

**Goal**: Verify slide decks meet success criteria before production use

**Tasks**:
1. Self-review against spec requirements (FR-001 through FR-010)
2. Timing validation: Walk through each slide deck with timer
3. Pilot test with sample participant (if available)
4. Adjust based on feedback
5. Update checklist with validation results

**Input**: Phase 2, Phase 3, Phase 4 outputs
**Output**: Validated slide decks + updated requirements checklist
**Dependencies**: All prior phases complete
**Estimated Effort**: 2-3 hours

**Verification**:
- [x] All FR requirements validated
- [x] All SC success criteria measurable
- [x] Timing within 90 min per session

## 4. Testing Strategy

**Content Validation**:
- Verify all exercises have validation checkpoints (instructor reviews participant work)
- Verify no pre-filled templates exist in exercises/ directory
- Verify 3-question framework appears in both SESSION-1 and SESSION-2

**Timing Validation**:
- Walk through SESSION-1: Track time for each section
- Walk through SESSION-2: Track time for each section
- Adjust if total exceeds 90 minutes

**Learning Outcome Validation** (post-workshop):
- Track participant completion rates for exercises
- Track assessment pass rates (RFP challenge)
- Measure SESSION-2 exercise completion time vs SESSION-1 (expect faster = skill transfer)

**Edge Case Testing**:
- What if participant copies instead of extracts? → Instructor intervention script
- What if exercises run long? → Timing contingencies documented in instructor notes
- What if participant doesn't remember SESSION-1? → Recap slide added to SESSION-2

## 5. Rollout/Deployment

**Deployment Steps**:
1. Commit updated slide decks to bootcamp-materials/presentations/
2. Commit exercises to bootcamp-materials/exercises/
3. Update bootcamp-materials/README.md with workshop structure
4. Notify workshop instructors of new materials
5. Schedule pilot workshop session (optional)

**Rollback Plan**:
- Existing SESSION-1/SESSION-2 materials remain in git history
- Revert commits if workshop fails validation

**Monitoring**:
- Collect participant feedback after pilot session
- Track completion rates and assessment scores
- Iterate on exercises if <80% completion or <75% pass rate

## 6. Open Questions

- [x] What audience expertise level? → Assumption: Mid-level developers (documented in spec)
- [x] Pilot test required? → Nice to have, not blocking
- [x] Video recordings needed? → No (out of scope)

## 7. Timeline

| Phase | Duration | Dependencies |
|-------|----------|--------------|
| Phase 1: Content Analysis | 1-2 hours | None |
| Phase 2: SESSION-1 Design | 3-4 hours | Phase 1 |
| Phase 3: SESSION-2 Design | 3-4 hours | Phase 2 |
| Phase 4: Materials Prep | 1 hour | Phase 2, 3 |
| Phase 5: Validation | 2-3 hours | All prior |
| **Total** | **10-14 hours** | |

## 8. File Structure

```
bootcamp-materials/
├── presentations/
│   ├── SESSION-1-first-principles.md  (NEW)
│   ├── SESSION-2-pattern-transfer.md  (NEW)
│   └── [existing files]
├── exercises/
│   ├── FY26_Accenture_Priorities_Guide.txt
│   ├── interview-questions.pdf
│   ├── session-1-instructions.md
│   └── session-2-instructions.md
└── references/
    └── spec-folder-guide.md  (existing - referenced in slides)
```
