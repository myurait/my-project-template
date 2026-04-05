# Project Knowledge

This file stores reusable lessons that should survive beyond a single task or phase.
Detailed chronology belongs in `development-log/`.

## 1. Greenfield Workflow

1. Write the project charter before writing code.
2. Read real reference implementations instead of summaries when they exist.
3. Create the roadmap before choosing tools and frameworks in detail.
4. Stabilize the foundation early: README, `.gitignore`, documentation, and test policy.
5. Make test isolation a first-class design requirement.

## 2. Documentation Discipline

- `INDEX.md` is the development documentation entry point.
- Design documents should evolve in visible project documents, not only in chat history.
- General lessons belong here.
- Detailed work history belongs in `development-log/`.

## 3. Review Discipline

- Review findings need durable evidence, not only chat output.
- Re-review every meaningful fix, especially when the original issue was architectural.
- A passing test suite does not prove the user workflow is correct.
- Undocumented exceptions are treated as process failures, not harmless shortcuts.

