# Instructor Notes: First-Principles Prompt Engineering Workshop

## Overview

**Duration**: 2 sessions × 90 minutes (3 hours total)
**Format**: Discovery-based learning with hands-on exercises
**Delivery**: In-person or virtual (optimized for both)
**Max participants**: 20 (ideal: 12-15 for peer review logistics)

---

## Pre-Workshop Preparation

### 1 Week Before

- [ ] Send participant pre-work email with:
  - FY26 Priorities Guide PDF
  - Interview questions TXT file
  - Blank template files (knowledge-base.md, specification.md, implementation-plan.md)
  - Markdown editor recommendations (VS Code, Obsidian, Typora)

- [ ] Confirm room setup (if in-person):
  - Tables for group work (clusters of 3-4)
  - Projector + screen for slides
  - Whiteboard for ad-hoc diagrams
  - Power outlets for laptops

- [ ] Test technology:
  - Presentation displays correctly (check Mermaid diagrams render)
  - Screen sharing works (if virtual)
  - Breakout rooms configured (if virtual)

### Day Before

- [ ] Review participant backgrounds (adjust examples if needed)
- [ ] Prepare printed handouts (optional but recommended):
  - 3-Question Framework diagram
  - FY26 Priorities Guide excerpts
  - Validation checkpoint checklist
- [ ] Load all materials on backup device (USB drive)

---

## SESSION 1: Framework Introduction (90 minutes)

### Timing Breakdown

| Segment | Duration | Slides | Notes |
|---------|----------|--------|-------|
| Welcome + Journey Overview | 5 min | 1-3 | Energy: High. Set positive tone |
| Problem framing | 5 min | 4 | Validate their pain points |
| Exercise setup | 5 min | 5 | Ensure everyone has materials |
| 3-Question Framework intro | 10 min | 6-9 | Core concept - go slow |
| **Micro-break #1** | 2 min | 10 | Enforce strictly (attention curve) |
| Live demo: Deconstruction | 15 min | 11-12 | **Critical segment - see notes** |
| Hands-on exercise | 30 min | 13 | Circulate + coach individuals |
| Validation checkpoint | 8 min | 14 | Facilitate pair reviews |
| Common mistakes review | 5 min | 15 | Use real examples from room |
| **Micro-break #2** | 2 min | 16 | Quick reset before wrap |
| Session recap + homework | 3 min | 17-18 | Preview Session 2 |

**Total**: 90 minutes

### Critical Facilitation Notes

#### Slide 6: 3-Question Framework (Mermaid Diagram)

**What to emphasize:**
- Point to each question while explaining
- Use hand gestures to reinforce flow (raw materials → questions → files)
- Pause after each question for "aha" moments

**Common participant confusion:**
- "What if something is both constant AND unique?"
  - **Answer**: If it applies to ALL instances → knowledge-base. Even one exception → specification.
- "Can implementation-plan.md reference specification.md?"
  - **Answer**: Yes! That's the hierarchy. Knowledge-base ← Spec ← Implementation.

**Time trap**: This slide can easily take 15-20 min if you let discussion spiral. Cap at 10 min, promise to revisit during live demo.

#### Slides 11-12: Live Demo (Deconstruction)

**Preparation:**
- Have FY26 guide open in PDF reader
- Blank `knowledge-base.md` file ready in editor (split screen)
- Practice this demo 3x before workshop (muscle memory critical)

**Demo script** (15 min):

1. **Open PDF** (2 min)
   - "I'm opening this with fresh eyes, pretending I know nothing about FY26 priorities"
   - Scroll through first few pages slowly
   - Think aloud: "I see categories... metrics... examples..."

2. **Ask the 3 questions** (3 min)
   - Pull up blank markdown file
   - Write headings: `## Q1: Constants | ## Q2: Unique | ## Q3: Process`
   - Point at PDF: "This 4-category list - does it change per person?" → No → Q1

3. **Extract constants** (10 min)
   - Copy strategic categories into knowledge-base.md
   - Format as markdown list
   - Add ABCD framework definitions
   - **Critical**: Show yourself re-reading the PDF, going back and forth
   - **Critical**: Make a mistake (e.g., accidentally put an example in constants), then catch it: "Wait, this is John's specific priority - that's Q2, not Q1. Let me move it."

