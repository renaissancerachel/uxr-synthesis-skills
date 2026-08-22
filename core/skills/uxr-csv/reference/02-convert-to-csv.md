# Phase 2 — Convert to CSV
*Part of the UXR Synthesis workflow: Clean, CSV, Tag, RQ, Findings, Report.*

---

## What this phase does

Takes the cleaned transcript from Phase 1 (or a pre-existing clean input) and converts it into a structured CSV where each row is one complete, standalone data point — a single thought, observation, or quote that can be tagged, analyzed, and traced independently.

The output of this phase is `[study-name]-data-points.csv`. This file is the working artifact for all remaining phases.

---

## CSV format

```
Timestamp, Speaker, Data point, Tags
```

| Column | What goes here |
|---|---|
| `Timestamp` | Original timestamp from the transcript (HH:MM:SS). Every row that came from the same original turn keeps the same timestamp — do not fabricate new timestamps for split rows. |
| `Speaker` | Participant identifier exactly as it appears in the transcript. Moderator rows keep the moderator's speaker label. |
| `Data point` | The cleaned text for this row — one complete thought, 1–3 sentences. |
| `Tags` | Leave blank. Populated in Phase 3. |

**Study-specific columns** may be added after `Tags`. Common examples: `Participant Role`, `Session`, `Study Phase`. The skill reads any additional columns and uses them in analysis — they do not need to match the base spec.

---

## Splitting rules

Most transcript turns will need to be split. Each turn in the cleaned transcript may contain multiple distinct ideas. The goal is one data point per row — not one turn per row.

**Split when a turn contains:**
- Two or more distinct observations about different topics
- A shift from one theme to another mid-response
- A turn longer than 3 sentences where the ideas can be cleanly separated

**Do not split when:**
- A longer turn is one continuous explanation of a single idea
- Splitting would break the logical flow of evidence (the second sentence only makes sense after the first)
- The turn is 1–2 sentences expressing one thought

**Timestamp rule on splits:**
All rows from the same original turn share the same original timestamp. Do not approximate, interpolate, or create new timestamps. Every split inherits the parent turn's timestamp.

---

## Row quality rules

**Minimum viable row:** 1 sentence that expresses a complete thought. *"I'd never use that."* is valid.

**Maximum row length:** 3 sentences. If a row runs longer and contains only one idea, it is acceptable — do not split for length alone.

**Rows to include:**
- All substantive participant turns
- All moderator turns (even questions — they provide context)
- Behavioral observations, if the transcript includes them (e.g., *"[clicked the wrong button]"*)

**Rows to drop at this stage:**
- Pure greetings with no content (*"Hi, great to meet you"*)
- Single-word acknowledgments that survived Phase 1 (*"Sure."*, *"Yep."*)
- Rows that are entirely punctuation or whitespace

---

## Moderator rows

Include moderator rows in the CSV. Set `Speaker` to the moderator's exact speaker label (e.g., `Interviewer`). Leave `Tags` blank. Moderator rows will be excluded from tagging in Phase 3 and from evidence in Phase 5, but they stay in the CSV for context.

---

## Output

When this phase is complete, produce the CSV in one of two ways depending on what the researcher asks:

**If researcher says "show me the CSV":**
Display as a formatted table in chat (first 20–30 rows, then offer to show more).

**If researcher says "export" or "give me the CSV":**
Produce a downloadable `.csv` file named `[study-name]-data-points.csv`.

**Do not auto-export.** Wait to be asked.

---

## What the CSV looks like

A few example rows from a moderated interview study:

```csv
Timestamp,Speaker,Data point,Tags
00:02:14,Interviewer,"Can you tell me about how you handle data ingestion at your company?",
00:02:22,NP,"Most of my projects in the last year have been heavily focused on generative AI and agentic AI applications.",
00:02:22,NP,"I primarily work with Python and build agents using LangGraph.",
00:05:10,Interviewer,"How do you decide what goes on-prem versus in the cloud?",
00:05:18,NP,"Data that's confidential — financial records, salary data — that always stays on-prem.",
00:05:18,NP,"For cloud, we only move aggregated results, never actual patient or PII data.",
```

Notice:
- Both rows at `00:05:18` came from the same original turn — split but same timestamp
- Moderator rows included, Tags blank
- Each row is one complete thought
