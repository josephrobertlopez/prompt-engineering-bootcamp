# Feature Specification: First-Principles Prompt Engineering Workshop

**Feature Branch**: `002-presentation-prompt-templates`
**Created**: 2025-11-17
**Status**: Draft
**Input**: Transform workshop presentations from template-based approach to first-principles teaching methodology for prompt file system design

## Clarifications

### Session 2025-11-17

- Q: Mermaid diagram complexity limits (for cognitive load management)? → A: Complex diagrams permitted (no node limit) - prioritize comprehensive visualization over simplicity
- Q: Marp export format priority (which formats are required vs nice-to-have)? → A: All three formats required (HTML, PDF, PowerPoint)
- Q: Marp theme & styling approach? → A: Google/Accenture slide format (corporate presentation standards)
- Q: Marp export automation approach? → A: Add Marp CLI build scripts (package.json or Makefile) for automated export on demand
- Q: Google/Accenture theme implementation (emulate vs official brand assets)? → A: Use Accenture brand guidelines (official purple/fonts/logos - may need approval)
- Q: Actual Accenture brand style observed from presentation screenshots? → A: Minimalist corporate style - white backgrounds with purple accents (not purple backgrounds), Graphik font, geometric overlays, simple color-coded diagrams, clean footer layout

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Workshop Participant Learns Pattern Recognition (Priority: P1)

As a workshop participant, I want to learn how to deconstruct ANY complex task into prompt files using first principles, so that I can design prompt systems for future tasks beyond the workshop examples.

**Why this priority**: This is the core value proposition - participants gain transferable skill, not just pre-made templates. This differentiates the workshop from "here's a template" approaches.

**Independent Test**: After SESSION-1, participant can deconstruct a new task (cloud migration proposal) into knowledge-base/specification/implementation-plan structure without guidance.

**Acceptance Scenarios**:

1. **Given** SESSION-1 slide deck with 3-question framework, **When** participant completes exercises, **Then** they can identify what's reusable vs unique vs process for priorities task
2. **Given** end-of-session challenge (RFP response design), **When** participant has 5 minutes, **Then** they correctly map components to the 3-file pattern
3. **Given** live deconstruction exercise in SESSION-1, **When** instructor asks "what stays constant?", **Then** participants call out correct answers ("4 categories", "ABCD framework", "metrics")

---

### User Story 2 - Instructor Facilitates Discovery Learning (Priority: P1)

As a workshop instructor, I want slide decks structured for discovery-based learning with guided exercises, so that participants build understanding themselves rather than copying templates.

**Why this priority**: Teaching methodology is critical - discovery learning creates deeper retention than passive template delivery. Instructor needs proper facilitation structure.

**Independent Test**: Instructor can deliver SESSION-1 using only the slide prompts/exercises without providing pre-filled templates, and participants successfully build files from scratch.

**Acceptance Scenarios**:

1. **Given** SESSION-1 Part 2 exercise instructions, **When** instructor facilitates Phase 1, **Then** participants build knowledge-base.md from Accenture guide without template
2. **Given** slide deck timing estimates (7min/8min/10min), **When** instructor delivers SESSION-1, **Then** total time remains within 90 minutes
3. **Given** validation checkpoints in exercises, **When** instructor shares participant screens, **Then** they can compare different approaches and discuss tradeoffs

---

### User Story 3 - Participant Transfers Skill Across Domains (Priority: P2)

As a workshop participant, I want SESSION-2 to apply the same first-principles pattern to a different domain (interview prep), so I can validate that the approach works beyond just priorities.

**Why this priority**: Pattern recognition requires seeing the structure in multiple contexts. Single domain = memorization, multiple domains = understanding.

**Independent Test**: After SESSION-2, participant can map priorities structure to interview prep structure and explain why they're the same pattern with different content.

**Acceptance Scenarios**:

