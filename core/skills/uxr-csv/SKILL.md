---
name: uxr-csv
description: Use when the user wants to convert a cleaned transcript into a CSV data-point format — Phase 2 of the UXR synthesis workflow. Structures one-row-per-thought for tagging.
---

# /uxr-csv — Phase 2: Convert to CSV

Structure cleaned transcript text into one-row-per-data-point CSV format.

## Input required

Cleaned transcript in `[HH:MM:SS] Speaker: Text` format — from Phase 1 output or a pre-cleaned transcript the researcher provides. If it's missing, ask.

## Split rules

Split transcript turns so each row is **one complete thought**. Apply these triggers:
- Two or more distinct observations about different topics in one turn
- A shift from one theme to another mid-response
- A turn longer than 3 sentences where ideas can be cleanly separated

Do not split when:
- A longer turn is one continuous explanation of a single idea
- Splitting would break logical flow (the second sentence only makes sense after the first)

**Timestamp on splits:** all rows from the same original turn share the original timestamp. Never fabricate or interpolate timestamps.

## Row quality

- Minimum: 1 sentence expressing a complete thought
- Maximum: 3 sentences (longer is acceptable if it's one undivided idea)
- Drop pure greetings, single-word acknowledgments, and punctuation-only rows

Include all moderator turns — leave their Tags cell blank. They stay for context.

## CSV format

```
Timestamp,Speaker,Data point,Tags
```

- `Timestamp` — HH:MM:SS from the original transcript
- `Speaker` — participant or moderator identifier exactly as it appears
- `Data point` — one complete cleaned thought
- `Tags` — leave blank; populated in Phase 3

Study-specific columns (e.g., `Participant Role`, `Session`) go after `Tags`. Add them if the session config specifies them.

## CSV quoting rules

Any cell whose value contains a comma **must** be wrapped in double-quotes:
```
"AI, agentic AI, use case"
```

Any cell whose value contains a double-quote character must escape it by doubling:
```
"What does ""standardization"" look like"
```

This applies to every column. When writing the file, always quote cells that contain commas — do not rely on the reader to infer boundaries. This ensures the file imports correctly into Airtable and other tools without columns splitting.

## Output

Show as a formatted table in chat — first 20–30 rows, then offer to show more. Produce a downloadable file only when the researcher asks for it, named `[study-name]-data-points.csv`.

Say `continue` to proceed to Phase 3.

## Full reference

`reference/02-convert-to-csv.md`
