# AI Knowledge

## Start Here

Read items 1–5 before starting any work. These are mandatory and must not be skipped.

1. `rules/AI_RUNTIME_RULES.md`
2. `rules/language-policy.md`
3. `INDEX.md`
4. `rules/coding-conventions.md`
5. `rules/development-process.md`
6. `knowledge.md`
7. `design/00-ideal-experience.md`
8. `requirements/requirement-discovery-rules.md`
9. `features/00-feature-index.md`
10. The planning-ready epic and supporting feature docs under `features/`
11. The structured deferred backlog under `features/01-feature-backlog.md`
12. The single active roadmap file at the root of `roadmap/`, if one exists
13. `reference/historical-documents/INDEX.md`
14. `README.md`

## Working Rules

- Treat this repository as the canonical source for development-facing documentation.
- Record detailed chronology in `development-logs/`.
- Record meaningful review evidence in `reviews/`.
- Keep the active development log in `development-logs/` and archive closed log files under `development-logs/archives/`.
- Keep at most one active roadmap file at the root of `roadmap/` and archive older roadmap files under `roadmap/archives/`.
- `rules/language-policy.md` is the canonical source for project-specific language settings and language-domain boundaries.
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
