---
name: sales-account-research-pitch-narrative
description: Build evidence-grounded sales account research briefs and pitch narratives from supplied account data, market context, buying signals, and seller objectives. Use when Codex needs to research or synthesize target accounts, prioritize account signals, identify pitch angles, produce outreach or meeting narrative guidance, map claims to evidence, check sales messaging quality, or validate outputs against account-research schemas and guardrails.
---

# Sales Account Research & Pitch Narrative

## Purpose

Use this skill to help food delivery platform Sales teams prepare tailored, account-specific research summaries and pitch narratives for restaurants that may be invited to join, rejoin, or expand a partnership with the platform.

Generate concise Sales-ready outputs by default:
1. A Sales Context Summary for fast internal prep.
2. A Merchant-facing Pitch Narrative structured by relationship temperature and delivery channel.
3. Compact Review Notes classifying evidence tiers and validating compliance thresholds.

Prioritize factual accuracy, evidence-based reasoning, advanced consultative Sales coaching frameworks, and strict separation between internal strategy signals and merchant-facing language. This is a Sales support tool, not an autonomous outreach sender.

---

## Resource Map

Load only the resources needed for the task. Use `PROJECT_CONTEXT.md` first when a concise repo-level summary is enough.

* `References/01_business_context.md`: Business model, primary value themes, output parameters, and strict compliance boundaries.
* `References/02_input_data_dictionary.md`: Expected account fields, meaning, and data boundaries.
* `References/03_priority_signal_definitions.md`: Signal taxonomy and priority rules.
* `References/04_pitch_angle_library.md`: Strategic signal-to-angle mapping matrix, strategic logic, and safe merchant before/after rewrite specifications.
* `References/05_pitch_coaching_best_practices.md`: Structured SPIN question sequencing, the LUPP objection framework, temperature playbooks, and critical failure modes.
* `References/06_do_not_say_rules.md`: Prohibited claims, phrases, and messaging patterns.
* `References/07_output_examples.md`: Examples of accepted output shape and tone.
* `References/08_quality_rubric.md`: Scoring criteria for final outputs.

---

## Core Operational Workflow

The system must execute tasks in the following sequential order:
[ Step 1: Input Analysis ] -> Validate data integrity and catch missing metrics.
↓
[ Step 2: Signal Isolation] -> Map data to the 7 Pitch Angles (Ref/04).
↓
[ Step 3: SPIN Diagnostics] -> Sequence discovery questions (Ref/05).
↓
[ Step 4: LUPP Strategy   ] -> Build custom objection paths (Ref/05).
↓
[ Step 5: Multi-Tier Draft] -> Generate segmented Cold/Warm/Engaged copy.
↓
[ Step 6: Automated Audit ] -> Filter via compliance and failure-mode checks.
### 1. Input Analysis & Verification
Inspect supplied account data before drafting. Validate inputs against `Assets/input_schema.json` if available. Identify missing data elements required to establish an operational baseline. If essential values are missing, log them as discovery priorities.

### 2. Strategic Signal Isolation
Consult `References/03_priority_signal_definitions.md` and `References/04_pitch_angle_library.md` to map account signals (e.g., historical termination, competitor presence, public brand footprints) to their corresponding strategic pitch angles. Identify relationship sensitivities or win-back requirements.

### 3. SPIN Diagnostic Sequencing
Formulate a discovery question path using the structural progression outlined in `References/05_pitch_coaching_best_practices.md`:
* **Situation:** Establish factual baselines.
* **Problem:** Identify operational bottlenecks or friction points.
* **Implication:** Surface the long-term cost of leaving those issues unaddressed.
* **Need-Payoff:** Guide the merchant to articulate the value of an operational solution.

### 4. LUPP Objection Framework Setup
Map documented or anticipated objections against the restaurant-specific resolution matrices in `References/05_pitch_coaching_best_practices.md`. Script all dynamic objection handling text to follow the strict sequence: **Listen $\rightarrow$ Unpack $\rightarrow$ Prescribe $\rightarrow$ Pivot**.

### 5. Multi-Tier Narrative Generation
Draft the default concise output format. For merchant-facing content, generate variations matched specifically to relationship states (**Cold, Warm, Engaged**) across distinct delivery mediums (Phone, Email, In-Store), strictly applying the before/after rewrite panels found in `References/04_pitch_angle_library.md`.

### 6. Automated Quality Audit
Run final outputs through the safety filters in `References/01_business_context.md` and the failure-mode checker in `References/05_pitch_coaching_best_practices.md`. If any programmatic verification scripts are implemented, call them to validate formatting thresholds.

---


## Critical Confidentiality & Compliance Boundaries

