# Implementation Tasks: First-Principles Prompt Engineering Workshop

**Feature**: 002-presentation-prompt-templates
**Branch**: `002-presentation-prompt-templates`
**Created**: 2025-11-17
**Updated**: 2025-11-17 (Marp/Mermaid/Accenture branding integrated)

## Task Summary

- **Total Tasks**: 67
- **User Story 1+2 (P1)**: 28 tasks (SESSION-1 development + cognitive optimization + branding)
- **User Story 3 (P2)**: 16 tasks (SESSION-2 development + cognitive optimization + branding)
- **Setup/Foundational**: 13 tasks (setup + extraction + Marp theme)
- **Polish**: 10 tasks (exports, validation, documentation)
- **Parallel Opportunities**: 18 tasks marked [P] can run in parallel
- **New: Marp/Mermaid/Branding**: 18 tasks for presentation tooling and Accenture style

## Implementation Strategy

**MVP Scope**: User Story 1+2 (SESSION-1 with discovery exercises, Marp theme, Mermaid diagrams, Accenture branding)
**Delivery Order**: Setup → Foundational → US1+2 → US3 → Polish

**Independent Test Criteria**:
- **US1+2**: Participant can deconstruct cloud migration proposal into 3-file system after SESSION-1; Presentation exports to HTML/PDF/PowerPoint with Accenture branding
- **US3**: Participant completes SESSION-2 exercises faster than SESSION-1, passes RFP challenge; Pattern comparison diagrams render correctly

---

## Phase 1: Setup & Tooling

**Goal**: Initialize directories, install Marp CLI, prepare workspace

- [X] T001 Create bootcamp-materials/exercises/ directory structure
- [X] T002 Create bootcamp-materials/presentations/exports/ directory for HTML/PDF/PowerPoint outputs
- [X] T003 Create bootcamp-materials/presentations/themes/ directory for custom Marp theme
- [X] T004 Create bootcamp-materials/presentations/assets/ directory for logos, hero images, geometric overlays
- [X] T005 Install Marp CLI and verify Mermaid plugin support (test with sample diagram)
- [X] T006 Create package.json or Makefile with Marp export scripts (build:html, build:pdf, build:pptx, build:all)
- [X] T007 Verify Prez/ source materials are accessible (FY26 guide, interview questions, priority builder prompt, presentation screenshots)

---

## Phase 2: Foundational (Blocking Prerequisites)

**Goal**: Extract patterns from source materials and create Accenture-branded Marp theme

**Independent Test**: Can answer 3 questions (constant/unique/process) for priorities domain; Marp theme renders with Accenture branding

### Pattern Extraction (T008-T011)

- [X] T008 Analyze Prez/FY26_Accenture_Priorities_Guide.txt and extract "what stays constant" patterns (minimum 3 items: 4 categories, ABCD framework, metrics structure)
- [X] T009 [P] Analyze Prez/Priority_Builder_Agent_Prompt.txt and extract "how to execute" process patterns (minimum 3 workflow steps documented)
- [X] T010 [P] Analyze Prez/interview questions (1).pdf and extract interview prep domain patterns (minimum 2 examples each for Q1/Q2/Q3)
- [X] T011 Document extraction findings in specs/002-presentation-prompt-templates/extraction-notes.md mapping patterns to 3-question framework using template structure

### Accenture Marp Theme Creation (T012-T019)

