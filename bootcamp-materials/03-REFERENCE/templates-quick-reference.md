# PROMPT TEMPLATES - COPY & PASTE READY
## 15-Minute Quick Start: Use AI Better RIGHT NOW

**Purpose:** You have a problem NOW. Don't read theory. Copy template. Customize. Solve problem.  
**Time:** 2 minutes to find template, 3 minutes to customize, 10 minutes to solution.

---

## 🎯 TEMPLATE SELECTOR

**Pick your scenario:**

| Your Situation | Use This Template | Time Saved |
|----------------|-------------------|------------|
| Code is broken, need to debug | [Chain of Thought - Debugging](#chain-of-thought-debugging) | 20-40 min |
| Choosing between tech options | [ReAct - Research](#react-research) | 1-3 hours |
| Architecture decision needed | [Tree of Thoughts - Architecture](#tree-of-thoughts-architecture) | 2-4 hours |
| Code review taking forever | [Structured - Code Review](#structured-code-review) | 15-25 min |
| Building complex feature | [ABCD - Feature Dev](#abcd-feature-development) | Ongoing |
| Script timing out | [Chain of Thought - Performance](#chain-of-thought-performance) | 30-60 min |
| API returning errors | [Chain of Thought - API Errors](#chain-of-thought-api-errors) | 15-30 min |
| Need design doc | [Structured - Design Doc](#structured-design-doc) | 1-2 hours |
| Choosing database | [Tree of Thoughts - Tech Choice](#tree-of-thoughts-tech-choice) | 2-3 hours |
| Writing tests | [Structured - Test Cases](#structured-test-cases) | 30-45 min |

---

## 📋 TEMPLATES BY TECHNIQUE

### CHAIN OF THOUGHT - DEBUGGING

**Copy this template:**

```
[DESCRIBE PROBLEM WITH SYMPTOMS]

Let's debug this step by step:
1. What are the common causes of [ERROR TYPE]?
2. Which causes match these symptoms: [LIST SPECIFIC SYMPTOMS]
3. What's the specific fix for the identified root cause?

Code:
[PASTE YOUR CODE]

Error logs:
[PASTE RELEVANT ERRORS]

Context:
- Happens: [WHEN IT OCCURS - always/sometimes/specific conditions]
- Environment: [PROD/DEV/LOCAL]
- Recent changes: [WHAT CHANGED RECENTLY IF KNOWN]
```

**Example - Filled In:**

```
My Kafka consumer keeps timing out after exactly 30 seconds when processing large messages (5MB+). 
Small messages (< 1MB) process fine. This started happening after we increased daily data volume.

Let's debug this step by step:
1. What are the common causes of 30-second Kafka consumer timeouts?
2. Which causes match these symptoms: works for small messages, fails on large messages, exactly 30 sec
3. What's the specific fix for the identified root cause?

Code:
```python
consumer = KafkaConsumer(
    'datasets',
    bootstrap_servers=['kafka:9092'],
    group_id='dataset-processor',
    auto_offset_reset='earliest'
)

for message in consumer:
    process_dataset(message.value)  # Takes 2-5 min for large datasets
```

Error logs:
```
ERROR: ConsumerStoppedError: Consumer stopped fetching
WARNING: Group coordinator request timed out
ERROR: Marking consumer as failed
```

Context:
- Happens: Only on datasets >5MB, consistently
- Environment: Production
- Recent changes: Increased daily volume from 500GB to 2TB
```

**Use when:**
- Code works sometimes, fails others
- Error message unclear
- Multiple possible causes
- Need systematic diagnosis

---

### CHAIN OF THOUGHT - PERFORMANCE

**Copy this template:**

```
[DESCRIBE PERFORMANCE PROBLEM]

Current performance: [METRICS]
Target performance: [GOAL]

Let's optimize this step by step:
1. Where is the bottleneck? (Profiling shows: [PROFILING DATA IF AVAILABLE])
2. What's causing the slowness at that bottleneck?
3. What's the specific optimization for that cause?
4. What's the expected improvement?

Code:
[PASTE SLOW CODE]

Data volumes:
- [INPUT SIZE]
- [PROCESSING FREQUENCY]
- [EXPECTED GROWTH]
```

**Example - Filled In:**

```
SDP dataset migration script processes 1 dataset every 3 minutes. Need to migrate 1,500 datasets 
in 8-hour overnight window (480 minutes). Current speed = 75 hours total. NOT ACCEPTABLE.

Current performance: 3 minutes per dataset
Target performance: 20 seconds per dataset (allows 8-hour completion)

Let's optimize this step by step:
1. Where is the bottleneck? (Each dataset requires 4 API calls executed sequentially)
2. What's causing the slowness? (Sequential API calls + network latency)
3. What's the specific optimization? (Parallel processing + connection pooling)
4. What's the expected improvement? (4x speedup = 45 seconds/dataset, fits in 18 hours with buffer)

Code:
```python
def migrate_dataset(dataset_id):
    # API call 1: Get metadata (500ms)
    metadata = requests.get(f"{OLD_SDP}/datasets/{dataset_id}")
    
    # API call 2: Validate schema (1000ms)
    validation = requests.post(f"{NEW_SDP}/validate", json=metadata)
    
    # API call 3: Create dataset (500ms)
    created = requests.post(f"{NEW_SDP}/datasets", json=metadata)
    
    # API call 4: Confirm (500ms)
    confirm = requests.post(f"{NEW_SDP}/datasets/{created['id']}/confirm")
    
# Process all datasets
for dataset_id in dataset_ids:
    migrate_dataset(dataset_id)  # Sequential = SLOW
```

Data volumes:
- 1,500 datasets total
- Each dataset 10-50MB
- Need to complete overnight (8 hours max)
- Future growth: 3,000 datasets by Q4
```

---

### CHAIN OF THOUGHT - API ERRORS

**Copy this template:**

```
API endpoint returning [ERROR CODE/MESSAGE] when [CONDITIONS].

Let's diagnose step by step:
1. What does [ERROR] typically mean in REST APIs?
2. What request am I sending that triggers this?
3. What's wrong with my request or setup?
4. What's the correct fix?

API call:
[PASTE REQUEST CODE]

Response:
[PASTE ERROR RESPONSE]

Documentation: [LINK TO API DOCS IF AVAILABLE]

Context:
- Auth method: [HOW YOU AUTHENTICATE]
- Worked before: [YES/NO - if yes, what changed]
- Frequency: [ALWAYS/INTERMITTENT/SPECIFIC CONDITIONS]
```

---

### REACT - RESEARCH

**Copy this template:**

```
I need to choose between [OPTION A] and [OPTION B] for [USE CASE].

Requirements:
- [REQUIREMENT 1]
- [REQUIREMENT 2]
- [REQUIREMENT 3]
- [REQUIREMENT 4]
- [REQUIREMENT 5]

Use ReAct pattern to research this:

Think: What criteria matter most for this decision?
Act: Compare [OPTION A] vs [OPTION B] on those criteria
Observe: Which tool better fits our requirements?
Think: What are the tradeoffs?
Act: Check community adoption, costs, learning curve
Observe: What's the final recommendation?

Provide: Final recommendation with clear reasoning based on my requirements.
```

**Example - Filled In:**

```
I need to choose between PostgreSQL and MongoDB for storing Data Products metadata.

Requirements:
- Store metadata for 500+ data products
- Each product has 20-30 fields (name, owner, schema, lineage, etc.)
- Need complex queries: "Find all products owned by X that depend on Y"
- Team knows SQL well, limited NoSQL experience
- Integration with existing PostgreSQL data warehouse
- Cost-conscious (avoid expensive managed services)

Use ReAct pattern to research this:

Think: What criteria matter most for this decision?
Act: Compare PostgreSQL vs MongoDB on those criteria
Observe: Which better fits our requirements?
Think: What are the tradeoffs?
Act: Check operational overhead, scaling characteristics, costs
Observe: What's the final recommendation?

Provide: Final recommendation with clear reasoning based on my requirements.
```

**Use when:**
- Comparing 2+ technologies/approaches
- Need systematic comparison
- Multiple factors to consider
- Want to see reasoning, not just answer

---

### REACT - LEARNING NEW TECH

**Copy this template:**

```
I need to learn [TECHNOLOGY] to [ACCOMPLISH GOAL].

Current knowledge:
- I know: [WHAT YOU ALREADY KNOW]
- I don't know: [WHAT YOU NEED TO LEARN]
- I have: [TIME AVAILABLE] to learn this

Use ReAct pattern to create learning plan:

Think: What are the core concepts I must understand?
Act: Order them from foundational to advanced
Observe: What's the learning path?
Think: What's the fastest way to learn each concept?
Act: Identify best resources (official docs, tutorials, examples)
Observe: Build practice projects at each stage

Provide: Step-by-step learning plan with time estimates and specific resources.
```

---

### TREE OF THOUGHTS - ARCHITECTURE

**Copy this template:**

```
We need to [ARCHITECTURE DECISION] for [SYSTEM/FEATURE].

Context:
- [KEY CONSTRAINT 1]
- [KEY CONSTRAINT 2]
- [KEY CONSTRAINT 3]
- [TEAM CONTEXT]
- [TECH STACK]

Generate 3 distinct approaches for [DECISION], then recommend best fit:

Approach A: [Conservative/Safe Option]
- How it works: [Description]
- Pros: [Benefits]
- Cons: [Drawbacks]
- Best fit for: [When to use]

Approach B: [Balanced/Pragmatic Option]
- How it works: [Description]
- Pros: [Benefits]
- Cons: [Drawbacks]
- Best fit for: [When to use]

Approach C: [Alternative/Optimized Option]
- How it works: [Description]
- Pros: [Benefits]
- Cons: [Drawbacks]
- Best fit for: [When to use]

Recommendation: [Which approach] because [reasoning based on my specific context].
```

**Example - Filled In:**

```
We need to decide how to handle schema evolution in our Data Products platform.

Context:
- 500+ data products, each with different schemas
- Producers update schemas monthly (add fields, change types)
- 50+ consumers depend on these products
- Need to avoid breaking downstream consumers
- Small team (4 engineers) managing platform
- Mix of batch and streaming products

Generate 3 distinct approaches for schema evolution, then recommend best fit:

Approach A: Strict Versioning (v1, v2, v3)
- How it works: New schema = new version, old versions maintained forever
- Pros: Never breaks consumers, clear contracts, explicit migrations
- Cons: Proliferation of versions, storage duplication, complex maintenance
- Best fit for: High-stakes systems where breaking changes are catastrophic

Approach B: Backward Compatible Changes Only
- How it works: Only allow additive changes, enforce with schema registry
- Pros: Single version, no duplication, simpler operations
- Cons: Restricts producers, can't fix bad design decisions easily
- Best fit for: Mature systems with well-designed schemas

Approach C: Schema Evolution with Grace Period
- How it works: Announce changes 30 days ahead, run both schemas during transition
- Pros: Balance of flexibility and safety, educates consumers
- Cons: Coordination overhead, requires discipline, grace period management
- Best fit for: Collaborative teams, medium-scale systems

Recommendation: Approach C (Schema Evolution with Grace Period) because:
1. Small team (4 engineers) can't maintain infinite versions (rules out A)
2. Schemas are evolving, need flexibility for improvements (rules out B strict enforcement)
3. 30-day grace period balances producer needs with consumer safety
4. Team size manageable for coordination overhead
```

---

### TREE OF THOUGHTS - TECH CHOICE

**Copy this template:**

```
Choosing [TECHNOLOGY TYPE] for [USE CASE].

Candidates:
- [OPTION 1]
- [OPTION 2]
- [OPTION 3]

Evaluation criteria:
- [CRITERION 1]
- [CRITERION 2]
- [CRITERION 3]
- [CRITERION 4]

For each candidate, evaluate:

[OPTION 1]:
- [CRITERION 1]: [RATING & REASONING]
- [CRITERION 2]: [RATING & REASONING]
- [CRITERION 3]: [RATING & REASONING]
- [CRITERION 4]: [RATING & REASONING]
- Pros: [LIST]
- Cons: [LIST]
- Best fit for: [USE CASE]

[Repeat for each option]

Recommendation: [CHOICE] because [reasoning based on my criteria weightings].
```

---

### STRUCTURED - CODE REVIEW

**Copy this template:**

```
Review this PR using the following structured template:

## Code Review Template

### 1. Correctness
- Does the code do what the PR description claims?
- Are there logical errors or edge cases missed?
- Are error conditions handled properly?

### 2. Performance
- Any obvious performance issues?
- Resource usage concerns?

### 3. Security
- Input validation present?
- Sensitive data handled correctly?
- Authentication/authorization checked?

### 4. Maintainability
- Code is readable and well-commented?
- Follows team conventions?
- Tests cover main paths and edge cases?

### 5. Architecture
- Fits into existing system design?
- Dependencies appropriate?

### 6. Required Changes (Blocking)
[List must-fix issues before merge]

### 7. Suggested Improvements (Non-blocking)
[List nice-to-have improvements]

### 8. Approval Status
[Approve / Request Changes / Comment]

---

PR Description:
[PASTE PR DESCRIPTION]

Code Changes:
[PASTE DIFF OR LINK TO PR]
```

---

### STRUCTURED - DESIGN DOC

**Copy this template:**

```
Write a design document for [FEATURE/SYSTEM] using this template:

## [Feature Name] Design Document

### 1. Problem Statement
- What problem are we solving?
- Who is impacted?
- Success criteria (measurable)

### 2. Proposed Solution
- High-level approach
- Key components
- Data flow

### 3. Technology Stack
- Technologies chosen and why
- Dependencies
- Infrastructure needs

### 4. Performance & Scale
- Expected throughput
- Latency requirements
- Scalability approach

### 5. Monitoring & Alerting
- Key metrics
- Alert conditions
- Dashboard plan

### 6. Testing Strategy
- Unit testing approach
- Integration testing
- Performance testing

### 7. Rollout Plan
- Phase 1: [Limited]
- Phase 2: [Expanded]
- Phase 3: [Full]
- Rollback procedure

### 8. Risks & Mitigations
- Technical risks
- Operational risks
- Timeline risks

### 9. Open Questions
- Unresolved questions
- Decisions needed

---

Context about this feature:
[DESCRIBE WHAT YOU'RE BUILDING]

Requirements:
- [REQUIREMENT 1]
- [REQUIREMENT 2]
- [REQUIREMENT 3]

Technical constraints:
- [CONSTRAINT 1]
- [CONSTRAINT 2]
```

---

### STRUCTURED - TEST CASES

**Copy this template:**

```
Generate comprehensive test cases for [FEATURE/FUNCTION] using this structure:

## Test Plan: [Feature Name]

### 1. Happy Path Tests
| Test Case | Input | Expected Output | Why Important |
|-----------|-------|-----------------|---------------|
| [Test 1]  | [In]  | [Out]          | [Reason]      |
| [Test 2]  | [In]  | [Out]          | [Reason]      |

### 2. Edge Case Tests
| Test Case | Input | Expected Output | Why Important |
|-----------|-------|-----------------|---------------|
| [Test 1]  | [In]  | [Out]          | [Reason]      |

### 3. Error Handling Tests
| Test Case | Input | Expected Error | Why Important |
|-----------|-------|----------------|---------------|
| [Test 1]  | [In]  | [Error]        | [Reason]      |

### 4. Performance Tests
| Test Case | Input Volume | Max Time | Why Important |
|-----------|--------------|----------|---------------|
| [Test 1]  | [Volume]     | [Time]   | [Reason]      |

### 5. Integration Tests
| Test Case | Dependencies | Expected Behavior | Why Important |
|-----------|--------------|-------------------|---------------|
| [Test 1]  | [Deps]       | [Behavior]        | [Reason]      |

---

Function to test:
[PASTE FUNCTION OR DESCRIBE FEATURE]

Requirements:
- [REQ 1]
- [REQ 2]
```

---

### ABCD - FEATURE DEVELOPMENT

**Copy this template:**

```
I want you to use ABCD Clarification Mode for this task.

Work autonomously when the path is clear, but stop and present ABCD options 
(A/B/C/D) whenever you encounter:
- Ambiguous requirements
- Technical decisions with tradeoffs
- Design choices affecting architecture
- Edge cases needing strategy

For each decision:
1. Present 4 options (Conservative, Balanced, Alternative, Edge case)
2. Make a recommendation with reasoning
3. Wait for my input
4. Continue with my choice

Task: [DESCRIBE WHAT YOU WANT BUILT]

Requirements:
- [REQUIREMENT 1]
- [REQUIREMENT 2]
- [REQUIREMENT 3]

Context:
- Team: [TEAM SIZE AND SKILLS]
- Tech stack: [CURRENT TECHNOLOGIES]
- Timeline: [DEADLINE OR CONSTRAINTS]
- Priorities: [SPEED/QUALITY/COST TRADEOFFS]
```

**Example - Filled In:**

```
I want you to use ABCD Clarification Mode for this task.

Work autonomously when the path is clear, but stop and present ABCD options 
whenever you encounter ambiguity or decisions with tradeoffs.

Task: Build automated data quality checks for Data Products platform

Requirements:
- Check 500+ data products daily
- Detect schema drift, missing data, outliers
- Alert product owners when issues found
- Run checks without impacting production pipelines
- Generate daily quality report for leadership

Context:
- Team: 4 data engineers (strong Python, some Spark experience)
- Tech stack: Python, Airflow, PostgreSQL, Kafka
- Timeline: MVP in 2 weeks, full system in 6 weeks
- Priorities: Reliability > Speed > Cost (quality checks are critical)
```

---

## 🎯 SCENARIO-SPECIFIC TEMPLATES

### KAFKA CONSUMER ISSUES

```
My Kafka consumer [DESCRIBE PROBLEM].

Let's debug step by step:
1. What are common Kafka consumer issues related to [SYMPTOM]?
2. Which matches my setup: [DESCRIBE YOUR SETUP]
3. What's the specific configuration fix?

Consumer configuration:
[PASTE CONSUMER CONFIG]

Error:
[PASTE ERROR]

Context:
- Topic has [MESSAGE SIZE] messages
- Consume [FREQUENCY]
- Consumer group: [GROUP ID]
```

### SQL QUERY OPTIMIZATION

```
This SQL query is slow: [EXECUTION TIME]

Let's optimize step by step:
1. What's the execution plan showing? (Run EXPLAIN if possible)
2. Where are the bottlenecks? (Full table scans? Missing indexes?)
3. What's the optimization strategy?
4. What's the expected improvement?

Query:
[PASTE SQL]

Table sizes:
- [TABLE 1]: [ROW COUNT]
- [TABLE 2]: [ROW COUNT]

Execution plan:
[PASTE EXPLAIN OUTPUT IF AVAILABLE]
```

### AIRFLOW DAG DEBUGGING

```
My Airflow DAG [DESCRIBE PROBLEM].

Let's debug step by step:
1. What Airflow issues cause [SYMPTOM]?
2. Which matches my DAG configuration?
3. What's the fix?

DAG code:
[PASTE DAG CODE]

Logs:
[PASTE RELEVANT LOGS]

Airflow version: [VERSION]
```

### API INTEGRATION ISSUES

```
Integrating with [API NAME], getting [ERROR].

Let's diagnose step by step:
1. What does this error typically mean?
2. What am I sending that causes it?
3. What should I send instead?

My request:
[PASTE REQUEST CODE]

API response:
[PASTE RESPONSE]

API documentation: [LINK OR PASTE RELEVANT DOCS]
```

---

## 💡 PRO TIPS

### Making Templates Work Better:

**1. Be Specific**
Bad: "Code is broken"
Good: "Kafka consumer times out after 30 seconds on messages >5MB"

**2. Include Context**
- What changed recently?
- When does it happen?
- What have you tried?

**3. Paste Relevant Info**
- Error logs (not just "got an error")
- Configuration (actual values)
- Code snippets (the relevant parts)

**4. State Your Goal**
- "Need this to process 1000/sec" (not just "make it faster")
- "Must complete in 8 hour window" (not just "too slow")

**5. Mention Constraints**
- Team skills ("team knows Python, not Scala")
- Timeline ("need this by Friday")
- Existing tech ("must work with our PostgreSQL setup")

---

## 📊 TRACKING YOUR WINS

After using a template, track:

```
Date: [TODAY]
Template used: [WHICH ONE]
Problem: [WHAT YOU WERE SOLVING]
Time before AI: [ESTIMATE]
Time with AI: [ACTUAL]
Time saved: [DIFFERENCE]
Quality: [BETTER/SAME/WORSE]
Will use again: [YES/NO]
```

**Example:**
```
Date: 2025-11-11
Template used: Chain of Thought - Debugging
Problem: Kafka consumer timeouts
Time before AI: 45 minutes typical debugging
Time with AI: 8 minutes (5 min prompt + 3 min implement fix)
Time saved: 37 minutes
Quality: Better (found root cause vs. guessing)
Will use again: YES
```

---

## 🚀 NEXT STEPS

1. **Pick one template** that matches your current problem
2. **Copy it** to your AI tool (Copilot/Claude/ChatGPT)
3. **Fill in the blanks** with your specifics
4. **Run it**
5. **Track the time saved**
6. **Share win** in Slack #ai-prompt-engineering

**Don't try to learn all templates at once. Master one. Then another. Then another.**

---

## 📞 HELP & FEEDBACK

**Having issues?**
- Slack #ai-prompt-engineering
- Ask teammate who's used it
- Check `/troubleshooting/` docs

**Found a better version?**
- Submit PR with improvement
- Share in Slack
- We'll update for everyone

**Template not working?**
- Make sure you filled in ALL the blanks
- Check if you're using right template for problem
- Try adding more context

---

**Document Status:** Living - Last updated 2025-11-11  
**Next:** After using templates, check `/week-1/DAILY-PRACTICE.md` for more exercises  
**Maintainer:** Joseph Lopez  
**Feedback:** Slack #ai-prompt-engineering
