# Projects

This folder contains all ideas that passed Stage 3 scope validation.

Each subfolder is a project that has been formally scoped and approved by the CEO persona.
Every project folder contains the full artifact chain from ideation to production.

## How to Browse

Each project is a subfolder named after the project slug (e.g., `remote-pt-tracker/`). Browse the folder directly to see all active and past projects. Open any project's `_log.md` for a full status brief including current stage, decisions made, and open questions.

> Projects are created automatically during Ideation Mode when an idea clears Stage 3 scope lock.

## Project Artifact Chain

Each project folder contains these files (populated as the project progresses through the playbook):

```
[project-slug]/
  CEO_Product_Plan.md       ← Stage 3  (Scope, kill criteria, press release)
  Architecture_Spec.md      ← Stage 4  (Data structures, API routes, perf contracts)
  Design_Audit.md           ← Stage 5  (UI/UX spec, component changes)
  Build_Brief.md            ← Stage 5  (Durable build brief — scope + arch + design summary for Stage 6)
  Code_Review.md            ← Stage 7  (Blast radius, threat model, drift analysis)
  QA_Report.md              ← Stage 8  (Happy flow + adversarial test results)
  Release_Readiness.md      ← Stage 9  (Sign-offs, rollback plan, changelog)
  _log.md                   ← Running  (All decisions, pivots, and notes)
```

