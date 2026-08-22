---
name: uxr-rq
description: Use when the user wants to assign research questions to tagged data points — Phase 4 of the UXR synthesis workflow. Maps each data point to the study's research questions for traceability.
---

# /uxr-rq — Phase 4: Assign Research Questions

Match each substantive data point to the study's research questions. Goal: traceability from finding → RQ → evidence.

## Input required

Two things. If either is missing, ask:
1. **Tagged CSV** — with `Timestamp, Speaker, Data point, Tags` columns (Phases 2–3 complete)
2. **Research questions** — the numbered list from the session config

For large datasets (100+ substantive participant rows): confirm with the researcher before running. Suggest batching or scoping to highest-content rows first.

## Matching rule

For each substantive participant row (not moderator rows), ask:

> Does this data point directly address or inform one of the research questions?

- **Direct hit** — the data point answers, partially answers, or meaningfully informs the RQ → apply it
- **Tangential** — loosely related to a topic the RQ covers, but doesn't actually speak to the question → leave blank
- **No match** — leave blank; not every row matches an RQ, and that is correct

A single row may match more than one RQ. Apply all that genuinely apply.

## Output format

Add a `Research Question(s)` column to the CSV after `Tags`.

**The cell value must be the full verbatim text of the research question — not a number or shorthand like "RQ2".** When a row matches multiple RQs, write all matching questions as a comma-separated list in a single cell.

```csv
Timestamp,Speaker,Data point,Tags,Research Question(s)
00:05:18,NP,"Data stays on-prem.","on-prem, privacy concern","What does 'standardization' look like in practice — who owns it, how is it enforced, and how does it break down?"
00:05:18,NP,"Only aggregated results move to cloud.","on-prem, cloud, hybrid","What does 'standardization' look like in practice — who owns it, how is it enforced, and how does it break down?, What would Data Stewards need to see, know, or control before adopting a skill created by someone else?"
00:02:22,NP,"I build agents using LangGraph.","Python, LangGraph, data engineer",""
```

This matches how Airtable resolves RQ links — by text matching against the Research Questions table.

## RQ coverage report

After matching, produce:

```
RQ coverage summary
-------------------
RQ1: [full question text]
  Matched rows: N   Strong evidence (3+ rows): yes/no

RQ2: [full question text]
  Matched rows: N   Strong evidence (3+ rows): yes/no

RQs with thin evidence (<3 rows): [list]
→ These may not support a finding. Flag for researcher.
```

This is a diagnostic signal, not a finding.

## Moderator rows

Leave Research Question(s) blank for all moderator rows.

## Full reference

`reference/04-research-questions.md`