1. **Given** SESSION-2 pattern recognition exercise, **When** comparing priorities vs interview prep, **Then** participant identifies knowledge-base/specification/plan parallels
2. **Given** interview prep exercise, **When** building files from scratch, **Then** participant completes it faster than SESSION-1 (showing skill transfer)
3. **Given** end-of-SESSION-2 challenge (RFP response), **When** participant designs 3-file system in 5 min, **Then** they demonstrate independent mastery

---

### Edge Cases

- **What if participants try to copy-paste from Accenture guide instead of extracting principles?**
  - Instructor intervention: "Don't copy text - extract the STRUCTURE. What are the categories? What does each mean?"
  - Success metric: knowledge-base.md is reorganized/structured, not raw paste

- **What if participants finish Phase 1 exercise in 10 min instead of 15 min?**
  - Use extra time for advanced challenge: "Add examples for each metric type"
  - Or: Move to Phase 2 early, extend Phase 3

- **What if participant asks "can't we just use a template?" during exercise?**
  - Instructor response scripted in slides: "Templates work once. First principles work forever. Next week you'll face a task with no template - this skill lets you design one."

- **What if SESSION-2 participants don't remember SESSION-1 framework?**
  - Recap slide (5 min) at start of SESSION-2 to refresh 3-question framework
  - Quick poll: "Who remembers the 3 questions?" before diving into new domain

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: SESSION-1 MUST include 3-question framework slide explaining knowledge-base/specification/implementation-plan pattern
- **FR-002**: SESSION-1 Part 2 MUST provide hands-on exercises where participants build files from scratch (no pre-filled templates)
- **FR-003**: SESSION-1 MUST include live deconstruction exercise using non-priorities example (e.g., cloud migration proposal)
- **FR-004**: SESSION-1 MUST include raw materials (Accenture FY26 guide, metric list) for participants to extract structure from
- **FR-005**: SESSION-2 MUST apply same 3-file pattern to different domain (interview prep) to demonstrate transferability
- **FR-006**: SESSION-2 MUST include pattern recognition exercise comparing priorities vs interview prep structures
- **FR-007**: End of SESSION-2 MUST include 5-minute assessment challenge (RFP response design) to validate skill acquisition
- **FR-008**: All exercises MUST have validation checkpoints where instructor reviews participant work
- **FR-009**: Slide decks MUST include timing estimates for each section (totaling 90 min per session)
- **FR-010**: Materials MUST include instructor notes for facilitation (when to intervene, expected answers, common mistakes)
- **FR-011**: Presentations MUST include Mermaid diagrams for workflows, comparisons, and conceptual frameworks (3-question framework visual, attention curve, concept dependency graph) - diagrams may be comprehensive/detailed without node count limits to prioritize completeness
- **FR-012**: Presentations MUST use Marp for markdown-to-slide conversion with ALL three export formats required: HTML (live delivery), PDF (handouts), and PowerPoint (offline compatibility)
- **FR-013**: Repository MUST include Marp CLI build scripts (package.json or Makefile) enabling automated export of all three formats on demand
- **FR-014**: Title slides MUST use hero images with geometric white overlays and dual logos (Accenture + partner/project logo if applicable)
- **FR-015**: Content slides MUST follow observed layout: clean white background, left-aligned content, simple color-coded diagrams, footer with logo/copyright/slide number

### Non-Functional Requirements

