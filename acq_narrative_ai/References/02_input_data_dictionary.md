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

## Potential and Priority Fields

| Field | Meaning | Allowed Use | Use It For | Do Not Infer |
| --- | --- | --- | --- | --- |
| `merchant_potential_tier` | Internal potential classification, such as A/B/C/D. | Internal only. | Prioritizing Sales effort and outreach depth. | Guaranteed performance or merchant-facing status. |
| `top_search` | Internal signal that the account, cuisine, or related category is linked to notable user search demand. | Internal only. | Demand-led internal strategy and discovery questions. | External demand claims, order volume, or customer acquisition. |
| `search_terms` | Internal search terms associated with user interest. | Internal only unless explicitly approved for external use. | Understanding themes for internal planning. | Exact customer intent, restaurant-specific demand, or merchant-safe keywords. |
| `dream_brand` | Internal strategic-priority signal for a target brand or restaurant. | Internal only. | High-touch strategic outreach planning. | Public brand status or merchant-facing priority label. |
| `low_choice` | Internal signal that an area or category may have limited platform supply relative to user interest. | Internal only. | Local opportunity strategy. | External supply gap claims or market weakness. |
| `other_priority_flags` | Additional internal prioritization signals. | Internal only unless documented otherwise. | Internal planning and risk review. | Merchant-safe claims without validation. |

## Historical Context Fields

| Field | Meaning | Allowed Use | Use It For | Do Not Infer |
| --- | --- | --- | --- | --- |
| `historical_transcript_summary` | Summary of previous Sales or merchant conversations. | Internal only unless explicitly approved for external use. | Preparing context, avoiding repeated mistakes, shaping discovery. | Permission to quote or paraphrase confidential details externally. |
| `previously_discussed_pain_points` | Pain points explicitly discussed with the merchant. | Internal. Merchant-facing use only as soft discovery if safe. | Objection-aware strategy and discovery questions. | Current pain points if old or unresolved status is unknown. |
| `known_objections` | Known objections raised by the merchant. | Internal. Merchant-facing use only as respectful topics, not accusations. | Objection handling and Sales coaching. | That objections still apply unless current evidence supports it. |
| `prior_partnership_status` | Whether the merchant has never partnered, currently partners, previously partnered, paused, rejected, or unknown. | Internal. Merchant-facing wording must be relationship-sensitive. | Choosing acquisition, reactivation, or win-back handling. | Why the relationship changed. |
| `terminated` | Whether the merchant was previously partnered and later terminated. | Internal. Merchant-facing use requires caution and human review. | Win-back handling and risk assessment. | Termination cause or merchant blame. |
| `termination_reason` | Stated reason for termination, if available. | Internal. Do not mention externally unless explicitly approved and relationship-safe. | Win-back strategy, risk review, and discovery planning. | Any cause beyond the stated reason. |
| `historical_performance_summary` | Internal summary of past platform performance, if available. | Internal only. | Sales preparation and risk review. | Future performance, guaranteed outcomes, or merchant-facing claims. |

## Online Footprint Fields

| Field | Meaning | Allowed Use | Use It For | Do Not Infer |
| --- | --- | --- | --- | --- |
| `google_rating` | Public Google rating. | Internal and merchant-facing if sourced and current enough. | Public reputation context. | Exact demand, delivery fit, or business performance. |
| `google_review_count` | Public Google review count. | Internal and merchant-facing if sourced and current enough. | Public visibility context. | Conversion, order volume, or customer acquisition. |
| `competitor_platform_presence` | Whether the restaurant appears on competing delivery platforms. | Internal. Merchant-facing use only as neutral channel context. | Incremental channel pitch and operational readiness hypothesis. | Competitor dissatisfaction or superiority claims. |
| `instagram_followers` | Public Instagram follower count. | Internal and merchant-facing if sourced and current enough. | Public visibility or digital footprint context. | Order potential or conversion. |
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
