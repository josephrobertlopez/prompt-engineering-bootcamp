# Feature Specification: Cleanup Stale Branch References

**Created**: 2025-11-12
**Status**: Active
**Type**: Technical Debt Removal

## REQUIRED

### Functional Requirements

- [ ] Remove all references to deleted `demo-day-1` branch
- [ ] Remove all references to deleted `demo-day-2` branch
- [ ] Update README.md to reference `main` branch only
- [ ] Update WORKSHOP-OVERVIEW.md to reference `main` branch only
- [ ] Update SESSION-2-advanced-patterns.md to remove stale branch text
- [ ] Update git instructions to reflect single-branch workflow

### Acceptance Criteria

- [ ] Zero mentions of "demo-day-1" in presentations folder
- [ ] Zero mentions of "demo-day-2" in presentations folder
- [ ] All GitHub URLs point to `main` branch
- [ ] Git instructions simplified (no branch switching)
- [ ] All hyperlinks resolve to valid paths

## RECOMMENDED

### User Story

**As a** workshop participant
**I want** correct repository URLs and instructions
**So that** I can clone and use demo materials without confusion

### Current State Analysis

**Dead Links (7 occurrences):**

| File | Lines | Issue |
|------|-------|-------|
| README.md | 11, 27, 71-72 | References deleted branches |
| SESSION-2-advanced-patterns.md | 400 | Mentions deleted branch |
| WORKSHOP-OVERVIEW.md | 34, 71, 240-241 | References deleted branches |

**Root Cause:** Branches `demo-day-1` and `demo-day-2` were merged to `main` and deleted, but documentation not updated comprehensively.

### Implementation Plan

**Phase 1: README.md Updates**
1. Line 11: `demo-day-1` → `main`
2. Line 27: `demo-day-2` → `main`
3. Lines 71-72: Remove branch checkout instructions, simplify to:
   ```
   git clone https://github.com/josephrobertlopez/spring-migration-demo
   cd demos/session-1-industry-standards/  # Day 1
   cd demos/session-2-advanced-patterns/   # Day 2
   ```

**Phase 2: WORKSHOP-OVERVIEW.md Updates**
1. Line 34: `demo-day-1` → `main`
2. Line 71: `demo-day-2` → `main`
3. Lines 240-241: Update to:
   ```
   demos/session-1-industry-standards/ - Session 1 materials (foundational patterns)
   demos/session-2-advanced-patterns/ - Session 2 materials (advanced orchestration)
   ```

**Phase 3: SESSION-2-advanced-patterns.md Updates**
1. Line 400: Remove "(demo-day-1, main branches)" → just reference main

**Phase 4: Validation**
1. Run `grep -r "demo-day" bootcamp-materials/presentations/` → expect zero results
2. Test all GitHub URLs resolve correctly
3. Verify git instructions work for new users

## OPTIONAL

### Edge Cases

**Case 1: User clones and tries `git checkout demo-day-1`**
- Error: "pathspec 'demo-day-1' did not match any file(s)"
- Mitigation: Clear documentation that all materials are in `main`

**Case 2: Old bookmarks to deleted branches**
- GitHub redirects gracefully
- Add deprecation notice in main README if needed

### Non-Functional Requirements

- **Clarity**: Instructions should be obvious for first-time users
- **Completeness**: No dead links or unresolved references
- **Consistency**: All docs use same terminology (main branch, not master)

## Design Decisions

### Decision 1: Single-Branch Strategy

**Chosen: All materials in `main` branch**

**Reasoning:** Merged both day-1 and day-2 branches to `main` for simplified participant experience. No branch switching required.

**Alternatives Considered:**

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| **A** | **Keep main only** | **Simple, no switching** | **N/A** |
| B | Keep separate branches | Isolated changes | Confusing for participants |
| C | Use tags instead | Versioned snapshots | Still requires checkout |

**Impact**: Reduces setup friction, eliminates branch confusion

---

### Decision 2: Documentation Update Strategy

**Chosen: Update all references atomically in single commit**

**Reasoning:** Comprehensive cleanup prevents partial state. Easier to review and roll back if needed.

**Alternatives Considered:**

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| **A** | **Atomic update** | **Complete, reviewable** | **N/A** |
| B | Incremental per file | Smaller commits | Temporary inconsistency |
| C | Deprecation warnings | Gradual transition | Confusing overlap period |

**Impact**: Clean state immediately, no lingering confusion

---

## Implementation Checklist

- [ ] Create this specification
- [ ] Update README.md (3 changes)
- [ ] Update WORKSHOP-OVERVIEW.md (4 changes)
- [ ] Update SESSION-2-advanced-patterns.md (1 change)
- [ ] Validate: `grep -r "demo-day" bootcamp-materials/presentations/` → zero results
- [ ] Test: Clone repo and follow updated instructions
- [ ] Commit with descriptive message
- [ ] Push to remote
