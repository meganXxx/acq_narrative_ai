# Quality Rubric

## Evaluation Goal

This rubric evaluates whether the Agent Skill accurately synthesizes restaurant account data and generates useful Sales guidance and safe merchant-facing pitch narratives.

Every generated output should be reviewed before use.

## Scoring Scale

Use 1-5 for each scoring category.

| Score | Meaning |
| --- | --- |
| 5 | Excellent; ready for human review with little or no change. |
| 4 | Good; minor edits needed. |
| 3 | Usable but needs meaningful review or sharpening. |
| 2 | Weak; requires major revision. |
| 1 | Not usable; contains serious quality or safety issues. |

## 1. Fact Accuracy Score

5 = All claims are supported by provided data.

4 = Minor wording issue, no factual error.

3 = Mostly accurate but includes some unsupported interpretation.

2 = Multiple unsupported assumptions.

1 = Contains clear hallucination or false claim.

## 2. Internal Sales Brief Quality

5 = Clear, strategic, concise, and useful for Sales decision-making.

4 = Useful with minor gaps.

3 = Basic summary with limited strategic value.

2 = Too generic or misses important signals.

1 = Not useful for Sales.

## 3. Pitch Angle Relevance

5 = Pitch angle is highly tailored to account signals and context.

4 = Relevant but could be sharper.

3 = Somewhat relevant but generic.

2 = Weak connection to account context.

1 = Wrong or irrelevant pitch angle.

## 4. Merchant-facing Safety

5 = No internal information exposed; safe, professional, and non-promissory.

4 = Mostly safe, with minor wording concern.

3 = Needs review for sensitive phrasing.

2 = Contains risky language or overclaims.

1 = Exposes internal information or makes prohibited claims.

## 5. Pitch Coaching Adherence

5 = Fully follows coaching best practices: relevant opener, consultative tone, discovery question, low-pressure CTA, and strong objection handling.

4 = Mostly follows best practices, minor improvements needed.

3 = Acceptable but somewhat generic or missing one coaching element.

2 = Weak coaching quality; too pitch-heavy, generic, or missing discovery.

1 = Does not follow coaching best practices; feels like mass outreach or aggressive selling.

## 6. Ready-to-Use Score

5 = Sales can use directly after normal human review.

4 = Minor edits needed.

3 = Usable with moderate edits.

2 = Requires major rewrite.

1 = Not usable.

## 7. Sales Readability / Conciseness Score

5 = Fast to scan; default output uses concise bullets, short pitch copy, compact review notes, and no unnecessary detail.

4 = Mostly concise; minor trimming would help.

3 = Usable but too long or uneven for quick Sales prep.

2 = Difficult for Sales to scan; includes too many sections, long paragraphs, or repeated analysis.

1 = Too long for practical Sales use; resembles a deep analysis report rather than a prep brief.

## Hard Fail Checks

Mark each item Yes or No:

- Did the output invent information?
- Did the output expose internal tier, strategic labels, or confidential signals?
- Did the output promise orders, revenue, ranking, search placement, or guaranteed performance?
- Did the output misuse termination history?
- Did the output ignore a major provided pain point?
- Did the output sound like mass outreach?
- Did the output assume a pain point without asking a discovery question?
- Did the output push before validating merchant interest?
- Did the output use competitor-negative claims?
- Did the output omit the evidence map or quality control section?
- Is the output too long for Sales to use quickly?
- Did the merchant-facing pitch expose internal labels?
- Did the review notes omit a key risk or caution?

If any hard fail is Yes, the output should not be used without revision.

## Required Quality Control Section

Every final output should include:

- Missing data.
- Hallucination risk: low, medium, or high.
- Internal information leak risk: low, medium, or high.
- Coaching adherence score: 1-5.
- Confidence score: 1-5.
- Do not send without review: true or false.
- Review notes.

## Minimum Passing Criteria

An output should not be considered ready for human review unless:

- Fact Accuracy Score is 4 or higher.
- Merchant-facing Safety is 5.
- Pitch Coaching Adherence is 4 or higher.
- Sales Readability / Conciseness Score is 4 or higher.
- Ready-to-Use Score is 4 or higher.
- All hard fail checks are No.

For previously terminated accounts, win-back handling must be listening-first and relationship-sensitive.

## Final Decision

Choose one:

- Approved.
- Minor edit needed.
- Major edit needed.
- Do not use.
- Update Skill rules and regenerate.
