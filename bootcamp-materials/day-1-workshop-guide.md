# DAY 1 WORKSHOP GUIDE
## 2-Hour Hands-On Prompt Engineering Training

**Goal:** Learn 4 core techniques + ABCD Mode, leave with working templates  
**Format:** Live exercises with real Capital One scenarios  
**Deliverable:** 3+ prompt templates you'll use Monday

---

## ⏰ WORKSHOP TIMELINE

### Setup (5 min) - Before we start
- Everyone has laptop + AI tool ready (Copilot/Claude/ChatGPT)
- Open template doc for copy-paste
- Quick intro round: Name, role, one problem you want AI to solve

### Hour 1: The 4 Core Techniques (60 min)
- 15min: Chain of Thought (Debugging)
- 15min: ReAct (Research & Analysis)
- 15min: Tree of Thoughts (Architecture Decisions)
- 15min: Structured Templates (Code Reviews)

### Hour 2: Production Integration (55 min)
- 30min: ABCD Clarification Mode (Orchestration)
- 20min: Live Practice (Your actual problems)
- 5min: Wrap-up + Next Steps

---

## 🎯 TECHNIQUE 1: CHAIN OF THOUGHT (15 MIN)

### The Problem You Face Daily:
Code breaks. You ask AI "fix this." It gives generic suggestions that don't work.

### The Solution:
Add "Let's think step by step:" or "Let's debug this systematically:" before your question.

### Why It Works:
Forces AI to show its reasoning, catches wrong assumptions early, teaches you the logic.

---

### ❌ BAD PROMPT EXAMPLE:

```
This Kafka consumer keeps timing out. Fix it.

[paste code]
```

**Result:** Generic timeout suggestions (increase timeout value, check network, restart service)

**Problem:** Doesn't diagnose ROOT CAUSE, you're guessing which fix to try

---

### ✅ GOOD PROMPT EXAMPLE:

```
This Kafka consumer keeps timing out after exactly 30 seconds when processing large messages. 
Let's debug this step by step:

1. What are the common causes of 30-second Kafka consumer timeouts?
2. Which causes match these symptoms: works fine for small messages, fails on 5MB+ messages
3. What's the specific configuration fix for the identified root cause?

Here's the consumer code:
[paste code]

Here's the error log:
[paste relevant error]
```

**Result:** 
```
Let me analyze step by step:

1. Common 30-second timeout causes:
   - max.poll.interval.ms exceeded (default 300000ms)
   - session.timeout.ms too low (default 10000ms)
   - Network issues
   - Slow message processing

2. Your symptoms (works on small, fails on large messages) point to:
   max.poll.interval.ms - Your processing takes longer than the poll interval,
   so Kafka thinks consumer died and triggers rebalance

3. Specific fix:
   Increase max.poll.interval.ms to match your processing time:
   
   consumer.properties:
   max.poll.interval.ms=600000  # 10 minutes instead of 5
   
   OR optimize processing to finish faster within current window
```

**Impact:** Found root cause in 2 minutes vs. 30 minutes trial-and-error

---

### 🏋️ LIVE EXERCISE (5 min):

**Your Scenario:** SDP dataset validation script returns random 404 errors on some datasets

**Your Task:** Write a Chain of Thought prompt to debug this

**Template:**
```
[Describe the problem with symptoms]

Let's debug this step by step:
1. [Question about possible causes]
2. [Question about pattern matching]
3. [Question about specific fix]

[Paste code]
[Paste error logs]
```

**Timer starts... GO!**

---

### 💡 SOLUTION EXAMPLE:

```
My SDP dataset validation script returns 404 errors on approximately 15% of datasets, 
but not consistently - same dataset passes sometimes, fails other times.

Let's debug this step by step:
1. What causes intermittent 404s in REST API calls?
2. Which cause matches pattern: same endpoint, different results, ~15% failure rate?
3. What's the fix for that specific cause?

Code:
def validate_dataset(dataset_id):
    response = requests.get(f"{SDP_URL}/datasets/{dataset_id}")
    return response.status_code == 200

Error pattern:
Dataset abc-123: Pass, Pass, Fail (404), Pass
Dataset def-456: Pass, Pass, Pass, Pass
Dataset ghi-789: Fail (404), Fail (404), Pass, Fail (404)
```

