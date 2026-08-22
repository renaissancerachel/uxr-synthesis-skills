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

## Two types of tags

### Taxonomy Tags
Controlled, stable proper nouns and technical terms. These are the vocabulary of your product space. Apply them when the participant explicitly mentions or clearly refers to the term.

**Examples:**
- Product/tool names: `watsonx.data`, `Databricks`, `Snowflake`, `Python`, `LangGraph`, `Milvus`
- Feature names: `metastore`, `data catalog`, `RAG`, `iceberg table`, `query engine`
- User roles: `data engineer`, `data steward`, `data analyst`, `platform admin`
- Company types: `bank`, `regulated industry`, `enterprise`

**The rule:** If it's a proper noun or specific technical term the team would search for by name, it's a taxonomy tag.

### Codes
Emergent, interpretive tags. These are the concepts, patterns, and signals you're pulling out of the data — what the participant is *telling* you, not just what words they used.

**Examples:**
- Behavioral: `workaround`, `comparison`, `habit`, `abandonment`, `shortcut`
- Sentiment: `frustration`, `delight`, `uncertainty`, `trust`, `skepticism`
- Conceptual: `discoverability`, `mental model`, `onboarding friction`, `information architecture`
- Process: `manual step`, `context switching`, `collaboration point`, `error recovery`

**The rule:** If it's something you're interpreting from what the participant said — what they're feeling, what pattern they're exhibiting, what concept underlies their statement — it's a code.

---

## How to tag a row

For each substantive data point row, ask these two questions in order:

**Question 1 — Keyword recognition:**
Did the participant mention a specific product, tool, feature, or role? Check against your taxonomy tags. If a match exists, apply it. A single row can have multiple taxonomy tags if multiple products/tools are mentioned.

**Question 2 — Semantic interpretation:**
What is this row actually about? What behavior, sentiment, concept, or process does it express? Apply the codes that represent that meaning.

Most rows get a mix of both. A row about struggling to find data in watsonx.data might get the taxonomy tag `watsonx.data` and the codes `discoverability` and `frustration`.

---

## Tagging limits

- **Maximum 5–7 tags per row.** If you're regularly hitting 8+, you're over-tagging. Ask: does each tag meaningfully differentiate this row from other rows, or is it just describing the study topic in general?
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
3. Discard keywords that don't match any tag in your config — they are not tags, they are surface-level term detections
4. Run the full two-question tagging pass (keyword recognition + semantic interpretation) as if starting fresh
5. The final Tags column is the output of your full pass, not the Keywords column

The Keywords column from the app is a starting point, not a result.

---

## Proposing new tags

If a concept or term appears in the data that genuinely does not fit any existing tag in your config:

Flag it this way:
> `PROPOSED: [tag name] — [type: Taxonomy/Code] — [suggested type-of-tag category] — appears in N rows. Reason: [one sentence on why this is a new tag, not an existing one in different form]`

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
