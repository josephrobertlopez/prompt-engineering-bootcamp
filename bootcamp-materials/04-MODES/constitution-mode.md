# MODE 1: CONSTITUTION

## What It Is

**Constitution** = Project rules that apply EVERYWHERE

Think of it as your project's "law book" - rules that never change file-to-file.

## Purpose

Write rules ONCE, use them FOREVER across all similar files in your project.

## When to Use

- Start of any project with repeated patterns
- When you notice yourself doing the same thing in multiple files
- Before migrating/refactoring multiple similar files

## Structure

```markdown
# Constitution: [Project Name]

## Package/Import Rules
- [Specific transformation rule 1]
- [Specific transformation rule 2]

## Code Pattern Rules
- [Pattern rule 1]
- [Pattern rule 2]

## Quality Standards
Code must:
- [Standard 1]
- [Standard 2]

Code must NOT:
- [Anti-pattern 1]
- [Anti-pattern 2]
```

## Spring Migration Example

```markdown
# Constitution: Spring 2→3 Migration

## Package Rules
- javax.servlet.* → jakarta.servlet.*
- javax.validation.* → jakarta.validation.*
- javax.persistence.* → jakarta.persistence.*

## Annotation Rules
- @RequestMapping(method=GET) → @GetMapping
- @RequestMapping(method=POST) → @PostMapping
- Remove @Autowired on constructor injection

## Quality Standards
Code must:
- Compile with Spring Boot 3.2+
- Pass all existing tests
- Maintain API contracts

Code must NOT:
- Change business logic
- Break backward compatibility
```

## How to Write a Good Constitution

### ✅ DO:
- Be SPECIFIC: "javax.servlet → jakarta.servlet" not "update imports"
- Be OBSERVABLE: Rules you can see in code
- Be REUSABLE: Works for ALL files in project
- Keep it SHORT: 5-15 rules is usually enough

### ❌ DON'T:
- Be vague: "Make code better" is not a rule
- Be one-off: "Fix line 47 in UserController" is not constitutional
- Be too long: 50+ rules means you're too detailed

## Time Investment

- **First time writing**: 15-30 minutes
- **Every file after**: 0 minutes (just reference it)
- **ROI**: Huge - write once, use for dozens/hundreds of files

## How to Use with AI

```
1. Copy entire Constitution file
2. Paste into AI tool at start of conversation
3. AI responds: "I understand the [project] rules"
4. Proceed with file-specific work
```

AI will now apply these rules to EVERYTHING it generates.

## Relationship to Other Modes

- **Constitution** → Rules that apply everywhere
- **Specification** → What to do in THIS file (uses Constitution rules)
- **Planning** → HOW to apply rules in order
- **ABCD** → WHICH approach when Constitution allows multiple valid options
- **Implementation** → Generate using ALL context

## Quick Reference

**Use Constitution when**: Same patterns repeat across files
**Time to create**: 15-30 min first time
**Time to reuse**: 0 min (just load it)
**File location**: Project root or prompts/ folder
**Naming**: `file-0-constitution.md` or `constitution-[project].md`

## Success Indicators

You wrote a good Constitution if:
- ✅ Teammate can use it for different file without editing
- ✅ Rules are specific enough to verify in code
- ✅ New team member understands project standards from reading it
- ✅ You can use same Constitution for 10+ files

---

**See Also:**
- [Specification Mode](./specification-mode.md) - File-specific details
- [Planning Mode](./planning-mode.md) - Execution order
- Complete example: [06-SPRING-WORKFLOW/file-0-constitution.md](../06-SPRING-WORKFLOW/file-0-constitution.md)
