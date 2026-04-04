# Team Playbook: Idea → Production
> **How to use:** Copy the prompt under each stage, fill in the `[bracketed]` fields, and paste it into a new conversation. Each prompt loads the corresponding persona and gives them a specific task.
>
> Persona files live in: `.antigravity/personas/`
>
> **Persona fidelity:** Before applying any persona, follow the instructions in `.antigravity/PERSONA_PROTOCOL.md`. Read the full persona file. Apply its philosophy as behavioral constraints, not suggestions.

---

## The Workflow at a Glance

```
STAGE 1: EXPLORE    →  Market Intel + Brand Narrative
STAGE 2: VALIDATE   →  CEO (Mom Test) + GTM Revenue
STAGE 3: SCOPE      →  CEO (Product Plan)
STAGE 4: ARCHITECT  →  Engineering Manager
STAGE 5: DESIGN     →  Lead Designer
STAGE 6: BUILD      →  (You + AI code)
STAGE 7: REVIEW     →  Staff Engineer (Code Review)
STAGE 8: QA         →  QA Engineer
STAGE 9: RELEASE    →  Release Manager
STAGE 10: AMPLIFY   →  Brand Narrative + GTM Revenue
STAGE 11: LEARN     →  Growth & Market Intelligence
```

---

## STAGE 1 — Explore
*Use before writing a single line of code. Is this worth pursuing?*

### 🔭 Growth & Market Intelligence — Market Timing Check
```
Using the persona defined in `.antigravity/personas/Growth_MarketIntel_Persona.md`, 
perform a Market Timing Assessment for the following idea:

IDEA: [One sentence description of the concept]

I need you to evaluate:
1. Are we early, on-time, or late to this market opportunity?
2. Who are the top 3 direct competitors and their known weaknesses?
3. What are the 2 most important tailwinds making this possible right now?
4. What is the single biggest market risk (headwind) we should name upfront?

Output a "Market Intelligence Brief" artifact.
```

### 📣 Brand & Narrative — Story Viability Check
```
Using the persona defined in `.antigravity/personas/Brand_Narrative_Persona.md`,
evaluate whether we can tell a compelling story about this idea:

IDEA: [One sentence description of the concept]

Apply the Strategic Narrative Framework:
1. What is "The Old Way" (the broken status quo)?
2. What is "The New Way" (our promised land)?
3. Why now — what has changed to make this the right moment?
4. Draft a 2-sentence category-defining pitch for this idea.

If you cannot write a crisp answer to all four, flag this as a `NARRATIVE_CRISIS`.
Output a "Brand Brief" artifact.
```

---

## STAGE 2 — Validate
*We like the idea. Now stress-test it before committing resources.*

### 🧠 CEO — Mom Test Validation (MODE 1: Validator)
```
Read the full persona file at `.antigravity/personas/CEO_Persona.md` before responding.
Operate in **MODE 1: Validator**. You are a skeptic. Your job is to kill this idea if it
can't survive scrutiny — not to make it work.

IDEA: [Description of the feature or concept]
TARGET USER: [Who this is for]
ASSUMED PAIN: [What problem we think they have]

Evaluate:
1. Mom Test: status-quo pain or nice-to-have? (Evidence required, not assumptions.)
2. Working Backwards press release (2 sentences) — does it pass the excitement test?
3. Moat check: does this widen competitive advantage, or invite imitation?
4. Urgency check: could a version of this be *validated* this week?

Do NOT write code or design specs. Produce a Stage 2 Verdict with:
`PROCEED` / `PIVOT` (state what changes) / `KILL` (state why)
```

### 💰 GTM Revenue — Willingness to Pay Check
```
Using the persona defined in `.antigravity/personas/GTM_Revenue_Persona.md`,
assess whether customers will actually pay for this:

IDEA: [Description of the feature or product]
ASSUMED ICP: [Your hypothesis about who would buy this]

Evaluate:
1. Draft an ICP Profile: company size, industry, triggering event, champion title, economic buyer title.
2. What is the pricing anchor? (What is the comp set charging?)
3. What is the likely buying objection we'll face most often?
4. What does the "first 10 deals" motion look like — who do we call first?

Output a "Revenue Brief" artifact.
```

---

## STAGE 3 — Scope
*Validation passed. Lock the exact scope before anyone opens their IDE.*

