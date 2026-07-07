# Input Data Dictionary

Use this dictionary to interpret account inputs. Not every field will be present for every account. Missing or uncertain data should be marked clearly rather than filled in.

For each field, preserve whether it is internal-only or potentially safe for merchant-facing use.

## Account Identity Fields

| Field | Meaning | Allowed Use | Use It For | Do Not Infer |
| --- | --- | --- | --- | --- |
| `account_id` | Unique account identifier. | Internal only. | Tracking accounts across inputs and outputs. | Merchant identity, priority, or quality. |
| `restaurant_name` | Restaurant or merchant name. | Internal and merchant-facing if supplied. | Personalizing briefs and outreach. | Ownership, brand strength, or cuisine. |
| `country` | Market country. | Internal and merchant-facing if relevant. | Localizing context and compliance review. | National performance or demand. |
| `city` | City or market. | Internal and merchant-facing if relevant. | Localizing pitch and account context. | Demand level or customer volume. |
| `location` | Area, district, delivery zone, address, or neighborhood. | Internal and merchant-facing if supplied and not sensitive. | Discussing local relevance. | Area demand, affluence, or supply gaps unless provided. |
| `cuisine` | Primary cuisine or category. | Internal and merchant-facing if supplied or publicly visible. | Selecting relevant pitch angles and discovery questions. | Menu items, demand, popularity, or customer fit. |
| `account_status` | Current lifecycle or sales pipeline status of the account (e.g., New, In Negotiation, Collecting Documents, Quote Signed, Quality Check, Menu Processing, Onboarding, Terminated, Lost). | Internal only. | Segmenting accounts and routing to correct automated or manual workflows. | Long-term partner sentiment or definitive operational health. |
| `preferred_language` | Primary language the merchant prefers for communication. | Internal and merchant-facing context. | Localizing outreach, selecting collateral, and matching with fluent representatives. | Absolute lack of proficiency in other regional languages. |
| `output_language` | The target language expected for generated briefs, pitches, or system outputs. | Internal only. | Configuring automation pipelines and quality assurance checks. | The merchant's sole operational language. |

## Potential and Priority Fields

| Field | Meaning | Allowed Use | Use It For | Do Not Infer |
| --- | --- | --- | --- | --- |
| `vendor_grade_potential_tier` | Internal potential classification, such as A/B/C/D. | Internal only. | Prioritizing Sales effort and outreach depth. | Guaranteed performance or merchant-facing status. |
| `top_search` | Internal signal that the account, cuisine, or related category is linked to notable user search demand. | Internal only. | Demand-led internal strategy and discovery questions. | External demand claims, order volume, or customer acquisition. |
| `search_terms` | Internal search terms associated with user interest. | Internal only unless explicitly approved for external use. | Understanding themes for internal planning. | Exact customer intent, restaurant-specific demand, or merchant-safe keywords. |
| `dream_brand` | Internal strategic-priority signal for a target brand or restaurant. | Internal only. | High-touch strategic outreach planning. | Public brand status or merchant-facing priority label. |
| `low_choice` | Internal signal that an area or category may have limited platform supply relative to user interest. | Internal only. | Local opportunity strategy. | External supply gap claims or market weakness. |
| `other_priority_flags` | Additional internal prioritization signals. | Internal only unless documented otherwise. | Internal planning and risk review. | Merchant-safe claims without validation. |

## Market Context Fields **[NEW SECTION]**

| Field | Meaning | Allowed Use | Use It For | Do Not Infer |
| --- | --- | --- | --- | --- |
| `Highly_searched_terms_or_brands` | Specific high-volume search keywords or major brands trending within the local market area. | Internal only. | Mapping broader macro-demand trends to localized sales strategies. | Direct restaurant-level search attribution or individual intent. |
| `fast_growing_cuisines` | Cuisines showing significant positive user search or order growth trends within the market. | Internal and merchant-facing if framed as macro-insights. | Highlighting market opportunities and validating the merchant’s growth potential. | Guaranteed individual account performance or instant high volume. |
| `under_saturated_cuisines` | Cuisine categories with high user demand but low platform vendor density in the local area. | Internal and merchant-facing if framed as macro-insights. | Emphasizing local supply gaps and building a strong competitive-advantage pitch. | Instant market dominance or total absence of niche competition. |

## Historical Context Fields

