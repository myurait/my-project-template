# Roadmap

Use this directory for active roadmap documents, not as a backlog dump.

## Rules

- Keep at most one active roadmap file at the root of `roadmap/`.
- Name roadmap files `roadmap_{YYYYMMDDhhmmss}_{scope}.md`.
- Move replaced, completed, cancelled, or superseded roadmap files to `roadmap/archives/`.
- If no active roadmap is currently selected, `roadmap/` root may contain no roadmap file other than `README.md` and templates.
- A roadmap must be derived from the active ideal experience spec and the current planning inputs.
- A roadmap milestone must explain which user experience it advances.
- Do not keep deferred feature requests as fake active phases.
- Move deferred or exploratory items to `features/`.

## Communication Templates

- `roadmap_consultation_template.md` — use when asking the user to choose the next roadmap direction.
- `roadmap_share_template.md` — use when sharing an already decided roadmap with the user.

## User-Facing Communication Rule

When generating a roadmap consultation or roadmap share message:

- Generate the final message in the Documentation Language defined in `rules/language-policy.md`.
- Do not lead with internal document names, file paths, or technical identifiers.
- Explain the user-facing meaning first, then add document references only if they improve traceability.
- Follow the usage principles written in each template.
