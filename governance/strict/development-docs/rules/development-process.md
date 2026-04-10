# Development Process

## 1. Review Rules

- Review for correctness, regression risk, missing tests, hidden coupling, and long-term maintainability.
- Persist review evidence for all meaningful changes.
- Use one review evidence file per review thread.
- Record the initial review, implementation response plan, and all follow-up reviews in that same file.
- Do not create separate follow-up files for the same review thread.
- Name review evidence files as `review_{YYYYMMDDhhmmss}_{scope_description}.md`.
- Keep `scope_description` concise, ASCII, and kebab-case.
- Keep only the newest 5 review evidence files in `reviews/`. Move older files to `reviews/archives/`.
- `reviews/README.md`, `reviews/review_template.md`, and `reviews/archives/` are not counted as review evidence files.
- Record severity, affected files, decision rationale, implementation response plan, and follow-up result.
- Record `Date` as the exact execution timestamp with timezone.
- Record `Reviewer` explicitly. When the reviewer is AI, write the model name in the publicly disclosable form.
- Record `Base Commit` for every initial review and every follow-up review entry.
- `Review Type` must match the actual review lens and criteria used.
- Do not use Markdown tables in review evidence. Use headings and flat bullet lists instead.
- Review critically by default. Do not assume the chosen work, approach, or decision is correct merely because it was implemented.
- Question not only the work output but also the work plan, decomposition, and decision-making that produced it.
- Explicitly check for unnecessary new layers, premature abstraction, and process complexity that is not justified by user value.
- Explicitly check whether the change can be explained to the user in concise terms, including why it exists and what decision or workflow it enables.
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
- Added structure is justified against simpler alternatives.
- The change can be explained to the user without relying on internal implementation context.

### Review Process

- Give constructive, respectful feedback.
- Focus on code quality, not personal preference.
- Explain the reasoning behind suggestions.
- Challenge whether the current direction is the right direction, not only whether it was executed cleanly.
- Treat unexplained complexity as a defect candidate, not as neutral style.
- Approve only when all concerns are addressed.
- After findings are produced, record the implementation response plan before fixes begin.
- Follow-up review must explicitly reference the implementation response plan items it verifies.

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
- Detect structure that was introduced too early and now creates maintenance burden without enough decision value.

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
- Look for changes that are technically defensible but harder to explain than the user value they unlock.
- Look for naming that hides intent.
- Look for missing error-path handling.
- Look for places that may pass tests but still fail in production use.
- Look for places where the tester environment differs from the real user environment.
- Look for designs that are technically correct but will hinder future changeability.

### 2.5 Evidence

- Tech lead review findings must be written to `reviews/`.
- Findings must include severity and file:line references when applicable.
- Fixes must receive follow-up review with the same review lens, not only a quick re-check.
- Append the implementation response plan and all fix results to the same review file.

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

- Append re-review results to the original review file as a follow-up review entry.
- Every follow-up review entry must include `Date`, `Reviewer`, `Base Commit`, `Review Type`, referenced plan items, result, and remaining risks.
- Do not leave `Remaining Risks` as passive notes. Every remaining risk must have an explicit disposition.
- Allowed dispositions are:
- accepted residual risk with monitoring or next-review trigger
- deferred planned work with tracked destination document or phase
- explicit user decision required
- unresolved finding that requires another fix-and-review cycle
- A follow-up review is not complete until each remaining risk has a recorded disposition and next handling path.
- Reject inadequate fixes and request re-work.
- After re-work, apply this section again. Repeat until all findings are resolved.

## 4. Documentation Rules

