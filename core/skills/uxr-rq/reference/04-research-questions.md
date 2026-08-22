# Phase 4 — Assign Research Questions
*Part of the UXR Synthesis workflow: Clean, CSV, Tag, RQ, Findings, Report.*

---

## What this phase does

Reads each substantive data point row and matches it to the study's research questions — the questions the study was designed to answer. The goal is traceability: when you draft a finding in Phase 5, you can see exactly which RQs it addresses and which data points support it.

This phase also serves as an early diagnostic: if an RQ has very few matching data points, either the study didn't generate much evidence for it, or the question wasn't well served by the research design. Both are worth knowing before you draft findings.

---

## How to match

For each substantive participant row (not moderator rows), ask:

> Does this data point directly address or inform one of the research questions?

**Direct hit:** the data point contains information that answers, partially answers, or meaningfully informs the RQ. Apply the RQ.

**Tangential:** the data point is loosely related to a topic the RQ covers, but it doesn't actually speak to the question being asked. Do not apply the RQ.

**No match:** many rows won't match any RQ. That is correct — not every data point is relevant to every research question, and some data points are context-setting rather than evidence. Leave the RQ column blank.

A single row may match more than one RQ. Apply all that genuinely apply.

---

## Output format

Add a `Research Question(s)` column to the CSV after `Tags`. Use the RQ number(s) from the session config:

```csv
Timestamp,Speaker,Data point,Tags,Research Question(s)
00:05:18,NP,"Data that's confidential — financial records — that always stays on-prem.","regulated industry, on-prem, privacy concern","RQ2"
00:05:18,NP,"For cloud, we only move aggregated results, never actual patient or PII data.","on-prem, cloud, hybrid, privacy concern","RQ2, RQ3"
00:02:22,NP,"I primarily work with Python and build agents using LangGraph.","Python, LangGraph, data engineer",""
```

If Airtable is the destination and Research Questions is a linked field (not a free-text column), note the RQ number in the CSV and link it manually in Airtable during import. The CSV is the source of truth — Airtable reflects it.

---

## Large datasets

If the CSV has 100 or more substantive participant rows, confirm with the researcher before running this phase. It is the most time-intensive phase and may be worth batching or scoping to the rows most likely to yield findings (highest-content rows, rows already tagged with study-relevant codes).

---

## RQ coverage report

After completing this phase, produce a short coverage report:

```
RQ coverage summary
-------------------
RQ1: [text of RQ1]
  Matched rows: N
  Strong evidence (3+ rows): [yes/no]

RQ2: [text of RQ2]
  Matched rows: N
  Strong evidence (3+ rows): [yes/no]

RQ3: [text of RQ3]
  Matched rows: N
  Strong evidence (3+ rows): [yes/no]

RQs with thin evidence (<3 rows): [list]
  → These may not support a finding. Flag for researcher.
```

This report is not a finding — it is a signal about where to look in Phase 5.

---

## Moderator rows

Do not assign RQs to moderator rows. Leave their Research Question(s) cells blank.
