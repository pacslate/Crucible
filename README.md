# Crucible

> **An AI-powered startup team that takes an idea from raw concept to production-ready product.**

Crucible is a prompt engineering system that gives an AI coding assistant (Antigravity) a full founding team of specialized personas. Instead of a single AI giving you generic answers, you get nine distinct experts — each with a specific role, philosophy, and output — working together in a defined process.

The team covers both **inward-facing** work (building the product) and **outward-facing** work (winning the market). Every idea is stress-tested before a line of code is written. Every feature ships with a paper trail.

---

## The Team

### Outward-Facing (Market & Revenue)
| Persona | Role | Owns |
|---|---|---|
| 📊 Growth & Market Intelligence | External Radar | Competitive intel, North Star metrics, market timing, retention |
| 📣 Brand & Narrative | Founder Storyteller | Company story, investor pitch, category creation, launch comms |
| 💰 GTM & Revenue | Revenue Lead | ICP, pipeline, pricing strategy, first 10 deals |

### Inward-Facing (Product & Engineering)
| Persona | Role | Owns |
|---|---|---|
| 🧠 CEO & Product Visionary | Scope & Vision | Mom Test, feature validation, product plan, kill criteria |
| ⚙️ Engineering Manager | System Architecture | Data structures, API design, performance contracts, reversibility |
| 🎨 Lead UI/UX Designer | User Experience | Design system, happy flow, motion language, competitive aesthetics |
| 🔍 Staff Engineer | Code Quality | Code review, blast radius, threat modeling, regression archaeology |
| 🧪 QA Engineer | Product Reliability | Happy flow testing, adversarial testing, reliability SLOs |
| 🚀 Release Manager | Deployment | Pre-flight checks, rollback plans, canary releases, changelogs |

Each persona is defined in `.antigravity/personas/` as a Markdown file with a core philosophy and a specific set of execution rules.

---

## How It Works

### Option A — Conversational Ideation (Recommended)
Just start talking. Say *"I have an idea..."* or type `/ideate`. The AI will automatically run each persona's lens in sequence, ask gate questions between stages, log the session, and create a project folder if the idea clears validation.

**You never have to name a persona or copy a prompt.**

```
You:  "I want to build a tool that helps physical therapists track patient progress remotely."

AI:   [Runs Growth & Market Intel → Brand & Narrative]
      STAGE 1 VERDICT: Market timing is strong. Telehealth tailwind is real...

      Want me to stress-test the idea itself?

You:  "Yes"

AI:   [Runs CEO Mom Test → GTM Revenue]
      STAGE 2 VERDICT: PROCEED. Clear status-quo pain. ICP is mid-size PT clinics...

      Ready to lock the scope? (This will create a project folder.)
```

### Option B — Manual Prompting via the Playbook
For any specific stage, use the pre-built prompt templates in `.antigravity/TEAM_PLAYBOOK.md`. Each prompt is copy-paste ready with `[bracketed]` fields to fill in. Use this when you want to run a single persona on a specific task without going through the full flow.

---

## The Build Lifecycle

```
STAGE 1:  EXPLORE     →  Market timing + story viability
STAGE 2:  VALIDATE    →  Mom Test + willingness to pay       [GATE: PROCEED / PIVOT / KILL]
STAGE 3:  SCOPE       →  Lock exact requirements             [GATE: Project folder created]
STAGE 4:  ARCHITECT   →  System design before any code       [GATE: Spec approved]
STAGE 5:  DESIGN      →  UX/UI spec before implementation    [GATE: Design approved]
STAGE 6:  BUILD       →  Implementation (you + AI)
STAGE 7:  REVIEW      →  Code review, blast radius, threats  [GATE: Engineer sign-off]
STAGE 8:  QA          →  Happy flow + adversarial testing    [GATE: QA sign-off]
STAGE 9:  RELEASE     →  Pre-flight, canary, rollback plan   [GATE: Release approval]
STAGE 10: AMPLIFY     →  Launch comms + sales enablement
STAGE 11: LEARN       →  Post-launch metrics debrief
```

Gates are explicit checkpoints. The AI will not advance past a gate without your confirmation.

---

## File Structure

```
Crucible/
├── README.md                          ← You are here
│
├── .agents/
│   └── workflows/
│       ├── ideate.md                  ← Conversational ideation workflow (/ideate)
│       └── resume.md                  ← Resume an in-progress project (/resume)
│
└── .antigravity/
    ├── TEAM_PLAYBOOK.md               ← Manual prompt templates for all 11 stages
    ├── PERSONA_PROTOCOL.md            ← How to load, embody, and exit a persona (AI instructions)
    │
    ├── personas/
    │   ├── CEO_Persona.md             ← MODE 1: Validator (Stage 2) / MODE 2: Product Owner (Stage 3)
    │   ├── Designer_Persona.md
    │   ├── Eng_Manager_Persona.md
    │   ├── Staff_Engineer_Persona.md
    │   ├── QA_Persona.md
    │   ├── Release_Manager_Persona.md
    │   ├── GTM_Revenue_Persona.md
    │   ├── Brand_Narrative_Persona.md
    │   └── Growth_MarketIntel_Persona.md
    │
    ├── ideation_vat/                  ← Every idea logged, win or lose
    │   └── YYYY-MM-DD_[idea].md
    │
    └── projects/                      ← Ideas that cleared Stage 3
        ├── _log_template.md           ← Template copied to every new project
        └── [project-slug]/
            ├── CEO_Product_Plan.md
            ├── Architecture_Spec.md
            ├── Design_Audit.md
            ├── Build_Brief.md
            ├── Code_Review.md
            ├── QA_Report.md
            ├── Release_Readiness.md
            └── _log.md
```

---

## Getting Started

### 1. Ideate on a new idea
```
/ideate
```
Or just say *"I have an idea I want to think through."*

The AI will guide you through Steps 1–3 conversationally and create a project folder if the idea clears validation.

### 2. Run a specific stage manually
Open `.antigravity/TEAM_PLAYBOOK.md`, find the stage you need, copy the prompt, fill in the `[brackets]`, and paste it into a conversation.

### 3. Continue work on an existing project
```
/resume
```
Or say *"Let's pick up the [project-slug] project."* The resume workflow reads the project's `_log.md` and presents a full status brief instantly — no re-explaining needed.

---

## Design Principles

**Gates before code.** Every feature is validated, scoped, and architecturally designed before implementation begins. No cowboy coding.

**Paper trail by default.** Every decision — including killed ideas — is logged. Future you will thank current you.

**Outward + inward balance.** Most AI dev setups are 100% inward (build faster). Crucible has three personas whose only job is to face the market: competitive intelligence, narrative, and revenue. You build *and* you win.

**Personas are opinionated.** These are not neutral assistants. Each persona has a defined philosophy, a set of heuristics from world-class operators, and the mandate to push back, flag risks, and say "kill it" when warranted.

**Conversational by default, manual when needed.** The `/ideate` workflow is the primary interface. The `TEAM_PLAYBOOK.md` is the escape hatch for surgical, single-stage work.
