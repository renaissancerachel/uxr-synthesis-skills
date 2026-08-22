---
name: uxr-airtable-import
description: Import a tagged UXR data-points CSV into an Airtable base. Resolves or creates the Project, Participant, and Session, then writes Data points and links their Tags and Research Questions. Use when pushing a completed data-points CSV into Airtable.
---

# Import data points into Airtable

Push a completed, tagged data-point CSV (the output of the core pipeline) into the user's Airtable base. Resolve prerequisites in order, then batch-create the Data point records.

## Before you start

- Get the **base ID** and **write policy** from the `--- AIRTABLE ---` block in the session config. If the base ID is missing, ask. Never guess.
- Address every table and field **by name** — internal IDs are unique to this copy of the template. Full map: [`reference/base-reference.md`](../../reference/base-reference.md).
- This skill **writes**. Confirm matches with the user before creating records, and honor the write policy (never write PII unless explicitly provided and asked).
- Use your connector's write operations (commonly `list_records_for_table`, `create_records_for_table`). Enable typecast if you need to add a new select option on write.

---

## Fast path — when everything is new

If the user confirms upfront that the Project, Participant, and Session are all new, skip the searches and create all three in sequence: **Project → Participant → Session**. Collect the required info first.

---

## Prerequisites — resolve in this order

### 1. Project
Search **Projects** for a record whose `Project Name 🌎` matches the study name (exact-match filter).
- **Found:** confirm — "Found project **[name]** — right one?" Wait.
- **Not found:** collect and create. Useful writable fields: `Project Name 🌎` (required), `Status 🌎` (default `Conducting`), `Method 🌎`, `Kick Off Date 🌎`, `Project Objective 🌎`, `Product  🌎`.

### 2. Participant
Identify the participant from the CSV (the non-moderator speaker/username).
Search **Participants** with an exact-match filter on `First Name`.
- **Found:** confirm (show name + job title). Wait.
- **Not found:** create. Writable: `First Name` (required), `Last Initial`, `Participant ID` (e.g. `P2`), `Job Title`, `Source`. For panel/usability-tool studies, store the username verbatim as `First Name` and omit last name.
- **Never write** `Email`, demographics, or any PII unless the user explicitly provides it and asks.

### 3. Session
Search **Sessions** for a record linked to both the resolved Project and Participant (filter on `Project Name`).
- **Found:** confirm — "Found session **[Session ID]** — use it?" Wait.
- **Not found:** create. Writable: `Project Name` (`[projectRecordId]`), `Participant` (`[participantRecordId]`), `Session #` (**set to the participant number**, e.g. `P2`), `Date ✅` (`YYYY-MM-DD`), `Recording`, `Raw Data link`.
- Do not write `Session ID` (formula). If an existing session is missing `Session #`, backfill it before importing.

---

## Tag resolution

Collect every unique tag string from the CSV `Tags` column (comma-separated, trimmed). Skip anything that isn't a short label (e.g. full sentences that landed in the wrong column).

For each valid unique tag:
1. Filter **Tags/Codes** with an **exact-match** filter on `Tag`. Do **not** use fuzzy `search_records` — it produces false positives.
2. **Found:** record `tagName → recordId`.
3. **Not found:** create a record with `Tag` = the string and **always set `Type of tag`** — never leave it blank. If the tag is in the user's taxonomy config, use that type; otherwise default to `keyword` (most new tags are keywords) and list it under **New tags created** so the user can retype the few that are really `Persona/Target User`, `Feature/Capability`, or an interpretive `Code`.

Resolve all tags before writing any Data points.

## Research Question resolution

If the CSV has a `Research Question(s)` column:
1. Collect unique RQ strings.
2. Check **Research Questions** with an exact-match filter first.
3. Only create new RQs after the user confirms they're new and approved — RQs require judgment. Build an `RQ text → recordId` map.

---

## Writing Data points

Include every row with a non-empty `Data point` cell (moderator turns included, for context). Skip blank rows.

Create records in **Data points** in batches of up to 50. Fields:

| Field | Source | Notes |
|---|---|---|
| `Data points` | CSV `Data point` | Required |
| `Timestamp` | CSV `Timestamp` | duration — convert `HH:MM:SS` to total seconds; skip `00:00:00`/missing |
| `Speaker` | CSV `Speaker` | |
| `Sessions` | resolved session | `[sessionRecordId]` |
| `Tags` | tag map | array of record IDs — **codes first, then keywords** |
| `Finding(s)` | — | link later during synthesis, not at import |
| `Research Questions` | RQ map | array of record IDs; skip rows with no match |

Do not write lookup/formula fields (`Participant (from Sessions)`, `Date ✅ (from Sessions)`, `Project Name (from Sessions)`, etc.).

---

## Summary on completion

Report:
- **Data points created:** N
- **New tags created:** names + `Type of tag` for each (flag any defaulted to `keyword` for review)
- **Records skipped:** N (reason)
- **RQs not matched:** any unmatched RQ strings
- **Session:** the Session ID you wrote to (for reference — not a record ID)

---

*Field map: [`reference/base-reference.md`](../../reference/base-reference.md). Setup: [`../../SETUP.md`](../../SETUP.md).*
