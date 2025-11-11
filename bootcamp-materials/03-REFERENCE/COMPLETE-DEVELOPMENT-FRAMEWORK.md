# THE COMPLETE DEVELOPMENT FRAMEWORK
## 3 Patterns That Transform How You Build Software with AI

**Version:** 1.0  
**Last Updated:** 2025-11-11  
**Audience:** Software Developers at All Levels  
**Purpose:** Master document integrating 5 Prompt Modes + CLI-First Architecture + Spec-Driven Artifacts

---

## 🎯 THE BIG PICTURE

You're about to learn **three interconnected patterns** that fundamentally change how you build software with AI:

### **Pattern 1: The 5 Prompt Modes** (HOW TO PROMPT)
Structure your AI collaboration systematically
- Constitution → Specification → Planning → ABCD → Implementation

### **Pattern 2: CLI-First Architecture** (HOW TO BUILD)
Build composable, testable, reusable tools
- Individual CLIs → Bash composition → Python enhancement

### **Pattern 3: Spec-Driven Artifacts** (WHAT TO BUILD + WHY)
Document requirements, decisions, and knowledge
- mainspec.md → implementation_plan.md → knowledge_bank.md → research.md → notes.md

---

## 🔗 HOW THE 3 PATTERNS CONNECT

```
┌─────────────────────────────────────────┐
│  Spec-Driven Artifacts                  │
│  (WHAT + WHY + DOCUMENTATION)           │
│                                         │
│  • mainspec.md - Requirements           │
│  • implementation_plan.md - Phases      │
│  • knowledge_bank.md - Decisions        │
└───────────────┬─────────────────────────┘
                ↓
┌─────────────────────────────────────────┐
│  5 Prompt Modes                         │
│  (HOW TO PROMPT AI)                     │
│                                         │
│  • Constitution - Rules                 │
│  • Specification - What to build        │
│  • Planning - How to build it           │
│  • ABCD - Decision points               │
│  • Implementation - Generate code       │
└───────────────┬─────────────────────────┘
                ↓
┌─────────────────────────────────────────┐
│  CLI-First Architecture                 │
│  (HOW TO STRUCTURE SOFTWARE)            │
│                                         │
│  • Individual CLIs - Focused tools      │
│  • Bash composition - Simple orchestr.  │
│  • Python wrapper - When needed         │
└───────────────┬─────────────────────────┘
                ↓
        Working Software
     (Documented, Testable, Maintainable)
```

---

## 📚 PATTERN 1: THE 5 PROMPT MODES

### **What It Is**
A systematic framework for structuring AI prompts to get consistent, high-quality output.

### **The 5 Modes Explained**

#### **Mode 1: Constitution** 🎼
**Purpose:** Define project rules that apply everywhere  
**Write once, use forever**

**Example - Spring Migration:**
```markdown
# Constitution: Spring 2→3 Migration

## Rules:
- javax.* → jakarta.*
- @RequestMapping → @GetMapping/@PostMapping
- WebSecurityConfigurerAdapter → SecurityFilterChain
- Constructor injection (no @Autowired)

## Constraints:
- Maintain API contracts
- Preserve business logic
- Java 17+ required
```

**When to write:** Start of project  
**Reusability:** All files in project  
**Think of it as:** Project DNA

---

#### **Mode 2: Specification** 🎯
**Purpose:** Describe WHAT to build in THIS file  
**Write once per file type**

**Example - Spring Controller:**
```markdown
# Specification: Migrate UserController

## Current State (Spring 2.7):
- javax.servlet imports
- @RequestMapping for all endpoints
- Old exception handling

## Target State (Spring 3.2):
- jakarta.servlet imports
- @GetMapping, @PostMapping specific annotations
- ProblemDetail error responses

## Success Criteria:
✓ Compiles with Spring 3.2
✓ All tests pass
✓ API endpoints unchanged
```

**When to write:** Once per file (5 min)  
**Reusability:** Template reusable  
**Think of it as:** The Blueprint

---

#### **Mode 3: Planning** 📋
**Purpose:** Define HOW to execute step-by-step  
**Write once per pattern**

**Example - Migration Plan:**
```markdown
# Migration Plan: UserController

## Phase 1: Package Updates (5 min)
- Task 1.1: javax.servlet → jakarta.servlet
- Task 1.2: javax.validation → jakarta.validation
- Validation: Code compiles

## Phase 2: Annotation Updates (10 min)
- Task 2.1: @RequestMapping → @GetMapping
- Task 2.2: Update parameter annotations
- Validation: Annotations correct

## Phase 3: Security Updates (15 min)
- Task 3.1: SecurityFilterChain pattern
- Validation: Tests pass

## Phase 4: Testing (5 min)
- Task 4.1: Run unit tests
- Task 4.2: Compare with target branch
```

**When to write:** Once per pattern  
**Reusability:** Same for similar files  
**Think of it as:** The Recipe

---

#### **Mode 4: ABCD Clarification** 🤔
**Purpose:** Handle decision points systematically  
**Write when ambiguity exists**

