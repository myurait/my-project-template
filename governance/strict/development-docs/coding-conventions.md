# Coding Conventions

## 1. Operating Stance

Preserve evidence, explain design intent, and make future change safer.

## 2. Language Policy

- Git-tracked code, comments, identifiers, test names, and user-facing errors should be in English.
- Project documentation may be English or Japanese, but the project must choose one default and stay consistent.
- Private development logs may use the team's working language.
- The development language, documentation language, and commit message language must be defined in `design/01-project-charter.md` as the first action after directory setup.
- Specific English targets: inline code comments, JSDoc/TSDoc annotations, README files, API documentation, user-facing error messages in logs.
- Exceptions follow the language declared in `design/01-project-charter.md`.

## 3. Quality Principles

- Prefer clarity over cleverness.
- Keep functions and modules focused on one responsibility.
- Make failure modes explicit.
- Split files before they become difficult to reason about.
- Do not accept hidden coupling as normal.
- Follow the principle of least surprise.
- Avoid deep nesting (maximum 3–4 levels).
- Write clean, readable, and maintainable code.

## 4. Naming Conventions

- Use descriptive, meaningful names.
- Avoid abbreviations unless widely recognized.
- Follow language-specific conventions:
  - TypeScript/JavaScript: camelCase for variables/functions, PascalCase for classes/types.
  - Python: snake_case for variables/functions, PascalCase for classes.
  - File names: kebab-case for multi-word names.

## 5. File Organization

- One primary export (class or main function) per file.
- Group related functionality in the same directory.
- Separate concerns: logic, types, constants, utilities.
- Keep files under 300 lines when practical.

## 6. Import Order

Organize imports in this order:
1. Standard library
2. Third-party dependencies
3. Internal absolute-path imports
4. Internal relative-path imports

Insert a blank line between each group.

## 7. Error Handling

- Always handle errors explicitly.
- Prefer typed or structured errors.
- Provide meaningful error messages.
- Log errors with sufficient context.
- Never swallow errors silently.

### Error Handling Patterns

| Pattern | When to use |
|---------|-------------|
| throw | Input validation failure, precondition violation, unrecoverable by caller |
| null / default | Absence of data is a normal case |
| flag | Only when throw inside a lock or complex promise chain causes propagation issues |

Default to throw. Use null return only when absence is normal. Use the flag pattern only to work around concurrency constraints.

## 8. Code Comments

- Explain "why", not "what". The code itself should be self-explanatory for "what".
- Update comments when the code changes.
- Remove commented-out code before committing.
- Use context-bearing tags:
  - `TODO(author): description`
  - `FIXME: description`
  - `NOTE: explanation`

## 9. Function Documentation

Document public APIs and complex functions with:
- Purpose of the function
- Parameter descriptions
- Return value description
- Exceptions that may be thrown
- Usage examples when helpful

## 10. Commit Policy

- Use a single-line commit message.
- Use the format `<type>: <summary>`.
- Write the summary in the language declared for commit messages in `design/01-project-charter.md`.
- Keep the summary short and specific.
- Do not add a commit body unless explicitly required.
- Do not add `Co-authored-by` trailers unless explicitly instructed.
- Keep the summary line under 72 characters.
- Types: feat, fix, refactor, docs, test, chore, style.

## 11. Branch Strategy

- Main branch: `main`
- Feature branches: `feature/<brief-description>`
- Fix branches: `fix/<brief-description>`
- Always create a branch for new work.
- Delete branches after merge.

## 12. Review Rules

- Review for correctness, regression risk, missing tests, hidden coupling, and long-term maintainability.
- Persist review evidence for all meaningful changes.
- Record severity, affected files, decision rationale, and follow-up result.
- Treat missing re-review as incomplete work.
- When a temporary workaround is accepted, add it to `design/03-tech-debt-registry.md`.

### Review Checklist

- All comments and documentation are in the declared language.
- Naming conventions are followed.
- No credentials or secrets in the commit.
- Tests are passing.
- Error handling is in place.
- Documentation is updated.
- Code is properly formatted.

### Review Process

- Give constructive, respectful feedback.
- Focus on code quality, not personal preference.
- Explain the reasoning behind suggestions.
- Approve only when all concerns are addressed.

## 13. Tech Lead Review