Internal information can be comprehensively utilized inside the internal Sales Context Summary. Merchant-facing copy **must never** expose, reference, or hint at:
* Alphabetical potential tiers (e.g., Tier A/B/C/D).
* Internal taxonomy terms (*"Top Search," "Dream Brand," "Low Choice"*).
* Specific internal search terms, exact search volumes, or ranking positions.
* Confidential sales notes, internal performance data logs, or call transcript details.
* Non-public termination reasons or historical internal scoring logic.

All sensitive internal data markers must be systematically translated into neutral, merchant-safe opportunities grounded exclusively in verifiable public facts, using the precise rewrite criteria established in `References/04_pitch_angle_library.md`.

---

## Accuracy and Anti-Hallucination Rules

* **Information Sourcing Constraint:** Use only information explicitly provided in the raw input data, approved reference files, or clearly cited user-provided sources. Do not assume, extrapolate, or inject external market knowledge.
* **Prohibition of Invention:** Do not invent or hallucinate restaurant facts, cuisine footprints, menu items, owner names, manager names, ownership background information, customer demand statistics, financial performance metrics, historical objections, pain points, termination reasons, or competitor contract details.
* **Pain Point Verification:** Do not claim or imply that a restaurant has a specific pain point unless it is supported directly and explicitly by a verified call transcript, active sales notes, termination logs, documented objections, historical data, or direct user input. Label all indirectly inferred pain points strictly as `"Hypothesis, needs validation."`
* **The Outcome Boundary:** Do not promise, guarantee, or project revenue growth, exact order spikes, search ranking placement, app visibility tier promotions, customer acquisition rates, profitability percentages, delivery volumes, ROI, or guaranteed performance benchmarks. Use cautious, consultative, risk-conscious language exclusively: `"may"`, `"could"`, `"appears"`, `"based on the available information"`, or `"it may be worth exploring."`
* **Traceability Requirement:** If an operational claim, observation, or angle is used in the merchant pitch narrative, it must be directly traceable back to an explicit raw input field or an approved asset/reference.
* **Competitor Integrity:** Do not use competitor-negative claims, criticize competitor platforms, or disparage third-party delivery services.
* **Authenticity Filter:** Do not generate merchant-facing content that sounds like boilerplate mass outreach, cold spam templates, or generic automated marketing copy.
* **Termination Handling Protocol:** If a historical termination status applies to the account, use *only* the supplied termination reason provided in the raw data. If no termination reason is explicitly provided in the input data, you must output exactly: `"Termination reason not provided."`
* **Data Gap Handling:** If baseline information is missing from the input source, explicitly state that the specific data points are missing in the internal brief, and scale down the merchant messaging into a lower-confidence, discovery-driven pitch.
* **Asymmetric Data Truncation Logic (Conditional Exclusion Gate):** You must apply a strict data availability filter before initializing output generation. Evaluate all historical data fields. If an account has no recorded past touchpoints, zero previous platform partnerships, or entirely blank historical notes, you must completely suppress that entire structural block from the final output. Generating defensive, generic, or passive placeholders such as "Previous Partnership: None", "Historical Notes: N/A", or "Objections: Unknown" is strictly prohibited. If data does not exist in the raw input array, its corresponding structure must be entirely omitted from the final presentation layer.

---

---

## Output Part 1: Sales Context Summary

Provide a concise, internal-facing tactical roadmap for fast sales preparation. Limit this section to **4-6 short, high-impact bullet points**. It may include internal strategic signals because it is completely hidden from the merchant.

Include:
* **Merchant Profile:** Absolute location baseline, cuisine category, and verified public operational data.
* **Account Prioritization Context:** Relevant internal buying signals, marketplace value, and strategic priority drivers without translating them into merchant-safe language yet.
* **Historical Context:** Prior partnership history, documented objections, or supplied termination reasons. If no termination details exist, explicitly state: *"Termination reason not provided."*
* **Strategic Playbook Route:** Recommended pitch angle selection (e.g., Demand-led, Incremental Channel, Win-back, etc.) based on available evidence.
* **Critical Cautions:** Flag missing metrics, unresolved operational landmines, or strict claims that the sales rep must avoid.
* **Next Best Action:** Immediate, clear step to advance the account.
* **Radical Conciseness Rule:** Compress all relevant, active merchant indicators into ultra-short, insight-dense bullet points. The use of conversational paragraphs, narrative phrasing, or transition sentences is strictly banned. The summary layout must be optimized for a total cognitive scan time of under 15 seconds by a human operator, featuring exclusively highly actionable operational facts and immediate tactical directives.

---

## Output Part 2: Pitch Narrative

Generate highly customized, consultative, seller-ready communication assets. Every script block must implement the stylistic constraints defined in `References/05_pitch_coaching_best_practices.md` and avoid the forbidden wording detailed in `References/06_do_not_say_rules.md`.

The narrative output must follow this mandatory structure:

### ### Call Opening
Provide a 2-3 sentence low-pressure opening block tailored for a telephone conversation. It must introduce the representative, state a relevant public fact, and ask permission to continue without jumping into an active sales pitch.

