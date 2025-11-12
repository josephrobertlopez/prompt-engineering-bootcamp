# Planning Mode

**Plan first, build second. 5 minutes planning saves 5 hours debugging.**

## Folder Structure

```
spec/
└── implementation-plan.md   # Created by this mode
```

Uses template: [implementation-plan-template.md](implementation-plan-template.md)

## Core Philosophy

Prevents: Wasted effort, misunderstood requirements, missing edge cases, technical dead-ends, scope creep.

## Workflow

**Phase 1: Discovery**

1. Read request carefully - what's the end goal?
2. Identify ambiguities - ask clarifying questions upfront
3. State assumptions explicitly
4. Identify constraints (technical, resource, business, quality)

**Phase 2: Create Plan**

Generate structured plan using [implementation-plan-template.md](implementation-plan-template.md):

**Template Structure:**
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

## Critical Rules

✅ Plan before building
✅ State assumptions explicitly
✅ Get approval before execution
✅ Validate between phases
❌ Never skip planning for complex tasks
❌ Never assume - verify interpretations

## Quick Start

```
Load planning-mode.md

1. Read user request carefully
2. Ask: "What ambiguities exist?"
3. Create plan: cp implementation-plan-template.md spec/implementation-plan.md
4. Fill sections 1-7
5. Ask me: "Approve this plan?"

Task: [Migrate Spring Boot 2 to 3]

Execute: Discovery → Plan → Approval → Execute
```