**AI Response:**
```
1. Intermittent 404 causes:
   - Eventually consistent system (data not yet replicated)
   - Race condition during dataset creation
   - Load balancer routing to different nodes with different data
   - Rate limiting returning wrong status code
   
2. Pattern match: 15% failure, same dataset fails then passes
   → Eventually consistent system. Some SDP nodes don't have dataset yet.
   
3. Fix: Add retry logic with exponential backoff:

def validate_dataset(dataset_id, max_retries=3):
    for attempt in range(max_retries):
        response = requests.get(f"{SDP_URL}/datasets/{dataset_id}")
        if response.status_code == 200:
            return True
        if response.status_code == 404 and attempt < max_retries - 1:
            time.sleep(2 ** attempt)  # 1s, 2s, 4s
            continue
        return False
    return False
```

**Time Saved:** 1 hour debugging → 5 minutes with targeted fix

---

### 📝 CHAIN OF THOUGHT - KEY TAKEAWAYS:

**When to use:**
- Debugging errors (production issues, failed tests)
- Understanding complex code (inherited legacy system)
- Analyzing performance problems (slow queries, high memory)

**Template structure:**
```
[Problem description with symptoms]

Let's [debug/analyze/understand] this step by step:
1. [Diagnostic question]
2. [Pattern matching question]
3. [Solution question]

[Code/logs/data]
```

**Pro tips:**
- Include error logs, not just code
- Mention what you've already tried
- Be specific about symptoms (when, how often, which conditions)

**Copy this template → Save for Monday**

---

## 🔬 TECHNIQUE 2: REACT (15 MIN)

### The Problem You Face Daily:
Need to research technical decisions (which library? what pattern? how to implement?) but AI gives you one opinion without showing reasoning.

### The Solution:
Use ReAct pattern: **Think → Act → Observe → Repeat**

---

### ❌ BAD PROMPT EXAMPLE:

```
Should we use Airflow or Prefect for our new data pipeline?
```

**Result:** "I recommend Airflow because it's more mature and widely adopted."

**Problem:** No research shown, no comparison, can't verify reasoning

---

### ✅ GOOD PROMPT EXAMPLE:

```
I need to choose between Airflow and Prefect for a new data pipeline project.

Requirements:
- 50+ pipelines eventually
- Some Python-only engineers on team
- Need good monitoring/alerting
- Deploy on Kubernetes

Use ReAct pattern to research this:

Think: What criteria matter most for this decision?
Act: Compare Airflow vs Prefect on those criteria
Observe: Which tool better fits our requirements?
Think: What are the tradeoffs?
Act: Check community adoption and support
Observe: What's the recommendation with reasoning?
```

**Result:**
```
Think: Key criteria are: learning curve (Python-only team), scalability (50+ pipelines),
       Kubernetes deployment, monitoring capabilities, community support

Act: Comparing both:

Airflow:
- Learning curve: Steeper (DAG syntax, complex)
- Scalability: Excellent, battle-tested at scale
- K8s: KubernetesExecutor built-in
- Monitoring: Robust UI, integrates with Prometheus
- Community: Massive (Apache project, 10+ years)

Prefect:
- Learning curve: Gentler (Pythonic, decorators)
- Scalability: Good, newer but growing
- K8s: Prefect Kubernetes Agent
- Monitoring: Modern UI, cloud-native
- Community: Smaller but active

Observe: Both handle requirements. Airflow = proven at scale but harder to learn.
         Prefect = easier for Python devs but less battle-tested.

Think: Given "Python-only engineers", learning curve matters. Given "50+ pipelines eventually",
       we need proven scalability.

Act: Check if ease-of-use difference is significant enough to outweigh battle-testing.
     Research: Teams with Python-only devs report 2-3 week ramp-up for Airflow vs
     1 week for Prefect. Both scale fine to 50-100 pipelines.

Observe: 1-2 week training difference vs years of production hardening.

Recommendation: **Airflow**
- Invest in training (2-3 weeks)
- Benefits: Proven at scale, massive community, better long-term support
- Mitigation: Create team-specific templates to reduce learning curve
- Consider: Prefect if team velocity matters more than long-term scalability
```

**Impact:** Informed decision in 10 minutes with full reasoning vs. 3 days of research

---

### 🏋️ LIVE EXERCISE (5 min):

**Your Scenario:** Choosing between storing intermediate pipeline results in S3 vs database

**Your Task:** Write a ReAct prompt to research this decision

