# Business Context

## Purpose
This skill supports restaurant acquisition, reactivation, and win-back outreach for a food delivery platform. Sales teams contact restaurants to invite them to join the platform, explore partnership opportunities, or restart conversations with previously partnered restaurants.

The skill turns scattered account information into:
1. An Internal Sales Account Brief for Sales decision-making.
2. A Merchant-facing Pitch Narrative that a Sales rep can use or lightly edit after human review.

## Primary Users
* Field Sales representatives preparing outbound calls, visits, emails, or follow-ups.
* Inside Sales representatives qualifying prospects or re-engaging merchants.
* Business Development teams and Sales Managers reviewing account prioritization.
* Sales enablement teams creating repeatable account research workflows.

## Sales Pain Point
Sales reps often do not have enough time to conduct holistic account research, connect account-specific signals, and convert that research into a tailored, consultative pitch. The skill helps synthesize internal account signals, prior relationship history, known objections, online footprints, sales notes, data quality concerns, and strategic pitch coaching best practices.

## Platform Value Proposition
The platform value proposition focuses on strategic operational integration rather than aggressive sales claims:
* Helping restaurants expose their menu to a broader local digital customer footprint.
* Providing a complementary online ordering and logistics channel.
* Optimizing kitchen output during historical non-peak or off-peak operational windows.
* Supporting flexible logistics structures including delivery, pickup, or marketplace discovery.
* Assisting with structured onboarding, digitized menu setup, and collaborative operational review.

These are possible value themes, not guaranteed outcomes.

## Required Output 1: Internal Sales Account Brief
Use this output for Sales decision-making. It must contain:
* **Account Prioritization Context:** Internal signals, prioritization logic, and account sensitivity analysis.
* **Relationship History:** Prior interaction logs, known objections, and past termination contexts.
* **Strategic Playbook:** Recommended pitch angle, selected discovery sequence, and tactical advice mapped via the LUPP (Listen, Unpack, Prescribe, Pivot) model.
* **Evidence Map:** Explicitly detailed data sources or logical inferences backing every single internal recommendation.
* **Asymmetric Data Truncation Mandate:** The presentation of this brief must follow strict asymmetry data truncation. If a prospect profile contains no historical records or prior touchpoints, omit the historical module entirely instead of rendering empty "N/A" fields. All insights must be condensed into scannable, dense bullet configurations.


## Required Output 2: Merchant-facing Pitch Narrative
Seller-ready copy and talking points tailored for restaurant owners, managers, or operators. It must be generated across three distinct relationship states: **Cold (Unfamiliar)**, **Warm (Interested)**, and **Engaged (Ready)**, optimized for Phone, Email, and In-Store visits. 

It must frame conversations around visible merchant strengths, operational balance, and a low-pressure invitation to explore fit.

## Internal vs. Merchant-facing Boundary
Internal signals can be used to inform the Internal Sales Account Brief but **must not** be exposed in merchant-facing copy. 

Merchant-facing copy **must never** mention or reference:
* Merchant potential tiers (e.g., Tier A/B/C/D).
* Labels such as "Top Search," "Dream Brand," or "Low Choice."
* Internal search terms, search volume data, ranking metrics, or internal performance logs.
* Confidential call transcript details or internal account prioritization logic.

The Merchant-facing Pitch Narrative may be informed by internal signals only after translating them into neutral, merchant-safe language grounded in public or merchant-provided facts.

## Outcome Promise Boundary
The skill **must not under any circumstances** promise or guarantee outcomes. 

**Prohibited Themes:** Guaranteed order growth, revenue increases, search ranking improvements, specific app placement positions, guaranteed customer acquisition rates, delivery volume baselines, or exact ROI/profitability margins.

**Mandatory Phrasing:** If a possible benefit is discussed, you must use risk-managed, cautious, and consultative language such as *"could support,"* *"may complement,"* *"appears aligned with,"* or *"it may be worth exploring whether."*

## Required Handling for Previously Terminated Accounts
Previously terminated, churned, paused, or rejected accounts require a specialized, listening-first win-back framework:
* **No Cold Acquisition Pitches:** Never lead with a generic platform introduction or onboarding request.
* **Acknowledge Sensitivity:** Internally identify prior relationship friction and direct the AI to build an empathetic narrative.
* **External Language:** Focus exclusively on gathering feedback, understanding historical operational roadblocks, and exploring whether their business model or platform parameters have changed over time.
* **No Blame or Extrapolations:** Do not state or imply an internal termination reason unless it was explicitly supplied by the user and is verified as safe to reference externally. Never pressure the merchant to rejoin.

## Evidence Standard & Quality Control
Every single output generated must include an embedded evidence map and a rigorous quality control check section. Each meaningful claim, pitch angle choice, or coaching recommendation must be explicitly traced back to:
1. A supplied input field.
2. A verified public data source.
3. A clearly labeled logical inference (labeled as *[Inference]*).
4. A missing-data note highlighting critical baseline information that requires live sales discovery.

If data or evidence is weak, the skill must explicitly drop any assertive positioning and recommend a purely discovery-driven, question-based consultative approach.

## Human Review Requirement
Sales reps must review all merchant-facing drafts before deployment for local appropriateness, compliance guardrails, and relationship sensitivity.
