# Language Policy

## Project Policy

- Development Language: (define after project setup)
- Documentation Language: (define after project setup)
- Code-Internal Language: English
- Supported Product Languages: (define in development planning or release planning)

## Purpose

This document defines how language is divided across the project.

Here, "language" includes:

- programming language
- project documentation language
- user-facing communication language
- commit message language
- code-internal language
- product text language

The purpose of this policy is:

- to define which kind of content is written in which language
- to prevent user-facing text from collapsing into mixed-language or internal-jargon-heavy output
- to separate English-only code rules from project-document and communication rules
- to make language setup explicit during project setup and major process redesign

## Language Categories

### 1. Development Language

- Meaning:
  - the programming language used to build the system
- Covers:
  - implementation code
  - long-lived services
  - adapters
  - sidecars
  - pipelines
  - helper scripts
- Decision rule:
  - follow architecture decisions or equivalent design decisions
- Notes:
  - this is separate from documentation and communication language

### 2. Documentation Language

- Meaning:
  - the shared language used for project documents, direct user communication, and commit message summaries
- Covers:
  - project-progress documents
  - design documents that evolve with project progress
  - development logs
  - review evidence
  - roadmap consultation messages
  - roadmap share messages
  - direct user explanations
  - commit message summaries
- Decision rule:
  - define it during project rule setup
- Notes:
  - in this project, dialogue language and commit message language are handled as part of Documentation Language

### 3. Code-Internal Language

- Meaning:
  - the language used inside code as a technical representation
- Covers:
  - identifiers
  - type names
  - function names
  - class names
  - module names
  - test names
  - code comments
  - API field names
- Decision rule:
  - fixed to English
- Notes:
  - this does not follow Documentation Language

### 4. Product Language

- Meaning:
  - the language or language set supported by the product for user-visible product text
- Covers:
  - UI text
  - user-facing error messages
  - status text
  - help text
  - onboarding text
- Decision rule:
  - decide it in development planning or release planning
- Notes:
  - this does not have to match Documentation Language

## Document Language Rules

### Stable Rule Documents

- Stable, low-transaction rule documents should be written in English.
- This includes documents whose purpose is to define reusable policy or general operating rules rather than record project progress.
- Typical examples:
  - rule documents under `rules/`

### Project-Progress Documents

- Documents that evolve with project progress should be written in Documentation Language.
- Typical examples:
  - roadmap documents
  - design documents tied to current project evolution
  - development logs
  - review evidence
  - backlog and feature planning artifacts
  - ADRs and project decisions unless the project explicitly chooses otherwise
  - user-facing messages generated from project templates

### README Documents

- README documents must exist in English.
- README documents may also exist in Documentation Language.
- If both exist, the English README is mandatory and the Documentation Language README is additional.

## Writing Rules

### For Documentation Language

- Content covered by Documentation Language should be written consistently in that language.
- Do not drift into partial English without reason.
- Standardized proper nouns, product names, protocol names, and code identifiers may remain unchanged.
- When technical or internal terms are necessary, explain the plain-language meaning first and add the internal term only as a supplement.
- Do not make internal document names or internal IDs the subject of user-facing explanations.

### For User-Facing Communication

- User-facing communication follows Documentation Language unless an explicit exception is declared.
- Do not assume the user knows internal identifiers, abbreviations, file names, milestone names, or feature IDs.
- Explain user meaning first, then add internal references only if they improve traceability.
- Explain not only what will be built, but also why it matters and what experience change it creates.

### For Commit Messages

- Commit message summaries follow Documentation Language.
- The type prefix remains the existing controlled vocabulary:
  - `feat`
  - `fix`
  - `docs`
  - `refactor`
  - `test`
  - `chore`
  - `style`
- The summary text itself follows Documentation Language.

### For Code-Internal Language

- Code-internal naming and comments are fixed to English.
- Documentation Language must not replace English inside code structure.
- Code-internal error messages, log messages, and exception messages follow Code-Internal Language.
- If a product-facing string is embedded in code, that string follows Product Language rules.

### For Product Language

- UI text follows Supported Product Languages.
- Product-facing error messages follow Supported Product Languages.
- Product-facing status and help text follow Supported Product Languages.
- Product-facing text must not silently fall back to Code-Internal Language unless that fallback behavior is explicitly accepted in project planning.

## Language Policy Setup Flow

During new project setup, or when the project undergoes major process redesign, decide the following in order:

1. Development Language
- what the primary implementation language is
- what any secondary language is allowed to do

2. Documentation Language
- what language project-progress documents, direct user communication, and commit summaries use

3. Code-Internal Language
- confirm that code-internal language is English

4. Product Language
- what supported product languages the product provides

5. Exception Rule
- where exceptions are recorded
- who decides them

## Exception Handling

- If a temporary exception is allowed, record the reason and scope explicitly.
- Do not leave language exceptions as implicit practice.
- If an exception becomes long-lived, reflect it in this document or in a related ADR.

## Notes

- This document defines language domains and their boundaries.
- Naming conventions, commit format, and code-style specifics are defined in other rule documents.