**Example - Security Decision:**
```markdown
---
Clarification Question 1: Security configuration approach

Recommended: Option B - Custom SecurityFilterChain

Reasoning: Your code has custom auth logic. Option B 
preserves that while modernizing to Spring 3 patterns.

| Option | Description |
|--------|-------------|
| A | Default SecurityFilterChain (simple, loses custom) |
| B | Custom SecurityFilterChain (balanced, recommended) |
| C | Keep deprecated pattern (works, not future-proof) |
| D | Multiple security chains (complex, overkill) |

Reply with: B, "recommended", or your choice
---
```

**When to write:** At decision points  
**Reusability:** Documents choices  
**Think of it as:** Decision Checkpoints

---

#### **Mode 5: Implementation** ⚙️
**Purpose:** Combine all context and generate code  
**Write every time, but fast**

**Example - Code Generation:**
```markdown
# Implementation: Generate Migrated UserController

## Context Loaded:
✓ Constitution: Migration rules from Mode 1
✓ Specification: UserController target from Mode 2
✓ Plan: Step-by-step from Mode 3
✓ Decisions: SecurityFilterChain Option B from Mode 4

## Input (Spring 2.7 code):
[Paste original UserController]

## Instructions:
Generate Spring 3.2 compatible code.
Apply all rules, follow plan, use chosen approaches.

## Output:
[AI generates clean Spring 3.2 code]
```

**When to write:** Every file (2 min)  
**Reusability:** Template constant  
**Think of it as:** The Performance

---

### **Why 5 Modes Beat "Wing It" Prompting**

| Aspect | Wing It | 5 Modes |
|--------|---------|---------|
| Consistency | Random | Systematic |
| Reusability | One-off | Templates |
| Quality | Variable | Controlled |
| Time (1st file) | 45 min guessing | 30 min setup |
| Time (2nd+ files) | 45 min each | 5 min each |
| Debugging | Hard (no structure) | Easy (isolated modes) |
| Team sharing | Can't share prompts | Share workflow |

**The magic:** First file takes 30 min. Every file after takes 5 min.

---

## 🏗️ PATTERN 2: CLI-FIRST ARCHITECTURE

### **What It Is**
Build small, focused command-line tools first, then orchestrate them with bash or Python.

### **Core Principles**

#### **1. Unix Philosophy: Do One Thing Well**

**Bad (Monolithic):**
```python
# One script that does everything
def migrate_spring_app(files):
    for file in files:
        update_imports(file)
        update_annotations(file)
        update_security(file)
        test_changes(file)
    # 500 lines of tangled logic
```

**Good (CLI-First):**
```bash
# Individual focused tools
./migrate-imports UserController.java
./migrate-annotations UserController.java
./migrate-security UserController.java
./test-migration UserController.java

# Compose them
for file in *.java; do
  ./migrate-imports "$file" && \
  ./migrate-annotations "$file" && \
  ./migrate-security "$file" && \
  ./test-migration "$file"
done
```

---

#### **2. Composability: Tools Work Together**

**CLI Signature Requirements:**
```python
# Each CLI must:
# 1. Parse arguments properly
import argparse
parser = argparse.ArgumentParser()
parser.add_argument('--input', required=True)
parser.add_argument('--output', default='-')  # stdout

# 2. Output structured data
import json
print(json.dumps(result))  # Not: print(f"Found {len(result)} items")

# 3. Exit with proper codes
sys.exit(0)  # Success
sys.exit(1)  # Failure

# 4. Include --help
parser.add_argument('--input', help='Input file path')

# 5. Accept stdin/stdout for piping
if args.input == '-':
    data = sys.stdin.read()
```

---

#### **3. Progressive Enhancement: Start Simple**

**Level 1: Raw CLI**
```bash
./search --query="Spring migration"
```

**Level 2: Bash One-Liner**
```bash
./search --query="API" | jq -r '.[] | .id' | while read id; do
  ./extract --id=$id
done
```

**Level 3: Bash Script**
```bash
#!/bin/bash
set -euo pipefail

for result in $(./search | jq -r '.[]'); do
  ./extract --input="$result" || echo "Failed: $result"
done
```

**Level 4: Python Orchestration** (only when needed)
```python
import subprocess
import time

def extract_with_retry(page_id, max_retries=3):
    for attempt in range(max_retries):
        try:
            return subprocess.run(
                ['./extract', '--id', page_id],
                check=True, capture_output=True
            )
        except subprocess.CalledProcessError:
            if attempt == max_retries - 1:
                raise
            time.sleep(2 ** attempt)  # Exponential backoff
```

---

### **Decision Tree: Bash vs Python**

```
Need to compose CLI tools?
│
├─ Simple pipeline (2-5 steps)?
│  └─ Use: Bash pipes and for loops
│
├─ Need error handling?
│  ├─ Basic (exit on error)
│  │  └─ Use: Bash with 'set -e' and '&&'
│  └─ Complex (retry, fallback, logging)
│     └─ Use: Python subprocess wrapper
│
├─ Need state management?
│  ├─ Simple (temp files, env vars)
│  │  └─ Use: Bash
│  └─ Complex (databases, sessions)
│     └─ Use: Python
│
├─ Need progress tracking?
│  └─ Use: Python (tqdm, rich)
│
├─ Integration with Python libs?
│  └─ Use: Python
│
└─ User wants customizable one-liner?
   └─ Use: Bash (easy to modify)
```

---

