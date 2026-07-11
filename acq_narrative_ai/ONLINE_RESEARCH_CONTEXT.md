# Online Research Context Layer — Design Summary

Compressed record of the design decisions made for the new "Online Research" capability added on top of the existing Sales Account Research & Pitch Narrative skill. Read this for the full picture without re-reading the design conversation; read `References/09_online_research_protocol.md` and `SKILL.md` for the actual operative spec.

## 1. Problem This Solves

The original skill (internal-data-driven Sales Context Summary + Pitch Narrative) is weak on accounts with sparse internal data — exactly the accounts Field Sales generates themselves by discovering a new restaurant with nothing but a name and address. Online Research closes that gap by adding a live public-footprint lookup step.

## 2. Trigger Design — `lead_source_channel`

New input field, added to `References/02_input_data_dictionary.md`:

| Value | Meaning | Step 0 default |
|---|---|---|
| `"field_sales_own_research"` | Field Sales self-discovered a new lead; little/no internal data exists yet | **Auto-run** — this step is usually the primary evidence source |
| anything else (`"system_lead"`, etc.) | Telesales working an existing system lead (scraping provider or merchant self-sign-up); internal data already exists | **Off by default** — reactive/on-demand only, to save cost/capacity |

Only one flag distinction was requested — no granular Telesales sub-types needed.

## 3. Execution Model — Skill vs. Tool-Dependent Step

Both the narrative-generation logic (Steps 1–6) and the Online Research step (Step 0) are documented *skill specifications* (instructions, not code). The real difference: Steps 1–6 are pure instruction-following — any LLM can run them with no tool access. Step 0 has a hard dependency — it can only be executed by an agent with live web search/browsing tool access; a plain text-completion model cannot run it. This distinction is written explicitly into `SKILL.md` under "Execution Model" and annotated directly on the workflow diagram.

## 4. Online Research Protocol (full spec: `References/09_online_research_protocol.md`)

- **Query anchor:** restaurant name + address together, never name alone (prevents same-name collisions).
- **Scope:** public rating/reviews, official website, social media, presence on delivery platforms (Uber Eats, Wolt, etc.).
- **Explicitly out of scope:** whether the account is already an existing Delivery Hero/foodora partner — that must come from existing internal fields (`account_status`, `prior_partnership_status`), not from this step. (Originally in scope; removed after discussion — see §6.)
- **Disambiguation rule:** accept a match only when ≥2 independent signals agree (e.g. name + exact address).
- **Confidence tiers:** `verified` (2+ sources or authoritative first-party match) / `likely` (single indexed source, unconfirmed by direct re-fetch) / `unconfirmed–not found` (state plainly, never guess).
- **Citation requirement:** every finding carries `source_url` + `confidence` + `retrieved_date`.
- **Merchant-facing use:** only `verified`-tier facts may reach merchant-facing copy; `likely`/`unconfirmed` stay internal until human-confirmed.
- **Numeric accuracy: still an open item** — no finalized rule yet for when a specific number (rating, review count, follower count) is reliable enough to report vs. should be omitted. Current interim guidance: prefer omitting over reporting low-confidence numbers.

## 5. Output Structure Change

New **Output Part 0: Online Research Findings** in `SKILL.md`, positioned before the Sales Context Summary:
- Appears only if Step 0 ran; omitted entirely (not rendered empty) otherwise.
- Presented as its own findings list/table (not folded silently into the Context Summary) — a rep should be able to see exactly what was found, with what confidence, from where.
- Full output order: **(0. Online Research Findings, conditional) → 1. Sales Context Summary → 2. Pitch Narrative → 3. Review Notes.**

## 6. PoC Validation

Tested inline (single Claude Code session, agent + general web search) on 2 real Swedish restaurants (Sannegården Karlskoga, Amo Seafood) added to `Assets/sample_accounts_redacted.json` as `sample-004-real` / `sample-005-real` with `lead_source_channel: "field_sales_own_research"`. Contact PII (phone/email) was deliberately excluded from the file per the repo's own data policy.

