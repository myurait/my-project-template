# Development Documentation Index

This repository contains development-facing project documentation.

## Reading Order

1. `AI_KNOWLEDGE.md`
2. `rules/AI_RUNTIME_RULES.md`
3. `rules/coding-conventions.md`
4. `rules/development-process.md`
5. `knowledge.md`
6. `roadmap/01-initial-roadmap.md`
7. `design/01-project-charter.md`
8. `design/02-architecture.md`
9. `decisions.md`

## Directory Map

```text
.
├── AI_KNOWLEDGE.md
├── INDEX.md
├── decisions.md
├── knowledge.md
├── rules/
├── design/
├── roadmap/
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
  ├── Roadmap
  │     └── Tech Debt Registry (03)
  │
  ├── Decisions (ADR)
  │
  └── Knowledge
        └── Development Logs (detailed chronology)
```

## First Use

1. Rewrite `design/01-project-charter.md`.
2. As the first action after directory setup, define the development language, documentation language, and commit message language in `design/01-project-charter.md`.
3. Fill `roadmap/01-initial-roadmap.md`.
4. Replace README placeholders with project-specific content.
5. Start the first active development log from `development-logs/log_template.md` and name it `log_{YYYYMMDDhhmmss}.md`.
6. Use the review template in `reviews/` for meaningful changes, keep each review thread in a single evidence file, and archive older review files under `reviews/archives/`.