### **Benefits of CLI-First**

**1. Testability**
```bash
# Test each CLI independently
./auth --token="fake"         # Expect 401
./search --limit=0            # Expect empty []
./extract --id="invalid"      # Expect error
```

**2. Reusability**
```bash
# Use CLIs in different contexts
cron job     → ./search | mail -s "Results"
bash script  → for i in ...; do ./extract --id=$i; done
Python       → subprocess.run(['./search'])
CI/CD        → ./test-all && ./deploy
```

**3. Debuggability**
```bash
# Debug step-by-step
./search > /tmp/debug.json
cat /tmp/debug.json | jq '.'
./extract --id="$(jq -r '.[0].id' /tmp/debug.json)"
```

**4. Flexibility**
```bash
# Users customize without touching code
./search --limit=10 | jq '.'              # Increase limit
./extract | pandoc -f md -t pdf           # Change format
./search | grep "API" | ./extract         # Filter results
```

---

## 📝 PATTERN 3: SPEC-DRIVEN ARTIFACTS

### **What It Is**
A structured approach to documenting requirements, decisions, and knowledge throughout development.

### **The 5 Core Artifacts**

#### **1. mainspec.md - Human-Written Requirements**
**Purpose:** Source of truth for WHAT to build

**Template:**
```markdown
# Feature Specification: Confluence Scraper

## Overview
Extract Confluence pages to Markdown for offline analysis

## Requirements

### Functional Requirements
- [ ] Authenticate to Confluence API with token
- [ ] Search pages by query string
- [ ] Extract page content preserving formatting
- [ ] Support batch processing of multiple pages

### Non-Functional Requirements
- Performance: Process 100 pages in <5 minutes
- Security: Never log authentication tokens
- Reliability: Retry failed requests with exponential backoff

## Acceptance Criteria
- [ ] Can authenticate with valid token (test with real token)
- [ ] Returns JSON with page IDs (verify structure)
- [ ] Extracts content as Markdown (compare with original)
- [ ] Handles API errors gracefully (test with invalid inputs)

## Technical Approach
Build as 3 composable CLI tools following Unix philosophy:
- confluence-auth: Validates credentials
- confluence-search: Returns page metadata as JSON
- confluence-extract: Converts HTML to Markdown

## Dependencies & Constraints
- Requires: Confluence Cloud API access, valid API token
- Constraints: Rate limited to 10 req/sec

## Out of Scope
- Does NOT include: Confluence Server support, image download
```

**When to create:** Before starting work  
**Who writes:** Human (you)  
**Updates:** Rarely (requirements change)

---

#### **2. implementation_plan.md - AI-Generated Execution Plan**
**Purpose:** Break mainspec into actionable phases and tasks

**Template:**
```markdown
# Implementation Plan: Confluence Scraper

## Discovery Summary
- Analyzed Confluence Cloud REST API v2
- Identified authentication via Bearer token
- Found rate limiting: 10 requests/second
- HTML content needs conversion to Markdown

## Implementation Phases

### Phase 1: Build Individual CLIs (30 min)
- [ ] confluence-auth
  - Files: scripts/confluence-auth
  - Dependencies: None
  - Risk: Low
  - Estimate: 10 min
  - Validation: Returns 200 with valid token, 401 with invalid

- [ ] confluence-search  
  - Files: scripts/confluence-search
  - Dependencies: confluence-auth
  - Risk: Medium (pagination)
  - Estimate: 15 min
  - Validation: Returns JSON array of page objects

- [ ] confluence-extract
  - Files: scripts/confluence-extract
  - Dependencies: None
  - Risk: Medium (HTML parsing)
  - Estimate: 15 min
  - Validation: Produces valid Markdown

### Phase 2: Test CLIs Independently (15 min)
- [ ] Test auth with fake token (expect 401)
- [ ] Test search with limit=0 (expect empty array)
- [ ] Test extract with invalid page ID (expect error)
- [ ] Test extract with real page (verify Markdown)

### Phase 3: Compose with Bash (10 min)
- [ ] Create one-liner: ./search | jq | while read id; do ./extract; done
- [ ] Add error handling (continue on failure)
- [ ] Test end-to-end with 5 pages

### Phase 4: Optional Enhancement (if needed)
- [ ] Add Python wrapper for retry logic
- [ ] Add progress bar for batch processing
- [ ] Add logging for debugging

## Risk Assessment
- **Risk**: Rate limiting causes failures
  - Probability: High
  - Impact: Medium
  - Mitigation: Add exponential backoff in Python wrapper

- **Risk**: HTML to Markdown conversion loses formatting
  - Probability: Medium
  - Impact: Low
  - Mitigation: Use pandoc library, test with complex pages

## Definition of Done
- [ ] All 3 CLIs exist and have --help
- [ ] Each CLI tested independently
- [ ] Bash one-liner works end-to-end
- [ ] Meets all acceptance criteria from mainspec.md
- [ ] Documentation updated (README.md)
```

**When to create:** After mainspec, before coding  
**Who writes:** AI (with your input)  
**Updates:** As phases complete (checkboxes)

---

#### **3. knowledge_bank.md - Living Context Document**
**Purpose:** Preserve decisions, context, and session logs

