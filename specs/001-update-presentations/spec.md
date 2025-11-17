# Feature Specification: Presentation Materials Update

**Feature Branch**: `001-update-presentations`
**Created**: 2025-11-16
**Status**: Draft
**Input**: User description: "Update presentation materials to include custom speckit workflow examples and real-world case studies from Features 001-012 (Hellcube proxy generator with MCTS+VLM). Replace GitHub Spec-Kit references with our proven /speckit.* commands workflow."

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Clarify Speckit Terminology (Priority: P1)

As a workshop instructor, I want the presentations to clearly distinguish between GitHub's Spec-Kit tool and our custom /speckit.* command workflow, so that participants understand they're learning our proven methodology, not an external experimental tool.

**Why this priority**: This is the most critical update because current presentations confuse two different tools (GitHub Spec-Kit vs our custom speckit commands), which undermines credibility and creates learning confusion. Fixing this unblocks all other improvements.

**Independent Test**: Can be fully tested by reviewing updated SESSION-1 and SESSION-2 presentations and verifying zero mentions of "GitHub Spec-Kit" in contexts describing our workflow, and all references to `/speckit.*` commands are accurate.

**Acceptance Scenarios**:

1. **Given** a presentation referencing "Spec-Kit", **When** reviewing the content, **Then** it clearly indicates whether it's GitHub's tool or our custom commands
2. **Given** SESSION-1 Tier 3 section, **When** reading the experimental tools section, **Then** GitHub Spec-Kit is listed separately from our "/speckit.* commands" with clear distinctions
3. **Given** any workflow diagram or code example, **When** showing command usage, **Then** it uses `/speckit.specify`, `/speckit.plan`, etc. format, not "spec-kit" CLI references

---

### User Story 2 - Add Real-World Case Study (Priority: P2)

As a workshop participant, I want to see a complete real-world example (Feature 012: Hellcube Proxy Generator) showing the speckit workflow end-to-end, so I can understand how it works on complex projects with actual constraints.

**Why this priority**: Current examples use only Spring Boot migration (simple refactoring). Adding Feature 012 (MCTS+VLM integration, monorepo patterns, 52 tasks, VLM image passing) shows the workflow scales to research-grade complexity and validates the methodology.

**Independent Test**: Can be tested by reviewing new SESSION-3 or sidebar examples in existing sessions, verifying Feature 012 appears with links to actual spec.md, plan.md, tasks.md, and contracts/ outputs from the magic-cards-edh-deck repo.

**Acceptance Scenarios**:

1. **Given** a participant wants a complex example, **When** they review the presentations, **Then** they find Feature 012 case study showing spec→plan→tasks→contracts progression
2. **Given** SESSION-2 advanced patterns section, **When** explaining ReAct or Tree of Thoughts, **Then** Feature 012 MCTS algorithm selection appears as a real decision-making example
3. **Given** a workshop instructor showing evidence of methodology success, **When** presenting, **Then** they can point to 12 completed features documented in the presentations

---

### User Story 3 - Update Tier Framework (Priority: P3)

As a workshop designer, I want the Tier framework updated to reflect our proven speckit workflow (12 features completed) as "Tier 2: Emerging Standard" instead of lumped with experimental tools, so participants understand it's battle-tested, not speculative.

**Why this priority**: Currently positions our workflow as "Tier 3: Experimental" alongside untested tools. After 12 features (including research-grade MCTS+VLM), it deserves "Tier 2: Proven in Production" status. This is lower priority than fixing terminology confusion (P1) or adding examples (P2) but important for credibility.

**Independent Test**: Can be tested by reviewing Tier framework slides in SESSION-1 and verifying our speckit workflow appears in Tier 2 with evidence (12 features, links to repos).

**Acceptance Scenarios**:

1. **Given** SESSION-1 Slide 2b, **When** reviewing tier classifications, **Then** our speckit workflow is listed under "Tier 2: Emerging Standards (1-3 years, proven in production)"
2. **Given** Tier framework documentation, **When** reading our workflow description, **Then** it includes evidence: "12 features completed including research-grade MCTS+VLM integration"
3. **Given** a comparison table between tiers, **When** reviewing adoption status, **Then** our workflow shows "Internal: Heavy use across magic-cards-edh-deck, agentic-code, docs repos"

---

### Edge Cases

- **What happens when referencing both GitHub Spec-Kit and our workflow in same slide?**
  - Use clear labeling: "GitHub Spec-Kit (external tool, Sept 2024)" vs "Our /speckit.* Commands (internal workflow, 12 features)"
  - Add visual distinction (icons, color coding)

- **How do we handle outdated date references ("Nov 2025 Status" written in Nov 2024)?**
  - Update to "As of [Month Year]" format with actual current date
  - Remove calculated age references ("~14 months old") - these become stale immediately

- **What if Feature 012 details are too complex for workshop audience?**
  - Create simplified sidebar summary: "Real Example: Hellcube Proxy Generator - Used speckit to plan 52-task implementation with VLM+MCTS integration"
  - Link to full spec.md for interested participants
  - Use screenshots of actual spec/plan/tasks outputs, not full technical details