**Template:**
```
[Describe decision to make]

Requirements:
- [List 3-5 key requirements]

Use ReAct pattern:
Think: [What matters most?]
Act: [Compare options]
Observe: [What did comparison reveal?]
Think: [What are tradeoffs?]
Act: [Check additional factors]
Observe: [Final recommendation]
```

**Timer starts... GO!**

---

### 💡 SOLUTION EXAMPLE:

```
Should we store intermediate pipeline results in S3 or PostgreSQL database?

Requirements:
- 1,500 datasets processed daily
- Results are 10-50MB JSON each
- Kept for 7 days then purged
- Need to query occasionally for debugging
- Cost-conscious

Use ReAct pattern:

Think: Key factors are storage cost, query capability, retention management, performance

Act: Compare S3 vs PostgreSQL:

S3:
- Cost: $0.023/GB/month (~$1,150/month for 50TB)
- Query: Athena possible but slow
- Retention: Lifecycle policies automatic
- Performance: High throughput, eventual consistency

PostgreSQL:
- Cost: RDS storage $0.115/GB/month (~$5,750/month) + instance costs
- Query: SQL, fast, indexed
- Retention: Manual cleanup jobs needed
- Performance: Good for structured queries, limited throughput

Observe: S3 is 5x cheaper and has built-in lifecycle management.
         PostgreSQL has better query capability.

Think: Do we actually need fast queries? Or just occasional debugging?

Act: Check actual query frequency in similar systems.
     Finding: Intermediate results queried ~5 times per month for debugging.

Observe: Paying 5x more for query capability used 5 times/month is wasteful.

Recommendation: **S3 with Athena**
- Store in S3 (80% cost savings)
- Use Athena for rare queries (pay per query)
- S3 lifecycle policy handles 7-day retention automatically
- Trade slower query speed for significant cost savings

Cost impact: Save ~$55K annually
```

---

### 📝 REACT - KEY TAKEAWAYS:

**When to use:**
- Technical decisions (choose framework, pattern, tool)
- Research tasks (best practices, competitive analysis)
- Requirements analysis (what do we actually need?)

**Template structure:**
```
[Decision to make]

Requirements:
- [List key constraints]

Use ReAct pattern:
Think: [Analysis]
Act: [Research action]
Observe: [What was learned]
[Repeat as needed]

Final recommendation: [Decision with reasoning]
```

