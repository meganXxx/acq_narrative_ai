# Sales Account Research & Pitch Narrative Agent Skill

## Project Overview

This repository is a portable documentation-based Agent Skill package for food delivery platform Sales teams.

The skill helps Sales representatives, Business Development teams, Sales managers, and Sales enablement teams prepare tailored account research and pitch narratives for restaurants they may invite to join the platform, reactivate, or approach through win-back outreach.

The Sales pain point is simple: reps often do not have enough time to conduct holistic account research and turn account-specific data into a tailored, evidence-grounded pitch narrative.

## What This Skill Generates

The skill generates a concise Sales-ready output by default:

1. Sales Context Summary

   A fast internal prep summary with 4-6 bullets covering account context, why it matters, likely angle, key caution, and next best action. This section may use internal signals and internal context.

2. Pitch Narrative

   Seller-ready call opening, email/message, follow-up, and concise objection handling that Sales can use or lightly edit after human review. This copy must not expose internal labels, confidential signals, or unsupported claims.

3. Review Notes

   Compact notes covering evidence used, do-not-say items, missing or uncertain data, risk level, confidence score, and human-review requirement.

Detailed mode is available when a user explicitly asks for a full account brief, full evidence map, full quality control, or detailed mode.

## Core Principles

- Factual accuracy: use only supplied account data, approved references, or cited user-provided sources.
- Evidence-based reasoning: every material claim should map to an input field, source, labeled inference, or missing-data note.
- No hallucinated facts: do not invent restaurant facts, pain points, menu items, owner names, termination reasons, demand claims, or performance claims.
- Internal vs merchant-facing separation: internal Sales reasoning may inform strategy, but must not leak into merchant-facing copy.
- Consultative sales coaching: lead with relevance, ask discovery questions, use low-pressure language, and avoid aggressive selling.
- Human review before use: all merchant-facing content must be reviewed by a human Sales representative before sending.

## Repository Structure

- `AGENTS.md`: workspace instructions and build rules for agents working in this repo.
- `SKILL.md`: the main Agent Skill instruction file and resource router.
- `PROJECT_CONTEXT.md`: concise source-of-truth project summary.
- `References/`: modular domain guidance loaded as needed by the skill.
- `Assets/`: planned schemas, sample data, prompt templates, and evaluation artifacts. Some files may still be placeholders.
- `scripts/tools/`: planned deterministic validation and scoring scripts. Current files may be placeholders until implemented.
- `tests/`: planned tests for schemas, scripts, and example outputs.
- `outputs/`: generated artifacts. Do not store sensitive real account data here.

## Reference Files

- `References/01_business_context.md`: business scenario, Sales motion, platform value themes, output expectations, and human review requirement.
- `References/02_input_data_dictionary.md`: account input fields, allowed use, and what not to infer from each field.
- `References/03_priority_signal_definitions.md`: internal priority signals, Sales meaning, merchant-safe phrasing, and do-not-say examples.
- `References/04_pitch_angle_library.md`: pitch angle options and signal-to-angle mapping.
- `References/05_pitch_coaching_best_practices.md`: consultative sales methodology, discovery questions, channel guidance, and objection handling.
- `References/06_do_not_say_rules.md`: forbidden internal labels, overpromises, invented facts, aggressive language, and safer alternatives.
- `References/07_output_examples.md`: fictional examples showing safe internal interpretation and merchant-facing phrasing.
- `References/08_quality_rubric.md`: scoring criteria, hard fail checks, quality control fields, and final decision guidance.

## Data Safety and Confidentiality

Do not put real confidential company data into this repo.

Do not store real account exports, real transcripts, real internal search terms, real performance data, or real merchant contact details in this portable package.

Internal signals may be used for internal brief generation, but they must not appear in merchant-facing pitch copy.

Merchant-facing copy must not expose:

- A/B/C/D tier.
- Top Search.
- Dream Brand.
- Low Choice.
- Internal search terms.
- Internal scoring.
- Confidential transcript details.
- Internal performance data.

## What Not To Do

- Do not use this as an autonomous outreach sender.
- Do not skip human review.
- Do not use personal AI accounts for confidential company data.
- Do not promise orders, revenue, ranking, search placement, customer acquisition, ROI, or guaranteed performance.
- Do not invent merchant facts, pain points, menu items, owner names, manager names, or termination reasons.
- Do not criticize competitors or claim the platform outperforms them.
- Do not add real company data to sample files, assets, tests, or outputs.
- Do not expose internal Sales reasoning in merchant-facing copy.


## Future Automation Path

Stage 1: Manual POC

- Use approved AI tools manually with fictional, redacted, or approved test accounts.
- Evaluate outputs with the quality rubric.
- Refine the skill and references.

Stage 2: Semi-automated Workspace workflow

- Use an approved Google Sheet or Workspace-based workflow.
- Standardize input columns and output columns.
- Add manual review gates.
- Use schemas and scorecards once populated.

Stage 3: Production automation

- Use approved APIs and infrastructure only.
- Potential components may include BigQuery, Vertex AI or Gemini API, CRM integration, deterministic validation, logging, monitoring, and a human approval gate.
- Do not automate merchant outreach without approved governance and human review.

## Current Status / Next Steps

- [x] Initial `AGENTS.md`
- [x] Initial `SKILL.md`
- [x] `References/` populated
- [x] Manual POC prompt
- [x] Sample redacted accounts
- [ ] POC test run
- [ ] Evaluation scorecard
- [ ] Optional validation scripts
