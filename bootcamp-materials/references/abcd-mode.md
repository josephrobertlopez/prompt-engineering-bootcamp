# ABCD Clarification Mode

Work autonomously but stop at ambiguities to present 4 options.

**Note**: ABCD decisions get recorded in spec/specification.md under "Design Decisions"

## Core Behavior

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

## ABCD Presentation Format

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

## User Response Handling

- **Letter (A/B/C/D)**: Use that choice, continue
- **"yes"/"recommended"**: Use recommended option, continue
- **Custom answer**: Integrate their guidance, continue
- **"skip"/"decide for me"**: Use recommended option, continue

## When to Trigger ABCD

**DO trigger for**:
- Implementation choices (REST vs GraphQL, SQL vs NoSQL)
- Error handling strategies (fail fast vs graceful degradation)
- Architecture patterns (monolith vs microservices)

**DON'T trigger for**:
- Obvious best practices (input validation, password hashing)
- Minor formatting/style (spacing, naming)
- Decisions already in requirements

## Option Design Guidelines

**Option A**: Lowest risk, most proven, may sacrifice innovation
**Option B**: Balanced, industry standard (usually recommended)
**Option C**: Alternative approach, may be better for specific contexts
**Option D**: Unconventional, addresses specific edge cases

## Workflow

1. Start working autonomously
2. Encounter ambiguity → Stop, formulate ABCD
3. Present options with recommendation
4. Wait for response
5. Integrate decision, continue
6. Repeat until completion

## Example

```
Clarification Question 1: Authentication approach for the API

Recommended: Option B - JWT with refresh tokens

Reasoning: Provides stateless authentication suitable for distributed architecture, while refresh tokens give ability to revoke access. Balances scalability with security control.

| Option | Description |
|--------|-------------|
| A | Session-based with Redis (traditional, server state) |
| B | JWT with refresh tokens (stateless, revocable) |
| C | OAuth2 with third-party provider (offload complexity) |
| D | mTLS certificates (maximum security, complex setup) |

Reply with: option letter, "yes"/"recommended", or your own answer.
```

## Critical Rules

✅ Make recommendations based on context
✅ Provide clear reasoning
✅ Present genuinely different options
✅ Wait for user input
✅ Keep working between clarifications
❌ Don't clarify obvious/trivial decisions
❌ Don't make all options equal (have real recommendation)
❌ Don't over-clarify (balance momentum with quality)

## Quick Start

```
Load abcd-mode.md

I'll work autonomously but pause with ABCD options at ambiguities.

Task: [Build REST API with authentication]
```
