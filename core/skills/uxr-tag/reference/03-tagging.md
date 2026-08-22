# Phase 3 — Tag the Data
*Part of the UXR Synthesis workflow: Clean, CSV, Tag, RQ, Findings, Report.*

---

## What this phase does

Reads each row in the CSV and populates the `Tags` column. The goal is to make every substantive data point findable by topic, behavior, and concept — so that in Phase 5, patterns can be discovered across participants by filtering and grouping on tags.

**Tagging requires two types of judgment:**
1. **Keyword recognition** — does this row mention a specific product, tool, feature, or role by name? Apply the taxonomy tag for it.
2. **Semantic interpretation** — what is this row actually expressing? What behavior, sentiment, or concept is the participant describing? Apply codes for those.

Both are required. Neither alone is enough.

---

## Two layers: keywords and codes

Every tag is classified by a `Type of code` field (the watsonx.data base calls it `Type of tag` — same values). The types fall into two layers.

### Keywords — the filter layer (`Tool/Software/Company`, `keyword`, `Persona/Target User`)
The concrete, searchable things a participant named or clearly referred to. This is the layer you filter by, so **more is better** — tag every one; there is no cap. **Grounded only:** the term must appear in the row, or clearly name a specific tool/product/company — never invent a paraphrase for a concept the row only implies (e.g. don't tag `TL;DR` on "just tell me what I need to know"). "Exhaustive" means over the terms actually present; inferred meaning is a *code*, not a keyword.

**Examples:**
- Tools / companies (`Tool/Software/Company`): `watsonx.data`, `Databricks`, `Snowflake`, `Figma`, `GitHub`, `Carbon MCP`, `Bob`
- Concrete terms & artifacts (`keyword`): `metastore`, `data catalog`, `RAG`, `screenshots`, `video`, `pull request`, `wireframe`, `presentation`, `repo`, `terminal`, `MCP`, `oncology`
- Roles / audiences (`Persona/Target User`): `data engineer`, `data steward`, `designer`, `UX engineer`, `developer`, `VP`

**The rule:** if a participant named it or referred to a concrete thing someone might filter by — a tool, company, role, or artifact — tag it. Reach wide.

### Codes — the interpretive layer (`Theme`, `Feature/Capability`, `Workflow/Process`)
Emergent, interpretive tags — what the participant is *telling* you, not just what words they used. Here **quality wins**: apply a few sharp ones, not a pile.

**Examples:**
- Behavioral / sentiment / conceptual Themes: `workaround`, `frustration`, `discoverability`, `onboarding friction`, `mental model`, `context switching`, `trust barrier`

**The rule:** if you're interpreting rather than transcribing — a feeling, a pattern, an underlying concept — it's a code (usually a `Theme`). Keep it tight; it feeds findings.

---

## How to tag a row

For each substantive data point row, ask these two questions in order:

**Question 1 — Keyword recognition (be exhaustive — more is better):**
Which concrete, filterable things does this row name or clearly refer to — products, tools, platforms, companies, roles, and artifacts (screenshots, video, PR, wireframe, deck, repo)? Apply a keyword for every one; reuse an existing keyword if it exists, propose a new one if not. Quantity is the goal for this layer — you never know what someone will filter by.

**Question 2 — Semantic interpretation:**
What is this row actually about? What behavior, sentiment, concept, or process does it express? Apply the codes that represent that meaning.

Most rows get a mix of both. A row about struggling to find data in watsonx.data might get the taxonomy tag `watsonx.data` and the codes `discoverability` and `frustration`.

---

## Tagging limits

- **Keywords: no cap — more is better.** Tag every product, tool, company, role, and artifact the row names. The keyword layer is the filter layer; completeness beats brevity.
- **Interpretive codes: keep it tight (~5).** If you're stacking 6+ *codes* (the behaviors/sentiments/themes you interpret), you're over-interpreting — each code should differentiate this row, not restate the study topic. Quality lives here; it feeds findings.
- **Minimum 0.** Many rows legitimately get no tags — moderator lines, greetings, conversational filler that survived earlier phases, rows that provide context but no analysis value. That is correct. Do not tag just to fill the column.
- **Do not tag moderator rows.** Ever. Leave their Tags cells blank.

---

## Naming rules

Tag names must be consistent to be useful. A tag `metastore` and a tag `metastores` are two different tags in a filter — one of them is invisible half the time.

**Always:**
- Singular form: `workaround` not `workarounds`, `metastore` not `metastores`
- Closed spelling for technical terms: `metastore` not `meta store`, `dataset` not `data set`
- Official product casing: `watsonx.data` (lowercase), `Databricks` (capitalized), `Db2` not `DB2`
- Full names over abbreviations unless the abbreviation is the industry standard: `SQL` is fine, `wxd` is not
- Human-readable form: `data engineer` not `DE`, `manual step` not `manual_step`

**Before applying a tag:** check whether it already exists in your tag config. If something close exists, use that one and note any variation. Do not create a near-duplicate.

---

## Disambiguation rules

Some terms need judgment to tag correctly:

**"catalog"** — could mean the IBM data catalog product, a Hive catalog, a catalog of services, or a mental model for how data is organized. Tag with the specific catalog name if known (`data catalog`, `Hive catalog`). Only use the generic `catalog` tag if the participant's meaning is truly ambiguous.

**"documents"** — could mean data documents (unstructured content being ingested), product documentation (help/reference), or governance documents (policy records). Apply the most specific tag that fits. Do not default to `documents` when `unstructured data` or `documentation` is more precise.

**"pipeline"** — could mean a data ingestion pipeline, a CI/CD pipeline, or a general workflow. Use `data pipeline`, `ingestion pipeline`, or the relevant specific term.

---

## Handling a CSV from the Transcript App

If the input CSV already has a Keywords column from the Transcript App:
1. Read the Keywords column as **candidate taxonomy tags only**
2. Keep the ones that match your taxonomy exactly (same name, correct spelling)
3. For a keyword that doesn't match your config, don't discard it reflexively — if it names a real product, tool, company, role, or artifact, keep it as a proposed new keyword (more is better). Drop only true noise (fragments, non-terms)
4. Run the full two-question tagging pass (keyword recognition + semantic interpretation) as if starting fresh
5. The final Tags column is the output of your full pass, not the Keywords column

The Keywords column from the app is a starting point, not a result.

---

## Proposing new tags

If a concept or term appears in the data that genuinely does not fit any existing tag in your config:

Flag it this way:
> `PROPOSED: [tag name] — [Type of code: Tool/Software/Company | keyword | Persona/Target User | Theme | Feature/Capability | Workflow/Process] — appears in N rows. Reason: [one sentence on why this is a new tag, not an existing one in different form]`

Do not add new tags to the CSV silently. The researcher reviews all proposals and decides whether to add them to the config.

After the researcher approves, add the new tag to the config file and apply it to all rows where it applies.

---

## Output

The `Tags` column is populated inline in the CSV. Tags are comma-separated.

```csv
Timestamp,Speaker,Data point,Tags
00:05:18,NP,"Data that's confidential — financial records, salary data — that always stays on-prem.","regulated industry, data governance, on-prem, privacy concern"
00:05:18,NP,"For cloud, we only move aggregated results, never actual patient or PII data.","on-prem, cloud, hybrid, privacy concern, PII"
00:02:22,NP,"I primarily work with Python and build agents using LangGraph.","Python, LangGraph, data engineer"
```

When tagging is complete, report:
- Total rows tagged
- Total rows with 0 tags (confirm this is expected)
- All proposed new tags with counts
- Any rows that were ambiguous (flag for researcher review)

Do not auto-export the CSV. Wait for the researcher to ask.
