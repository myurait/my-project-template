# Roadmap Consultation Template

Use this template when asking the user to choose the next roadmap direction.

This is a direct user-facing message template, not an internal planning memo.
It should help the user quickly understand where the product stands against the ideal experience and what decision is being requested now.

## Usage Principles

- Generate the final user-facing message in the Documentation Language defined in `rules/language-policy.md`.
- Explain the user meaning first, then add internal document names or identifiers only if they improve traceability.
- Do not make internal labels such as `feature-003`, `epic-001`, or `roadmap_...` the subject of the main message.
- If technical or internal terms are necessary, explain the plain-language meaning first and add the internal term only as a supplement.
- Prefer the wording and experience framing used in `design/00-ideal-experience.md`.
- Keep one consultation message focused on one decision.
- Emphasize "which part of the ideal experience this roadmap will close" before listing implementation work.

## Template

### 1. Why This Roadmap Consultation Is Happening

- State one of the following first:
  - the previous roadmap has been completed
  - the current roadmap needs a major correction

### 2. Current Position Against the Ideal Experience

- Relevant ideal experience area:
  - describe it in plain language instead of citing the document section as the main explanation
- What already works:
  - what the user can already do today
- What is still missing:
  - what remains inconvenient or incomplete for the user
- Progress view:
  - which ideal-experience pillars have already advanced
  - which pillars are still clearly behind

### 3. The Decision Requested From the User

- Write this in one sentence.
- Example:
  - Decide which missing part of the ideal experience should be prioritized in the next roadmap.

### 4. Recommended Direction

- Recommendation:
  - write it in plain language
- Why this is recommended:
  - how much it advances the ideal experience
  - how much it removes blockers for other strong candidates
  - what change the user would actually feel

### 5. Other Options

- Option A:
  - what it would advance
  - strengths
  - weaknesses
- Option B:
  - what it would advance
  - strengths
  - weaknesses

### 6. What This Roadmap Would Advance

- If this is chosen, this part of the ideal experience moves forward:
- This part still would not be addressed yet:
- Expected user-visible change after the roadmap completes:

### 7. What Would Still Remain Afterward

- Remaining gaps in the ideal experience:
- The next major decision likely to follow:

### 8. Closing Question

- End with one short, direct question.
- Do not combine multiple unrelated decisions in the same closing question.

## Bad Directions

- `We should do feature-003 first.`
- `We need to fix the context memory model before narrowing the dispatcher boundary.`
- `We will place roadmap_202604... in current.`

## Better Direction Examples

- `I think the next roadmap should first reduce the need for users to repeat the same context.`
- `The main reason is that the biggest current frustration is still the amount of manual explanation required before work can begin.`
- `If we choose this direction now, the next stage can build more advanced automation on stable foundations.`
