# Coding Conventions

## 1. Operating Stance

Preserve evidence, explain design intent, and make future change safer.

## 2. Language Policy

- Git-tracked code, comments, identifiers, test names, and user-facing errors should be in English.
- Project documentation may be English or Japanese, but the project must choose one default and stay consistent.
- Private development logs may use the team's working language.
- The development language, documentation language, and commit message language must be defined in `design/01-project-charter.md` as the first action after directory setup.

## 3. Quality Principles

- Prefer clarity over cleverness.
- Keep functions and modules focused on one responsibility.
- Make failure modes explicit.
- Split files before they become difficult to reason about.
- Do not accept hidden coupling as normal.

## 4. Commit Policy

- Use a single-line commit message.
- Use the format `<type>: <summary>`.
- Write the summary in the language declared for commit messages in `design/01-project-charter.md`.
- Keep the summary short and specific.
- Do not add a commit body unless explicitly required.
- Do not add `Co-authored-by` trailers unless explicitly instructed.

## 5. Review Rules

- Review for correctness, regression risk, missing tests, hidden coupling, and long-term maintainability.
- Persist review evidence for all meaningful changes.
- Record severity, affected files, decision rationale, and follow-up result.
- Treat missing re-review as incomplete work.
- When a temporary workaround is accepted, add it to `design/03-tech-debt-registry.md`.

## 6. Tech Lead Review

Tech lead review is a required review lens for architecture changes, cross-cutting refactors,
behavior changes with high blast radius, and any work that can create long-term maintenance debt.

### 5.1 Debt Prevention

- Identify structures that are likely to become future debt.
- Detect hidden dependencies and coupling.
- Detect designs that will make testing, replacement, or extension harder later.
- Detect duplicated knowledge that should be centralized.

### 5.2 Decomposition and Boundaries

- Check whether modules are split at the right level of responsibility.
- Check whether any file or component has accumulated multiple unrelated concerns.
- Check whether abstractions are justified rather than ornamental.
- Check whether interface shapes are consistent across the same layer.

### 5.3 Alignment With Declared Design

- Verify alignment with the architecture documents and ADRs.
- Verify that public operational behavior matches the documented rules.
- Verify that exceptions to the current design are explicit, not accidental.

### 5.4 Senior-Engineer Smell Detection

- Look for structures that feel unnatural or over-complicated.
- Look for naming that hides intent.
- Look for missing error-path handling.
- Look for places that may pass tests but still fail in production use.
- Look for places where the tester environment differs from the real user environment.

### 5.5 Evidence

- Tech lead review findings must be written to `reviews/`.
- Findings must include severity and file references when applicable.
- Fixes must receive follow-up review with the same review lens, not only a quick re-check.

## 7. Documentation Rules

- Treat this repository as the canonical source for development-facing documentation.
- Log all non-trivial architecture and policy decisions in `decisions.md`.
- Extract reusable lessons into `knowledge.md`.

## 8. Testing Rules

- Add tests for important paths, edge cases, and failure behavior.
- Design tests from real user workflows, not only implementation details.
- Verify environment differences when behavior depends on shells, containers, background workers, or external services.
- Record why a manual test still exists and what would be needed to automate it.

## 9. Development Flow

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
