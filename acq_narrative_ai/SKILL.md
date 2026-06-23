---
name: sales-account-research-pitch-narrative
description: Build evidence-grounded sales account research briefs and pitch narratives from supplied account data, market context, buying signals, and seller objectives. Use when Codex needs to research or synthesize target accounts, prioritize account signals, identify pitch angles, produce outreach or meeting narrative guidance, map claims to evidence, check sales messaging quality, or validate outputs against account-research schemas and guardrails.
---

# Sales Account Research & Pitch Narrative

## Purpose

Use this skill to help food delivery platform Sales teams prepare tailored, account-specific research summaries and pitch narratives for restaurants that may be invited to join, rejoin, or expand a partnership with the platform.

Generate concise Sales-ready outputs by default:

1. A Sales Context Summary for fast internal prep.
2. A Merchant-facing Pitch Narrative that Sales can use or lightly edit after human review.
3. Compact Review Notes with evidence used, risks, confidence, and human-review status.

Prioritize factual accuracy, evidence-based reasoning, consultative Sales coaching quality, and strict separation between internal strategy signals and merchant-facing language. This is a Sales support tool, not an autonomous outreach sender.

## Resource Map

Load only the resources needed for the task. Use `PROJECT_CONTEXT.md` first when a concise repo-level summary is enough.

- `References/01_business_context.md`: business model, seller objective, target users, and package assumptions.
- `References/02_input_data_dictionary.md`: expected account fields and meaning.
- `References/03_priority_signal_definitions.md`: signal taxonomy and priority rules.
- `References/04_pitch_angle_library.md`: reusable pitch-angle patterns.
- `References/05_pitch_coaching_best_practices.md`: guidance on seller-ready narrative style.
- `References/06_do_not_say_rules.md`: prohibited claims, phrases, and messaging patterns.
- `References/07_output_examples.md`: examples of accepted output shape and tone.
- `References/08_quality_rubric.md`: scoring criteria for final outputs.
- `Assets/input_schema.json`: structured account input schema.
- `Assets/output_schema.json`: structured output schema.
- `Assets/sample_accounts_redacted.json`: safe sample data for tests and demonstrations.
- `Assets/evaluation_scorecard.csv`: manual or automated evaluation criteria.
- `Assets/manual_poc_sheet_columns.csv`: spreadsheet-oriented proof-of-concept column definitions.
- `Assets/prompt_manual_poc.md`: manual workflow prompt, if a spreadsheet proof of concept is requested.

For merchant-facing pitch content, always use `References/05_pitch_coaching_best_practices.md` when available. For detailed field meanings and allowed-use boundaries, use `References/02_input_data_dictionary.md`.

## Core Workflow

1. Clarify the sales motion, audience, account list, output format, and constraints.
2. Inspect supplied account data before drafting. If schemas are available, validate inputs against `Assets/input_schema.json`.
3. Load the minimum relevant references:
   - Business scenario and output expectations: `References/01_business_context.md`.
   - Input fields and allowed use: `References/02_input_data_dictionary.md`.
   - Internal priority signals: `References/03_priority_signal_definitions.md`.
   - Pitch angle selection: `References/04_pitch_angle_library.md`.
   - Merchant-facing coaching: `References/05_pitch_coaching_best_practices.md`.
   - Prohibited claims and phrases: `References/06_do_not_say_rules.md`.
   - Examples or scoring only when needed: `References/07_output_examples.md`, `References/08_quality_rubric.md`.
4. Build an evidence map before finalizing claims.
5. Identify internal priority signals, relationship sensitivities, missing data, and termination or win-back context.
6. Select pitch angles supported by evidence. Convert weak evidence into discovery questions.
7. Draft the requested outputs using the concise Sales-ready default format unless the user asks for detailed mode.
8. Run quality checks when scripts are implemented:
   - `scripts/tools/validate_input_schema.py`
   - `scripts/tools/validate_output_schema.py`
   - `scripts/tools/evidence_map_checker.py`
   - `scripts/tools/forbidden_phrase_checker.py`
   - `scripts/tools/score_poc_outputs.py`
9. Revise until the output is grounded, merchant-safe, consultative, and ready for human review.

## Manual POC First

Support manual proof-of-concept work before automation: clear inputs, spreadsheet-friendly outputs when useful, manual evidence mapping, and human quality review. Automation, schemas, and validators should support a proven workflow rather than replace Sales judgment too early.

## Critical Confidentiality Rule

Internal information may be used in the Internal Sales Account Brief.

Merchant-facing copy must not expose:

- A/B/C/D merchant potential tier.
- Top Search.
- Dream Brand.
- Low Choice.
- Internal search terms.
- Internal scoring.
- Internal prioritization logic.
- Internal performance data.
- Confidential transcript details.
- Confidential Sales notes.
- Non-public termination details.

Translate internal signals into neutral, merchant-safe language grounded in public or merchant-provided facts. See `References/03_priority_signal_definitions.md` and `References/06_do_not_say_rules.md` for safe translations and prohibited wording.

## Accuracy and Anti-Hallucination Rules

