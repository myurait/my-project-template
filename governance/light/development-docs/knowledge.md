# Project Knowledge

This file stores reusable lessons that should survive beyond a single task or phase.
Detailed chronology belongs in `development-log/`.

## 1. Greenfield Workflow

1. Write the project charter before writing code.
2. Create the roadmap before choosing tools in detail.
3. Stabilize the foundation early: README, `.gitignore`, docs, and test policy.
4. Keep process lean until the project justifies more ceremony.
5. Read real reference implementations instead of summaries when they exist.
6. Cross-check the roadmap against reference implementations. Identify gaps and excess.
7. Do not accumulate test debt. Refactor untestable code immediately.
8. Pre-place test stubs for future phases.
9. Make test isolation a first-class design requirement.
10. Keep design documents in sync with the implementation. Add numbered design documents as the project evolves.
11. Start each cycle by confirming the roadmap; end each cycle by updating it.

## 2. Documentation Discipline

- `INDEX.md` is the development documentation entry point.
- General lessons belong here.
- Detailed work history belongs in `development-log/`.
- Architecture documents (02) should provide an overview only. Delegate details to dedicated documents (single source of truth).
- Update the tech debt registry at the end of each phase.
- Split log files at roughly 20 entries per file.

## 3. Review Discipline

- A passing test suite does not prove the real user workflow is correct.
- Risky changes should leave durable review evidence.
- Code review alone cannot detect user-experience problems. Explicitly incorporate end-user perspective testing into the process.

## 4. Architecture Lessons

- Reference implementations carry implicit constraints. When adopting one, explicitly verify its design assumptions.
- Problems surfaced by tests are system problems, not test-design problems. Recognize architectural defects rather than patching tests.
- When applying a band-aid fix, record a root-cause fix plan in the tech debt registry. Never stop at the band-aid alone.

## 5. Security Lessons

- Prevent injection in structured data (YAML, JSON, SQL) by using safe serialization functions, not string interpolation.
- Prevent command injection by validating external input against a whitelist before passing it to shell commands.
- Never use pipe-to-shell patterns (`curl | bash`) in project scripts. Show the commands and let the user run them manually.