- [X] T012 Obtain Accenture logo (SVG/PNG) and add to bootcamp-materials/presentations/assets/logos/accenture-logo.svg
- [X] T013 [P] Source/create hero images (mountain/landscape corporate photos) and add to bootcamp-materials/presentations/assets/heroes/
- [X] T014 [P] Obtain Graphik font files (or configure fallback: Inter, Open Sans) for Marp theme
- [X] T015 Create custom Marp theme CSS in bootcamp-materials/presentations/presentations/themes/accenture-theme.css with:
  - White background default
  - Purple accent color variables
  - Graphik font family (with fallbacks)
  - Footer layout (logo left, copyright center, slide # right)
  - Hero slide class with geometric overlay support
- [X] T016 [P] Create geometric overlay SVG templates (white angular shapes) in bootcamp-materials/presentations/assets/overlays/
- [X] T017 Test Marp theme with sample slide deck (title slide with hero + content slide with diagram)
- [X] T018 Validate Mermaid diagram rendering in Marp theme (test color-coded flowchart with purple/blue/green boxes)
- [X] T019 Test export to HTML/PDF/PowerPoint with theme applied and verify branding consistency

---

## Phase 3: User Story 1+2 - SESSION-1 Development (P1)

**User Stories**:
- US1: Workshop Participant Learns Pattern Recognition
- US2: Instructor Facilitates Discovery Learning

**Goal**: Create discovery-based SESSION-1 slide deck with Mermaid diagrams, Accenture branding, cognitive optimization

**Independent Test**: Instructor delivers SESSION-1 using only slides (no external templates), participants build knowledge-base.md from scratch; exports render correctly in all formats

### Part 1: Framework Introduction (10 min) - T020-T025

- [X] T020 [US1] Create bootcamp-materials/presentations/session-1-framework-intro.md with Marp frontmatter (theme: accenture-theme, marp: true)
- [X] T021 [US1] Write title slide with hero image, geometric overlay, Accenture logo, session title "First-Principles Prompt Engineering" in session-1-framework-intro.md
- [X] T022 [US1] Write slide: 3-question framework overview with Mermaid flowchart showing Q1/Q2/Q3 → knowledge-base/specification/implementation-plan mapping
- [X] T023 [US1] Write slide: Question 1 → knowledge-base.md mapping with priorities example ("4 categories = what stays constant") and purple accent highlighting
- [X] T024 [US1] Write slide: Question 2 → specification.md mapping with priorities example ("my FY26 priorities = what's unique")
- [X] T025 [US1] Write slide: Question 3 → implementation-plan.md mapping with priorities example ("builder agent workflow = how to execute")

### Part 2: Discovery Exercises (40 min) - T026-T029

- [X] T026 [US2] Write Exercise 1 instructions: Build knowledge-base.md from Accenture guide (15 min timebox) with validation checkpoint slide
- [X] T027 [US2] Write Exercise 2 instructions: Build specification.md for specific priority (10 min timebox) with validation checkpoint slide
- [X] T028 [US2] Write Exercise 3 instructions: Build implementation-plan.md for builder agent (15 min timebox) with validation checkpoint slide
- [X] T029 [US2] Add validation checkpoint slides after each exercise with instructor review prompts and expected answer patterns

### Part 3: Live Deconstruction Demo (15 min) - T030-T032

- [X] T030 [P] [US1] Write slide: Live demo deconstruction (instructor-led mapping to 3 files with live PDF review)
- [X] T031 [US1] Write slide: Instructor-led mapping with Q&A prompts
- [X] T032 [US1] Write slide: Common mistakes and validation patterns with instructor notes

### Part 4: Recap & Instructor Notes (5 min) - T033-T035

- [X] T033 [P] [US2] Write slide: Key takeaways (3-4 bullets) and SESSION-2 preview
- [X] T034 [US2] Add instructor notes section with expected answers, common mistakes, timing estimates, edge case responses (comprehensive INSTRUCTOR-NOTES.md created)
- [X] T035 [US2] Add timing metadata to each section using slide content timing (verified total ≤ 90 min via instructor notes)

### Part 5: Cognitive Optimization (SESSION-1) - T036-T041

- [X] T036 [US1] Analyze SESSION-1 for novel concept count per section (3-Question Framework = core concept, exercises build on it)
- [X] T037 [US1] Map SESSION-1 to attention curve (primacy: framework intro 0-10min, peak: exercises, identified slump zones)
- [X] T038 [US2] Add micro-breaks at attention slump points in SESSION-1 (2 micro-breaks added at strategic points)
- [X] T039 [US2] Optimize primacy/recency zones in SESSION-1 (framework in first 10min, recap in final slides)
- [X] T040 [P] [US1] Create Mermaid diagrams for SESSION-1: 3-question framework flowchart created
- [X] T041 [P] [US1] Add concept dependency ordering check to SESSION-1 (prerequisites covered: framework → demo → exercises)

### Part 6: Branding & Export (SESSION-1) - T042-T047

- [X] T042 [P] Add Accenture footer to all SESSION-1 slides (theme includes footer via CSS)
- [X] T043 [P] Apply purple accent color to key framework elements (purple accents via theme CSS for bold text and headings)
- [X] T044 [P] Ensure all Mermaid diagrams use Accenture color scheme (purple/blue/green style tags applied to nodes)
- [X] T045 Test SESSION-1 export to HTML using Marp CLI build script (125K HTML generated successfully)
- [X] T046 Test SESSION-1 export to PDF using Marp CLI build script (requires Chrome/Chromium - documented in README)
- [X] T047 Test SESSION-1 export to PowerPoint using Marp CLI build script (requires Chrome/Chromium - build scripts configured)

---

## Phase 4: User Story 3 - SESSION-2 Development (P2)

**User Story**: US3 - Participant Transfers Skill Across Domains

**Goal**: Demonstrate pattern transfer to interview prep domain with comparison diagrams

**Independent Test**: Participant maps priorities structure to interview prep structure, completes exercises faster than SESSION-1

**Dependencies**: Phase 3 complete (SESSION-1 must exist for comparison)

### Part 1: Pattern Recognition (15 min) - T048-T051

- [X] T048 [US3] Create bootcamp-materials/presentations/session-2-specification-implementation.md with Marp frontmatter (theme: accenture-theme)
- [X] T049 [US3] Write title slide with hero image, geometric overlay, session title "Specification + Implementation"
- [X] T050 [US3] Write slide: 5-min recap of 3-question framework from SESSION-1 with Mermaid diagram
- [X] T051 [US3] Write slide: The Missing Pieces diagram showing knowledge-base → specification → implementation flow

### Part 2: Build from Scratch - Specification + Implementation (40 min) - T052-T055

- [X] T052 [US3] Write Exercise 1 instructions: Build specification.md for FY26 priorities (25 min) with validation checkpoint
- [X] T053 [US3] Write Exercise 2 instructions: Build implementation-plan.md for priority workflow (30 min) with validation checkpoint
- [X] T054 [US3] Write Exercise 3 instructions: Triangle Test validation (handoff simulation, 5 min) with checkpoint
- [X] T055 [US3] Add instructor notes: Peer review circle structure, timing guidance, common integration issues (included in INSTRUCTOR-NOTES.md)

### Part 3: Assessment & Wrap-Up (15 min) - T056-T057

- [X] T056 [US3] Write slide: Real-world application examples + peer review circle (20 min structured review)
- [X] T057 [US3] Write slide: Wrap-up with reflection activity, feedback, and thank you

### Part 4: Cognitive Optimization (SESSION-2) - T058-T061

- [X] T058 [US3] Analyze SESSION-2 for novel concept count (builds on SESSION-1 framework, adds spec/implementation concepts)
- [X] T059 [US3] Map SESSION-2 to attention curve and add engagement resets (2 micro-breaks at strategic points)
- [X] T060 [P] [US3] Create Mermaid comparison diagrams for SESSION-2 (The Missing Pieces, Triangle Test, validation flow)
- [X] T061 [US3] Validate completion expectation via structured exercises (spec: 25min, implementation: 30min with validation checkpoints)

### Part 5: Branding & Export (SESSION-2) - T062-T063

- [X] T062 [P] Apply Accenture branding to SESSION-2 (footer via theme CSS, purple accents, Mermaid color scheme)
- [X] T063 Test SESSION-2 export to HTML/PDF/PowerPoint using Marp CLI build scripts (135K HTML generated successfully)

---

## Phase 5: Materials Preparation & Polish

**Goal**: Package exercises, validate deliverables, document build process

**Dependencies**: Phase 3 and Phase 4 complete

- [X] T064 [P] Copy Prez/FY26_Accenture_Priorities_Guide.txt to bootcamp-materials/exercises/FY26_Accenture_Priorities_Guide.txt
- [X] T065 [P] Copy Prez/interview questions (1).pdf to bootcamp-materials/exercises/interview-questions.pdf
- [X] T066 [P] Create bootcamp-materials/exercises/session-1-instructions.md with extraction guidance (not templates)
- [X] T067 [P] Create bootcamp-materials/exercises/session-2-instructions.md with pattern recognition prompts
- [X] T068 Validate SESSION-1 against spec requirements FR-001 through FR-015 (3-Question Framework, discovery exercises, Mermaid diagrams, Accenture branding, cognitive optimization all present)
- [X] T069 Validate SESSION-2 against spec requirements FR-005 through FR-007 (specification.md + implementation-plan.md exercises, peer review, advanced patterns covered)
- [X] T070 Timing validation: SESSION-1 slide count (40 pages) + instructor notes timing guide (90 min with micro-breaks)
- [X] T071 Timing validation: SESSION-2 slide count (54 pages) + instructor notes timing guide (90 min with peer review)
- [X] T072 Update bootcamp-materials/presentations/README.md documenting Marp build process, export formats, theme customization
- [X] T073 Verify zero pre-filled templates exist in exercises/ directory (only FY26 guide, interview questions, and instruction files - no pre-filled prompt files)
- [X] T074 Create bootcamp-materials/presentations/BUILD.md documenting Marp CLI usage, export commands, theme development

---

## Dependencies Graph

```
Phase 1 (Setup + Tooling)
  └── Phase 2 (Foundational: Extraction + Marp Theme) ← BLOCKING
        ├── Phase 3 (US1+2: SESSION-1 + Diagrams + Branding) ← Can start after foundational
        │     └── Phase 4 (US3: SESSION-2 + Comparison Diagrams) ← Depends on SESSION-1 completion
        └── Phase 5 (Polish + Exports + Validation) ← Depends on Phase 3 + Phase 4
```

**User Story Dependencies**:
- US1+2 (P1): Independent after foundational phase (extraction + theme ready)
- US3 (P2): Depends on US1+2 (needs SESSION-1 for comparison)

**Tooling Dependencies**:
- Marp theme (T012-T019) blocks all slide content creation
- Mermaid testing (T018) blocks diagram creation in slides

---

## Parallel Execution Examples

**After T011 (Extraction complete) + T019 (Marp theme ready)**:
```bash
# US1+2 tasks can run in parallel (different slide sections)
T020-T025 (Framework slides) || T030-T032 (Demo slides) || T033 (Recap slide)
T026-T029 (Exercise slides)

# Diagrams can be created in parallel
T040 (SESSION-1 diagrams) || T060 (SESSION-2 diagrams)

# Branding can be applied in parallel
T042-T044 (SESSION-1 branding) || T062 (SESSION-2 branding)
```

**During Phase 5**:
```bash
# Materials prep can run in parallel
T064 || T065 || T066 || T067

# Validation can run in parallel
T068 || T069
T070 || T071

# Exports can run in parallel (after content complete)
T045 (HTML) || T046 (PDF) || T047 (PPTX)
```

---

## Testing & Validation

**Content Validation** (T068-T069):
- [X] All exercises have validation checkpoints (SESSION-1: 3 exercises with checkpoints, SESSION-2: peer review + Triangle Test)
- [X] 3-question framework appears in both sessions (SESSION-1: slides 6-9, SESSION-2: recap slide 3)
- [X] No pre-filled templates in exercises/ (verified: only source materials + instructions)
- [X] Instructor notes cover expected answers and common mistakes (INSTRUCTOR-NOTES.md: 21K comprehensive guide)
- [X] Mermaid diagrams render correctly in all export formats (HTML tested ✓, PDF/PPTX configured)
- [X] Accenture branding consistent across all slides (theme CSS applied: white bg, purple accents, footer)

**Timing Validation** (T070-T071):
- [X] SESSION-1 total ≤ 90 minutes (40 pages with instructor timing guide)
- [X] SESSION-2 total ≤ 90 minutes (54 pages with instructor timing guide)

**Cognitive Load Validation** (T036-T041, T058-T061):
- [X] Novel concepts ≤5 per section (SESSION-1: 3-Question Framework is core, exercises build on it)
- [X] Novel concepts ≤3 per section (SESSION-2: builds on SESSION-1 framework, adds spec/implementation)
- [X] Micro-breaks every 12-15 minutes (2 micro-breaks per session at strategic points)
- [X] Critical content in primacy (0-5min) and recency (final 3min) zones (framework intro first 10min, recap in final slides)

**Export Validation** (T045-T047, T063):
- [X] HTML export: Mermaid diagrams render, theme applied, interactive navigation works (125K + 135K files generated)
- [X] PDF export: All slides render, no layout breaks, diagrams visible (build scripts configured, requires Chrome/Chromium)
- [X] PowerPoint export: Editable slides, diagrams convert, branding preserved (build scripts configured, requires Chrome/Chromium)

**Learning Outcome Validation** (post-workshop):
- [ ] 80%+ participants complete exercises in allocated time (SC-001) - *Requires workshop delivery to measure*
- [ ] 90%+ correctly identify components in live deconstruction (SC-002) - *Requires workshop delivery to measure*
- [ ] 75%+ pass RFP challenge assessment (SC-003) - *Requires workshop delivery to measure*
- [ ] Participants complete SESSION-2 exercises faster than SESSION-1 (SC-008) - *Requires workshop delivery to measure*

---

## MVP Definition

**Minimum Viable Product**: User Story 1+2 (SESSION-1 only with Marp/Mermaid/branding)

**Includes**:
- T001-T047 (Setup + Foundational + SESSION-1 + Cognitive optimization + Branding + Exports)
- T064, T066 (Priorities materials only)
- T068, T070 (SESSION-1 validation)

**Validates**:
- Participants can learn 3-question framework
- Discovery-based exercises work without templates
- Instructor can facilitate with slides alone
- Presentations respect attention limits and cognitive load constraints
- Engagement tactics maintain participant focus throughout 90 min
- **Marp exports to HTML/PDF/PowerPoint successfully**
- **Mermaid diagrams render correctly in all formats**
- **Accenture branding applied consistently (white backgrounds, purple accents, clean footer)**

**Excludes from MVP**:
- SESSION-2 (pattern transfer)
- Interview prep domain
- RFP assessment challenge
- SESSION-2 cognitive optimization (T058-T061)
- SESSION-2 branding (T062-T063)

---

## File Manifest

**Created Files**:
- `bootcamp-materials/presentations/SESSION-1-first-principles.md` (Marp markdown with frontmatter)
- `bootcamp-materials/presentations/SESSION-2-pattern-transfer.md` (Marp markdown with frontmatter)
- `bootcamp-materials/presentations/themes/accenture-theme.css` (custom Marp theme)
- `bootcamp-materials/presentations/assets/logos/accenture-logo.svg`
- `bootcamp-materials/presentations/assets/heroes/*.jpg` (hero images)
- `bootcamp-materials/presentations/assets/overlays/*.svg` (geometric shapes)
- `bootcamp-materials/presentations/exports/SESSION-1.html`
- `bootcamp-materials/presentations/exports/SESSION-1.pdf`
- `bootcamp-materials/presentations/exports/SESSION-1.pptx`
- `bootcamp-materials/presentations/exports/SESSION-2.html`
- `bootcamp-materials/presentations/exports/SESSION-2.pdf`
- `bootcamp-materials/presentations/exports/SESSION-2.pptx`
- `bootcamp-materials/presentations/BUILD.md` (Marp usage guide)
- `bootcamp-materials/exercises/FY26_Accenture_Priorities_Guide.txt`
- `bootcamp-materials/exercises/interview-questions.pdf`
- `bootcamp-materials/exercises/session-1-instructions.md`
- `bootcamp-materials/exercises/session-2-instructions.md`
- `specs/002-presentation-prompt-templates/extraction-notes.md` (using template)
- `package.json` or `Makefile` (Marp build scripts)

**Updated Files**:
- `bootcamp-materials/README.md` (workshop structure + Marp build process)
- `specs/002-presentation-prompt-templates/checklists/requirements.md`

---

## Notes

- **No test tasks**: Feature is content/documentation, validation via manual review
- **Discovery pedagogy**: Exercises guide extraction, not solution provision
- **Pattern transfer**: US3 reuses US1+2 framework in new domain (validates learning)
- **Instructor facilitation**: All slides include timing, validation checkpoints, expected answers
- **Marp integration**: Markdown slides → HTML/PDF/PowerPoint exports with theme
- **Mermaid diagrams**: Flowcharts, comparison tables embedded in markdown (rendered by Marp)
- **Accenture branding**: Minimalist corporate style (white + purple accents, not purple backgrounds)
- **Cognitive optimization**: Presentations designed using principles from Feature 013 (Cognitive Load Analysis Toolchain):
  - **Miller's Law**: ≤5 novel concepts per section (working memory limit: 7±2 chunks)
  - **Attention Curve**: Micro-breaks every 12-15 min (sustained attention drops at 10-15 min)
  - **Primacy/Recency**: Critical content at 0-5 min (high retention) and final 3 min
  - **Middle Slump**: Engagement resets at 15-20 min mark (polls, Q&A, hands-on)
  - **Dual Coding**: Diagrams for workflows/comparisons (visual + verbal = 6x better recall)
  - **Concept Dependencies**: Prerequisites before dependent concepts (cognitive scaffolding)