**Pro tips:**
- List requirements upfront (constraints matter)
- Compare on same criteria (apples-to-apples)
- Check assumptions with data (don't just theorize)
- Quantify tradeoffs when possible (cost, time, risk)

**Copy this template → Save for Monday**

---

## 🌳 TECHNIQUE 3: TREE OF THOUGHTS (15 MIN)

### The Problem You Face Daily:
Architecture decision with multiple valid approaches. Need to compare options systematically.

### The Solution:
Tree of Thoughts: Generate 3+ distinct approaches, compare pros/cons, pick best fit.

---

### ❌ BAD PROMPT EXAMPLE:

```
How should we handle failed dataset migrations in the SDP migration tool?
```

**Result:** "You should retry with exponential backoff and log failures."

**Problem:** Only one approach suggested, no alternatives considered, what if that doesn't fit?

---

### ✅ GOOD PROMPT EXAMPLE:

```
We're building an SDP migration tool for 1,500 datasets. Some will fail validation.

Context:
- Migrations run overnight (8-hour window)
- Business wants report of what succeeded/failed by morning
- Some failures are transient (retry works), some permanent (bad data)
- Team needs to manually fix permanent failures

Generate 3 distinct approaches for handling failures, then recommend best fit:

Approach A: [Conservative/safe option]
Approach B: [Balanced/pragmatic option]
Approach C: [Aggressive/optimized option]

For each approach, provide:
- How it works
- Pros
- Cons
- Best fit for

Then recommend which approach for our context with reasoning.
```

**Result:**
```
APPROACH A: Fail-Fast Strategy
How it works:
- Stop entire process on first failure
- Generate detailed failure report
- Manual intervention required to continue

Pros:
- Safest approach
- No risk of cascading failures
- Full visibility before proceeding

Cons:
- Could block 1,499 successful migrations for 1 failure
- Doesn't meet overnight completion requirement
- Inefficient use of maintenance window

Best fit for: High-risk migrations where any failure needs immediate attention

---

APPROACH B: Continue-with-Logging Strategy
How it works:
- Log failed datasets to database/file
- Continue processing remaining datasets
- Generate summary report at end (succeeded/failed counts)
- Retry transient failures 2-3 times before marking as failed

Pros:
- Maximizes successful migrations in window
- Clear failure report by morning
- Distinguishes transient vs permanent failures via retry

Cons:
- Permanent failures sit until manual fix
- Need good logging infrastructure
- Could mask systemic issues if many fail

Best fit for: Large batch operations where most succeed, failures are independent

---

APPROACH C: Multi-Phase Strategy
How it works:
Phase 1: Validate all datasets (fast, no migration)
Phase 2: Migrate validated datasets
Phase 3: Auto-retry failed validations
Phase 4: Report permanently failed items

Pros:
- Catches bad data before expensive migration
- Multiple retry opportunities
- Clearest separation of failure types

Cons:
- Most complex to implement
- Takes longest overall (4 phases)
- May not fit in 8-hour window

Best fit for: When validation is much cheaper than migration, need maximum reliability

---

RECOMMENDATION: Approach B - Continue-with-Logging

Reasoning:
1. Must complete overnight (8-hour window) → Rules out Approach A (fail-fast)
2. 1,500 datasets suggests most will succeed → Approach B handles this well
3. Morning report requirement → Approach B provides clear summary
4. Manual fixes needed anyway → Logging sufficient, don't need multi-phase complexity

Implementation:
- Retry transient failures 3x with exponential backoff (1s, 2s, 4s)
- Log to: dataset_id, timestamp, error_type, error_message, retry_count
- Morning report: "1,450 migrated, 50 failed (30 transient gave up, 20 bad data)"
- Team triages 50 failures, fixes bad data, re-runs those specifically

Expected outcome: ~97% success rate overnight, clear action items by 8am
```

**Impact:** Confident architecture decision in 15 minutes vs. 2-day debate

---

### 🏋️ LIVE EXERCISE (5 min):

**Your Scenario:** Deciding how to handle data validation in the Data Products pipeline

**Options to consider:**
- Validate before ingestion
- Validate after ingestion
- Validate on read
- Multi-stage validation

**Your Task:** Generate Tree of Thoughts comparing 3 approaches

**Template:**
```
[Describe decision context]

Context:
- [List key constraints]

Generate 3 distinct approaches:

Approach A: [Option]
- How it works: [Description]
- Pros: [Benefits]
- Cons: [Drawbacks]
- Best fit for: [When to use]

Approach B: [Option]
[Same structure]

Approach C: [Option]
[Same structure]

Recommendation: [Choice] because [reasoning based on your context]
```

**Timer starts... GO!**

---

### 💡 SOLUTION EXAMPLE:

```
How should we handle data validation in the Data Products pipeline?

Context:
- Ingesting data from 10+ source systems
- Data quality varies by source (some dirty, some clean)
- Downstream consumers need reliable data
- Processing 100GB daily
- Team is 4 engineers

Generate 3 distinct approaches:

APPROACH A: Pre-Ingestion Validation (Fail Invalid Data)
How it works:
- Validate at ingestion boundary
- Reject invalid records immediately
- Only clean data enters system

Pros:
- System only contains valid data
- Simple downstream logic
- Failures visible immediately

Cons:
- Data loss (rejected records gone unless logged)
- May block entire batch for few bad records
- Source systems might not fix data quickly

Best fit for: Critical systems where invalid data causes failures

---

APPROACH B: Post-Ingestion Validation (Quarantine Pattern)
How it works:
- Ingest all data raw
- Run validation as separate step
- Move invalid records to quarantine table
- Flag for manual review

Pros:
- No data loss (everything captured)
- Can process valid data while quarantine gets fixed
- Historical record of data quality issues

Cons:
- Downstream must check quarantine or trust flags
- Storage cost for invalid data
- Manual intervention loop needed

Best fit for: When data source quality varies, need audit trail

---

APPROACH C: Lazy Validation (Validate on Read)
How it works:
- Ingest everything
- Validate when downstream requests data
- Return validated subset or error

Pros:
- Fastest ingestion
- Different consumers can have different rules
- No upfront validation cost

Cons:
- Downstream gets inconsistent results
- Validation logic duplicated across consumers
- Debug issues harder (when did bad data enter?)

Best fit for: Exploratory/research systems, flexible requirements

---

RECOMMENDATION: Approach B - Post-Ingestion Validation (Quarantine Pattern)

Reasoning:
1. "Data quality varies by source" → Need to capture everything for audit
2. "Downstream needs reliable data" → Can't serve invalid data (rules out Approach C)
3. "10+ source systems" → Some will have issues, can't block pipeline (rules out Approach A)
4. "4 engineers" → Need manageable manual review process

Implementation:
- Raw table: Ingest everything with source_system, timestamp
- Validation rules table: System-specific rules
- Valid table: Records passing validation
- Quarantine table: Records failing validation + reason
- Daily report: Quarantine size by source system, SLA for fixes

Expected outcome: 
- 0% data loss
- Downstream sees only valid data
- Clear accountability per source system
- 2-3 hours/week manual quarantine review vs constant pipeline debugging
```

---

### 📝 TREE OF THOUGHTS - KEY TAKEAWAYS:

**When to use:**
- Architecture decisions (system design, pattern choice)
- Complex tradeoff decisions (speed vs quality, cost vs features)
- Comparing multiple valid approaches
- Need to justify decision to stakeholders

**Template structure:**
```
[Decision context]

Context:
- [Key constraints and requirements]

Generate 3 distinct approaches:

Approach A: [Conservative option]
- How it works: [Description]
- Pros: [Benefits]
- Cons: [Drawbacks]
- Best fit for: [When to use]

[Repeat for B and C]

Recommendation: [Choice] because [reasoning tied to your specific context]
```

**Pro tips:**
- Make approaches genuinely different (not just variations)
- Tie pros/cons to your specific context
- Quantify tradeoffs when possible
- "Best fit for" helps recognize similar situations later
- Document decision for future reference

**Copy this template → Save for Monday**

---

## 📋 TECHNIQUE 4: STRUCTURED TEMPLATES (15 MIN)

### The Problem You Face Daily:
Code reviews, documentation, status updates take forever and quality varies.

### The Solution:
Create consistent structured templates that AI fills in, ensuring quality and saving time.

---

### ❌ BAD PROMPT EXAMPLE:

```
Review this PR.

[paste PR diff]
```

**Result:** "Looks good! Ship it."

**Problem:** No depth, missed issues, inconsistent quality

---

### ✅ GOOD PROMPT EXAMPLE:

```
Review this PR using the following structured template:

## Code Review Template

### 1. Correctness
- Does the code do what the PR description claims?
- Are there logical errors or edge cases missed?
- Are error conditions handled properly?

### 2. Performance
- Any obvious performance issues? (N+1 queries, unnecessary loops)
- Resource usage concerns? (memory leaks, connection pools)

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
- Future extensibility considered?

### 6. Required Changes (Blocking)
[List must-fix issues before merge]

### 7. Suggested Improvements (Non-blocking)
[List nice-to-have improvements]

### 8. Approval Status
[Approve / Request Changes / Comment]

---

PR Description:
[paste PR description]

Code Changes:
[paste diff]
```

**Result:**
```
## Code Review: SDP Dataset Validation PR

### 1. Correctness ✓
- Code correctly validates datasets against schema
- Edge case handled: empty datasets return validation error (good)
- Error condition handled: API timeout returns specific error message

⚠️ Issue: Line 45 - division by zero possible if `total_records == 0`

### 2. Performance ✓
- Validation runs in parallel (good use of ThreadPoolExecutor)
- No N+1 issues detected
- Connection pooling used correctly

💡 Suggestion: Consider batch validation API if available (reduce API calls by 90%)

### 3. Security ✓
- API key passed via environment variable (good)
- Input sanitized before logging
- No sensitive data in error messages

### 4. Maintainability ⚠️
- Code readable overall
- Missing docstrings on 3 functions (validation_rules, parse_response, handle_error)
- Test coverage: 85% (meets requirement)

🔧 Required: Add docstrings before merge

### 5. Architecture ✓
- Fits validation pattern used in other pipelines
- Dependency on `requests` library appropriate
- Extensible design (easy to add new validation rules)

### 6. Required Changes (Blocking)
1. Fix division by zero on line 45:
   ```python
   if total_records > 0:
       success_rate = valid_records / total_records
   else:
       success_rate = 0.0
   ```

2. Add docstrings to functions (validation_rules, parse_response, handle_error)

### 7. Suggested Improvements (Non-blocking)
1. Consider batch validation API to reduce latency
2. Add retry logic for transient API failures
3. Log validation duration for performance monitoring

### 8. Approval Status
**Request Changes** - Fix division by zero and add docstrings, then approve.

Estimated fix time: 15 minutes
```

**Impact:** Thorough review in 5 minutes vs. 30 minutes manual review, consistent quality

---

### 🏋️ LIVE EXERCISE (5 min):

**Your Task:** Create a structured template for writing Data Engineering design docs

**Requirements to cover:**
- Problem statement
- Proposed solution
- Data flow
- Technology choices
- Monitoring/alerting
- Rollout plan

**Template format:**
```
## [Document Type] Template

### 1. [Section Name]
- [What to address]
- [What to address]

### 2. [Section Name]
[Repeat]

[Usage instructions]
```

**Timer starts... GO!**

---

### 💡 SOLUTION EXAMPLE:

```
## Data Engineering Design Doc Template

### 1. Problem Statement
- What problem are we solving?
- Who is impacted and how?
- What happens if we don't solve it?
- Success criteria (measurable)

### 2. Current State
- Existing system/process description
- Pain points and limitations
- Data volumes and performance metrics
- Dependencies on other systems

### 3. Proposed Solution
- High-level approach
- Why this solution over alternatives?
- Key components and their responsibilities
- Data flow diagram (ASCII or link)

### 4. Data Model
- Input data sources and schemas
- Intermediate data structures
- Output data format
- Data retention and lifecycle

### 5. Technology Stack
- Primary technologies and versions
- Why chosen over alternatives?
- Dependencies and libraries
- Infrastructure requirements (compute, storage, network)

### 6. Performance & Scale
- Expected throughput (records/sec, GB/day)
- Latency requirements
- Scalability approach (vertical/horizontal)
- Bottlenecks and mitigation strategies

### 7. Monitoring & Alerting
- Key metrics to track
- Alert conditions and thresholds
- Dashboards and visualization
- On-call runbook link

### 8. Testing Strategy
- Unit testing approach
- Integration testing
- Performance/load testing
- Data quality validation

### 9. Rollout Plan
- Phase 1: [Limited rollout]
- Phase 2: [Expanded rollout]
- Phase 3: [Full production]
- Rollback procedure if issues arise

### 10. Risks & Mitigations
- Technical risks and mitigation plans
- Operational risks and owner assignments
- Timeline risks and contingencies

### 11. Open Questions
- [Unresolved technical questions]
- [Need input from: team/person]
- [Decisions needed by: date]

---

Usage Instructions:
1. Copy this template
2. Paste into new doc
3. Fill in each section with specifics
4. Use AI to help draft sections:
   "Using the following design doc template, draft the 'Proposed Solution' section for [describe your project]"
5. Review and refine
6. Share for feedback
```

---

### 📝 STRUCTURED TEMPLATES - KEY TAKEAWAYS:

**When to use:**
- Repetitive tasks (code reviews, docs, reports)
- Quality standards needed (consistency across team)
- Onboarding new team members (templates teach standards)
- Complex tasks (templates ensure nothing missed)

**Template structure:**
```
## [Task Name] Template

### 1. [Section]
- [Checklist item]
- [Checklist item]

[Repeat sections]

---

Usage: [How to use with AI]
```

**Pro tips:**
- Start simple, evolve template based on use
- Get team buy-in (collaborative templates work better)
- Version your templates (track improvements)
- Share successful templates across team
- AI can help generate initial template based on examples

**Copy this template → Save for Monday**

---

## 🔗 TECHNIQUE 5: ABCD CLARIFICATION MODE (30 MIN)

### Now We Orchestrate All 4 Techniques

You've learned:
- Chain of Thought (debugging)
- ReAct (research)
- Tree of Thoughts (architecture)
- Structured Templates (consistency)

**ABCD Mode = How to combine them in real workflows**

---

### The Problem:
When building something complex, you don't use just one technique. You use all 4 at different points. How do you know when to switch?

### The Solution:
ABCD Clarification Mode is a workflow pattern that:
1. Works autonomously when path is clear
2. Stops at ambiguity
3. Presents 4 options (A/B/C/D)
4. Makes recommendation
5. Waits for your decision
6. Continues with your choice

**It's like having a senior engineer pairing with you who knows when to ask vs when to just do.**

---

### ABCD Mode Structure:

```
When you encounter ambiguity during implementation:

---
Clarification Question [N]: [State the specific decision point]

Recommended: Option [X] - [One-line summary]

Reasoning: [2-3 sentences explaining why based on context, best practices, tradeoffs]

| Option | Description |
|--------|-------------|
| A | [Conservative/safe approach] |
| B | [Balanced/pragmatic approach] |
| C | [Alternative/creative approach] |
| D | [Edge case/contrarian approach] |

Reply with: option letter (e.g., "B"), "yes"/"recommended", or custom answer.
---
```

---

### Real Example: Building SDP Migration Tool

**You say:** "Build automation to migrate 1,500 datasets from old SDP to new SDP"

**AI starts working...** (creates migration script, dataset validation, logging)

**AI encounters ambiguity:** "How should I handle datasets that fail validation?"

**AI presents ABCD:**

```
---
Clarification Question 1: Dataset validation failure handling

Recommended: Option B - Log failures, continue with others

Reasoning: You mentioned 1,500 datasets and overnight processing window. 
Stopping on first failure would block remaining datasets. Logging allows 
batch processing now with manual review of failures later, balancing 
speed with safety.

| Option | Description |
|--------|-------------|
| A | Stop entire process on first failure (safest) |
| B | Log failures, continue with others (pragmatic) |
| C | Auto-retry failed datasets 3x before logging (resilient) |
| D | Skip validation entirely, migrate all (fastest) |

Reply with: option letter, "yes"/"recommended", or custom answer.
---
```

**You say:** "B"

**AI continues...** (implements logging, continues migration)

**AI encounters next ambiguity:** "Performance is slow, 3 minutes per dataset = 75 hours total"

**AI presents ABCD using Chain of Thought:**

```
---
Clarification Question 2: Migration performance optimization

Recommended: Option C - Parallel processing with rate limiting

Reasoning: Current sequential processing = 75 hours (exceeds 8-hour window). 
Let's think through options step by step:
- Option A: No optimization keeps us at 75 hours (misses deadline)
- Option B: Async without limits risks overwhelming SDP API
- Option C: Controlled parallelism gets benefits of async while respecting API
- Option D: Batch API unknown availability

Option C balances speed gains with API stability.

| Option | Description |
|--------|-------------|
| A | Keep sequential processing, run over multiple nights (safe, slow) |
| B | Full async parallelism, no rate limiting (fast, risky) |
| C | Parallel processing with rate limiting (balanced) |
| D | Use batch API if available (optimal but uncertain) |

Reply with: option letter, "yes"/"recommended", or custom answer.
---
```

**You say:** "C but check if batch API exists first"

**AI continues...** (uses ReAct to research batch API, finds it doesn't exist, implements Option C)

**Result:** Migration tool built in 45 minutes with YOUR architecture decisions at key points

---

### 🏋️ LIVE EXERCISE (15 min):

**Scenario:** You're building a Data Products feature that needs to aggregate data from multiple sources

**Your Task:** Practice ABCD Mode with your partner

**Roles:**
- Person A: You're the AI (present ABCD decisions)
- Person B: You're the developer (make decisions)

**Instructions:**
1. Person B describes feature to build
2. Person A "works" and hits 3 ambiguous points:
   - How to handle missing data from some sources?
   - How to refresh aggregated data (schedule vs on-demand)?
   - How to handle sources with different update frequencies?
3. Person A presents ABCD for each decision point
4. Person B makes decisions
5. Switch roles and repeat with different scenario

**Timer starts... GO!**

---

### ABCD Mode Integration with 4 Techniques:

**ABCD Mode USES your 4 techniques:**

1. **Uses Tree of Thoughts** for the 4 options (A/B/C/D)
2. **Uses Chain of Thought** in reasoning ("Let's think through...")
3. **Uses ReAct** when researching options ("Think: X, Act: Research, Observe: Y")
4. **Uses Structured Templates** for consistent presentation format

**Example - AI researching which option to recommend:**

```
[AI internal process - not shown to user]

Think: User needs to handle missing source data. What are the patterns?
Act: Research common approaches (skip source, use defaults, fail loudly, mark as incomplete)
Observe: Each has different tradeoffs for data quality vs availability
Think: User's context mentioned "downstream consumers need reliable data"
Act: Analyze which approach maintains reliability
Observe: Marking as incomplete preserves data quality signal
Recommendation: Option B - Use defaults but mark record as incomplete

[Then AI presents ABCD to user]
```

**This is why ABCD Mode is powerful - it orchestrates all techniques automatically.**

---

### 📝 ABCD MODE - KEY TAKEAWAYS:

**When to use:**
- Complex implementation tasks
- Multiple decisions needed
- Want AI to work autonomously but maintain control
- Building something with your team (collaborative)

**How to activate:**
```
I want you to use ABCD Clarification Mode for this task.

Work autonomously when the path is clear, but stop and present 
ABCD options (A/B/C/D) whenever you encounter:
- Ambiguous requirements
- Technical decisions with tradeoffs
- Design choices affecting architecture
- Edge cases needing strategy

For each decision:
1. Present 4 options (Conservative, Balanced, Alternative, Edge case)
2. Make a recommendation with reasoning
3. Wait for my input
4. Continue with my choice

Task: [Describe what you want built]

Context:
- [Key requirements]
- [Constraints]
- [Team/tech context]
```

**Pro tips:**
- Provide good context upfront (helps AI recommendations)
- You can override recommendations ("B but change X")
- AI learns from your choices (adjust future recommendations)
- Works great for pair programming
- Document decisions for team reference

**Copy this template → Save for Monday**

---

## 🎯 HOUR 2: LIVE PRACTICE (20 MIN)

### Now Use These Techniques on YOUR Real Problems

**Instructions:**
1. Think of a problem you're facing RIGHT NOW in your work
2. Pick the technique that fits:
   - Debugging something? → Chain of Thought
   - Research needed? → ReAct
   - Architecture decision? → Tree of Thoughts
   - Repetitive task? → Structured Template
   - Complex project? → ABCD Mode

3. Write the prompt using the template
4. Run it through AI tool
5. Share result with group

**Let's go around the room - what problems are you tackling?**

[10 minutes: Individual work]

[10 minutes: Share results and discuss]

---

## 📊 WRAP-UP & NEXT STEPS (5 MIN)

### What You Learned Today:

✅ **Chain of Thought** - Systematic debugging  
✅ **ReAct** - Research with reasoning  
✅ **Tree of Thoughts** - Compare approaches  
✅ **Structured Templates** - Consistent quality  
✅ **ABCD Mode** - Orchestrate all techniques  

### What You're Taking Away:

📝 5 prompt templates ready to use Monday  
💡 Clear framework for when to use each technique  
🎯 One problem solved during practice session  

---

### Your Week 1 Challenge:

**Goal:** Use each technique at least once this week

**Track in Slack #ai-prompt-engineering:**
- Monday: Use Chain of Thought to debug something
- Tuesday: Use ReAct to research a decision
- Wednesday: Use Tree of Thoughts for architecture choice
- Thursday: Use Structured Template for code review
- Friday: Share wins, time saved, and lessons learned

**Accountability:**
- Post to Slack when you use a technique
- Share the time saved
- Help teammates who ask questions

---

### Resources Available:

📁 **Templates folder** - All copy-paste prompts  
📚 **Week 1 guide** - Daily exercises  
💬 **Slack channel** - Questions and support  
🎥 **Recordings** - Re-watch sections  
📝 **Metrics tracker** - Document improvements  

---

### Success Metrics for This Week:

By Friday, you should have:
- [ ] Used all 4 techniques at least once
- [ ] Saved 2+ hours cumulative (tracked with timestamps)
- [ ] Helped 1 teammate
- [ ] Contributed 1 improvement to templates
- [ ] Feel more confident with AI tools (self-rate 1-10)

---

### Questions?

**Common questions:**

Q: "What if the AI gives bad advice?"  
A: That's why you're making decisions, not blindly accepting. ABCD Mode puts YOU in control.

Q: "Will this work with Copilot/ChatGPT/Claude?"  
A: Yes! These patterns work across all AI tools.

Q: "How do I know I'm using the right technique?"  
A: Follow the decision tree in `/reference/TECHNIQUE-SELECTOR.md`

Q: "What if I get stuck?"  
A: Slack #ai-prompt-engineering - we're all learning together.

---

### Final Thought:

**This is Day 1 of your prompt engineering journey.**

You now have:
- Framework for thinking about AI collaboration
- Practical techniques that work today
- Templates to get started immediately
- Team support to keep improving

**The goal isn't perfection, it's progress.**

Use one technique Monday. Document the win. Share it with team. Repeat.

**By end of week, you'll be 2x faster. By end of month, 10x.**

---

### See You in Week 1!

📅 **Next touchpoint:** Friday standup (share wins)  
📊 **Track progress:** Slack updates throughout week  
🎯 **Goal:** 5+ technique uses per person this week  

**Now go save some time. 🚀**

---

**Workshop Complete!**

Document Status: Living - Last updated 2025-11-11  
Maintainer: Joseph Lopez  
Feedback: Slack #ai-prompt-engineering
