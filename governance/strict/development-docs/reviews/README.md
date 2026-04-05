# Review Evidence

Store meaningful review results here so findings and re-review history are durable.

## Review Thread Rule

- Use one file per review thread.
- Name review evidence files `review_{YYYYMMDDhhmmss}_{scope_description}.md`.
- Keep `scope_description` concise, ASCII, and kebab-case.
- Record the initial review, the implementation response plan, and every follow-up review in that same file.
- Do not create a new sibling file for a follow-up review of the same thread.
- Record `Date` as an exact timestamp with timezone.
- Record `Reviewer` explicitly. If AI performs the review, write the model name in the publicly disclosable form.
- Record `Base Commit` for the initial review and for each follow-up review entry.
- `Review Type` must be chosen from the template and must match the actual review lens.
- Do not use Markdown tables in review evidence. Use headings and flat bullet lists.

## Archive Rule

- Keep only the newest 5 review evidence files in `reviews/`.
- Move older review evidence files to `reviews/archives/`.
- `README.md`, `review_template.md`, and `archives/` are not counted as review evidence files.

## Legacy Note

- Older review evidence may still use split follow-up files. That layout is deprecated.