| Field | Meaning | Allowed Use | Use It For | Do Not Infer |
| --- | --- | --- | --- | --- |
| `Lead_Intent` | The stated or inferred motivation/goal of the lead (e.g., captured via AI Voice-Assist or inbound forms). | Internal only. | Directing early-stage sales angles and accelerating high-intent responses. | Signed contract commitments or finalized partnership parameters. |
| `historical_transcript_summary` | Summary of previous Sales or merchant conversations. | Internal only unless explicitly approved for external use. | Preparing context, avoiding repeated mistakes, shaping discovery. | Permission to quote or paraphrase confidential details externally. |
| `historical_text_comms_summary` | Summary of historical written interactions (emails, SMS, chat transcripts). | Internal only. | Maintaining relationship continuity, checking previous touchpoints, and avoiding redundant queries. | Explicit permission to quote text verbatim in external pitches. |
| `previously_discussed_pain_points` | Pain points explicitly discussed with the merchant. | Internal. Merchant-facing use only as soft discovery if safe. | Objection-aware strategy and discovery questions. | Current pain points if old or unresolved status is unknown. |
| `known_objections` | Known objections raised by the merchant. | Internal. Merchant-facing use only as respectful topics, not accusations. | Objection handling and Sales coaching. | That objections still apply unless current evidence supports it. |
| `last_contact_date` | The timestamp of the absolute most recent communication or outreach attempt. | Internal only. | Enforcing outreach cadence limits and tracking stale leads. | The qualitative depth or success of the interaction. |
| `last_contact_outcome` | The finalized result of the most recent contact event (e.g., spoke to decision-maker, gatekeeper block, no answer). | Internal only. | Determining next-best sales actions or sequence adjustments. | Permanent merchant sentiment based on a single instance. |
| `last_objection_date` | The date on which the merchant last raised an objection or refusal. | Internal only. | Assessing the recency of roadblocks to evaluate if they are still relevant or ready for re-engagement. | Automatic resolution of the objection via the passage of time alone. |
| `prior_partnership_status` | Whether the merchant has never partnered, currently partners, previously partnered, paused, rejected, or unknown. | Internal. Merchant-facing wording must be relationship-sensitive. | Choosing acquisition, reactivation, or win-back handling. | Why the relationship changed. |
| `terminated` | Whether the merchant was previously partnered and later terminated. | Internal. Merchant-facing use requires caution and human review. | Win-back handling and risk assessment. | Termination cause or merchant blame. |
| `termination_reason` | Stated reason for termination, if available. | Internal. Do not mention externally unless explicitly approved and relationship-safe. | Win-back strategy, risk review, and discovery planning. | Any cause beyond the stated reason. |
| `historical_performance_summary` | Internal summary of past platform performance, if available. | Internal only. | Sales preparation and risk review. | Future performance, guaranteed outcomes, or merchant-facing claims. |
| `regret_score` | Score calculated by the Vendor Health team reflecting the strategic/financial loss value if this vendor is inactive. | Internal only. | Calibrating win-back incentive thresholds and prioritizing commercial recovery efforts. | The merchant's willingness to rejoin or public brand reputation. |

## Online Footprint Fields

| Field | Meaning | Allowed Use | Use It For | Do Not Infer |
| --- | --- | --- | --- | --- |
| `google_rating` | Public Google rating. | Internal and merchant-facing if sourced and current enough. | Public reputation context. | Exact demand, delivery fit, or business performance. |
| `google_review_count` | Public Google review count. | Internal and merchant-facing if sourced and current enough. | Public visibility context. | Conversion, order volume, or customer acquisition. |
| `competitor_platforms` | Explicit list of competing delivery platforms where the restaurant is currently active. | Internal only (or neutral merchant-facing reference if highly relevant). | Dissecting multi-homing behavior and analyzing competitor operational footprint. | Merchant satisfaction with competitors or exclusive contract vulnerability. |
| `competitor_platform_presence` | Whether the restaurant appears on competing delivery platforms. | Internal. Merchant-facing use only as neutral channel context. | Incremental channel pitch and operational readiness hypothesis. | Competitor dissatisfaction or superiority claims. |
| `instagram_followers` | Public Instagram follower count. | Internal and merchant-facing if sourced and current enough. | Public visibility or digital footprint context. | Order potential or conversion. |
| `has_website` | Boolean flag indicating if a valid primary website was located during data scraping pipelines. | Internal and merchant-facing if relevant. | Gauging fundamental digital footprint completeness and assessing technical setup. | Website traffic quality, conversion rate, or active content maintenance. |
| `website` | Restaurant website. | Internal and merchant-facing if relevant. | Digital footprint and menu discovery. | Business quality or online ordering need. |
| `menu_url` | Public menu link. | Internal and merchant-facing if relevant. | Understanding cuisine/category if menu details are provided. | Signature dishes or menu strategy unless visible and cited. |

## Sales Notes

| Field | Meaning | Allowed Use | Use It For | Do Not Infer |
| --- | --- | --- | --- | --- |
| `sales_notes` | Internal Sales notes. | Internal. Merchant-facing use only after confidentiality review. | Context, relationship sensitivity, discovery planning. | Merchant-safe facts without evidence. |
| `data_quality_notes` | Notes about missing, outdated, incomplete, or uncertain data. | Internal and quality control sections. | Confidence scoring and review flags. | That missing information can be filled by assumption. |

## Evidence Strength Labels

- `direct`: The claim is explicitly supported by supplied data.
- `moderate`: The claim is a reasonable interpretation of multiple signals.
- `speculative`: The claim is weak or uncertain; convert it into a discovery question.
- `missing`: Required information is absent.
- `conflicting`: Inputs disagree or need human review.

## Data Handling Rules

- Do not invent missing fields.
- Do not normalize ambiguous values into stronger claims.
- Do not treat internal signals as merchant-facing facts.
- Do not treat historical performance as a future performance promise.
- Do not rely on stale online footprint data without noting that it may need review.