**Why the "mistake" is important**: Participants fear perfection. Modeling error correction builds psychological safety.

**Backup plan**: If demo goes long (>17 min), skip detailed ABCD framework entry. Say "I'll finish this offline" and jump to slide 13.

#### Slides 13-14: Hands-On Exercise + Validation (38 min total)

**Launch (slide 13, 2 min):**
- "You have 30 minutes. I'll give a 5-minute warning."
- "Your goal is NOT to finish perfectly. It's to practice the framework."
- "I'll circulate - raise your hand if stuck."

**During exercise (30 min):**

*Minutes 0-10:* Expect quiet focus. Don't interrupt. Circulate silently, glance at screens to gauge progress.

*Minutes 10-20:* Start answering questions. Common blockers:
- "I don't know where to start" → Point them to Table of Contents in PDF: "What sections appear in every person's priorities?"
- "Is this too detailed?" → "If it helps someone NEW understand the system, include it."

*Minute 25:* "5 minutes left - wrap up your current section."

*Minute 30:* "Pens down. Find a partner for validation."

**Validation checkpoint (slide 14, 8 min):**

*Minute 1-2:* Pair people up (if virtual: breakout rooms of 2)
*Minute 3-5:* Pairs review using 4 questions on slide
*Minute 6-7:* Give feedback (2 stars + 1 wish format)
*Minute 8:* Return to main room, ask for 1-2 volunteers to share a "star" they received

**Facilitation trap**: Participants will want to keep working during validation. Enforce the stop: "Learning happens in the review, not just the doing."

#### Slide 15: Common Mistakes

**How to use this slide:**
- Ask room: "Did anyone accidentally include example data in knowledge-base?" (hands will go up)
- Validate their experience: "That's THE most common mistake. You're in good company."
- Show slide examples
- Ask: "Why is this a problem?" → Let them answer (reinforces learning)

**Optional**: If you noticed a specific mistake during circulation, ask that person if they're comfortable sharing (builds community).

#### Slide 18: Homework

**Framing:**
- "This is optional, but those who practice on a 2nd domain learn 3x faster in Session 2."
- "Recipe example: constant = cooking techniques, unique = your ingredients, execute = recipe steps."
- "If you do it, bring it to Session 2 - we'll do a 2-minute show-and-tell."

**Why optional homework works**: No guilt, but creates aspiration. ~30% will do it, and their insights enrich Session 2.

---

## SESSION 2: Specification + Implementation (90 minutes)

### Timing Breakdown

| Segment | Duration | Slides | Notes |
|---------|----------|--------|-------|
| Recap + session goals | 5 min | 1-3 | Bridge from Session 1 |
| Specification.md intro | 10 min | 4-5 | Structure + anti-patterns |
| Exercise: Build spec | 25 min | 6 | Shorter than Session 1 (faster pace) |
| Anti-patterns review | 5 min | 7-8 | Real examples from room |
| **Micro-break #1** | 2 min | 9 | Quick reset |
| Implementation.md intro | 10 min | 10-12 | Actionable steps emphasis |
| Exercise: Build implementation | 30 min | 13 | Deepest exercise - full workflow |
| Validation: Triangle Test | 5 min | 14 | Handoff simulation |
| Real-world application | 3 min | 15 | Broaden context |
| Peer review circle | 20 min | 16 | Groups of 3, structured |
| Integration issues | 5 min | 17 | Common cross-file problems |
| **Micro-break #2** | 2 min | 18 | Before advanced patterns |
| Advanced patterns | 10 min | 19-21 | Optional depth for fast learners |
| Workshop wrap-up | 5 min | 22-25 | Celebration + reflection |
| Reflection activity | 10 min | 26 | Metacognition consolidation |
| Feedback + Q&A | 5 min | 27-28 | Close strong |

**Total**: 90 minutes (tighter pacing than Session 1)

### Critical Facilitation Notes

#### Slide 3: The Missing Pieces (Mermaid Diagram)

