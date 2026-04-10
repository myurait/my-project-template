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

- `roadmap_consultation_template.md`
  - use when asking the user to choose the next roadmap direction
  - this is a direct user-facing message template, not an internal planning outline
- `roadmap_share_template.md`
  - use when sharing an already decided roadmap with the user
  - this is a direct user-facing message template, not a file-change summary

## User-Facing Communication Rule

- Follow the Documentation Language defined in `rules/language-policy.md`.
- Explain user meaning first, then add internal file names only if they help traceability.
- Do not assume the user knows internal identifiers, feature IDs, epic IDs, milestone labels, or technical shorthand.
- Prefer the language of `design/00-ideal-experience.md` over implementation-oriented jargon.
- Every roadmap consultation or share message must answer:
  - where the product stands against the ideal experience now
  - what part of the ideal experience this roadmap will advance
  - what will still remain after this roadmap