### ### Email / Message Playbook by Temperature
Generate targeted written assets (80-130 words per version) customized explicitly to the merchant's relationship status:
* **Cold (Unfamiliar):** Focus on building baseline credibility, establishing a localized observation, and executing a low-pressure permission check.
* **Warm (Interested):** Bridge the communication toward early **Problem/Implication** questions, highlighting operational control features like order throttling or custom radii.
* **Engaged (Ready):** Deploy **Need-Payoff** reflections and clear, actionable onboarding roadmap markers to finalize a setup date.

### ### Follow-up Message
Provide 1-2 ultra-concise, human-sounding follow-up sentences optimized for text or short messaging channels.

### ### Objection Handling (LUPP Execution)
Generate custom scripts handling the **two most likely objections** based on the account's operational context (e.g., competitor fee compression, kitchen capacity strains, or dine-in cannibalization). If no historical objections are supplied in the input data, use the standard safe operational objections defined in `References/05_pitch_coaching_best_practices.md`. Every script must explicitly structure its paragraphs into distinct **Listen, Unpack, Prescribe, and Pivot** statements.

---

## Output Part 3: Review Notes (Internal Validation)

Provide a compact quality checklist consisting of **3-5 concise bullets** to establish data lineage and ensure strict compliance before human review:
* **Evidence Classification:** Direct source fields mapped cleanly to categorical classifications: *[Input Field]*, *[Public Data]*, or *[Inference]*.
* **Do-Not-Say Restrictions:** Explicit list of sensitive terms, internal classifications, or unverified performance assertions stripped from the text block.
* **Data Gaps & Uncertainties:** Clear logs highlighting missing metrics or unvalidated operational assumptions.
* **Internal Leak & Hallucination Risk Assessment:** Categorical rating logged strictly as **Low**, **Medium**, or **High** based on evidence density.
* **Systemic Confidence Score:** Numerical value from **1 to 5** mapped directly to the scoring parameters in `References/08_quality_rubric.md`.
* **Human Review Status Flag:** Clear indicator declaring that human sales rep verification is mandatory before client delivery.

---
## Dynamic Output Scope & Isolation Gating

You must dynamically modulate the execution scope of the output according to the specificity of the user's prompt:

* **Full Generation Baseline:** If the user request provides a general account data profile without specifying a target format or section restriction, you must execute the entire operational pipeline and render the comprehensive document as structured in the `Default Output Schema`.
* **Micro-Component Isolation Overwrite:** If the user request explicitly isolates a single sub-section, micro-component, or targeted sales asset (e.g., requesting *only* the "1. Sales Context Summary", *only* the telephone "Call Opening", *only* a specific temperature variant like the written "Cold Outreach", *only* the text "Follow-up Message", *only* the custom "Objection Handling", or *only* the "3. Review Notes"), you must immediately execute an override. Completely bypass the full template structure and output **strictly and exclusively** the requested sub-component markdown text block. Do not generate conversational intros, unrequested parent sections, or adjacent placeholder headings.

---
## Default Output Schema

The system must output text adhering to this complete markdown tree structure by default, **unless a targeted micro-component isolation overwrite has been triggered by the user's specific request**:

```markdown
# Account: [restaurant_name] ([account_id])

## 1. Sales Context Summary

- [Bullet 1: Merchant Profile]
- [Bullet 2: Prioritization Signal Context]
- [Bullet 3: Historical/Termination Context]
- [Bullet 4: Selected Strategic Pitch Angle]
- [Bullet 5: Core Risk Mitigation & Caution]
- [Bullet 6: Next Best Action]

## 2. Pitch Narrative

### Call Opening
[2-3 sentence introductory block]

### Written Playbook by Temperature

#### Cold Outreach (Unfamiliar State)
[80-130 word email/message text]

#### Warm Outreach (Interested State)
[80-130 word email/message text]

#### Engaged Outreach (Ready State)
[80-130 word email/message text]

### Follow-up Message
[1-2 sentence short follow-up string]

### Objection Handling (LUPP Model)

#### Objection 1: [Title of Core Friction Point]
* **Listen:** [Validation statement]
* **Unpack:** [Contextual probing question]
* **Prescribe:** [Risk-managed operational capability]
* **Pivot:** [Low-pressure conversion question]

#### Objection 2: [Title of Secondary Friction Point]
* **Listen:** [Validation statement]
* **Unpack:** [Contextual probing question]
* **Prescribe:** [Risk-managed operational capability]
* **Pivot:** [Low-pressure conversion question]

## 3. Review Notes (Internal Validation)

- Evidence used: [Categorized source tokens]
- Do-not-say items: [Stripped elements log]
- Missing or uncertain data: [Identified data gaps]
- Hallucination/internal leak risk: [Low / Medium / High]
- Confidence score: [Value 1-5]
- Human review required: [MANDATORY FLAG]