- Treat this repository as the canonical source for development-facing documentation.
- Log all non-trivial architecture and policy decisions in `decisions.md`.
- Extract reusable lessons into `knowledge.md`.
- Keep at most one active roadmap file at the root of `roadmap/`.
- Name roadmap files `roadmap_{YYYYMMDDhhmmss}_{scope}.md`.
- Move replaced, completed, cancelled, or superseded roadmap files to `roadmap/archives/`.
- The canonical ideal experience planning source is `design/00-ideal-experience.md`.
- Raw interviews, imported user specifications, superseded drafts, and other historical planning inputs must be archived under `reference/historical-documents/`.
- Historical documents are preserved for traceability only. They are not authoritative for active planning once normalized.
- Every historical document archive must have an entry in `reference/historical-documents/INDEX.md` with archive date, archive reason, summary, and canonical successor documents.

## 5. Decision Escalation Rules

- Ask the user to decide before finalizing any long-lived choice that is materially preference-sensitive or changes the project's canonical structure.
- This includes at least:
- canonical source selection
- document hierarchy and new persistent layers
- user-visible workflow changes
- product-direction choices with meaningful tradeoffs
- When escalating a decision, present:
- the recommended option
- the main alternatives
- the merits and drawbacks of each option
- the expected impact scope
- Do not silently choose one side of a durable structural tradeoff when reasonable user preference can change the answer.

## 6. Planning and Requirement Discovery Rules

- Do not start roadmap planning or implementation from a raw feature list alone.
- The active ideal experience spec for planning is `design/00-ideal-experience.md`. If it does not exist or is no longer trusted, run requirement discovery first.
- Requirement discovery rules and templates live under `requirements/`.
- Roadmaps must be derived from:
- the canonical ideal experience
- the current planning reviews
- planning-ready epic and supporting feature inputs
- A roadmap item is invalid unless it states:
- which intended user experience it advances
- which source feature or planning input it comes from
- how success will be validated against user intent
- Supporting features are only for roadmap-adjacent candidates that are likely to be compared for the next planning window.
- Do not create a supporting feature for every deferred request by default.
- Feature backlog lines are not implementation-ready by default, but they must still be structurally informative.
- Changes to backlog `priority assumption`, `thickness`, `design impact`, or supporting-feature promotion for heavy or architectural items must receive critical review before they are treated as stable planning input.
- Every backlog item must record:
- priority assumption
- expected order
- blockers
- experience tie
- thickness
- design impact
- current design constraint
- Heavy or architectural backlog items must also be reflected in the relevant active design document or open design questions before adjacent implementation proceeds.
- Roadmap sequencing among `near` items must be decided explicitly in roadmap planning or through user decision. Do not silently infer sequence from file order or supporting-feature order.
- Validation must test "did we build what the user meant?" and not only "does the code run?".
- For major planning changes, run a design review before implementation begins.

## 7. Testing Rules

- `rules/testing.md` is the canonical testing policy for this repository.
- All test scope, coverage, design, isolation, naming, execution, and manual-test rules in `rules/testing.md` must be followed.

## 8. Development Flow

```text
Stage A: Planning and intent alignment
Step 0: Confirm or create the ideal experience input
Step 1: Run requirement discovery when needed
Step 2: Derive or refresh planning inputs
Step 3: Select or revise the roadmap item
Step 4: Define cycle acceptance and validation
Stage B: Delivery
Step 5: Implement
Step 6: Add or update tests
Step 7: Update public documents
Step 8: Write a development log entry
Step 9: Run review
Step 10: Fix review findings
Step 11: Re-check tests, docs, and validation evidence
Step 12: Run follow-up review
Step 13: Commit
Step 14: Update roadmap and feature state
```

- Every step is mandatory.
- Missing documentation, review evidence, or roadmap updates means the task is not complete.

### Step Details

**Step 0 — Confirm or create the ideal experience input**
- Read `design/00-ideal-experience.md` if it exists.
- If no reliable canonical ideal experience document exists, do not continue to roadmap planning. Move to Step 1 first.
- If the user provides a new or conflicting ideal experience input in another file or chat artifact, normalize it into `design/00-ideal-experience.md` and archive the source under `reference/historical-documents/`.
- Treat the canonical ideal experience as a planning prerequisite, not as optional background.

