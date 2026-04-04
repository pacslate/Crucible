---
description: Resume an existing project from where it left off. Reads the project's _log.md to restore full context without requiring the user to re-explain anything.
---

# Resume Workflow

## How to Trigger
This workflow activates when the user:
- Uses `/resume`
- Says something like "let's continue on [project]", "pick up where we left off", "what's the status of [project]?", "resume [project name]"

When triggered, you MUST read this entire file before responding.

---

## Your Role

You are resuming a session mid-stream. The user should feel like they're talking to a co-founder who was in the room last time and remembers everything. **Never ask the user to re-explain context that should exist in the project files.** Do the reading first, ask questions second.

---

## Resume Steps

### Step 1 — Identify the Project

**If the user named a project:** Go directly to Step 2 using that project name.

**If no project was named:**
1. List all folders in `.antigravity/projects/` 
2. Present the list to the user: *"You have [N] active projects: [list]. Which one are we picking up?"*
3. Wait for their selection, then go to Step 2.

---

### Step 2 — Load Project State

Read the following files from `.antigravity/projects/[project-slug]/`:

1. **`_log.md`** — This is your primary briefing doc. Read it in full.
   - Note the **Current Stage**
   - Note the **Stage Sign-Off Tracker** (what's approved, what's pending)
   - Note the **Decisions Log** (what's been locked)
   - Note the **Open Questions** (what still needs answers)
   - Note the **Session History** (what happened last time)

2. **The artifact for the current stage** (if it exists):
   - Stage 3 → `CEO_Product_Plan.md`
   - Stage 4 → `Architecture_Spec.md`
   - Stage 5 → `Design_Audit.md` + `Build_Brief.md`
   - Stage 6 → `Build_Brief.md`
   - Stage 7 → `Code_Review.md`
   - Stage 8 → `QA_Report.md`
   - Stage 9 → `Release_Readiness.md`

---

### Step 3 — Brief the User

Present a concise project status summary in this format:

```
📁 PROJECT: [Project Name]
📍 CURRENT STAGE: Stage [X] — [Stage Name]

✅ COMPLETED:
  - Stage 2: Validated (PROCEED — [1-line reason])
  - Stage 3: Scope locked ("[1-line intent from CEO Product Plan]")
  - [any other completed stages]

⏳ IN PROGRESS:
  - Stage [X]: [What's been done so far, if anything]

❓ OPEN QUESTIONS:
  - [List any unresolved questions from _log.md]

🔜 NEXT ACTION: [What the team does next]
```

Keep this tight — 10 lines max. The user knows their project. This is a status ping, not a recap essay.

---

### Step 4 — Resume

After presenting the status, ask:

*"Ready to continue from Stage [X]? Or is there something specific you want to address first?"*

If they say continue: resume the ideation workflow from the correct stage, using the same conversational facilitation model defined in `ideate.md`.

If they have a specific question or issue: address it, update `_log.md` with the decision or note, then ask again if they want to continue the stage sequence.

---

## Updating `_log.md` During a Resumed Session

Every resumed session should add a new entry to the **Session History** section of `_log.md`:

```markdown
- **[YYYY-MM-DD]:** Resumed at Stage [X]. [Brief summary of what was done/decided. 1-2 sentences.]
```

If any decisions are made during the session, add them to the **Decisions Log**.
If any open questions are resolved, check them off or remove them.
If a stage is completed, update the **Stage Sign-Off Tracker**.

---

## Edge Cases

**If `_log.md` doesn't exist or is empty:**
Tell the user: *"I found the project folder for [name] but the log is empty — it looks like we may not have run the full ideation flow yet. Want me to start from the beginning with `/ideate`, or can you tell me what stage you're at?"*

**If the project folder doesn't exist at all:**
Tell the user: *"I don't see a project folder for '[name]' in `.antigravity/projects/`. It may not have cleared Stage 3 yet. Want to start a fresh ideation session with `/ideate`?"*

**If a required artifact file is missing for the current stage:**
Flag it: *"The [Stage X] artifact ([filename]) appears to be empty. We may need to re-run that stage before proceeding. Want to do that now?"*
