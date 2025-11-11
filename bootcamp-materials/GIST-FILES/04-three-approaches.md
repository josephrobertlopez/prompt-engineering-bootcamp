# Three Valid Approaches to Prompt Engineering

**Key Insight:** The patterns matter. The format doesn't.

You can apply Few-shot, Chain-of-Thought, ReAct, Tree of Thoughts through multiple formats. Choose based on team maturity and task complexity.

---

## Overview Comparison

| Approach | Maturity | Effort | Best For | Files |
|----------|----------|--------|----------|-------|
| **A: ADRs + Config** | 🟢 Tier 1 | Low | Most teams | docs/adr/, .github/copilot-instructions.md |
| **B: Structured Files** | 🟠 Tier 3 | Medium | Learning, complex tasks | 5-file workflow |
| **C: Tool-Assisted** | 🟡🟠 Tier 2-3 | Low | IDE-committed teams | Platform-specific |

**Recommendation for most teams:** Start with Option A (ADRs + Config)

---

## Option A: ADRs + Config Files ⭐

**Maturity:** 🟢 Tier 1 (10+ years proven)
**Used by:** Microsoft, AWS, Google, Spotify, Netflix

### What It Is
Lightweight decision docs + team configuration files

**Files:**
- `docs/adr/0001-spring-migration-standards.md` (decisions)
- `.github/copilot-instructions.md` or `.windsurfrules` (rules for AI)
- Simple prompts referencing above

### Example Structure

**File: docs/adr/0001-spring-migration-standards.md**
```markdown
# ADR 0001: Spring Boot 3 Migration Standards

## Status
Accepted

## Context
Migrating from Spring Boot 2.7 to 3.2 requires javax → jakarta namespace changes and annotation modernization.

## Decision
Use these transformation rules:
- javax.validation.* → jakarta.validation.*
- @RequestMapping(method=GET) → @GetMapping

Keep current exception handling (minimal changes strategy).

## Consequences
Positive: Low risk, fast migration
Negative: Not using all Spring 3 features (can enhance later)

## Alternatives Considered
- Option B: Adopt ProblemDetail (more changes, better structure)
- Option C: Full RFC 7807 (over-engineered for scope)
```

**File: .github/copilot-instructions.md**
```markdown
# GitHub Copilot Instructions - Spring Boot 3 Migration

## Project Context
Migrating from Spring Boot 2.7 to Spring Boot 3.2.

### Technology Stack
- Spring Boot 3.2+
- Java 17+
- Jakarta EE

## Migration Standards

### Package Transformations
javax.* → jakarta.*

### Annotation Modernization
@RequestMapping(method=X) → @XMapping

### Dependency Injection
Constructor injection (no @Autowired)

## References
- ADR: docs/adr/0001-spring-migration-standards.md
```

**Prompt:**
```
Following ADR 0001 and GitHub Copilot instructions, migrate UserController.java to Spring 3.
```

### Advantages
✅ **Simple:** Just markdown files
✅ **Proven:** 10+ years at scale
✅ **Widely understood:** Team onboarding easy
✅ **Low overhead:** Minimal files to maintain
✅ **Flexible:** Easy to adapt

### Disadvantages
⚠️ Less explicit about pattern application
⚠️ Requires discipline to keep updated
⚠️ Not as structured for complex orchestration

### When to Use
- ✅ Production teams
- ✅ Established workflows
- ✅ Simple to medium complexity tasks
- ✅ Want low maintenance overhead

### Getting Started
1. Create `docs/adr/` folder
2. Write first ADR documenting standards
3. Create `.cursorrules` with team conventions
4. Use AI with "follow ADR 000X"

---

## Option B: Structured Files 📚

**Maturity:** 🟠 Tier 3 (experimental)
**Use case:** Learning patterns, complex tasks, auditability needed

### What It Is
5-file workflow explicitly mapping to patterns

