# Base reference — UX Research template

The field map both add-on skills work from. Everything here is addressed **by name**, because your copy of the template base has its own internal IDs. Wherever a skill says "the Data points table" or "the `Tag` field," resolve it by name against the base ID in your session config.

> **No IDs, no secrets.** This file names tables and fields only. Access comes from your own connector — see [SETUP.md](../SETUP.md).

---

## Tables (8)

| Table | Purpose |
|---|---|
| **Projects** | One row per study (or source). Parent record for Sessions. |
| **Participants** | The people you talked to. May hold personal info — never publish. |
| **Sessions** | One row per research session; links a Participant to a Project. |
| **Data points** | Verbatim quotes/observations — the primary evidence layer. |
| **Tags/Codes** | Coding backbone — interpretive **Codes** + exhaustive **keyword** tags. |
| **Findings** | Synthesized statements (patterns across Data points, not opinions). |
| **Research Questions** | The questions the study set out to answer. |
| **Screens** | *Optional.* UI screens tied to the Data points about them. |

---

## Key fields per table

> **Projects field names end with a 🌎 emoji** — exact strings matter when filtering (e.g. `Project Name 🌎`). The Sessions date field is `Date ✅`.

### Projects
| Field | Type | Notes |
|---|---|---|
| `Project Name 🌎` | singleLineText | Primary field |
| `Status 🌎` | singleSelect | Planning / Conducting / Synthesis / Complete / Backlog / Paused-Blocked / Canceled / Support |
| `Method 🌎` | multipleSelects | Interview, Usability Test, Survey, Card Sort, Tree Test, … |
| `Project Objective 🌎` | richText | |
| `Key Findings 🌎` | richText | |
| `Kick Off Date 🌎` / `Completed Date 🌎` | date | `YYYY-MM-DD` |
| `Link to research plan 🌎` / `Link to final deliverables 🌎` | url | |
| `Product  🌎` | singleLineText | What was studied |
| `Researchers 🌎` | multipleCollaborators | Real Airtable users only |
| `Research Sessions 🌎` | link → Sessions | |

### Participants ⚠️ may contain personal info — never publish
| Field | Type | Notes |
|---|---|---|
| `Name` | formula | Auto: `Source, Participant ID` — read-only |
| `Participant ID` | singleLineText | e.g. `P1`, `P2` |
| `First Name` | singleLineText | For panel/usability tools, may store the username verbatim |
| `Last Initial` | singleLineText | |
| `Job Title` | singleLineText | |
| `Source` | singleSelect | How they were recruited |
| `Employment Status` / `Industry` / `Company Size` / `Seniority Level` / `Interest level` | select/text | Profile fields |
| `Agreement signed?` | checkbox | |
| `Sessions` | link → Sessions | |

### Sessions
| Field | Type | Notes |
|---|---|---|
| `Session ID` | formula | Auto: `Session #, Project` — read-only |
| `Participant` | link → Participants | pass `[participantRecordId]` |
| `Project Name` | link → Projects | pass `[projectRecordId]` |
| `Session #` | singleLineText | Set to the participant number (`P1`, `P2`, …) |
| `Date ✅` | date | `YYYY-MM-DD` |
| `Recording` | url | |
| `Raw Data link` | url | transcript / survey / notes |
| `Session Notes` | richText | |
| `Raw data` | link → Data points | inverse of Data points → Sessions |

### Data points — the evidence layer
| Field | Type | Notes |
|---|---|---|
| `Data points` | multilineText | The raw quote/observation — primary field |
| `Speaker` | singleLineText | Who said it |
| `Timestamp` | duration | store total **seconds** (e.g. `01:02:03` → 3723) |
| `Sessions` | link → Sessions | pass `[sessionRecordId]` |
| `Tags` | link → Tags/Codes | array of tag record IDs — **codes first, then keywords** |
| `Finding(s)` | link → Findings | |
| `Research Questions` | link → Research Questions | |
| `Screens` | link → Screens | optional |
| `Participant / Project Name / Date (from Sessions)` | lookup | read-only — do not write |

### Tags/Codes — two layers in one table
| Field | Type | Notes |
|---|---|---|
| `Tag` | singleLineText | Tag name — primary field |
| `Type of tag` | singleSelect | `Code` (interpretive) · `keyword` · `Feature/Capability` · `Workflow/Process` · `Persona/Target User` · `Tool/Software` · `Company` |
| `Details` | richText | Neutral definition of what the tag labels |
| `Data points` | link → Data points | **Fastest path to every quote on a topic — read this field** |
| `# of Observations` | count | read-only |

**The two layers:**
- **Codes** (`Type of tag = Code`) — interpretive labels for what a quote *means* (a behavior, barrier, pattern). Keep tight: ~5 max per quote.
- **Keywords** (all other types) — concrete, filterable things a quote *names* (tools, features, roles, artifacts). **Grounded only:** tag a keyword just when the term is explicitly in the quote, or it clearly refers to a named tool/product. Be exhaustive over the terms actually in the text — never invent paraphrase tags.

### Findings
| Field | Type | Notes |
|---|---|---|
| `Finding statement` | singleLineText | 5–15 words, sentence case, one observation — primary field |
| `Details` | richText | Bullets + supporting quotes + a `Recommendation` section |
| `Severity` | singleSelect | Major Issue · Minor Issue · Benefit/Positive · Suggestion · Behavior |
| `Data points` | link → Data points | the evidence |
| `# of Observations` | count | read-only — how many Data points back it |

### Research Questions
| Field | Type | Notes |
|---|---|---|
| `Research Question` | singleLineText | Primary field |
| `Conclusion` | richText | Fill once evidence is in |
| `Associated follow up questions` | richText | |
| `Data points` | link → Data points | |

### Screens *(optional)*
| Field | Type | Notes |
|---|---|---|
| `Screen name` | singleLineText | Primary field |
| `Screen` | attachment | The image (upload in the UI) |
| `Type` | singleSelect | e.g. Base tab / View / Record — your own values |
| `Notes` | richText | |
| `Data points` | link → Data points | quotes about this screen |

---

## Write rules

**Never write to these field types — they error:** `formula`, `rollup`, `count`, `multipleLookupValues`, `autoNumber`, `createdTime`, `lastModifiedTime`, `createdBy`, `lastModifiedBy`, `button`.

**Linked-record fields:** pass an array of record IDs, e.g. `["recXXXXXXXXXXXXXX"]`.

**Select fields:** pass the option **name** as a plain string (e.g. `"Complete"`), not the `{id,name,color}` object a read returns. To add a new option on write, enable your connector's typecast option.

---

## Querying tips

- **Fastest path to quotes on a topic:** find the Tags/Codes record where `Tag` matches, then read its `Data points` field — returns every linked quote with no substring searching. This is also how an AI agent should query the base.
- **Pull an interpretive theme vs. a concrete thing:** filter Tags/Codes by `Type of tag` — `Code` for behaviors/patterns, `keyword`/`Feature/Capability`/`Tool/Software` for filterable specifics.
- **A Finding that spans multiple Projects** (dedupe the project list of its linked Data points) is an especially strong one.
- **Deduplicate lookup fields** (e.g. `Project Name (from Sessions)`) before counting — they repeat once per linked Data point.

## Attribution (for output)

- Real-name studies: first initial + last initial only (e.g. `RM`).
- Panel/usability-tool usernames: use the `First Name`/`Speaker` value verbatim; don't alter it even if it looks like a real name.
- **Never include Airtable record IDs in user-facing output.**
- Don't conflate Finding records with Data point records — both start with `rec`, different tables.
