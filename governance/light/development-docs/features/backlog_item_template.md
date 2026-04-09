# Feature Backlog Item Template

Use this template for items in `01-feature-backlog.md`.

## Required Fields

- Source:
- Status: deferred
- Priority Assumption:
  - `near`, `later`, or `far`
- Expected Order:
  - what should happen before this item is considered
- Blockers:
  - design decisions or capabilities that must exist first
- Experience Tie:
  - which part of `design/00-ideal-experience.md` this item affects
- Thickness:
  - `light`, `medium`, or `heavy`
- Design Impact:
  - `local`, `cross-cutting`, or `architectural`
- Current Design Constraint:
  - what present-day implementation must avoid assuming because this deferred item may change the design
- Supporting Feature:
  - path if a roadmap-adjacent supporting feature exists, otherwise `none`
- Why Not In Roadmap Yet:
  - why it stays deferred for now

## Rules

- Do not leave backlog items as one-line reminders.
- A heavy or architectural backlog item must be rich enough that later AI work does not mistake it for a minor feature.
- If `Thickness` is `heavy` or `Design Impact` is `architectural`, mirror the constraint in the active design docs before adjacent implementation proceeds.