- **NFR-001**: SESSION-1 and SESSION-2 MUST each complete within 90 minutes including exercises
- **NFR-002**: Exercises MUST be completable by mid-level developers without prior prompt engineering experience
- **NFR-003**: Slide content MUST use discovery-based language ("What do you think?" vs "Here's the answer")
- **NFR-004**: All examples MUST use real Accenture materials (FY26 guide, DrinkForge interview questions) for authenticity
- **NFR-005**: Presentations MUST follow Accenture minimalist corporate style: white backgrounds with purple accents (not full purple), Graphik font (or fallback: Inter/Open Sans), Accenture logo footer, geometric shape overlays on hero images, simple color-coded diagrams, clean footer layout (logo left, copyright center, slide # right)

### Key Entities *(include if feature involves data)*

- **3-Question Framework**: Core mental model for deconstructing tasks
  - Q1: What stays constant? → knowledge-base.md
  - Q2: What's unique to this instance? → specification.md
  - Q3: How do I execute systematically? → implementation-plan.md

- **Workshop Session**: 90-minute module with slides + exercises
  - SESSION-1: Build mental model using priorities domain
  - SESSION-2: Transfer skill to interview prep domain

- **Discovery Exercise**: Structured activity where participants build from scratch
  - Phases: Design knowledge-base (15min) → Design specification (10min) → Design implementation-plan (15min)
  - Validation: Instructor reviews 2-3 participant screens, compares approaches

- **Assessment Challenge**: 5-minute task to validate skill transfer
  - Task: Design 3-file system for RFP response
  - Success: Participant correctly maps components to knowledge-base/specification/plan

- **Raw Materials**: Source content for extraction exercises
  - Accenture FY26 Priorities Guide (for SESSION-1)
  - Interview questions PDF (for SESSION-2)
  - Participants extract structure, don't copy-paste

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: 80% of participants complete SESSION-1 exercises within allocated time (15min/10min/15min phases)
- **SC-002**: 90% of participants correctly identify knowledge-base/specification/plan components during live deconstruction exercise
- **SC-003**: 75% of participants pass end-of-SESSION-2 assessment (RFP response design in 5 min with correct 3-file mapping)
- **SC-004**: Zero pre-filled templates provided to participants during exercises (validated by instructor materials review)
- **SC-005**: Participants build at least 2 complete prompt file systems (priorities + interview prep) from scratch during workshop
- **SC-006**: SESSION-1 and SESSION-2 each complete within 90 minutes (validated by pilot run timing)
- **SC-007**: Instructor can facilitate exercises using only slide prompts and validation checkpoints (no external materials required)
- **SC-008**: Participants demonstrate faster completion time on SESSION-2 exercises vs SESSION-1 (showing skill transfer)

## Assumptions

- Workshop participants have mid-level software development or business analysis experience
- Participants have access to laptop/text editor during hands-on exercises
- Accenture FY26 Priorities Guide and interview questions PDF are available for distribution
- Participants attend both SESSION-1 and SESSION-2 (not drop-in)
- Instructors have experience with discovery-based teaching methods
- Workshop room supports screen sharing for validation checkpoints

## Dependencies

- **Source Materials**:
  - Accenture FY26 Priorities Guide (from Prez/FY26_Accenture_Priorities_Guide.txt)
  - Interview questions PDF (from Prez/interview questions (1).pdf)
  - Priority Builder Agent prompt (from Prez/Priority_Builder_Agent_Prompt.txt) as example

- **Existing Structure**:
  - Current SESSION-1/SESSION-2 presentations in bootcamp-materials/presentations/
  - Spec folder guide (bootcamp-materials/references/spec-folder-guide.md) as reference

- **Pedagogy Reference**:
  - Discovery learning principles (instructor must understand facilitation approach)

- **Brand Assets & Tooling**:
  - Accenture logo (SVG/PNG for footer placement)
  - Graphik font files (or fallback fonts: Inter, Open Sans)
  - Accenture purple color spec (observed as purple accent, not #A100FF)
  - Hero images (mountain/landscape corporate stock photos)
  - Geometric overlay templates (white angular shapes)
  - Brand asset access/approval from Accenture marketing/legal (if using official assets)
  - Marp CLI and Mermaid support for diagram rendering

## Out of Scope

- Pre-filled template files for participants to copy
- Video recordings of workshop sessions (slides only)
- Automated assessment tools (instructor manual validation)
- Creating SESSION-3 or additional domains beyond priorities/interview prep
- Integration with LLM tools during exercises (participants build files in text editor first)
- Providing solutions/answer keys (defeats discovery learning purpose)
- Support for self-paced learning (designed for instructor-led facilitation)
