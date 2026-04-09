# Features

Use this directory for feature planning artifacts that are not themselves active roadmap documents.

## Rules

- Use `00-feature-index.md` as the feature planning index.
- Keep active implementation phases in `roadmap/`.
- Use `01-feature-backlog.md` as the structured ledger for deferred requests.
- Use `epics/` for planning-ready, experience-linked epics.
- Use `supporting/` only for roadmap-adjacent candidates that are likely to be compared in the next planning window.
- Use `backlog_item_template.md` when adding or rewriting deferred items in `01-feature-backlog.md`.
- Before a feature can drive a roadmap, normalize it using `feature_template.md` or an equivalent structured feature spec.
- Every supporting feature must explain:
- Problem
- Experience contribution
- Why important
- Dependencies
- Acceptance
- Promotion condition
- Validation scenarios
- Failure signals
- Do not leave deferred work as an open roadmap phase.
- Promote a feature into the roadmap only after an explicit planning decision.
- Every backlog item must also record priority, expected order, blockers, experience tie, thickness, design impact, and current design constraints.
- If a backlog item is heavy or architectural, reflect the constraint in the active design docs before freezing adjacent implementation.
