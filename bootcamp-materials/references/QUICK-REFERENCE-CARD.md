# THE 3 PATTERNS - QUICK REFERENCE CARD
## One-Page Guide to AI-Assisted Development

---

## 🎯 PATTERN 1: THE 5 PROMPT MODES

**Purpose:** Structure AI collaboration systematically

| Mode | What | When | Time |
|------|------|------|------|
| **Constitution** 🎼 | Project rules | Once per project | 15 min |
| **Specification** 🎯 | What to build THIS file | Once per file | 5 min |
| **Planning** 📋 | Step-by-step approach | Once per pattern | 5 min |
| **ABCD** 🤔 | Decision points | When ambiguous | 5 min |
| **Implementation** ⚙️ | Generate code | Every file | 2 min |

**First file:** 30 min setup | **Every file after:** 5 min

---

## 🏗️ PATTERN 2: CLI-FIRST ARCHITECTURE

**Purpose:** Build composable, testable tools

### **Progression:**
```
1. Build individual CLIs
   ↓
2. Test independently
   ↓
3. Compose with bash
   ↓
4. Add Python only if needed
```

### **Decision Tree:**
- **Simple pipeline?** → Bash pipes
- **Complex retry?** → Python wrapper
- **State management?** → Python
- **Progress tracking?** → Python
- **User customization?** → Bash

**Rule:** Start with bash, add Python when bash becomes painful

---

## 📝 PATTERN 3: SPEC-DRIVEN ARTIFACTS

**Purpose:** Document requirements, decisions, knowledge

### **The 5 Artifacts:**

| Artifact | Purpose | When to Create | Who Writes |
|----------|---------|----------------|------------|
| **mainspec.md** | Requirements | Before work | Human |
| **implementation_plan.md** | Execution plan | After mainspec | AI + Human |
| **knowledge_bank.md** | Decisions & logs | Start of work | Human (ongoing) |
| **research.md** | Discovery findings | During research | Human |
| **notes.md** | Quick thoughts | During dev | Human (rapid) |

**Update continuously** - artifacts are living documents

---

## 🔗 HOW THEY WORK TOGETHER

```
Step 1: Spec-Driven Artifacts
  • mainspec.md (WHAT to build)
  • implementation_plan.md (phases)
        ↓

Step 2: 5 Prompt Modes
  • Constitution (rules)
  • Specification (target)
  • Planning (approach)
  • ABCD (decisions)
  • Implementation (generate)
        ↓

Step 3: CLI-First Architecture
  • Build individual CLIs
  • Test independently
  • Compose with bash
  • Enhance with Python if needed
        ↓

Step 4: Update Artifacts
  • knowledge_bank.md (decisions)
  • implementation_plan.md (progress)
        ↓

Working Software
(Documented, Testable, Maintainable)
```

---

## 🎓 QUICK START CHECKLIST

### **Starting a New Feature:**

- [ ] **Create mainspec.md** (10 min)
  - Write requirements
  - Define acceptance criteria

- [ ] **Use 5 Modes for Planning** (10 min)
  - file-0: Constitution (project rules)
  - file-1: Specification (this feature)
  - file-2: Planning (phases)
  - file-4: Generate implementation_plan.md

- [ ] **Build Using CLI-First** (30-60 min)
  - Design CLI interfaces (--help first)
  - Implement individual CLIs
  - Test each CLI independently
  - Compose with bash

- [ ] **Document Decisions** (5 min)
  - Update knowledge_bank.md
  - Mark implementation_plan.md tasks complete

**Total Time: ~1 hour for first feature**

---

## 💡 DECISION MATRICES

### **Which Patterns to Use?**

| Your Situation | Patterns Needed |
|----------------|-----------------|
| Quick script | 5 Modes only |
| Team feature | All 3 patterns |
| Solo exploration | 5 Modes + notes.md |
| Production system | All 3 patterns |
| Simple automation | CLI-First only |
| Learning project | 5 Modes + CLI-First |

### **When to Use Each Pattern?**

