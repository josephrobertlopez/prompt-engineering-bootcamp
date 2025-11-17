# Extraction Notes

**Domain**: Priorities (Accenture FY26)
**Source Materials**:
- Prez/FY26_Accenture_Priorities_Guide.txt
- Prez/Priority_Builder_Agent_Prompt.txt
- Prez/FY26_Priorities_FINAL.csv

**Date**: 2025-11-17

---

## Q1: What Stays Constant?

*Items that remain the same across all instances in this domain*

1. **4 Strategic Categories**
   - Description: Every employee must set ONE priority in EACH category
   - Categories: (1) Client Value Creation, (2) AI Enablement, (3) Great Place to Work for Reinventors, (4) Community
   - Maps to: knowledge-base.md section "Domain Structure → Categories"

2. **Priority Structure (6 Required Fields)**
   - Description: Every priority must have these components
   - Fields: Priority Description, Metrics (1-3), Value/Expected Outcome, ABCD Reflection, Status, Reviewer
   - Maps to: knowledge-base.md section "Domain Structure → Priority Fields"

3. **ABCD Reflection Framework**
   - Description: Standard template for documenting accomplishments
   - Framework: A (Accomplishments), B (Business Impact), C (Challenges Overcome), D (Development & Learning)
   - Maps to: knowledge-base.md section "Frameworks → ABCD Reflection"

4. **Metric Types (28 predefined options)**
   - Description: Standard set of metrics to choose from
   - Categories: 24 non-financial + 4 financial metrics
   - Examples: AI Proficiency, Client Partnership, Innovation, On Time/On Budget Delivery
   - Maps to: knowledge-base.md section "Domain Structure → Available Metrics"

5. **Reflection Writing Best Practices (10 principles)**
   - Description: Guidelines that apply to all reflection writing
   - Examples: Be specific, quantify impact, use STAR method, update quarterly
   - Maps to: knowledge-base.md section "Best Practices → Reflection Writing"

---

## Q2: What's Unique to This Instance?

*Elements that change per specific use case*

1. **Individual Employee's Priorities (4 specific goals)**
   - Description: What THIS employee chooses to accomplish in each category
   - Example 1: "Implement AI-powered data analytics solution for key client" (Client Value Creation)
   - Example 2: "Earn Azure AI Engineer certification and use Copilot daily" (AI Enablement)
   - Maps to: specification.md section "Functional Requirements → Priority Descriptions"

2. **Selected Metrics (1-3 per priority)**
   - Description: Which metrics from the 28 options apply to this priority
   - Example 1: Priority 1 uses "High Quality Deliverables / Client Delivery"
   - Example 2: Priority 2 uses "AI Proficiency / Skills" + "Skills/Specializations/Learning"
   - Maps to: specification.md section "Key Entities → Selected Metrics"

3. **Specific ABCD Reflections (Personal accomplishments)**
   - Description: Individual's unique achievements, impact, challenges, learning
   - Example 1: "Reduced client reporting from 5 days to 2 days (60% improvement)"
   - Example 2: "Navigated stakeholder resistance through 8 workshops demonstrating ROI"
   - Maps to: specification.md section "User Stories → Document Progress"

4. **Target Values/Outcomes (Measurable goals)**
   - Description: What success looks like for this specific priority
   - Example 1: "Deployed solution reducing client reporting time by 60%"
   - Example 2: "Complete 3 AI certifications by Q2"
   - Maps to: specification.md section "Success Criteria → Measurable Outcomes"

---

## Q3: How Do I Execute This Systematically?

*Repeatable process/workflow for using this system*

### Workflow Steps

1. **Step 1: Category Selection & Priority Definition**
   - Input: Knowledge of role, responsibilities, strategic goals
   - Output: 4 priority descriptions (one per category)
   - Example from materials: "Implement AI-powered data analytics solution for key client" → Client Value Creation category

2. **Step 2: Metric Selection & Value Definition**
   - Input: Priority description from Step 1
   - Output: 1-3 metrics + expected outcome/value statement
   - Example from materials: Priority "Implement AI solution" → Metric "High Quality Deliverables" → Value "60% reporting time reduction"

3. **Step 3: Execution & Regular Documentation**
   - Input: Active work on priorities throughout the year
   - Output: Quarterly ABCD reflection updates
   - Example from materials: "Update reflections quarterly... document in ABCD format"

4. **Step 4: Manager Review & Iteration**
   - Input: Draft priorities + reflections
   - Output: Approved priorities, feedback incorporated
   - Example from materials: "Discuss with manager during 1:1s... align with manager before finalizing"

5. **Step 5: Year-End Finalization**
   - Input: Completed priorities with full ABCD reflections
   - Output: Final documentation for performance review
   - Example from materials: "Complete final reflections before year-end review cycle"

### Maps to implementation-plan.md
- Phase structure: Setup (categories) → Define (priorities) → Execute (work + document) → Review (manager) → Finalize (year-end)
- Decision points: Category mapping, metric selection, manager alignment

---

## 3-File Mapping Summary

| 3-Question Framework | File | Key Content from Materials |
|---------------------|------|---------------------------|
| Q1: What stays constant? | knowledge-base.md | 4 categories, ABCD framework, 28 metric types, 6 required fields, 10 reflection best practices |
| Q2: What's unique? | specification.md | Individual's 4 priorities, selected metrics (1-3 per priority), specific ABCD reflections, target values |
| Q3: How to execute? | implementation-plan.md | 5-step workflow: Select categories → Choose metrics → Execute & document quarterly → Manager review → Year-end finalize |

---

## Notes

- **Observation**: The priority system is highly structured (4 categories, 28 metrics, ABCD framework) which makes "what stays constant" very clear and extensive
- **Challenge**: Distinguishing between generic reflection best practices (constant) vs individual accomplishments (unique) - resolved by categorizing principles as constant, specific achievements as unique
- **Recommendation for exercises**: Have participants first identify the 4 categories (constant), then practice mapping a fictional priority to one category (unique), then outline the 5-step workflow (process)