Tech lead review is a required review lens for architecture changes, cross-cutting refactors,
behavior changes with high blast radius, and any work that can create long-term maintenance debt.

- Tech lead review is triggered when a review is explicitly labeled as such.
- It emphasizes a senior engineer's intuition and "code smell" detection at a high level of abstraction.
- It applies project-wide and is not limited to a specific phase or scope.

### 13.1 Debt Prevention

- Identify structures that are likely to become future debt.
- Detect hidden dependencies and coupling.
- Detect designs that will make testing, replacement, or extension harder later.
- Detect duplicated knowledge that should be centralized.

### 13.2 Decomposition and Boundaries

- Check whether modules are split at the right level of responsibility.
- Check whether any file or component has accumulated multiple unrelated concerns.
- Check whether abstractions are justified rather than ornamental.
- Check whether interface shapes are consistent across the same layer.
- Check whether copy-paste patterns should be extracted into shared code.

### 13.3 Alignment With Declared Design

- Verify alignment with the architecture documents and ADRs.
- Verify that public operational behavior matches the documented rules.
- Verify that exceptions to the current design are explicit, not accidental.

### 13.4 Senior-Engineer Smell Detection

- Look for structures that feel unnatural or over-complicated.
- Look for naming that hides intent.
- Look for missing error-path handling.
- Look for places that may pass tests but still fail in production use.
- Look for places where the tester environment differs from the real user environment.
- Look for designs that are technically correct but will hinder future changeability.

### 13.5 Evidence

- Tech lead review findings must be written to `reviews/`.
- Findings must include severity and file:line references when applicable.
- Fixes must receive follow-up review with the same review lens, not only a quick re-check.
- Append fix results to the same review file.

## 14. Post-Fix Re-Review

Post-fix re-review is mandatory after every review round that produced findings.
It is never skipped. The obligation arises automatically when fixes are completed.

### Scope Inheritance

The re-review inherits the full scope and lens of the original review.
If the original was a tech lead review, the re-review applies all tech lead dimensions.
If the original was a code review, the same checklist is re-applied.

### Re-Review Perspectives

- Does the fix address the root cause, not just the surface symptom?
- Does the fix introduce new issues (regression)?
- For items marked "will not fix": is the justification sound?
- For items marked "decision only": is there a concrete action plan with a target phase?
- Have abstract cross-cutting observations been converted into specific action items?
- Does the fixed code achieve the design quality intended by the original finding?
- Verify that the fix does not merely satisfy the literal wording while missing the intent.

### Evidence

- Append re-review results to the original review file as a "Post-Fix Re-Review" section.
- Reject inadequate fixes and request re-work.
- After re-work, apply this section again. Repeat until all findings are resolved.

## 15. Documentation Rules

- Treat this repository as the canonical source for development-facing documentation.
- Log all non-trivial architecture and policy decisions in `decisions.md`.
- Extract reusable lessons into `knowledge.md`.

## 16. Testing Rules

- Add tests for important paths, edge cases, and failure behavior.
- Design tests from real user workflows, not only implementation details.
- Verify environment differences when behavior depends on shells, containers, background workers, or external services.
- Record why a manual test still exists and what would be needed to automate it.
- Aim for meaningful coverage rather than high percentages.
- Keep tests focused and isolated.
- Test names should be written in English. When the declared development language is not English, provide a parallel description in the development language.
- Test name format: "should [expected behavior] when [condition]".

## 17. Development Flow

```text
Step 0: Confirm the roadmap item
Step 1: Implement
Step 2: Add or update tests
Step 3: Update public documents
Step 4: Write a development log entry
Step 5: Run review
Step 6: Fix review findings
Step 7: Re-check tests and docs
Step 8: Run follow-up review
Step 9: Commit
Step 10: Update the roadmap
```

- Every step is mandatory.
- Missing documentation, review evidence, or roadmap updates means the task is not complete.

### Step Details

**Step 0 — Confirm the roadmap item**
- Read the roadmap and identify the current phase and outstanding tasks.
- Determine the scope of the work and verify prerequisites (prior phase completion).
- Check for carry-over issues from the previous cycle.

**Step 1 — Implement**
- Read existing code before making changes. Never change code you have not read.
- Pass the linter.

