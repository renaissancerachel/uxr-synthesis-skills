---
name: uxr-tag
description: Use when the user wants to tag a UXR data-point CSV with taxonomy tags and semantic codes — Phase 3 of the UXR synthesis workflow. Applies keyword recognition and semantic interpretation to every substantive row.
---

# /uxr-tag — Phase 3: Tag the Data

Populate the Tags column for every substantive data point row. Two types of tags required: taxonomy tags (keyword recognition) and codes (semantic interpretation).

## Input required

A CSV with `Timestamp, Speaker, Data point, Tags` columns — either from Phase 2 or from the Transcript App. If it's missing, ask.

If the input is from the **Transcript App**, treat its Keywords column as candidate taxonomy tags only. Keep matches. Discard non-matches. Run the full two-question pass as if starting fresh.

## Tag every substantive row with two questions

**Q1 — Semantic codes:** What is this row actually expressing — what behavior, barrier, pattern, or process? Apply the codes that capture that meaning. **Codes go first.**

**Q2 — Keyword recognition (be exhaustive — more is better):** Which concrete, filterable things does the row name or clearly refer to — products, tools, platforms, companies, roles, and artifacts (screenshots, video, PR, wireframe, deck, repo)? Apply a keyword for every one. **Keywords go after codes.**

Both questions, every row. Neither alone is enough. The Tags cell is one comma-separated value containing both — codes first, then keywords.

## Tag ordering rule

Within the Tags cell, always write **codes before keywords**:
```
trust barrier, hallucination risk, AI, instruction
```
Not:
```
AI, instruction, trust barrier, hallucination risk
```

This makes the interpretive signal visible first when scanning the column.

## Limits

- **Keywords: no cap — more is better.** Apply a keyword for every product, tool, company, role, or artifact the row names. The keyword layer is the filter layer; completeness is the goal (you never know what someone will filter by).
- **Interpretive codes: keep it tight (~5).** Stacking 6+ *codes* (the themes/behaviors you interpret) is over-interpreting — each should differentiate the row, not restate the study topic. Quality is for findings.
- Minimum 0. Many rows legitimately get no tags — that is correct.
- Moderator rows: leave Tags blank. Always.

## Avoid catch-all codes

Do not use `pain point` as a tag. It carries no meaning on its own — every substantive row is about a pain point. Replace it with the specific code that names what kind of problem it is:

| Instead of `pain point` | Use |
|---|---|
| Manual substitute for a broken path | `workaround` |
| Doubt about output accuracy/safety | `trust barrier` |
| Fear of confident wrong answers | `hallucination risk` |
| Can't reach data or tool needed | `access friction` |
| Wrong assumption about who can access what | `access confusion` |
| Unclear or unenforced governance rule | `governance gap` |
| Agent lacks org-specific context | `domain knowledge gap` |
| Work follows a fixed repeating pattern | `repetitive task` |
| Structural or political barrier | `org friction` |
| Need for real-time vs. static data | `live data dependency` |

If none of these fit, propose a new specific code using the `PROPOSED:` format rather than falling back to `pain point`.

## Naming rules

- Singular form: `workaround` not `workarounds`
- Closed spelling: `metastore` not `meta store`, `dataset` not `data set`
- Official product casing: `watsonx.data`, `Databricks`, `Db2`
- Full names over abbreviations unless the abbreviation is the industry standard: `SQL` is fine, `wxd` is not
- Human-readable: `data engineer` not `DE`

Before applying a tag, check it exists in the config. Use the closest match; do not create near-duplicates.

## Tag config

Use the team taxonomy and codes from `reference/taxonomy.json` and `reference/codes.json`, plus any study-specific tags in the session config. If no config is available in context, ask the researcher to provide it or paste relevant sections.

## Proposing new tags

When a concept genuinely doesn't fit any existing tag:
> `PROPOSED: [tag name] — [Type of code: Tool/Software/Company | keyword | Persona/Target User | Theme | Feature/Capability | Workflow/Process] — appears in N rows. Reason: [one sentence]`

Flag it; do not add it to the CSV silently. The researcher decides.

## When the researcher approves a proposed tag

Apply it to all rows where it fits, then add it to the config.

## Disambiguation

Common ambiguous terms and how to resolve them:
- **catalog** — use the specific catalog name (`data catalog`, `Hive catalog`) unless meaning is truly ambiguous
- **documents** — distinguish `unstructured data`, `documentation`, or `governance documents` based on context
- **pipeline** — use `data pipeline`, `ingestion pipeline`, or the relevant specific term

Full disambiguation reference: `reference/03-tagging.md`

## Output

Tags column populated inline in the CSV (comma-separated). After tagging, report:
- Total rows tagged
- Total rows with 0 tags (confirm expected)
- All proposed new tags with row counts
- Any rows flagged as ambiguous

Produce a downloadable CSV only when the researcher asks. Say `continue` to proceed to Phase 4.

## Full reference

`reference/03-tagging.md` · `reference/tagging-and-coding-guide.md`
