# Development Process

## 1. Review Rules

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

## 2. Tech Lead Review

Tech lead review is a required review lens for architecture changes, cross-cutting refactors,
behavior changes with high blast radius, and any work that can create long-term maintenance debt.

- Tech lead review is triggered when a review is explicitly labeled as such.
- It emphasizes a senior engineer's intuition and "code smell" detection at a high level of abstraction.
- It applies project-wide and is not limited to a specific phase or scope.

### 2.1 Debt Prevention

- Identify structures that are likely to become future debt.
- Detect hidden dependencies and coupling.
- Detect designs that will make testing, replacement, or extension harder later.
- Detect duplicated knowledge that should be centralized.

### 2.2 Decomposition and Boundaries

- Check whether modules are split at the right level of responsibility.
- Check whether any file or component has accumulated multiple unrelated concerns.
- Check whether abstractions are justified rather than ornamental.
- Check whether interface shapes are consistent across the same layer.
- Check whether copy-paste patterns should be extracted into shared code.

### 2.3 Alignment With Declared Design

- Verify alignment with the architecture documents and ADRs.
- Verify that public operational behavior matches the documented rules.
- Verify that exceptions to the current design are explicit, not accidental.

### 2.4 Senior-Engineer Smell Detection

- Look for structures that feel unnatural or over-complicated.
- Look for naming that hides intent.
- Look for missing error-path handling.
- Look for places that may pass tests but still fail in production use.
- Look for places where the tester environment differs from the real user environment.
- Look for designs that are technically correct but will hinder future changeability.

### 2.5 Evidence

- Tech lead review findings must be written to `reviews/`.
- Findings must include severity and file:line references when applicable.
- Fixes must receive follow-up review with the same review lens, not only a quick re-check.
- Append fix results to the same review file.

## 3. Post-Fix Re-Review

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

## 4. Documentation Rules

- Treat this repository as the canonical source for development-facing documentation.
- Log all non-trivial architecture and policy decisions in `decisions.md`.
- Extract reusable lessons into `knowledge.md`.

## 5. Testing Rules

- `rules/testing.md` is the canonical testing policy for this repository.
- All test scope, coverage, design, isolation, naming, execution, and manual-test rules in `rules/testing.md` must be followed.

## 6. Development Flow

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
- Follow `rules/testing.md` for required test scope, execution rules, and actor analysis.

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
- Re-check tests according to `rules/testing.md`, including regression gaps and actor-analysis expectations.

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
