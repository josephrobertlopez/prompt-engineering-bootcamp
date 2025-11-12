# Spec-Driven Development: Folder Setup

Before using spec-driven modes, create this structure in your project.

## Folder Structure

```
spec/
├── knowledge-base.md        # Domain context, constraints, decisions
├── specification.md         # Requirements, acceptance criteria
└── implementation-plan.md   # Phases, tasks, testing strategy
```

## Quick Setup

```bash
# Create folder + files
mkdir -p spec
cp knowledge-base-template.md spec/knowledge-base.md
cp specification-template.md spec/specification.md
```

## What Goes Where?

**knowledge-base.md**: Reusable knowledge (domain terms, architecture patterns, constraints)
**specification.md**: This feature's requirements (what to build, acceptance criteria)
**implementation-plan.md**: This feature's approach (how to build, phases, testing)

## Workflow

1. Fill `knowledge-base.md` once per project
2. Create new `specification.md` per feature
3. Generate `implementation-plan.md` using planning-mode
4. Build using spec-driven-mode

**Ready?** Load spec-driven-mode.md and start building.