**Files:**
1. `file-1-system-prompt.md` - Persona + Few-shot (reusable rules)
2. `file-2-task-spec.md` - Template pattern (this task's goals)
3. `file-3-react-plan.md` - ReAct pattern (phased execution, optional)
4. `file-4-tree-decisions.md` - Tree of Thoughts (alternatives, optional)
5. `file-5-synthesize.md` - Meta-prompting (orchestration)

### Example Structure

**File: file-1-system-prompt.md**
```markdown
# System Prompt: Spring Boot 3 Migration Specialist

## Role (Persona Pattern)
You are an expert Spring Boot migration specialist.

## Transformation Rules (Few-shot Pattern)
Example: javax.validation.Valid → jakarta.validation.Valid
Example: @RequestMapping(method=GET) → @GetMapping

## Quality Standards
- Must compile with Spring 3.2
- All tests pass
- APIs unchanged
```

**File: file-2-task-spec.md**
```markdown
# Task Specification: UserController Migration

## Current State
- File: UserController.java
- Uses javax imports, verbose annotations

## Success Criteria (Template Pattern)
- [ ] jakarta imports only
- [ ] Specific HTTP method annotations
- [ ] All 7 endpoints preserved
- [ ] Tests pass
```

**File: file-3-react-plan.md** (optional for complex tasks)
```markdown
# ReAct Plan: Migration Phases

## Phase 1: Imports
THINK: Dependencies first
ACT: Replace javax with jakarta
OBSERVE: mvn compile succeeds

## Phase 2: Annotations
THINK: Build on updated imports
ACT: Modernize @RequestMapping
OBSERVE: No deprecated warnings
```

**File: file-4-tree-decisions.md** (optional when decisions exist)
```markdown
# Tree of Thoughts: Exception Handling

BRANCH A: Keep current (✓ recommended)
BRANCH B: Adopt ProblemDetail
BRANCH C: Full RFC 7807

Decision: Branch A (minimal changes strategy)
```

**File: file-5-synthesize.md**
```markdown
# Code Generation: Pattern Orchestration

Context from file-1: ✓ Rules loaded
Context from file-2: ✓ Goals defined
Context from file-3: ✓ Phases planned
Context from file-4: ✓ Decisions made

Generate migrated code following all above.
```

**Usage:**
Load files 1→2→3→4→5 into AI tool, generate code

### Advantages
✅ **Explicit:** Clear pattern application
✅ **Learning:** Great for understanding patterns
✅ **Auditability:** Full reasoning trail
✅ **Complex tasks:** Handles dependencies well

### Disadvantages
⚠️ **Overhead:** More files to maintain
⚠️ **Experimental:** Not industry standard (Tier 3)
⚠️ **Overkill:** For simple tasks, ADRs simpler

### When to Use
- ✅ Learning prompt engineering patterns
- ✅ Complex multi-phase tasks
- ✅ Need audit trail of reasoning
- ✅ Teaching others the approach

### Getting Started
1. Copy template files
2. Fill in project-specific context
3. Load into AI tool in order (1→5)
4. Generate and validate

---

## Option C: Tool-Assisted 🔧

**Maturity:** 🟡🟠 Tier 2-3 (varies by tool)
**Use case:** Team committed to specific IDE/platform

### What It Is
Built-in workflow tools in IDEs/platforms

**Tools:**
- **GitHub Spec-Kit** (🟠 Tier 3 - Sept 2024, ~14 months old)
- **GitHub Copilot Workspace** (🟡 Tier 2 - official GitHub)
- **Cursor Composer** (🟡 Tier 2 - growing adoption)

### Example: Spec-Kit

**Workflow:**
```
1. constitution.md → Project-wide rules
2. spec.md → Feature specification
3. plan.md → Implementation plan
4. tasks.md → Task breakdown
5. Execute → CLI implements
```

**Command:**
```bash
spec-kit constitution --create
spec-kit specify --feature "spring-migration"
spec-kit plan
spec-kit implement
```

### Example: Copilot Workspace

**Workflow:**
```
1. Create task list in workspace
2. Copilot generates plan
3. Review and refine
4. Generate code
5. Commit directly from workspace
```

### Example: Cursor Composer

**Workflow:**
```
1. Add files to context (Cmd+Shift+I)
2. Write prompt in composer
3. AI generates across multiple files
4. Review diffs, accept/reject
```

### Advantages
✅ **Built-in:** No external files
✅ **Guided:** Tool provides structure
✅ **Real-time:** Immediate feedback

### Disadvantages
⚠️ **Tool lock-in:** Platform-specific
⚠️ **Varying maturity:** Spec-Kit experimental, others newer
⚠️ **Learning curve:** Each tool different

### When to Use
- ✅ Team committed to specific IDE
- ✅ Want built-in guardrails
- ✅ Okay with tool dependency

### Getting Started
1. Install tool (Spec-Kit, Cursor, etc.)
2. Follow tool's onboarding
3. Start with simple task
4. Evaluate fit for team

---

## Decision Matrix

### Choose ADRs + Config when:
- ✅ Want proven approach (Tier 1)
- ✅ Need low maintenance
- ✅ Simple to medium tasks
- ✅ Team uses multiple tools

### Choose Structured Files when:
- ✅ Learning prompt patterns
- ✅ Complex task with many concerns
- ✅ Need audit trail
- ✅ Teaching approach to others

### Choose Tool-Assisted when:
- ✅ Team committed to specific IDE
- ✅ Want built-in workflow
- ✅ Okay with platform dependency
- ✅ Tool maturity acceptable (check tier)

---

## Hybrid Approaches

**You can mix approaches!**

### Hybrid 1: ADRs + Structured Files
- Use ADRs for decisions (Tier 1 proven)
- Use structured files for complex execution only
- Best of both: proven decisions, detailed execution when needed

### Hybrid 2: Config + Tool
- Use .cursorrules for team standards (Tier 2)
- Use Copilot Workspace for generation (Tier 2)
- Consistent standards across IDE workflow

### Hybrid 3: All Three
- ADRs for decisions
- Config files for rules
- Structured files for complex tasks
- Tool for daily development
- Ultimate flexibility, higher complexity

---

## Real-World Examples

### Startup (3-5 engineers)
**Approach:** ADRs + Cursor Composer
**Why:** Fast moving, small team, okay with tool dependency
**Files:** Lightweight ADRs, .cursorrules

### Enterprise (50+ engineers)
**Approach:** ADRs + Config Files
**Why:** Multiple tools, need proven approach, low maintenance
**Files:** Mature ADR process, .github/copilot-instructions.md

### Learning Team (10 engineers, upskilling)
**Approach:** Structured Files
**Why:** Teaching patterns explicitly, build understanding
**Files:** Complete 5-file workflow with templates

---

## Migration Path

### Phase 1: Start with ADRs
Everyone begins with lightweight ADRs + config files.

### Phase 2: Add Structure for Complex Tasks
When task demands it, use structured files.

### Phase 3: Tool Integration
Once patterns mastered, integrate IDE tools if helpful.

### Never: Force one approach
Different tasks, different approaches. Flexibility is key.

---

## 📊 Effort Comparison

### Simple Task (migrate 1 controller)
| Approach | Time | Files Created |
|----------|------|---------------|
| ADRs + Config | 5 min | 0 (reuse existing ADR) |
| Structured Files | 20 min | 5 files |
| Tool-Assisted | 5 min | 0 (tool manages) |

**Winner:** ADRs or Tool (tie)

### Complex Task (migrate 10 controllers with decisions)
| Approach | Time | Files Created |
|----------|------|---------------|
| ADRs + Config | 30 min | 1-2 ADRs + prompts |
| Structured Files | 45 min | 5 files per controller type |
| Tool-Assisted | 40 min | Tool-managed |

**Winner:** ADRs (proven + efficient)

### Learning Exercise (understand patterns)
| Approach | Time | Files Created |
|----------|------|---------------|
| ADRs + Config | 1 hr | Implicit patterns |
| Structured Files | 2 hr | Explicit patterns |
| Tool-Assisted | 1.5 hr | Tool abstracts patterns |

**Winner:** Structured Files (explicit learning)

---

## ✅ Quick Decision Flowchart

```
Is this a simple task?
  Yes → Use ADRs + prompt
  No → Continue

Are you learning patterns?
  Yes → Use Structured Files
  No → Continue

Is team committed to one IDE?
  Yes → Use Tool-Assisted
  No → Use ADRs + Config
```

---

**Key Takeaway:** All three approaches are valid. ADRs + Config is simplest and proven (recommended starting point). Structured Files great for learning. Tool-Assisted good if team committed. Choose based on context, not dogma.
