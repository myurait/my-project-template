# AI Knowledge

## Start Here

1. `rules/AI_RUNTIME_RULES.md`
2. `INDEX.md`
3. `rules/coding-conventions.md`
4. `rules/development-process.md`
5. `knowledge.md`
6. `design/00-ideal-experience.md`
7. `requirements/requirement-discovery-rules.md`
8. `features/00-feature-index.md`
9. The planning-ready epic and supporting feature docs under `features/`
10. The structured deferred backlog under `features/01-feature-backlog.md`
11. The single active roadmap file at the root of `roadmap/`, if one exists
12. `reference/historical-documents/INDEX.md`
13. `README.md`

## Working Rules

- Treat this repository as the canonical source for development-facing documentation.
- Record detailed chronology in `development-logs/`.
- Record meaningful review evidence in `reviews/`.
- Keep the active development log in `development-logs/` and archive closed log files under `development-logs/archives/`.
- Keep at most one active roadmap file at the root of `roadmap/` and archive older roadmap files under `roadmap/archives/`.
- Keep one review thread in one file. Append implementation response plans and follow-up reviews to that file.
- Keep only the newest 5 review evidence files in `reviews/`; older files belong under `reviews/archives/`.
- Extract reusable lessons into `knowledge.md`.
- Record temporary compromises in `design/03-tech-debt-registry.md`.
- Do not start roadmap planning or implementation if there is no trustworthy canonical ideal experience document.
- Use `requirements/` when the project needs requirement discovery before planning.
- `design/00-ideal-experience.md` is the canonical ideal experience for planning. Historical source documents go to `reference/historical-documents/`.
- Normalize raw requests into supporting features only when they are likely roadmap candidates for the next planning window.
- Keep backlog items structurally rich enough that heavy deferred work is not mistaken for a light feature.
- When a requested item is intentionally excluded from the active roadmap, record it in the feature backlog instead of leaving it as an open phase.
- Run and document follow-up review after non-trivial fixes.