- Use only information provided in the input, approved references, or clearly cited user-provided sources.
- Do not invent restaurant facts, cuisine details, menu items, owner names, manager names, ownership information, customer demand, financial performance, historical objections, pain points, termination reasons, or competitor contract details.
- Do not claim a restaurant has a pain point unless supported by transcript, notes, termination reason, known objection, historical data, or explicit user input.
- Label indirectly inferred pain points as "Hypothesis, needs validation."
- Do not promise revenue, orders, ranking, search placement, customer acquisition, profitability, delivery volume, ROI, or guaranteed performance.
- Do not use competitor-negative claims or criticize competitor platforms.
- Do not generate merchant-facing content that sounds like mass outreach.
- If termination status applies, use only the supplied termination reason. If none is provided, state "Termination reason not provided."
- If information is missing, state that it is missing in the internal brief and generate a lower-confidence pitch.
- If a claim is used in the pitch, it must be traceable to an input field or approved reference.
- Use cautious language when uncertain: "may", "could", "appears", "based on the available information", or "it may be worth exploring."

## Sales Coaching Rules

Merchant-facing content must follow `References/05_pitch_coaching_best_practices.md`.

Lead with relevance, use a safe account-specific opener, present hypotheses as hypotheses, connect to platform value without promises, ask discovery questions, use a low-pressure CTA, and keep the language easy for a Sales representative to say aloud.

For previously terminated, churned, paused, or rejected accounts, use win-back and listening-first handling. Do not lead with a generic acquisition pitch.

## Output Part 1: Sales Context Summary

Default to a concise internal-facing summary for fast Sales prep. Use 4-6 bullets only. The section may mention internal signals because it is internal-facing.

Include:

- Who the restaurant is: location, cuisine, and key public signals if provided.
- Why the account matters: based on internal signals, without reusing those labels in merchant-facing language.
- Key known context: transcript insights, objections, prior partnership, or termination reason if provided.
- Likely sales angle: demand-led, strategic brand, local opportunity, incremental channel, win-back, operational support, reputation leverage, or consultative discovery-first.
- Key caution: missing data, unresolved objection, termination risk, or claim to avoid.
- Next best action.

Keep bullets short. Do not write long paragraphs.

For detailed field handling, termination guidance, and pitch angle patterns, use `References/02_input_data_dictionary.md`, `References/03_priority_signal_definitions.md`, and `References/04_pitch_angle_library.md`.

## Output Part 2: Pitch Narrative

Generate merchant-facing content that Sales can use or lightly edit. It must be customized, safe, consultative, and free of internal labels or confidential data.

Include:

- `Call Opening`: 2-3 professional, consultative, low-pressure sentences.
- `Email / Message`: 80-130 English words. Include a safe account-specific opener, reason for reaching out, platform value connection, and discovery question or soft CTA.
- `Follow-up`: 1-2 short sentences.
- `Objection Handling`: only 1-2 likely objections. If input provides known objections, use those. If no objections are provided, use safe general objections.

Use `References/05_pitch_coaching_best_practices.md` for structure and tone. Use `References/06_do_not_say_rules.md` before finalizing. If no objections are provided, use only general safe objections; do not invent account-specific objections.

## Output Part 3: Review Notes

Default to compact review notes instead of a full evidence map table or long quality control section. Use 3-5 bullets only.

Include:

- Evidence used: short source field list, not a full evidence table.
- Do-not-say items.
- Missing or uncertain data.
- Hallucination/internal leak risk: low, medium, or high.
- Confidence score: 1-5.
- Human review required.

If evidence is weak, use discovery questions rather than assertive claims. Use `References/08_quality_rubric.md` for score definitions and minimum passing criteria.

## Default Output Format

Use this concise Sales-ready structure for each account unless the user asks for detailed mode:

```markdown
# Account: [restaurant_name] ([account_id])

## 1. Sales Context Summary

- [4-6 concise bullets only]

## 2. Pitch Narrative

### Call Opening

### Email / Message

### Follow-up

### Objection Handling

## 3. Review Notes

- Evidence used:
- Do-not-say items:
- Missing or uncertain data:
- Hallucination/internal leak risk:
- Confidence score:
- Human review required:
```

## Detailed Mode

If the user asks for "detailed mode", "full account brief", "full evidence map", or "full quality control", generate the longer format:

- Internal Sales Account Brief with Account Snapshot, Strategic Priority Signals, Commercial Potential, Historical Context, Termination / Win-back Context, Online Footprint, Likely Merchant Pain Points, Recommended Sales Strategy & Coaching Guidance, Best Pitch Angles, Risks and Cautions, and Next Best Action.
- Merchant-facing Pitch Narrative with Call Opening, Email Subject, Email Body, WhatsApp / Short Message, Follow-up Message, and Objection Handling.
- Full Evidence Map table with Claim, Source Field, Internal Only, and Safe for Merchant.
- Full Quality Control with missing data, hallucination risk, internal info leak risk, coaching adherence score, confidence score, do-not-send-without-review flag, and review notes.

## Handling Missing Resources

This package may be built incrementally. If a referenced file is empty or absent, continue with the best available instructions, clearly note the missing resource, and avoid presenting placeholder guidance as package policy.

## Portability and Data Policy

Keep guidance portable for company-approved AI environments, including Gemini Pro, Gemini Gems, or other approved tools. Do not rely on hidden local state, proprietary tool behavior, or undocumented assumptions.

Do not add real company data, real merchant confidential data, or sensitive account information to this repo. Use fictional, redacted, or synthetic examples only.

## Final Instruction

This skill is a Sales support tool, not an autonomous outreach sender. It must not send messages, imply that outreach has been sent, or bypass Sales judgment.

All merchant-facing content must be reviewed by a human Sales representative before use.