**Step 1 — Run requirement discovery when needed**
- Follow `requirements/requirement-discovery-rules.md`.
- Run a structured interview when the ideal experience is missing, stale, contradicted, or too weak to drive planning.
- Record the result in requirement discovery artifacts before continuing.

**Step 2 — Derive or refresh planning inputs**
- Convert the canonical ideal experience and requirement discovery into planning inputs.
- Clarify the current problem statement, experience pillars, major design questions, and validation expectations.
- Confirm whether current epic documents are sufficient and whether any roadmap-adjacent candidates need supporting features.
- Keep distant deferred requests in the backlog unless there is a clear near-term planning need.

**Step 3 — Select or revise the roadmap item**
- Read the active roadmap and identify the current milestone or create a revised roadmap from the planning inputs.
- Every selected roadmap item must trace back to a user problem and intended experience delta.
- Do not select work only because it is technically convenient.

**Step 4 — Define cycle acceptance and validation**
- Before implementation, define how to tell whether the work matches user intent.
- Record user-visible acceptance conditions, validation evidence, and any required manual scenario checks.
- If this cannot be stated clearly, the work is not ready for implementation.

**Step 5 — Implement**
- Read existing code before making changes. Never change code you have not read.
- Pass the linter.

**Step 6 — Add or update tests**
- Follow `rules/testing.md` for required test scope, execution rules, and actor analysis.

**Step 7 — Update public documents**
- Update design documents if the implementation diverges from them.
- Update the roadmap with completed items and new discoveries.
- Roadmap consultation and roadmap share messages are direct user communication, not internal memo format.
- Use the Documentation Language defined in `rules/language-policy.md`.
- Explain ideal-experience meaning before internal document names, identifiers, or technical labels.
- For process, planning, or document-structure changes, record a concise user-facing summary of what changed, why it changed, and what decision or workflow it enables.

**Step 8 — Write a development log entry**
- Record what was done, why, and how in `development-logs/`.
- Keep the active file name as `log_{YYYYMMDDhhmmss}.md`, where the timestamp is the file creation time.
- Every log entry must record `Date` as the exact execution timestamp with timezone and `Author` explicitly.
- Keep at most 20 entries in one active log file.
- If the next append would exceed 20 entries, move the current file to `development-logs/archives/` and create a new active file in `development-logs/`.

**Step 9 — Run review**
- Review criteria: security (injection, path manipulation, permissions), robustness (error handling, edge cases, cross-platform), design (future extensibility, debt accumulation), test quality (coverage, flakiness, environment dependency).
- For planning, roadmap, feature, or requirement-discovery changes, include traceability and validation completeness in the review criteria.
- Open or create one review thread file and record the initial review metadata there.

**Step 10 — Fix review findings**
- Critical and High findings must be fixed.
- Medium findings: fix or record as future work with justification.
- Low and design-only findings: recording is sufficient.
- Before changing code or documents, append the implementation response plan to the active review thread file.

**Step 11 — Re-check tests, docs, and validation evidence**
- Re-check tests according to `rules/testing.md`, including regression gaps and actor-analysis expectations.
- Re-check that the intended user-visible validation still makes sense after the implementation and review fixes.

**Step 12 — Run follow-up review**
- Verify that fixes did not introduce new problems.
- Confirm final linter and test suite pass.
- Confirm that traceability from user intent to roadmap item to delivered work is still visible.
- Explicitly acknowledge remaining risks.
- Append the follow-up review to the same review thread file instead of creating a sibling file.

**Step 13 — Commit**
- Stage files explicitly by name. Do not use `git add -A`.
- Do not commit runtime or generated files.

**Step 14 — Update roadmap and feature state**
- Mark completed tasks with `[x]`.
- Add newly discovered issues or future tasks to the roadmap or features as appropriate.
- Clarify the next task to be tackled.
- If a deferred feature changed state, update the feature documents too.
