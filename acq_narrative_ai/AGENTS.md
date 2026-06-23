# Sales Account Research & Pitch Narrative Agent Skill

## Workspace Purpose

This repository is an Agent Skill package for creating evidence-grounded sales account research and pitch narratives. It is intended to help an AI agent turn account inputs, business signals, and sales context into concise, usable account briefs and pitch angles for acquisition, expansion, or renewal conversations.

## Package Shape

- `SKILL.md`: primary Codex skill instructions and trigger metadata.
- `References/`: domain guidance that should be loaded only when needed.
- `Assets/`: schemas, examples, scorecards, and sample data used to validate or demonstrate the workflow.
- `scripts/tools/`: deterministic validators and quality checks.
- `outputs/`: generated artifacts. Do not commit sensitive real account data here.
- `tests/`: tests for scripts, schemas, and example outputs.

## Working Rules

- Keep the skill concise. Put detailed domain rules, examples, rubrics, and long lists in `References/` or `Assets/`, then link to them from `SKILL.md`.
- Do not invent company facts, customer proof points, account relationships, financials, initiatives, or buying signals. Mark unknowns clearly and separate evidence from inference.
- Preserve provenance. Every claim used in a pitch narrative should map back to a supplied input field, cited source, or explicitly labeled assumption.
- Avoid manipulative, exaggerated, or fear-based sales language. Pitch narratives should sound specific, useful, and commercially credible.
- Treat account data as confidential. Use redacted samples in examples and tests.
- Prefer deterministic checks for schema validity, evidence mapping, forbidden phrases, and output scoring once the scripts are implemented.

## Current Build Status

The repository currently contains placeholder reference, asset, script, and test files. When continuing the package build, populate these in this order:

1. Business context and input/output schemas.
2. Priority signal definitions and pitch angle library.
3. Do-not-say rules, coaching best practices, output examples, and quality rubric.
4. Validation scripts and tests.

Update `SKILL.md` whenever a new resource becomes required for the agent workflow.
