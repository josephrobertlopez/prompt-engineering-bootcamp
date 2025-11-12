# Spec-Driven Development Mode

**Never waste implementation time on misunderstood requirements. Read 3 docs first, build second.**

## Folder Structure

```
spec/
├── knowledge-base.md        # Domain context
├── specification.md         # Requirements
└── implementation-plan.md   # Technical approach
```

**First time?** See [spec-folder-setup.md](spec-folder-setup.md)

## Required Documents

**1. knowledge-base.md** - Domain knowledge, architectural decisions, constraints
**2. specification.md** - Requirements, acceptance criteria, API contracts
**3. implementation-plan.md** - Technical approach, phases, testing strategy

## Workflow

**Step 1: Document Discovery**

Search for the three required files. Report what you find:

```
Found: knowledge-base.md, specification.md
Missing: implementation-plan.md
```

**Step 2: Read and Extract**

From knowledge-base: Domain concepts, architectural decisions, constraints
From specification: Requirements, acceptance criteria, edge cases
From implementation-plan: Current phase, dependencies, testing approach

**Step 3: Synthesize and Clarify**

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

**Step 4: Get Approval**

Present plan before implementation. Wait for explicit approval.

**Step 5: Execute Phase-by-Phase**

Implement according to plan, validate between phases.

**Step 6: Update Documentation**

After implementation, update knowledge-base.md with decisions and lessons learned.

## Handling Missing Documents

**Missing knowledge-base.md**: Proceed, document decisions as you go
**Missing specification.md**: CRITICAL - Create it first based on user description
**Missing implementation-plan.md**: Offer to create using Planning Mode

## Integration with Other Modes

- **Planning Mode**: Creates implementation-plan.md
- **ABCD Mode**: Handles ambiguities in specs
- **Progressive Disclosure**: Each phase adds complexity incrementally

## Critical Rules

✅ Read all documentation before starting
✅ Create missing specification.md
✅ Verify understanding before implementation
✅ Update documentation after implementation
❌ Never implement without specification
❌ Never skip acceptance criteria verification

## Quick Start

```
Load spec-driven-mode.md

1. Search for spec/*.md files
2. Read found files
3. Ask me: "Ready to clarify requirements?"
4. After approval: Start Phase 1

Task: [Implement user authentication with OAuth2]
```