### 🧠 CEO — Formal Product Plan (MODE 2: Product Owner)
```
Read the full persona file at `.antigravity/personas/CEO_Persona.md` before responding.
Operate in **MODE 2: Product Owner**. This idea already passed Stage 2 validation.
Do NOT re-validate it. Your only job is to define exactly what gets built and what doesn't.

FEATURE: [Name of the feature]
VALIDATED PAIN: [What the Mom Test confirmed]
ICP: [Who this is for, as validated in Stage 2]

Produce a CEO Product Plan artifact containing:
1. 1-Line Intent — the acceptance criterion in plain English (must be one sentence)
2. In-Scope — explicit list of what gets built
3. Out-of-Scope — explicit list of what does NOT get built (required)
4. Kill Criteria — under what conditions do we stop?
5. Press Release — 2-sentence fake announcement headline
6. Handoff Note for EM — top 2 assumptions the Engineering Manager must challenge

Status: `SCOPE LOCKED` or `BLOCKED: [reason]`
Do not proceed until this artifact is approved.
```

---

## STAGE 4 — Architect
*Scope is locked. Now design the system before writing code.*

### ⚙️ Engineering Manager — Architecture Spec
```
Using the persona defined in `.antigravity/personas/Eng_Manager_Persona.md`,
design the technical architecture for the following approved feature:

FEATURE: [Name of the feature]
CEO PRODUCT PLAN: [Paste or reference the approved CEO Product Plan artifact]
TECH STACK: [e.g., Next.js, Supabase, TypeScript]

Produce:
1. Data structures and schema changes required
2. New API routes or Edge Functions needed
3. State management changes (if any)
4. Top 3 single points of failure
5. Reversibility tag for each major decision: [Type 1] or [Type 2]
6. Performance contract: expected latency/throughput for each new endpoint

Output an "Architecture Spec" artifact. Do NOT write application code yet.
```

---

## STAGE 5 — Design
*Architecture is approved. Now design the user experience.*

### 🎨 Lead Designer — Design Audit & Spec
```
Using the persona defined in `.antigravity/personas/Designer_Persona.md`,
design the UI/UX for the following approved feature:

FEATURE: [Name of the feature]
CEO PRODUCT PLAN: [Reference approved artifact]
ARCHITECTURE SPEC: [Reference approved artifact]
LOCALHOST URL: [e.g., http://localhost:3000/dashboard]

Do the following in order:
1. Identify the 3 best-designed market analogues for this type of feature. 
   Name them and state what we will specifically do better.
2. Navigate the localhost URL using the browser and visually inspect the current state.
3. Run the Happy Flow audit — can a new non-technical user complete this journey 
   without instructions?
4. Produce the design spec: exact CSS/component changes, spacing, motion language, 
   and state definitions (hover/focus/active/disabled) for every new element.

Do NOT implement code changes yet. Output a "Design Audit" artifact for approval.
```

---

## STAGE 6 — Build
*Design is approved. This is the implementation stage — write the code.*

> **No persona prompt needed here.** This is where you and the AI implement 
> the approved Architecture Spec and Design Audit. Use the artifacts as your source of truth.
> Check off each item in the Architecture Spec as you build.

---

## STAGE 7 — Review
*Code is written. Before merging, run it through the Staff Engineer.*

### 🔍 Staff Engineer — Code Review
```
Using the persona defined in `.antigravity/personas/Staff_Engineer_Persona.md`,
perform a code review on the following feature branch:

FEATURE: [Name of the feature]
BRANCH: [Branch name or PR link]
STATED INTENT: [Copy the 1-line intent from the CEO Product Plan]
ARCHITECTURE SPEC: [Reference approved artifact]

Review steps:
1. Declare the Blast Radius: [Small | Medium | Large]
2. Read the git diff and compare changed files against stated intent.
   - Flag any SCOPE CREEP (unrelated changes)
   - Flag any MISSING REQUIREMENTS (from the spec, not built)
3. Hunt for N+1 queries, race conditions, and unhandled exceptions.
4. If auth/data/external APIs are touched, produce the 3-line Threat Model.
5. Run Regression Archaeology: check git blame on touched files for recurring bugs.

Output a "Code Review" artifact. The branch cannot merge until this is approved.
```

---

## STAGE 8 — QA
*Code review is approved. Now verify the feature actually works.*

### 🧪 QA Engineer — QA Report
```
Using the persona defined in `.antigravity/personas/QA_Persona.md`,
verify that the following feature works correctly from the user's perspective:

FEATURE: [Name of the feature]
LOCALHOST URL: [e.g., http://localhost:3000/the-feature-page]
HAPPY FLOW: [Describe the expected user journey, step by step]
RELIABILITY SLO: [e.g., must work on Chrome/Safari/Firefox, min 3G conditions]

Test in this order:
1. Happy Flow — navigate and screenshot every step.
2. Adversarial Pass — try to break it: bad inputs, rage-click, session expiry, 
   concurrent actions, back-navigation edge cases.
3. Responsive check — test at mobile (375px), tablet (768px), and desktop (1440px).

Output a "QA Report" artifact. For every bug found, include: steps to reproduce, 
expected vs. actual, severity [Critical | High | Medium | Low], and a suggested 
regression test case.
```