Results:
- Disambiguation rule correctly caught and excluded a same-named-but-unrelated NYC restaurant (`amoseafood.com`) that would otherwise have contaminated the findings.
- Found real, citable public data: ratings, websites, Instagram handles, presence on Wolt/Uber Eats.
- Both test accounts turned out to already be active foodora partners. This was initially treated as the PoC's most important finding (preventing an embarrassing cold-pitch-to-existing-partner mistake) and drove an early design where Step 0 checked DH/foodora partnership status first via internal DB access. **That specific check was later removed from Step 0's scope** (§4) — it's cheaper and more reliable to answer from existing internal fields than to re-derive it through research, so it was descoped rather than built here.
- Numbers pulled via web search (ratings, review counts) landed at `likely` confidence rather than `verified`, because the agent has to read/summarize search snippets rather than read a structured field — flagged as a structural property of the web-search approach, not a one-off measurement gap (see §7).

## 7. Production Implementation Options (for engineering)

Documented in `References/09` as non-exclusive alternatives:

- **Option A — Agent + web search tool** (what the PoC used). Broad/holistic coverage, clickable sources, low integration cost (built into current Gemini/GPT/Claude agent platforms) — but numeric fields stay lower-confidence by nature.
- **Option B — Structured business-data API** (e.g. Google Places API). Narrow coverage (basically just Google's own rating/review count) but those specific fields come back verifiable/structured.
- **Recommendation:** ship Option A first (matches validated PoC, least new procurement); treat Option B as a later optional upgrade specifically to raise confidence on numeric fields.
- Either option still needs: tool-calling capability on the chosen platform, an API key + quota/billing sized to `field_sales_own_research` volume, and legal/compliance review of the underlying data source's ToS — **none of this has been done yet**; PoC usage is explicitly not pre-approved for production.
- Findings must be persistently logged (source/confidence/date), not just embedded in generated text — a data-store decision for engineering.

## 8. Files Touched This Session

- `SKILL.md` — Execution Model section; Step 0 added to workflow (with agent/model requirement annotations); Output Part 0 added; Default Output Schema template updated; Resource Map updated.
- `References/02_input_data_dictionary.md` — added `lead_source_channel` field; added source/confidence/date note under Online Footprint Fields.
- `References/09_online_research_protocol.md` — new file; full protocol, prerequisites, and the two implementation-option analysis.
- `Assets/sample_accounts_redacted.json` — added `sample-004-real`, `sample-005-real` (real accounts, no contact PII); added `lead_source_channel` to all 5 accounts (3 fictional → `system_lead`, 2 real → `field_sales_own_research`).

## 9. Known Open Items / Gaps (not yet resolved)

- **Numeric accuracy rule** — still undefined (§4), explicitly deferred.
- **`lead_source_channel` doesn't exist yet in any real CRM/Salesforce system** — the auto-trigger logic depends on a field that hasn't been confirmed to exist or been wired up.
- **Validation sample is tiny (n=2) and both were unusually well-documented, already-active accounts** — the "unconfirmed/not found" path for a genuinely obscure, low-footprint restaurant has never actually been exercised.
- **No usage-volume estimate** — needed before procurement/compliance can size an API budget.
- **Compliance/legal review has not started** for any data source (general web search or a business-data API).
- **`Assets/input_schema.json` / `output_schema.json` are still empty placeholders** — the new field and output structure exist only in markdown prose, not in a machine-readable schema.
- **Pre-existing issues from before this feature, still unresolved:** possible filename inconsistencies under `References/` from earlier drafts; field-naming mismatches between `References/02` prose and `Assets/sample_accounts_redacted.json` (e.g. `merchant_potential_tier` vs. dictionary's `vendor_grade_potential_tier`); a tone tension in `References/05`/`06` where mandated "curated marketing" euphemisms may push past "no overpromising" into obscuring what the product actually is.

## 10. Overall Verdict (as of this session)

Feasible and valuable as a mechanism; validated at PoC level with real evidence (correct disambiguation, real citable findings). Ready to hand to engineering **as a behavior specification and discussion starting point**, not as a locked build-spec — §9's open items should be closed or at least explicitly flagged during handoff so expectations on timeline/accuracy are set correctly.