**Template:**
```markdown
# Knowledge Bank: Confluence Scraper

## Current Status
- **Phase**: Phase 3 - Bash Composition
- **Progress**: 75% complete (3 CLIs built, tested, composing)
- **Last Updated**: 2025-11-11 14:30

## Session Log

### Session 2025-11-11 Morning (2 hours)
- **Phase**: Phase 1 - Build CLIs
- **Completed**:
  - Built confluence-auth (works perfectly)
  - Built confluence-search (returns JSON)
  - Built confluence-extract (initial version)
- **Blockers**:
  - HTML to Markdown conversion losing code blocks
  - Decided to use pandoc instead of custom parser
- **Next Steps**:
  - Fix extract CLI to preserve code blocks
  - Test all 3 CLIs independently
  - Move to bash composition

### Session 2025-11-11 Afternoon (1 hour)
- **Phase**: Phase 2 - Testing
- **Completed**:
  - Fixed extract CLI (now uses pandoc)
  - All CLIs tested independently
  - All tests passing
- **Next Steps**:
  - Create bash one-liner for composition
  - Test end-to-end

## Key Decisions

### Decision: Use Pandoc for HTML to Markdown
- **Context**: Initial regex-based conversion was losing code blocks and tables
- **Options Considered**:
  - Custom HTML parser (complex, error-prone)
  - BeautifulSoup + manual conversion (medium complexity)
  - Pandoc library (simple, robust)
  - markdownify library (Python-specific)
- **Decision**: Use Pandoc via subprocess call
- **Rationale**:
  - Pandoc handles 95% of HTML → Markdown edge cases
  - Well-tested, maintained by community
  - Already installed on most dev machines
  - Falls back gracefully if pandoc missing
- **Trade-offs**:
  - External dependency (mitigated: check at runtime)
  - Slightly slower (acceptable: <100ms per page)
- **Validation**: Tested with 10 complex pages, all rendered correctly

### Decision: Bash Composition Over Python Wrapper
- **Context**: Need to orchestrate 3 CLIs together
- **Options Considered**:
  - Bash one-liner (simplest)
  - Bash script (adds error handling)
  - Python wrapper (most robust)
  - Make workflow (overkill)
- **Decision**: Start with bash one-liner, add Python only if needed
- **Rationale**:
  - Bash sufficient for linear pipeline
  - Users can easily customize
  - No retry logic needed (Confluence API is stable)
  - KISS principle
- **Trade-offs**:
  - No built-in retry (acceptable: API is reliable)
  - No progress bar (acceptable: fast enough)
- **Validation**: Tested with 50 pages, no failures

## Context & References
- Research findings: [research.md](./research.md#confluence-api-analysis)
- API documentation: https://developer.atlassian.com/cloud/confluence/rest/v2/
- Pandoc docs: https://pandoc.org/MANUAL.html
- Related: Similar pattern used in wiki-scraper project
```

**When to create:** Start of project  
**Who writes:** You (throughout development)  
**Updates:** Continuously (every session)

---

#### **4. research.md - Codebase Analysis**
**Purpose:** Document exploration and integration findings

**Template:**
```markdown
# Research: Confluence Scraper

## Codebase Analysis
- **Existing patterns**: No existing Confluence integration
- **Similar implementations**: Found wiki-scraper project (different API)
- **Integration points**: Will be standalone scripts in scripts/ directory

## Technical Findings

### Confluence API Analysis
- **Base URL**: https://your-domain.atlassian.net/wiki/rest/api/
- **Authentication**: Bearer token in Authorization header
- **Rate Limiting**: 10 requests/second (documented)
- **Pagination**: Uses "start" and "limit" parameters
- **Content Format**: Returns HTML in "body.storage.value"

### API Endpoints Used
1. `/rest/api/content/search` - Search pages by CQL
   - Returns: Array of page objects with id, title, space
2. `/rest/api/content/{id}?expand=body.storage` - Get page content
   - Returns: Full page with HTML body

### Dependencies Discovered
- **Required**: requests library for HTTP
- **Optional**: pandoc for HTML conversion (fallback to markdownify)
- **Testing**: pytest for unit tests

## Integration Strategy

### Entry Points
- Scripts will live in: `scripts/confluence-*`
- Can be called from: Command line, cron jobs, CI/CD

### Affected Systems
- None (standalone tools)

### Testing Approach
- Unit tests: Mock API responses
- Integration tests: Test with real API (separate test space)
- End-to-end: Scrape 5 pages, verify Markdown output
```

**When to create:** During discovery phase  
**Who writes:** You (while exploring)  
**Updates:** As you discover new things

---

#### **5. notes.md - Quick Context Capture**
**Purpose:** Stream-of-consciousness notes during development