- **How do we maintain presentation consistency across SESSION-1, SESSION-2, and references/?**
  - Create shared snippets file (e.g., `shared-definitions.md`) for reused content (tier definitions, workflow diagrams)
  - Update all references atomically when making terminology changes
  - Add consistency checklist to validation

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: Presentations MUST distinguish "GitHub Spec-Kit" (external tool) from "/speckit.* commands" (our custom workflow) in all references
- **FR-002**: SESSION-1 Tier framework MUST update our workflow from "Tier 3: Experimental" to "Tier 2: Emerging Standard (proven in production)"
- **FR-003**: Presentations MUST include at least one complete real-world case study showing speckit workflow (spec.md → plan.md → tasks.md → contracts/)
- **FR-004**: All command examples MUST use correct `/speckit.*` format: `/speckit.specify`, `/speckit.plan`, `/speckit.clarify`, `/speckit.tasks`, `/speckit.analyze`, `/speckit.implement`, `/speckit.constitution`
- **FR-005**: Presentations MUST remove or update stale date references ("Nov 2025 Status" written in 2024, "~14 months old" calculated ages)
- **FR-006**: Feature 012 (Hellcube Proxy Generator) MUST be documented as primary case study with links to actual outputs in magic-cards-edh-deck repo
- **FR-007**: Updated content MUST reference evidence of workflow success: "12 features completed across 3 repos (magic-cards-edh-deck, agentic-code, docs)"
- **FR-008**: SESSION-2 advanced patterns MUST use Feature 012 decision-making (MCTS algorithm selection, VLM evaluation strategy) as ReAct/Tree of Thoughts examples
- **FR-009**: All three presentation files (SESSION-1, SESSION-2, WORKSHOP-OVERVIEW) MUST have consistent terminology and tier classifications
- **FR-010**: Updated presentations MUST maintain existing learning objectives and hands-on exercises (only augment, don't replace Spring Boot examples)

### Non-Functional Requirements

- **NFR-001**: Updated presentations MUST not exceed 120 minutes total (SESSION-1: 90min, SESSION-2: 90min remains unchanged)
- **NFR-002**: New case study content MUST be understandable to mid-level developers without ML/research background
- **NFR-003**: All links to spec.md, plan.md, tasks.md files MUST use correct GitHub URLs pointing to actual repos
- **NFR-004**: Updated tier framework evidence MUST be factually accurate and verifiable (links to actual feature branches)

### Key Entities *(include if feature involves data)*

- **Presentation Session**: A 90-minute workshop module with slides, demos, and exercises
  - Attributes: title, duration, learning objectives, demo repo, prerequisite knowledge
  - Current sessions: SESSION-1 (industry standards), SESSION-2 (advanced patterns)

- **Tier Classification**: Category for prompt engineering tools/workflows by maturity
  - Tiers: Tier 1 (10+ years, production-ready), Tier 2 (1-3 years, emerging standard), Tier 3 (months to 1-2 years, experimental)
  - Current issue: Our workflow incorrectly placed in Tier 3

- **Case Study**: Real-world example demonstrating workflow application
  - Attributes: feature name, repo, complexity indicators, outputs (spec/plan/tasks/contracts)
  - Current: Only Spring Boot migration (simple)
  - Adding: Feature 012 Hellcube (complex, research-grade)

- **Speckit Command**: Custom slash command in our workflow
  - Commands: /speckit.specify, /speckit.plan, /speckit.clarify, /speckit.tasks, /speckit.analyze, /speckit.implement, /speckit.constitution
  - Currently confused with GitHub Spec-Kit external tool

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Zero references to "GitHub Spec-Kit" when describing our custom /speckit.* workflow (100% terminology accuracy)
- **SC-002**: Feature 012 case study appears in at least 3 distinct presentation sections (tier evidence, advanced patterns examples, case study sidebar)
- **SC-003**: Our workflow classification updated from "Tier 3: Experimental" to "Tier 2: Emerging Standard" with supporting evidence (12 features documented)
- **SC-004**: All 7 speckit commands correctly formatted with `/` prefix in every code example and workflow diagram
- **SC-005**: Workshop instructors can demonstrate methodology credibility by showing links to 12 completed feature specs in presentations
- **SC-006**: Updated presentations maintain 90-minute duration per session (verified by slide count and demo timing)
- **SC-007**: All GitHub repo links are valid and point to correct spec.md, plan.md, tasks.md files (100% link validation)
- **SC-008**: Participants can distinguish our workflow from GitHub Spec-Kit after reading updated SESSION-1 Tier section (validated through comprehension questions)

## Assumptions

- The magic-cards-edh-deck, agentic-code, and docs repositories are publicly accessible (or links can be shared with workshop participants)
- Feature 012 (Hellcube Proxy Generator) spec.md, plan.md, tasks.md, and contracts/ files are complete and representative of quality output
- Workshop audience has mid-level software development experience (can understand complex examples with guidance)
- Current Spring Boot migration examples remain valuable and should be kept (augment, don't replace)
- Presentation format remains markdown-based slide decks (not PowerPoint or other formats)
- Our /speckit.* commands are stable and won't undergo major renaming before workshops are delivered

## Dependencies

- **Source Material**: Access to magic-cards-edh-deck repo Feature 012 outputs (spec.md, plan.md, tasks.md, contracts/mcts_layout.md, contracts/vlm_evaluators.md)
- **Existing Presentations**: SESSION-1-industry-standards.md, SESSION-2-advanced-patterns.md, WORKSHOP-OVERVIEW.md in docs/bootcamp-materials/presentations/
- **Reference Materials**: Tier framework, foundational patterns, advanced patterns docs in docs/bootcamp-materials/references/
- **Tier Framework Source**: Current tier definitions need updating to reflect our workflow's proven status

## Out of Scope

- Creating new Session 3 (only updating existing SESSION-1 and SESSION-2)
- Removing Spring Boot migration examples (they remain primary hands-on exercises)
- Redesigning tier framework categories (only updating our workflow's placement within existing tiers)
- Creating video recordings or other media (markdown presentations only)
- Translating presentations to other languages
- Creating interactive workshop tools or assessment quizzes
- Detailed technical deep-dive into MCTS algorithm implementation (case study remains high-level for accessibility)
