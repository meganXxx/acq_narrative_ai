# Online Research Protocol

## Purpose

Defines how to perform a live public online-footprint lookup for a restaurant account using only its name and location, so the Sales Context Summary can be enriched with verified public signals even when internal data is sparse or absent.

This step supplements internal data. It never overrides internal data, and it never invents a value when no confident match exists.

## When This Step Runs

Trigger behavior depends on the account's `lead_source_channel` field (see `References/02_input_data_dictionary.md`):

- `lead_source_channel = "field_sales_own_research"`: run automatically, before Step 1. These leads typically start with only a restaurant name and location, so this step is usually the primary source of usable evidence for the account.
- Any other or unspecified `lead_source_channel` value (system-provided leads worked by Telesales, regardless of whether they originated from a scraping provider or merchant self-sign-up): do not run by default. Only run this step when the user explicitly requests online research for the account. Internal data is assumed sufficient unless the user says otherwise.

**Environment capability check:** this step requires an execution environment with live web search or browsing tool access. If the current environment cannot perform live web lookups, skip this step entirely and mark the affected `online_footprint` fields as "not available in this session." Do not fabricate a result to fill the gap, and do not silently skip without noting that the step was unavailable.

See "Prerequisites / Access Requirements" below for what that capability concretely requires in a production build.

## Prerequisites / Access Requirements

This step was validated in a PoC using a general-purpose AI agent with ad hoc web search/fetch tools. That is sufficient for a proof of concept; it is not sufficient for production. None of the following is controlled by this document — it must be provisioned and approved by the engineering team and relevant compliance/procurement stakeholders before this step runs against real accounts at scale.

### 1. Tool-calling / function-calling capability

The executing agent must run on a platform that supports live tool or function calls (standard on Gemini, GPT, and Claude-based agent platforms, among others). Enabling this is a platform configuration task for whichever engineering stack is chosen — it is not something this skill package can turn on by itself.

### 2. External data-access requirement

Public footprint lookup (rating, review count, website, social media, presence on delivery platforms such as Uber Eats and Wolt) requires an external web search and/or business-data capability. Two implementation approaches are viable. They are not mutually exclusive — a phased approach is recommended below.

**Option A — Agent with web search tool access (this is what was validated in this PoC).** The executing agent is given a general-purpose web search/browsing tool, the kind already built into current Gemini, GPT, and Claude-based agent platforms.
- Strength: broad, holistic coverage in a single pass. This PoC's two-account test returned the official website, Instagram, TikTok, Wolt, Uber Eats, foodora, and independent review aggregators (TripAdvisor, Restaurant Guru) — each with a clickable source link — none of which a narrow places-data API alone would have surfaced.
- Weakness: the agent has to read and summarize search-result text rather than read a structured field, so precise numbers (rating, review count, follower count) carry lower confidence. In this PoC those numbers mostly landed at "likely" rather than "verified" (see Numeric Accuracy below). This is a property of the approach, not a one-off measurement error, and should be expected to persist.
- Access needed: the chosen AI platform's web search/browsing tool enabled, that platform's own usage quota/billing, and compliance review of the underlying search provider's terms of service — this requirement does not disappear just because it is "web search" rather than a dedicated data API.

