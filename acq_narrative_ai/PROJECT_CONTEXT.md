# Sales Account Research & Pitch Narrative Agent Skill

## Project Summary

This repo contains an Agent Skill package for creating evidence-grounded sales account research and pitch narratives.

The business scenario is a food delivery platform Sales team, such as a global platform or local brand, contacting restaurants to invite them to join, rejoin, or expand their partnership with the platform.

## Sales Pain Point

Sales reps lack time to conduct holistic account research and convert account-specific data into a tailored pitch narrative. The skill helps synthesize internal signals, relationship history, online footprint, and Sales notes into seller-ready guidance.

## Target Users

- Sales reps.
- Business Development teams.
- Sales managers.
- Sales enablement teams.

## Expected Outputs

1. Internal Sales Account Brief.
2. Merchant-facing Pitch Narrative.

The Internal Sales Account Brief supports Sales decision-making and may include internal signals. The Merchant-facing Pitch Narrative must be safe for a restaurant owner, manager, or operator after human review.

## Input Data Types

Inputs may include:

- Restaurant name, country, city, location, and cuisine.
- Merchant potential tier A/B/C/D.
- Strategic priority signals: Top Search, search terms, Dream Brand, Low Choice.
- Historical transcript summary.
- Previously discussed pain points.
- Known objections.
- Prior partnership status.
- Termination status and termination reason.
- Historical performance summary.
- Online footprint: Google rating, Google review count, competitor platform presence, Instagram followers, website, menu URL.
- Sales notes.
- Data quality notes.
- Pitch coaching best practices library.

## Internal vs Merchant-facing Separation

Internal signals can be used in the Internal Sales Account Brief.

Internal signals must not be exposed in merchant-facing copy. Merchant-facing content must not mention merchant potential tier, Top Search, search terms, Dream Brand, Low Choice, internal scoring, internal prioritization, internal performance data, confidential transcript details, or non-public Sales notes.

Merchant-facing copy may be informed by internal signals only after translating them into neutral, safe, evidence-grounded language.

## Anti-hallucination Rules

Do not invent restaurant facts, pain points, menu items, owner names, manager names, termination reasons, performance claims, demand claims, customer behavior, competitor contract details, or future outcomes.

Do not promise revenue, orders, ranking, search placement, customer acquisition, profitability, delivery volume, ROI, or guaranteed performance.

Every material claim should map to supplied input, a provided source, a clearly labeled inference, or a missing-data note. Weak evidence should become a discovery question, not an assertion.

## Pitch Coaching Requirement

Merchant-facing pitch narratives must follow consultative sales coaching best practices:

- Start from safe, specific evidence.
- Connect to a relevant possible business conversation.
- Use low-pressure language.
- Ask discovery questions.
- Respect known objections and prior relationship context.
- Use win-back and listening-first handling for previously terminated, churned, paused, or rejected accounts.

Human review is required before any merchant-facing content is used.

## Manual POC First Approach

Build and validate the workflow manually first before automating. Initial proof-of-concept work should prioritize:

- Clear inputs and output formats.
- Spreadsheet-friendly columns where useful.
- Fictional or redacted sample accounts.
- Manual evidence mapping.
- Manual quality review against the rubric.

Automation, schemas, and validators should support the proven manual workflow rather than replace judgment too early.

## Portability Requirement

Content should be portable to a company-approved AI environment, including Gemini, Gemini Gems, or another approved internal tool. Keep instructions clear, vendor-neutral where possible, and easy to reuse outside this local repo.

Avoid relying on hidden local state, proprietary tool behavior, or undocumented assumptions.

## Data Policy

No real company data, real merchant confidential data, or sensitive account information should be stored in this repo.

Use fictional, redacted, or synthetic examples only. Treat account data as confidential, and keep generated outputs with sensitive information out of versioned files.