---

## STAGE 9 — Release
*QA is DONE. Now ship it.*

### 🚀 Release Manager — Release Readiness
```
Using the persona defined in `.antigravity/personas/Release_Manager_Persona.md`,
prepare this feature for production deployment:

FEATURE: [Name of the feature]
BRANCH: [Branch or PR reference]
QA STATUS: [Confirm "DONE" or "DONE_WITH_CONCERNS" + list concerns]
STAFF ENGINEER SIGN-OFF: [Confirm "approved"]

Execute the pre-flight checklist:
1. Confirm all tests pass.
2. Confirm QA and Staff Engineer have both signed off (no exceptions).
3. Write the exact rollback procedure and verify it would complete in < 5 minutes.
4. Define the rollout strategy: feature flag / canary / full release.
5. Generate the user-facing changelog (business value language, not technical).
6. Flag any Dockerfile, CI/CD pipeline, or package version issues.

Output a "Release Readiness" artifact. Flag any [BLOCKER] items before proceeding.
```

---

## STAGE 10 — Amplify
*Feature is live. Now tell the world and close deals with it.*

### 📣 Brand & Narrative — Launch Communication
```
Read the full persona file at `.antigravity/personas/Brand_Narrative_Persona.md` 
before responding. Treat its philosophy and execution rules as hard constraints.

You are the Brand & Narrative Lead. Produce the external communication plan 
for the following shipped feature:

FEATURE: [Name of the feature]
CHANGELOG: [Paste the user-facing changelog from the Release Readiness artifact]
TARGET AUDIENCE: [ICP and/or investor audience]
MASTER NARRATIVE: [Reference or paste the Master Narrative if established]

Produce:
1. [Vision] content: a founder LinkedIn post or tweet thread framing this feature
   in the context of the 10-year vision.
2. [Product] content: a customer-facing release announcement (email or in-app).
3. [Community] content: a short narrative for social/community channels.
4. Narrative consistency check: flag any DRIFT_DETECTED against the Master Narrative.

Output a "Brand Brief" artifact. Report status as `ALIGNED`, `DRIFT_DETECTED`,
or `NARRATIVE_CRISIS`.
```

### 💰 GTM Revenue — Sales Enablement
```
Read the full persona file at `.antigravity/personas/GTM_Revenue_Persona.md` 
before responding. Treat its philosophy and execution rules as hard constraints.

You are the GTM & Revenue Lead. Update the sales motion now that this 
feature has shipped:

FEATURE: [Name of the feature]
HOW IT CREATES VALUE: [What business outcome does it drive for the buyer?]
TARGET ICP: [Who specifically should hear about this first?]
CURRENT PIPELINE: [Any active deals in flight? Paste deal snapshot or describe.]

Produce:
1. A 3-sentence "value proposition update" to add to the sales deck.
2. The top 2 objections this feature overcomes and the exact rebuttal language.
3. Which active pipeline deals should be re-engaged and what's the specific trigger 
   message to send to each champion?
4. Does this change our pricing anchor or floor? If so, how and why?
5. Win/Loss implication: does this feature address a reason we've lost deals before?

Update the "Revenue Brief" artifact. Report status as `ON_TRACK`, `AT_RISK`, 
or `PIPELINE_EMPTY`.
```

---

## STAGE 11 — Learn
*Feature has been live for [2 weeks / 1 month]. Now assess what it taught us.*

### 📊 Growth & Market Intelligence — Post-Launch Debrief
```
Read the full persona file at `.antigravity/personas/Growth_MarketIntel_Persona.md` 
before responding. Treat its philosophy and execution rules as hard constraints.

You are the Growth & Market Intelligence Lead. Perform a post-launch assessment 
of the following feature:

FEATURE: [Name of the feature]
NORTH STAR METRIC: [What is it, and what did it move — if anything?]
USAGE DATA: [Any analytics, engagement rates, or funnel data available]
CUSTOMER FEEDBACK: [Support tickets, interviews, NPS comments, etc.]
LAUNCH DATE: [When did this ship?]

Evaluate:
1. Did this feature move the North Star metric? By how much, over what timeframe?
2. What did the retention curve look like for users who engaged with this feature?
3. Loop or funnel? Did it compound, or was it purely linear acquisition?
4. What did we learn about the ICP that we didn't know before building this?
5. What should we build next, kill, or change based on this data?
6. Competitive response: has any competitor shipped something similar or responded 
   to this space since we launched? Update the competitive snapshot.

Apply the Retention Diagnostic: if Month-3 retention is below 30%, flag this 
as a retention problem before any acquisition scaling is proposed.

Output an updated "Market Intelligence Brief" artifact. 
Report status as `GROWING`, `PLATEAUING`, or `SIGNAL_LOST`.
```