**Option B — Structured business-data API (e.g. Google Places API or similar).** The agent calls a dedicated, licensed API that returns typed, canonical fields (rating, review count, address) for a specific place.
- Strength: the specific numeric fields it covers (typically Google's own rating/review count) come back as directly verifiable structured data — meaningfully higher confidence for those particular fields than Option A.
- Weakness: narrow coverage. It does not surface Instagram, competitor delivery platforms, or general web mentions the way Option A does.
- Access needed: procurement and vendor approval, an API key, a billing/quota allocation, and legal/compliance review of that provider's terms of service (e.g. limits on caching or redisplaying ratings data, attribution requirements) before production use.

**Recommended path:** ship Option A first. It is what this PoC validated, requires the least new vendor/procurement setup, and delivers the broad, holistic findings that make this step valuable. Treat Option B as an optional later enhancement specifically to raise confidence on the handful of numeric fields, once budget and procurement allow. Whichever option (or combination) is chosen, it needs a billing/quota allocation sized to expected usage volume, driven primarily by `lead_source_channel = "field_sales_own_research"` volume, since that is what auto-triggers this step. Neither option has gone through legal/compliance review yet — this PoC's web search usage was for demonstration only and must not be treated as pre-approved for production.

### 3. Persistent, queryable logging of findings

Every finding must be stored with its `source_url`, `confidence` tier, and `retrieved_date` — not just embedded in generated text — so results stay auditable later. This requires a data store, not just an LLM call; where this lives (e.g. alongside existing account records) is an engineering decision.

### 4. What this document does not decide

This document defines the required *behavior* (query method, disambiguation rule, confidence tiers, citation requirement). It does not select a vendor, an API, or a cloud platform — that choice belongs to the engineering team, in consultation with procurement and compliance.

## Query Method

- Always search using `restaurant_name + location/address` together. Never search by name alone — same-name collisions across chains, franchises, and even different cities or countries are common (see Disambiguation Rule).
- Perform separate, targeted lookups for:
  1. Business identity and address confirmation.
  2. Cuisine or category and Menu Baseline..
  3. Public rating and review count (Google and other aggregators).
  4. Presence on delivery platforms (e.g. Uber Eats, Wolt, and other platforms common in the local market).
  5. Official website.
  6. Social media presence.

Whether the account is already an existing Delivery Hero/foodora partner is out of scope for this step — that should be answered from existing internal account data (e.g. `account_status`, `prior_partnership_status`), not re-derived through public web research.

## Disambiguation Rule

- Accept a match only when at least two independent signals agree — for example, business name AND exact address, or business name AND city AND cuisine.
- If multiple candidate matches exist (chains, franchises, unrelated businesses sharing a name), the account's exact address must match before any data from that source is used.
- Documented failure case from PoC testing: a same-named restaurant in an entirely different city/country ranked highly in search results and had to be excluded after an address cross-check. Always verify address before trusting a single source.

## Confidence Tiers

- **verified**: confirmed via at least two independent sources, or one authoritative first-party source (official site, direct platform listing) with matching address.
- **likely**: found via a single indexed source with an address match, but the source could not be independently re-confirmed (e.g., direct fetch was blocked).
- **unconfirmed / not found**: no confident match. State this explicitly rather than omitting the field silently or guessing.

## Numeric Accuracy

Open item, to be refined separately: rules for when a specific number (rating, review count, follower count) is reliable enough to report versus when it should be omitted rather than stated with a caveat. Until that guidance is finalized, prefer omitting a specific number over reporting one with low confidence.

This is a more acute problem under Option A (agent + web search, see Prerequisites above) than under Option B (structured business-data API), since Option A numbers are read out of search-result text rather than a canonical field. Do not treat a number surfaced via Option A as equivalent in reliability to one that would come from Option B.

## Citation and Freshness

Every finding must carry:
- `source_url`
- `confidence` (verified / likely / unconfirmed)
- `retrieved_date`

## Output Handoff

Compiled findings serve two purposes, not one:

1. **Feed Steps 1–6** as additional evidence, using the extended `online_footprint` structure described in `References/02_input_data_dictionary.md`, alongside any existing internal data. Online research findings supplement internal data; they do not overwrite it. If a research finding conflicts with supplied internal data, flag the conflict for human review rather than resolving it silently.
2. **Surface as their own standalone deliverable** — Output Part 0 in `SKILL.md` ("Online Research Findings"). Do not fold these findings silently into the Sales Context Summary only; the raw findings (with confidence tier, source URL, retrieved date) must also be presented on their own so a rep can see exactly what was found and how sure the system is, independent of how the Context Summary chose to use it.

## Merchant-Facing Use

Only `verified`-tier public facts may be translated into merchant-facing copy, following the same internal/external separation rules as `References/06_do_not_say_rules.md`. `likely` and `unconfirmed` findings stay internal-only (Sales Context Summary / Review Notes) until a human confirms them.