**Visual technique:**
- Point to the checkmark on knowledge-base.md: "You built this!"
- Trace arrows: "Today we complete the triangle"
- Emphasize bidirectional flow: "These files talk to each other"

**Engagement hook**: Ask "Who looked at their knowledge-base.md between sessions?" (hands up) → "What did you notice?" → Listen for insights, validate them.

#### Slides 6-8: Specification Exercise + Anti-Patterns

**Common participant struggle**: Wanting to copy-paste from knowledge-base instead of referencing it.

**Coaching technique**: When you see someone duplicating content, ask:
- "If the knowledge-base changes, would you have to update this file?"
- "Could you link to the knowledge-base instead?"

**Example fix** (show on projector if needed):
```markdown
BAD:
## Strategic Categories
1. Client Value - focuses on customer outcomes
2. AI Enablement - ...

GOOD:
## Selected Priorities
From knowledge-base.md Strategic Categories (Section 2):
- Priority 1: Client Value → Increase NPS by 10 points
```

#### Slides 13-14: Implementation Exercise + Triangle Test

**Setup (slide 13, 2 min):**
- "This is your most complex exercise. 30 minutes."
- "Goal: Someone with ZERO context could follow your steps."
- "Include inputs, outputs, validation for each step."

**During exercise (30 min):**

*Minutes 0-15:* Silent focus period (no interruptions unless hands raised)

*Minute 15:* Midpoint check-in: "Who has at least 3 steps drafted?" (gauge progress)

*Minutes 15-25:* Active coaching. Look for:
- Vague verbs ("review" → what specifically?)
- Missing validation ("How do you know step 2 succeeded?")
- No prerequisites listed

*Minute 25:* "5 minutes. Finish your current step, doesn't need to be perfect."

**Triangle Test (slide 14, 5 min):**
- Pair up participants
- Person A gives their 3 files to Person B
- Person B attempts to understand what to do (no talking)
- After 2 min: "Could you execute this? What's missing?"
- Person B shares feedback
- **Swap roles** (B shares with A)

**Why this works**: Forces empathy. Writers realize what they assumed vs. what they documented.

#### Slide 16: Peer Review Circle (20 min)

**Formation (2 min):**
- Groups of 3 (if virtual: breakout rooms)
- Assign roles: Person A presents first, B second, C third
- Set timer: 6 min per person (strict)

**Structure per person (6 min × 3 = 18 min):**
- Min 1-3: Presenter shares screen, explains their 3-file system
- Min 4-5: Reviewers ask questions
- Min 6: Reviewers give feedback (2 stars + 1 wish each)

**Facilitation:**
- Visit each group briefly (in-person) or join breakout rooms randomly (virtual)
- Listen for rich feedback moments - note them for whole-group debrief

**Debrief (2 min):**
- Return to main room
- "What's one star you gave someone?" (3-4 quick shares)
- "What's one wish you received that really helped?" (2-3 shares)

#### Slides 19-21: Advanced Patterns

**Pacing decision point:**

If running behind (85+ min used), **skip slides 19-21**. Say:
- "We're out of time for advanced patterns. I've included them in your slide deck for self-study."
- Jump directly to slide 22 (wrap-up)

If on time, **speed through** at high level:
- Slide 19 (Templating): "Once you have a system, turn spec into a template."
- Slide 20 (Conditionals): "For complex domains, add IF/THEN logic to implementation."
- Slide 21 (Validation): "Embed rules from knowledge-base into your process."
- "These are advanced. Try them on project #2, not today."

**Why this works**: Gives fast learners something to aspire to without overwhelming everyone.

#### Slide 26: Reflection Activity (10 min)

**Critical for learning consolidation:**

*Minutes 1-5:* Silent individual writing
- Give participants the 4 reflection questions
- "Write answers for yourself - you won't have to share unless you want to."

*Minutes 6-10:* Optional sharing
- "Who discovered a big insight?" (2-3 shares)
- "What's your immediate application?" (2-3 shares)
- "Any unanswered questions?" (address 1-2)

**Facilitation tip**: The silence is uncomfortable but essential. Don't fill it with talking. Let them think.

