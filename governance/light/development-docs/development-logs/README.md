# Development Logs

Use this directory for detailed chronological notes that are too granular for stable documents.

## Active File Rule

- Keep exactly one active log file in this directory.
- Name the active file `log_{YYYYMMDDhhmmss}.md`, where the timestamp is the file creation time.
- `README.md`, `log_template.md`, and `archives/` are not counted as active log files.

## Entry Rule

- Record each entry with `Date` as an exact timestamp with timezone.
- Record `Author` explicitly for each entry.
- Keep at most 20 entries in one active log file.

## Archive Rule

- If the next append would exceed 20 entries, move the current active file to `development-logs/archives/`.
- Create the next active file in `development-logs/` from `log_template.md`.
