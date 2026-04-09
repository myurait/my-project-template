# Development Documentation Index

This repository contains development-facing project documentation.

## Reading Order

1. `AI_KNOWLEDGE.md`
2. `rules/AI_RUNTIME_RULES.md`
3. `rules/coding-conventions.md`
4. `rules/development-process.md`
5. `knowledge.md`
6. `design/00-ideal-experience.md`
7. `requirements/requirement-discovery-rules.md`
8. `features/00-feature-index.md`
9. `features/epics/`
10. `features/supporting/`
11. `features/01-feature-backlog.md`
12. The active roadmap file at the root of `roadmap/`, if one exists
13. `design/01-project-charter.md`
14. `design/02-architecture.md`
15. `decisions.md`
16. `reference/historical-documents/INDEX.md`

## Directory Map

```text
.
├── AI_KNOWLEDGE.md
├── INDEX.md
├── requirements/
├── decisions.md
├── features/
├── knowledge.md
├── rules/
├── design/
├── roadmap/
│   └── archives/
├── reviews/
│   └── archives/
├── development-logs/
│   └── archives/
└── reference/
```

## Document Relationships

```text
Project Charter (01)
  ├── Architecture (02) ── overview only, details in dedicated docs
  │
  ├── Rules/
  │     ├── AI Runtime Rules
  │     ├── Coding Conventions
  │     ├── Development Process
  │     └── Testing Strategy
  │
  ├── Requirement Discovery
  │     ├── Rules
  │     ├── Interview Template
  │     └── Ideal Experience Spec Template
  │
  ├── Roadmap
  │
  ├── Features
  │     ├── Feature Index
  │     ├── Epics
  │     ├── Supporting Features
  │     └── Feature Backlog
  │
  ├── Tech Debt Registry (03)
  │
  ├── Decisions (ADR)
  │
  └── Knowledge
        └── Development Logs (detailed chronology)
```

## First Use

1. Rewrite `design/01-project-charter.md`.
2. As the first action after directory setup, define the development language, documentation language, and commit message language in `design/01-project-charter.md`.
3. If no ideal experience input exists, run requirement discovery and create it before planning the roadmap.
4. Normalize the ideal experience into `design/00-ideal-experience.md` before deriving major planning artifacts.
5. Archive superseded or imported planning inputs under `reference/historical-documents/` with an index entry.
6. Use `features/00-feature-index.md`, `features/epics/`, and `features/supporting/` to organize roadmap-adjacent planning inputs.
7. Use `features/01-feature-backlog.md` as the structured deferred request ledger.
8. Create the active roadmap as `roadmap/roadmap_{YYYYMMDDhhmmss}_{scope}.md` only after the planning inputs are clear enough to derive milestones.
9. Keep at most one active roadmap file at the root of `roadmap/`; move older ones to `roadmap/archives/`.
10. Replace README placeholders with project-specific content.
11. Start the first active development log from `development-logs/log_template.md` and name it `log_{YYYYMMDDhhmmss}.md`.
12. Use the review template in `reviews/` for meaningful changes, keep each review thread in a single evidence file, and archive older review files under `reviews/archives/`.