**Template:**
```markdown
# Notes: Confluence Scraper

## 2025-11-11 Morning - Initial Setup
- Started with confluence-auth CLI
- Question: Should we cache tokens? → No, keep stateless
- Decided to use argparse for all CLIs (consistency)
- Note: Confluence API returns 404 for invalid page IDs (not 400)

## 2025-11-11 Afternoon - HTML Conversion Issue
- extract CLI losing code blocks in conversion
- Tried regex: NOPE (too complex)
- Tried BeautifulSoup: Better but still losing formatting
- **AHA MOMENT**: Use pandoc! It Just Works™
- Implementation: subprocess.run(['pandoc', '-f', 'html', '-t', 'markdown'])
- Need to check if pandoc installed (add --help suggestion)

## Scratchpad
- TODO: Add rate limiting check (10 req/sec)
- TODO: Test with pages containing tables
- TODO: Document required environment variables
- IDEA: Could add --format flag to support other outputs (PDF, reStructuredText)

## Questions to Answer
- Q: Should we support Confluence Server (on-prem)?
  - A: Out of scope for v1 (mainspec.md)
- Q: How to handle images in content?
  - A: Out of scope for v1, just preserve image URLs in Markdown
```

**When to create:** Start of first session  
**Who writes:** You (rapid notes)  
**Updates:** Constantly (don't overthink it)

---

### **When to Create Which Artifact**

```
Project Start:
  ↓
mainspec.md (requirements)
  ↓
research.md (discovery)
  ↓
implementation_plan.md (execution plan)
  ↓
knowledge_bank.md (sessions begin)
  ↓
notes.md (ongoing thoughts)
  ↓
[Throughout Development - Update All]
  ↓
Project Complete
```

---

### **Artifact Quality Gates**

**Before starting Phase 1:**
- [ ] mainspec.md has clear requirements
- [ ] mainspec.md has testable acceptance criteria
- [ ] implementation_plan.md has actionable tasks
- [ ] research.md documents API/codebase findings

**Before transitioning phases:**
- [ ] Previous phase checkboxes marked complete
- [ ] knowledge_bank.md updated with session notes
- [ ] Key decisions documented with rationale
- [ ] notes.md converted to knowledge_bank (if important)

**Before considering "done":**
- [ ] All acceptance criteria met from mainspec.md
- [ ] All implementation_plan.md checkboxes complete
- [ ] knowledge_bank.md has final status update
- [ ] Documentation reflects decisions made

---

## 🔄 THE COMPLETE WORKFLOW

### **How All 3 Patterns Work Together**

Let's build a **Confluence Scraper** from scratch using all 3 patterns.

---

### **STEP 1: Create Spec-Driven Artifacts** (15 min)

#### **1.1: Write mainspec.md** (10 min)
```markdown
# Feature Specification: Confluence Scraper

## Requirements
- [ ] Authenticate to Confluence API
- [ ] Search pages by query
- [ ] Extract content to Markdown
- [ ] Handle 100+ pages in batch

## Acceptance Criteria
- [ ] Valid token returns 200
- [ ] Search returns JSON with page IDs
- [ ] Extract produces valid Markdown
- [ ] Processes 100 pages in <5 minutes
```

#### **1.2: Create research.md** (5 min)
```markdown
# Research: Confluence Scraper

## API Analysis
- Endpoint: /rest/api/content/search
- Auth: Bearer token
- Rate limit: 10/sec
- Content: HTML in body.storage.value
```

**Result:** Clear requirements documented

---

### **STEP 2: Generate implementation_plan.md Using 5 Prompt Modes** (10 min)

#### **2.1: Load Constitution Mode**
```markdown
# file-0: Constitution

## CLI-First Architecture Rules:
- Build individual focused CLIs
- Output JSON for structured data
- Accept stdin/stdout for piping
- Exit codes: 0=success, 1+=error
- Include --help documentation

## Confluence Integration Rules:
- Use Bearer token authentication
- Handle rate limiting (10 req/sec)
- Preserve Markdown formatting
```

#### **2.2: Load Specification Mode**
```markdown
# file-1: Specification

Build 3 CLI tools:
1. confluence-auth: Validates token (returns 200/401)
2. confluence-search: Returns page IDs as JSON
3. confluence-extract: Converts page to Markdown

Success Criteria from mainspec.md:
✓ All CLIs testable independently
✓ Composable via bash pipes
✓ Handle 100+ pages efficiently
```

#### **2.3: Load Planning Mode**
```markdown
# file-2: Planning

## Phase 1: Build CLIs (30 min)
- confluence-auth (10 min)
- confluence-search (10 min)
- confluence-extract (10 min)

## Phase 2: Test (15 min)
- Unit tests for each CLI
- Integration test end-to-end

## Phase 3: Compose (10 min)
- Bash one-liner
- Error handling
```

#### **2.4: Generate implementation_plan.md**
```markdown
# file-4: Implementation

Generate implementation_plan.md that follows:
- Constitution rules (CLI-first)
- Specification requirements (3 CLIs)
- Planning phases (build → test → compose)

Output complete implementation_plan.md with:
- Detailed tasks per phase
- Risk assessment
- Definition of done
```

**Result:** AI generates complete `implementation_plan.md`

---

### **STEP 3: Build CLIs Using 5 Prompt Modes** (30 min)

#### **3.1: Build confluence-auth CLI**

**Load all 5 modes:**
```markdown
# file-0: Constitution (CLI-first rules)
# file-1: Spec (auth CLI requirements)
# file-2: Plan (implement → test)
# file-3: ABCD (decision: use requests library vs urllib)
# file-4: Generate confluence-auth script
```

**AI Output:**
```python
#!/usr/bin/env python3
import argparse
import requests
import sys
import json

def main():
    parser = argparse.ArgumentParser(description='Validate Confluence auth')
    parser.add_argument('--url', required=True, help='Confluence base URL')
    parser.add_argument('--token', required=True, help='API token')
    args = parser.parse_args()
    
    try:
        response = requests.get(
            f"{args.url}/rest/api/content",
            headers={"Authorization": f"Bearer {args.token}"},
            params={"limit": 1}
        )
        
        if response.status_code == 200:
            print(json.dumps({"status": "authenticated"}))
            sys.exit(0)
        else:
            print(json.dumps({"error": f"HTTP {response.status_code}"}), 
                  file=sys.stderr)
            sys.exit(1)
            
    except Exception as e:
        print(json.dumps({"error": str(e)}), file=sys.stderr)
        sys.exit(1)

if __name__ == '__main__':
    main()
```

**Update knowledge_bank.md:**
```markdown
## Session 2025-11-11 10:00
- Built confluence-auth CLI
- Decision: Used requests library (simpler than urllib)
- Tested: Works with valid/invalid tokens
```

#### **3.2: Build confluence-search CLI** (same process)
#### **3.3: Build confluence-extract CLI** (same process)

**Result:** 3 working CLIs following CLI-first architecture

---

### **STEP 4: Test CLIs (CLI-First Pattern)** (15 min)

```bash
# Test auth
./confluence-auth --url=$URL --token="fake"
# Expected: Exit 1, JSON error

./confluence-auth --url=$URL --token=$REAL_TOKEN
# Expected: Exit 0, {"status": "authenticated"}

# Test search
./confluence-search --query="test" --limit=0
# Expected: Exit 0, []

./confluence-search --query="API" --limit=5
# Expected: Exit 0, JSON array with 5 page objects

# Test extract
./confluence-extract --page-id="invalid"
# Expected: Exit 1, error message

./confluence-extract --page-id="123456"
# Expected: Exit 0, Markdown content
```

**Update implementation_plan.md:**
```markdown
## Phase 2: Test CLIs
- [x] Test auth with fake token ✓
- [x] Test search with limit=0 ✓
- [x] Test extract with invalid ID ✓
```

---

### **STEP 5: Compose with Bash (CLI-First Pattern)** (10 min)

```bash
# Simple composition
./confluence-search --query="Spring migration" --limit=10 | \
  jq -r '.[] | .id' | \
  while read id; do
    ./confluence-extract --page-id="$id" --output="${id}.md"
  done
```

**Result:** Working end-to-end workflow

---

### **STEP 6: Document in knowledge_bank.md** (5 min)

```markdown
## Key Decisions

### Decision: Bash Composition Sufficient
- **Context**: Need to orchestrate 3 CLIs
- **Options**: Bash one-liner vs Python wrapper
- **Decision**: Bash one-liner
- **Rationale**: 
  - Simple linear pipeline
  - No retry needed (API stable)
  - Users can customize easily
- **Trade-offs**: No progress bar (acceptable)
- **Validation**: Tested with 50 pages, worked perfectly

## Current Status
- **Phase**: Complete
- **Progress**: 100%
- **All acceptance criteria met** ✓
```

---

### **COMPLETE WORKFLOW SUMMARY**

```
1. Spec-Driven Artifacts
   ├─ mainspec.md (requirements)
   ├─ research.md (API analysis)
   └─ implementation_plan.md (execution plan)
          ↓
2. 5 Prompt Modes (generate CLIs)
   ├─ Constitution (CLI-first rules)
   ├─ Specification (what to build)
   ├─ Planning (how to build)
   ├─ ABCD (decisions)
   └─ Implementation (code generation)
          ↓
3. CLI-First Architecture (structure)
   ├─ Build individual CLIs
   ├─ Test independently
   ├─ Compose with bash
   └─ Enhance only if needed
          ↓
4. Update Spec-Driven Artifacts
   ├─ knowledge_bank.md (decisions)
   ├─ implementation_plan.md (progress)
   └─ notes.md (learnings)
          ↓
Working Software (Documented, Testable, Maintainable)
```

---

## 📊 DECISION MATRICES

### **When to Use Which Pattern**

#### **Use 5 Prompt Modes When:**
- ✅ Building anything with AI assistance
- ✅ Need consistent output across team
- ✅ Want reusable prompt templates
- ✅ Complex multi-step generation
- ✅ Teaching others to prompt effectively

#### **Use CLI-First When:**
- ✅ Building automation tools
- ✅ Data processing pipelines
- ✅ Developer utilities
- ✅ Need composability
- ✅ Users should customize behavior

#### **Use Spec-Driven Artifacts When:**
- ✅ Multi-session projects
- ✅ Team collaboration needed
- ✅ Decisions need documentation
- ✅ Knowledge preservation matters
- ✅ Complex requirements

---

### **Pattern Combinations**

| Your Situation | Use These Patterns |
|----------------|-------------------|
| **Simple script** | 5 Modes only |
| **Complex feature** | All 3 patterns |
| **Quick automation** | CLI-First only |
| **Team project** | Spec + 5 Modes |
| **Exploratory work** | 5 Modes + notes.md |
| **Production system** | All 3 patterns |
| **Learning/teaching** | 5 Modes + CLI-First |

---

## 🎓 REAL-WORLD EXAMPLES

### **Example 1: Spring Boot 2→3 Migration**

**Spec-Driven Artifacts:**
```
specs/spring-migration/
├── mainspec.md           (Requirements: javax→jakarta, security updates)
├── implementation_plan.md (Phase 1: Imports, Phase 2: Annotations, etc.)
├── knowledge_bank.md     (Decision log: SecurityFilterChain approach)
└── research.md           (Spring 3 API changes analysis)
```

**5 Prompt Modes:**
```
file-0: Constitution (migration rules)
file-1: Specification (UserController target state)
file-2: Planning (systematic migration phases)
file-3: ABCD (security config decision)
file-4: Implementation (generate migrated code)
```

**CLI-First Architecture:**
```bash
# Build individual migration tools
./migrate-imports UserController.java
./migrate-annotations UserController.java
./migrate-security UserController.java

# Compose for batch migration
for file in src/**/*.java; do
  ./migrate-imports "$file" && \
  ./migrate-annotations "$file" && \
  ./migrate-security "$file"
done
```

**Result:** Systematic, documented, reusable migration process

---

### **Example 2: Data Engineering Pipeline**

**Spec-Driven Artifacts:**
```
specs/sap-pipeline/
├── mainspec.md           (Requirements: validate, transform, load)
├── implementation_plan.md (Phase 1: Validation, Phase 2: Transform, etc.)
└── knowledge_bank.md     (Decisions: validation rules, error handling)
```

**5 Prompt Modes:**
```
file-0: Constitution (data quality rules, error handling patterns)
file-1: Specification (validation CLI, transform CLI, load CLI)
file-2: Planning (build → test → orchestrate)
file-3: ABCD (decision: streaming vs batch)
file-4: Implementation (generate CLIs)
```

**CLI-First Architecture:**
```bash
# Individual pipeline stages
./validate-dataset input.csv
./transform-dataset input.csv | ./enrich-data
./load-to-warehouse transformed.csv

# Orchestrate with bash
./validate-dataset data/*.csv && \
./transform-dataset data/*.csv | ./enrich-data | ./load-to-warehouse
```

**Result:** Modular, testable data pipeline

---

### **Example 3: Agentic Workflow (LangGraph)**

**Spec-Driven Artifacts:**
```
specs/pr-reviewer-agent/
├── mainspec.md           (Requirements: analyze PR, suggest improvements)
├── implementation_plan.md (Phase 1: Analysis node, Phase 2: Suggestion node)
└── knowledge_bank.md     (Decisions: LangGraph vs custom orchestration)
```

**5 Prompt Modes:**
```
file-0: Constitution (agent behavior rules, API patterns)
file-1: Specification (each node as focused CLI)
file-2: Planning (build nodes → test → connect with LangGraph)
file-3: ABCD (decision: sequential vs parallel review)
file-4: Implementation (generate node CLIs)
```

**CLI-First Architecture:**
```bash
# Each LangGraph node is a CLI
./analyze-pr --pr-number=123 > analysis.json
./suggest-improvements --analysis=analysis.json > suggestions.json
./generate-comment --suggestions=suggestions.json

# LangGraph orchestrates the CLIs
# (Python wrapper calls subprocess for each node)
```

**Result:** Testable agent with reusable components

---

## 🚀 GETTING STARTED

### **Quick Start: Your First Project**

#### **Step 1: Choose a Small Task** (5 min)
Pick something you're building this week:
- Migrate 1 Spring controller
- Build a data validation script
- Create an API integration tool

#### **Step 2: Create mainspec.md** (10 min)
```markdown
# Feature Specification: [Your Task]

## Requirements
- [ ] [What it must do]
- [ ] [What it must do]

## Acceptance Criteria
- [ ] [How you know it's done]
- [ ] [How you know it's done]
```

#### **Step 3: Use 5 Modes to Generate Plan** (5 min)
```markdown
file-0: Constitution (your project rules)
file-1: Specification (what to build)
file-2: Planning (how to build it)
file-4: Generate implementation_plan.md
```

#### **Step 4: Build Using CLI-First** (30 min)
- Build 1-3 focused CLIs
- Test each independently
- Compose with bash

#### **Step 5: Document in knowledge_bank.md** (5 min)
```markdown
## Session [Today]
- Built [what you built]
- Decision: [key choice you made]
- Next: [what's next]
```

**Total Time:** ~1 hour  
**Result:** Working software + complete documentation

---

### **Scaling Up: Team Adoption**

#### **Week 1: Individual Practice**
- Each person does 1 project using all 3 patterns
- Share mainspec.md and knowledge_bank.md in Slack
- Discuss what worked / what didn't

#### **Week 2: Pair Programming**
- Two people work on same feature
- One writes specs, one uses 5 modes to generate
- Both document in knowledge_bank.md

#### **Week 3: Team Library**
- Create shared `constitutions/` folder
- Reusable file-0 for common projects
- Template implementation_plan.md files

#### **Week 4: Process Refinement**
- Review what's working
- Update templates
- Document team-specific patterns

---

## 📈 MEASURING SUCCESS

### **Individual Metrics**

**Before Using Patterns:**
- Time to build feature: 4-6 hours
- Documentation: None or minimal
- Reusability: Low (start from scratch each time)
- Knowledge transfer: Hard (tribal knowledge)

**After Using Patterns:**
- Time to build feature: 1-2 hours (first time), 30 min (reusing templates)
- Documentation: Complete (mainspec, knowledge_bank, plan)
- Reusability: High (CLIs + templates)
- Knowledge transfer: Easy (read artifacts)

### **Team Metrics**

Track in shared spreadsheet:

| Engineer | Features Built | Patterns Used | Time Saved | Artifacts Created |
|----------|---------------|---------------|------------|-------------------|
| Ahmad    | 3             | All 3         | 8 hours    | 15 files          |
| Bala     | 5             | All 3         | 15 hours   | 25 files          |
| Ray      | 2             | 5 Modes only  | 4 hours    | 10 files          |

**Business Value:**
- Hours saved × hourly rate = ROI
- Artifacts created = knowledge preserved
- Patterns adopted = team capability

---

## 💡 BEST PRACTICES

### **Do's:**
✅ Start with mainspec.md (know what you're building)  
✅ Use 5 modes for consistent AI output  
✅ Build individual CLIs before orchestration  
✅ Document decisions in knowledge_bank.md  
✅ Test each component independently  
✅ Update artifacts continuously  
✅ Share templates with team  

### **Don'ts:**
❌ Don't skip mainspec (leads to scope creep)  
❌ Don't write monolithic code (loses composability)  
❌ Don't forget to document decisions (lose context)  
❌ Don't overcomplicate orchestration (bash often sufficient)  
❌ Don't let artifacts go stale (update them!)  
❌ Don't hoard patterns (share with team)  

---

## 🎯 COMMON PITFALLS & SOLUTIONS

### **Pitfall 1: "Too much documentation overhead"**
**Solution:** Start minimal
- Day 1: Just mainspec.md (10 min)
- Day 2: Add implementation_plan.md (AI generates)
- Week 1: Add knowledge_bank.md (as you work)

### **Pitfall 2: "CLIs add complexity"**
**Solution:** Progressive enhancement
- Start: One monolithic script
- If used twice: Extract as CLI
- If used by others: Document as tool

### **Pitfall 3: "5 modes take too long"**
**Solution:** Reuse templates
- First file: 30 min (create modes)
- Second file: 5 min (reuse file-0, 1, 2)
- Tenth file: 2 min (just file-4)

### **Pitfall 4: "Artifacts become stale"**
**Solution:** Build into workflow
- End of session: Update knowledge_bank
- Complete task: Check implementation_plan
- Make decision: Document in knowledge_bank

---

## 🔗 INTEGRATION WITH OTHER TOOLS

### **Git Integration**
```bash
# Version control your artifacts
git add specs/feature-name/
git commit -m "Add feature specs and implementation plan"

# Reference artifacts in commits
git commit -m "Implement auth CLI (see specs/auth/mainspec.md)"
```

### **CI/CD Integration**
```yaml
# Test CLIs in CI pipeline
test:
  script:
    - ./validate-all-specs.sh
    - pytest tests/cli/
    - ./test-cli-composition.sh
```

### **Code Review Integration**
```markdown
## PR Description
**Specs:** `specs/feature-name/`
**Implementation Plan:** Completed Phase 2 (tasks 2.1-2.3)
**Key Decisions:** See knowledge_bank.md section "Decision: Database Choice"
```

---

## 📚 REFERENCE QUICK LINKS

### **5 Prompt Modes**
- Day 1 Workshop: `DAY-1-SESSION-GUIDE.md`
- Day 2 Workshop: `DAY-2-SESSION-GUIDE.md`
- Templates: `templates-quick-reference.md`

### **CLI-First Architecture**
- Full guide: `CLI-FIRST-ARCHITECTURE.md` (when created)
- Decision tree: See "Decision Tree: Bash vs Python" above

### **Spec-Driven Artifacts**
- Full spec: This document, "Pattern 3" section
- Templates: See mainspec, implementation_plan, knowledge_bank templates above

---

## 🎉 CONCLUSION

You now have **three powerful patterns** that transform how you build software with AI:

1. **5 Prompt Modes** - Structure AI collaboration systematically
2. **CLI-First Architecture** - Build composable, testable tools
3. **Spec-Driven Artifacts** - Document requirements and knowledge

**Together, they provide:**
- ✅ Consistent, high-quality AI output (5 Modes)
- ✅ Modular, reusable software (CLI-First)
- ✅ Complete documentation (Spec Artifacts)
- ✅ Knowledge preservation across team
- ✅ Measurable productivity gains

**Start small:**
1. Pick one feature
2. Create mainspec.md
3. Use 5 modes to generate
4. Build as CLIs
5. Document decisions

**Scale up:**
- Reuse templates
- Share with team
- Build library of patterns
- Measure and improve

**The compound effect:**
- Week 1: Save 5 hours
- Month 1: Save 20 hours
- Quarter 1: Save 60 hours
- Year 1: Transform how team works

**Now go build something awesome.** 🚀

---

**Document Status:** Master Integration Guide v1.0  
**Last Updated:** 2025-11-11  
**Maintainer:** Joseph Lopez  
**Purpose:** Complete framework integrating all 3 patterns  
**Usage:** Reference for all projects using AI-assisted development
