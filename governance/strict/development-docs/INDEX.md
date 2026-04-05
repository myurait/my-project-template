# Development Documentation Index

This repository contains development-facing project documentation.

## Reading Order

1. `AI_KNOWLEDGE.md`
2. `AI_RUNTIME_RULES.md`
3. `coding-conventions.md`
4. `knowledge.md`
5. `roadmap/01-initial-roadmap.md`
6. `design/01-project-charter.md`
7. `design/02-architecture.md`
8. `decisions.md`

## Directory Map

```text
.
├── AI_KNOWLEDGE.md
├── AI_RUNTIME_RULES.md
├── INDEX.md
├── coding-conventions.md
├── decisions.md
├── knowledge.md
├── testing.md
├── design/
├── roadmap/
├── reviews/
├── development-log/
└── reference/
```

## Document Relationships

```text
Project Charter (01)
  ├── Architecture (02) ── overview only, details in dedicated docs
  │
  ├── Coding Conventions
  │     ├── Testing Strategy
  │     └── Development Flow (Step 0–10)
  │
  ├── Roadmap
  │     └── Tech Debt Registry (03)
  │
  ├── Decisions (ADR)
  │
  └── Knowledge
        └── Development Log (detailed chronology)
```

## First Use

1. Rewrite `design/01-project-charter.md`.
2. As the first action after directory setup, define the development language, documentation language, and commit message language in `design/01-project-charter.md`.
3. Fill `roadmap/01-initial-roadmap.md`.
4. Replace README placeholders with project-specific content.
5. Start the first development log from `development-log/log_template.md`.
6. Use the review template in `reviews/` for meaningful changes.