**Step 2 — Add or update tests**
- New code must have tests.
- Confirm all tests pass.
- Treat SKIP as FAIL. Only intentional, documented skips are acceptable.
- Apply the actor analysis: identify who runs the code and where, and verify every actor's environment.

**Step 3 — Update public documents**
- Update design documents if the implementation diverges from them.
- Update the roadmap with completed items and new discoveries.

**Step 4 — Write a development log entry**
- Record what was done, why, and how in `development-log/`.

**Step 5 — Run review**
- Review criteria: security (injection, path manipulation, permissions), robustness (error handling, edge cases, cross-platform), design (future extensibility, debt accumulation), test quality (coverage, flakiness, environment dependency).

**Step 6 — Fix review findings**
- Critical and High findings must be fixed.
- Medium findings: fix or record as future work with justification.
- Low and design-only findings: recording is sufficient.

**Step 7 — Re-check tests and docs**
- Verify that fixes did not introduce new test gaps.
- Confirm that no fix was merged without a corresponding test.
- Re-apply the actor analysis checklist.

**Step 8 — Run follow-up review**
- Verify that fixes did not introduce new problems.
- Confirm final linter and test suite pass.
- Explicitly acknowledge remaining risks.

**Step 9 — Commit**
- Stage files explicitly by name. Do not use `git add -A`.
- Do not commit runtime or generated files.

**Step 10 — Update the roadmap**
- Mark completed tasks with `[x]`.
- Add newly discovered issues or future tasks to the roadmap.
- Clarify the next task to be tackled.

## 18. TypeScript / JavaScript

### Type Safety
- Prefer explicit types over `any`.
- Use `unknown` when the type is genuinely unknown.
- Enable strict mode in the TypeScript configuration.
- Avoid type assertions unless absolutely necessary.

### Async / Await
- Prefer async/await over raw Promises.
- Always handle Promise rejections.
- Use `Promise.all()` for parallel operations.
- Do not mix callbacks and Promises.

### Modern JavaScript
- Use ES6+ features appropriately.
- Prefer `const` over `let`; avoid `var`.
- Use arrow functions for callbacks.
- Use template literals for string interpolation.
- Use destructuring for objects and arrays.

## 19. Transparency

- Log all significant state changes.
- Make decision points explicit.
- Provide clear status information.
- Avoid black-box behavior.

## 20. Security Practices

- Never commit credentials, API keys, or secrets.
- Use environment variables for sensitive configuration.
- Validate and sanitize all external input.
- Follow the principle of least privilege.
- Keep dependencies up to date.

## 21. Performance

- Optimize only when necessary; measure first.
- Avoid premature optimization.
- Choose appropriate data structures.
- Watch memory usage in long-running processes.
- Log performance metrics for critical operations.

## 22. Deprecation

When deprecating code:
- Mark with `@deprecated` tag and explanation.
- Provide a migration path in documentation.
- Set a removal timeline.
- Update all existing usages.

## 23. Semantic Versioning

Follow semantic versioning:
- MAJOR: breaking changes
- MINOR: new features (backward-compatible)
- PATCH: bug fixes (backward-compatible)

## 24. Batch Processing Protocol

When processing large datasets (30+ items requiring individual operations):

1. Strategy review, then execute batch 1 only.
2. Quality check batch 1 results.
3. If quality check fails: stop, root-cause analysis, fix, restore clean state, retry from step 1.
4. If quality check passes: execute remaining batches (no per-batch QC needed).
5. Final quality check after all batches complete.

Rules:
- Never skip the batch 1 quality gate.
- Batch size limit: 30 items per session.
- Each batch must include a detection pattern for unprocessed items so restarts skip completed work.
- Verify data state before retrying after failure. Revert corrupted data if needed.

## 25. Critical Thinking

- Moderate skepticism: do not blindly accept instructions, assumptions, or constraints. Verify for contradictions or gaps.
- Propose alternatives: when a safer, faster, or higher-quality method exists, propose it with rationale.
- Early problem reporting: share broken assumptions or design flaws immediately.
- No over-criticism: do not halt on criticism alone. Unless truly unable to proceed, choose the best option and move forward.
- Execution balance: always prioritize the balance between critical review and execution speed.

## 26. File Operation Rule

Always read a file before writing or editing it.