**5 Prompt Modes:**
- ✅ Always (consistent AI output)
- ✅ Complex generation tasks
- ✅ Need reusable templates
- ✅ Team collaboration

**CLI-First:**
- ✅ Automation tools
- ✅ Data pipelines
- ✅ Developer utilities
- ✅ Need composability

**Spec-Driven Artifacts:**
- ✅ Multi-session work
- ✅ Team projects
- ✅ Complex requirements
- ✅ Knowledge preservation

---

## 🚀 EXAMPLES IN 30 SECONDS

### **Spring Migration:**
```bash
# 1. Spec Artifacts
specs/spring-migration/mainspec.md
specs/spring-migration/implementation_plan.md

# 2. 5 Modes generate:
file-0: Constitution (migration rules)
file-1: Spec (UserController migration)
file-4: Implementation (generate code)

# 3. CLI-First (if batch migration):
./migrate-imports *.java
./migrate-annotations *.java
```

### **Confluence Scraper:**
```bash
# 1. Spec Artifacts
specs/confluence-scraper/mainspec.md

# 2. 5 Modes generate:
3 CLI tools (auth, search, extract)

# 3. CLI-First compose:
./search | jq -r '.[] | .id' | \
while read id; do ./extract --id=$id; done
```

### **Data Pipeline:**
```bash
# 1. Spec Artifacts
specs/data-pipeline/mainspec.md

# 2. 5 Modes generate:
./validate, ./transform, ./load CLIs

# 3. CLI-First compose:
./validate data.csv && \
./transform data.csv | \
./load
```

---

## 📊 TIME SAVINGS

### **Without Patterns:**
- Feature development: 4-6 hours
- Documentation: None
- Reusability: Start from scratch
- Knowledge transfer: Tribal knowledge

### **With Patterns:**
- **First feature:** 1-2 hours (setup + build)
- **Second feature:** 30 min (reuse templates)
- **Tenth feature:** 15 min (all patterns established)
- Documentation: Complete, always
- Reusability: High (CLIs + templates + artifacts)
- Knowledge transfer: Easy (read artifacts)

**ROI: 3-5x productivity after initial investment**

---

## ⚠️ COMMON PITFALLS

| Pitfall | Solution |
|---------|----------|
| "Too much documentation" | Start minimal: just mainspec.md |
| "CLIs add complexity" | Progressive: monolith → CLI when reused |
| "5 modes too slow" | Reuse: file-0,1,2 same for similar files |
| "Artifacts go stale" | Build into workflow: update at session end |

---

## 🎯 SUCCESS METRICS

**You're succeeding when:**
- [ ] Features built in <2 hours (first time)
- [ ] Reusing templates saves 70%+ time
- [ ] Team can understand any feature from artifacts
- [ ] CLIs composed in multiple workflows
- [ ] Knowledge preserved across sessions
- [ ] New teammates onboard from docs

---

## 📚 WHERE TO LEARN MORE

### **Day 1: The 5 Prompt Modes** (1.5 hours)
- Teach modes as thinking framework
- Run pre-built Spring workflow
- File: `DAY-1-SESSION-GUIDE.md`

### **Day 2: Writing Workflows** (1.5 hours)
- Write 5-mode workflows
- Build from real code
- File: `DAY-2-SESSION-GUIDE.md`

### **Complete Framework Guide** (5,200 words)
- All 3 patterns integrated
- Multiple examples
- File: `COMPLETE-DEVELOPMENT-FRAMEWORK.md`

---

## 🔥 THE BOTTOM LINE

**3 Patterns = Complete System:**

1. **5 Prompt Modes** → Consistent AI output
2. **CLI-First** → Composable software
3. **Spec-Driven Artifacts** → Complete docs

**Use all 3 → Transform how you build software**

**Start now:** Pick one feature, create mainspec.md, go! 🚀

---

**Quick Reference Card v1.0**  
**Print this page** - Keep at desk  
**Full docs:** `COMPLETE-DEVELOPMENT-FRAMEWORK.md`
