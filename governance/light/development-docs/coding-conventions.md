# Coding Conventions

## 1. Operating Stance

Optimize for speed and low ceremony while preserving basic quality and traceability.

## 2. Language Policy

- Git-tracked code, comments, identifiers, test names, and user-facing errors should be in English.
- Project documentation may be English or Japanese, but the project should pick one default and stay consistent.
- Private development logs may use the team's working language.
- The development language, documentation language, and commit message language must be defined in `design/01-project-charter.md` as the first action after directory setup.

## 3. Quality Principles

- Prefer clarity over cleverness.
- Keep modules focused on one responsibility.
- Make failure modes explicit.
- Split files when reviewability starts to degrade.

## 4. Commit Policy

- Use a single-line commit message.
- Use the format `<type>: <summary>`.
- Write the summary in the language declared for commit messages in `design/01-project-charter.md`.
- Keep the summary short and specific.
- Do not add a commit body unless explicitly required.
- Do not add `Co-authored-by` trailers unless explicitly instructed.

## 5. Review Rules

- Review for correctness, regression risk, missing tests, and hidden coupling.
- Review may be synchronous in chat or PR comments.
- Persist review evidence only for high-risk or architecture-affecting changes.
- Follow-up review is recommended when a fix changes behavior or structure.

## 6. Documentation Rules

- Update the roadmap and development log every cycle.
- Documentation may lag by one small iteration if the change is still unstable.
- Log only hard-to-reverse decisions in `decisions.md`.

## 7. Development Flow

```text
Step 0: Confirm the roadmap item
Step 1: Implement
Step 2: Add or update tests
Step 3: Update documents
Step 4: Write a development log entry
Step 5: Review
Step 6: Fix important findings
Step 7: Re-check tests and docs
Step 8: Commit
Step 9: Update the roadmap
```

- The sequence should be preserved, but small low-risk tasks may merge adjacent steps.
- Minimum expectation: roadmap note, implementation, verification, and at least one durable record.