---

## Materials Checklist

### For Participants (send 1 week before)

- [ ] FY26 Priorities Guide (PDF)
- [ ] Interview questions (TXT)
- [ ] Blank template files:
  - knowledge-base.md
  - specification.md
  - implementation-plan.md
- [ ] Markdown editor setup guide
- [ ] Workshop agenda + Zoom link (if virtual)

### For Instructor (bring to session)

- [ ] Laptop with presentations loaded
- [ ] Backup slides on USB drive
- [ ] Printed handouts (3-Question Framework diagram)
- [ ] Timer/phone for tracking micro-breaks
- [ ] Whiteboard markers (if in-person)
- [ ] Sample completed file system (for demo)
- [ ] Participant roster (for breakout room assignments)

---

## Troubleshooting Guide

### Technical Issues

**Mermaid diagrams don't render:**
- Backup: Have static PNG versions of diagrams ready
- Show diagram on slide, explain verbally while PNG displays

**Participant can't open markdown files:**
- Direct them to online editor: https://stackedit.io
- Pair them with tech-savvy neighbor for session

**Screen sharing fails (virtual):**
- Pre-record demo video as backup
- Play video instead of live demo

### Engagement Issues

**Participant finishes exercise early (15+ min remaining):**
- Ask them to review their work using validation checkpoint questions
- Suggest: "Apply the framework to a 2nd domain (recipe, API docs)"
- Pair them with slower participant as peer coach (if they're willing)

**Participant is stuck/frustrated:**
- Don't solve it for them - ask discovery questions:
  - "What have you tried so far?"
  - "Which of the 3 questions are you answering right now?"
  - "Can you find a similar example in the FY26 guide?"
- If still stuck after 5 min: Show them 2-3 sentences as a starter, have them continue

**Group is silent during discussions:**
- Use targeted questions: "Sarah, what's one thing you noticed in the demo?"
- Lower stakes: "Quick poll - raise hand if you've made Mistake #1" (then discuss)
- Pair-share first, then whole group (less intimidating)

**Advanced participant challenges framework:**
- Validate their point: "That's a great edge case - what would you propose?"
- Invite them to extend: "Try adding that to your implementation-plan as a conditional rule"
- Defer if disruptive: "Let's discuss that 1:1 after session - I don't want to derail the group"

### Time Management

**Running 10+ minutes behind:**
- Cut "Common Mistakes" slide to 2 min (just show examples, no discussion)
- Reduce final Q&A from 5 min to 2 min
- Skip advanced patterns (slides 19-21) in Session 2
- **Never cut**: Hands-on exercises or micro-breaks (degrades learning)

**Finishing early (10+ min remaining):**
- Extend peer review with "switch partners and review again"
- Open floor: "Show and tell - who built something cool?"
- Advanced topic deep-dive: Pick one advanced pattern, do live demo

---

## Post-Workshop Follow-Up

### Within 24 Hours

- [ ] Send thank-you email with:
  - Link to slide decks (HTML exports)
  - Completed sample file system (reference)
  - Recommended reading: "The Pragmatic Programmer" (Ch. 7 on documentation)
  - Feedback survey link

### Within 1 Week

- [ ] Review survey results
- [ ] Update slides based on feedback
- [ ] Reach out to participants who requested 1:1 coaching
- [ ] Share participant success stories with leadership (if approved)

### Within 1 Month

- [ ] Host optional "Office Hours" session:
  - Participants bring real projects
  - Apply framework live with instructor coaching
  - 60 min, informal format
- [ ] Collect examples of participant-created file systems (with permission)
- [ ] Build case study library for future workshops

---

## Cognitive Science Behind the Design

*This section explains WHY the workshop is structured this way (optional reading for instructors)*

### Miller's Law (7±2 chunks)

Each slide presents 3-7 key points (never more than 9). The 3-Question Framework is deliberately 3 questions (not 5 or 7) to fit comfortably in working memory.

### Attention Curves (Primacy/Recency)

Micro-breaks are placed at 30-40 min intervals to reset attention. Most critical content (3-Question Framework, live demo) is front-loaded in first 30 min when attention is highest.

### Discovery Learning vs. Direct Instruction

Exercises ask participants to extract structure from raw materials (FY26 guide) rather than receiving pre-made templates. This creates deeper understanding and better transfer to new domains.

### Peer Review for Metacognition

Validation checkpoints and peer review circles force participants to articulate their thinking, which consolidates learning. The "Triangle Test" specifically targets empathy for users of their documentation.

### Spaced Repetition

Two 90-min sessions (vs. one 180-min session) allow time between for subconscious processing. Homework (optional) provides additional repetition in a new context.

---

## Customization Guide

### Adapting to Different Audiences

**For technical teams (engineers, data scientists):**
- Replace FY26 Priorities with API documentation or system design doc
- Emphasize implementation-plan.md (they love process details)
- Add advanced pattern: "Validation rules as unit tests"

**For non-technical teams (marketing, HR):**
- Keep FY26 Priorities example (familiar domain)
- Simplify markdown syntax (use rich text editor option)
- Add example: Marketing campaign as knowledge-base/spec/plan

**For executives (short on time):**
- Condense to 1 session (60 min)
- Focus only on 3-Question Framework + knowledge-base exercise
- Position as "strategic thinking tool" not "prompt engineering"

### Virtual vs. In-Person

**Virtual-specific tips:**
- Use chat for "raise hand if..." polls (less awkward than video)
- Pre-assign breakout rooms (don't auto-assign)
- Share timer on screen during exercises (everyone can see countdown)
- Record sessions (with permission) for participants who miss

**In-person advantages:**
- Easier to read room energy (circulate during exercises)
- Whiteboard for ad-hoc diagrams
- Stronger peer connections during breaks

---

## Instructor Self-Assessment

After each workshop, rate yourself (1-5 scale):

- [ ] **Pacing**: Stayed within 90 min per session without rushing
- [ ] **Clarity**: Explained 3-Question Framework in ≤10 min
- [ ] **Engagement**: >80% of participants actively participated
- [ ] **Demo quality**: Live demo felt smooth, included intentional "mistake"
- [ ] **Coaching**: Circulated during exercises, answered ≥5 questions
- [ ] **Safety**: Participants felt comfortable sharing mistakes
- [ ] **Energy**: Maintained enthusiasm from start to finish

**Improvement areas** (if scored ≤3):
- Pacing: Practice with timer, cut less-critical content
- Clarity: Simplify language, use more visual aids
- Engagement: Add more pair-share before whole-group
- Demo: Rehearse 3x before next workshop
- Coaching: Set goal to visit each participant at least once
- Safety: Model vulnerability (share your own learning mistakes)
- Energy: Take breaks between sessions, stay hydrated

---

## Frequently Asked Questions

**Q: What if participants haven't done pre-work?**
A: Build in 5-min "skim the FY26 guide" activity at start of Session 1. Cuts into exercise time but ensures everyone has baseline context.

**Q: Can this be self-paced (no instructor)?**
A: Possible but not recommended. The live demo and peer reviews are critical learning moments that don't work async. If you must: Record demo video, create written self-assessment rubric for exercises.

**Q: How do I handle mixed experience levels (some know markdown, some don't)?**
A: Pair novices with experienced users during exercises. Emphasize: "Markdown syntax is not the goal - structured thinking is."

**Q: What if participants want to use their own project instead of FY26 Priorities?**
A: Encourage it! Say: "Use FY26 for the first exercise to learn the pattern, then apply to your project in exercise 2." Risk: They get stuck in domain complexity. Offer to revert to FY26 if that happens.

**Q: Should I share my own completed file system as a reference?**
A: Yes, AFTER Session 1 ends (not before). Seeing a polished example too early creates "I'll just copy this" behavior instead of discovery.

**Q: How technical should the implementation-plan.md steps be?**
A: Depends on audience. For FY26 example: Mid-level detail (not code, but actionable steps like "Open Workday → Navigate to Priorities section → Click 'Add Priority' button"). Adjust based on participant feedback during exercise.

---

**Version**: 1.0 (2025-11-17)
**Last updated**: Initial creation
**Maintainer**: Workshop development team
