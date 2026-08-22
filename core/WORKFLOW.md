# UXR Synthesis — Workflow Overview
*Tool-agnostic. Runs in Bob, Claude Code, or any assistant that can load Agent Skills or accept file input.*

---

## What this workflow does

Turns raw research transcripts into structured, tagged, traceable data — then converts that data into actionable findings and a research report. Designed for qualitative UX researchers working with interview transcripts, usability sessions, or any free-text research data.

Six phases, each its own skill:

| Phase | Skill | What happens | Output |
|---|---|---|---|
| **1 — Clean** | `uxr-clean` | Remove noise from transcript; preserve meaning exactly | Cleaned transcript text |
| **2 — Convert to CSV** | `uxr-csv` | Structure cleaned text into one-row-per-data-point format | `study-data-points.csv` |
| **3 — Tag** | `uxr-tag` | Apply taxonomy tags and behavioral codes to each row | Tags column populated |
| **4 — Research questions** | `uxr-rq` | Match each data point to the study's research questions | RQ column populated |
| **5 — Findings** | `uxr-findings` | Identify patterns across all data; draft actionable findings | Findings document |
| **6 — Report** | `uxr-report` | Assemble findings into a structured research report | Research report |

Two more skills round out the set:
- **`uxr`** — a router. Start here if you're not sure which phase you need.
- **`uxr-research-plan`** — write a research plan *before* a study (independent of the synthesis phases).

Phases 1–4 work at the **row level** (one data point at a time). Phases 5–6 work at the **dataset level** (looking across all rows to find patterns).
**Do not start Phase 5 until Phases 2–4 are complete and the Phase 4.5 coding-QA checkpoint (`/uxr-coding-qa`) has passed.** Findings can only emerge from a complete, consistently coded dataset — the QA pass makes coding consistent (keyword completeness, uneven-code backfill, near-duplicate merges) before synthesis.

---

## How to start a session

Paste this block at the top of your session (or fill in the fields when the skill asks). See `config-template.md` for a reusable version and `config-example.md` for a filled-in one.

```
I want to run the UXR synthesis workflow on a research transcript.

--- SESSION CONFIG ---
Study name: [exact name — used for file naming]
Study goal: [one sentence: what were you trying to learn?]
Research questions:
  RQ1: [text]
  RQ2: [text]
  RQ3: [text]
Participant roles: [e.g., "5 data engineers, 3 platform admins, 2 data analysts"]
Study type: [moderated interview / unmoderated usability test / tree test / card sort / survey]
Moderator name: [exact speaker label as it appears in the transcript]
Tag config: [attach your taxonomy.json + codes.json, or write "using team default"]

--- INPUT ---
[Choose one:]
  A. Raw transcript (VTT or DOCX pasted below or attached)
  B. Pre-cleaned transcript (pasted below or attached)
  C. Transcript App CSV (attached — re-tag only, skip Phase 1)

[Paste or attach input here]

--- WORKFLOW MODE ---
[Choose one:]
  Step-by-step: show me each phase output and wait for "continue" before proceeding
  Auto-chain: run Phases 1→2→3→4 automatically, pause before Phase 5 for my review
```

> **Tip:** Save your filled-in config as `my-synthesis-config.md` in your project folder and paste it at the start of every session instead of retyping it.

---

## Operating modes

**Step-by-step (default).** The assistant completes one phase, shows the output, then waits for you to say `continue` before moving on. Use it while learning the workflow or when you want to review before the next phase runs.

**Auto-chain.** The assistant runs Phases 1–4 automatically with two mandatory pause points:
1. **After the Phase 1 pilot** (5 example cleanings) — you approve before the full clean runs.
2. **Before Phase 5** (findings) — you explicitly say `proceed to findings` after reviewing the tagged CSV.

---

## Shared rules (apply across all phases)

**CSV format** — the working file for this workflow:
```
Timestamp, Speaker, Data point, Tags
```
Add study-specific columns after `Tags` (e.g., `Research Question`, `Participant Role`, `Session`) and the skills will use them.

**Moderator rows** — include them in Phases 1–2 for context; do not tag them in Phase 3; do not use them as evidence in Phase 5.

**Quote attribution** — UserTesting usernames verbatim; real names as first-initial + last-initial only (e.g., `RM`). Never include record IDs, session dates, companies, or roles in the attribution line.

**Tag limits** — keywords: no cap (more is better — tag every tool, company, role, and artifact named); interpretive codes: keep tight (~5, each should differentiate the row); 0 minimum (many rows get none).

**Proposing new tags** — flag as `PROPOSED: [tag] — [type] — reason: appears in N rows`. Never add silently; the researcher decides.

**No auto-export** — don't produce a downloadable CSV until the researcher says "export."

---

## Files-first, Airtable optional

This workflow runs **entirely with files** — the CSV is the database. Each study gets a folder; the working file is `[study-name]-data-points.csv`, which accumulates structure across phases and is both human-readable (Excel, Sheets, Numbers) and assistant-readable.

When your team keeps its research in **Airtable**, the optional **Airtable add-on** (`../airtable-addon/`) adds two skills: one to push a finished CSV into the base, one to query and report from it. The core pipeline produces the CSV; the add-on handles Airtable separately. The add-on needs its own one-time setup — see its README.

---

## What's in this bundle

```
core/
  WORKFLOW.md            ← this file
  config-template.md     ← reusable session config (fill in once)
  config-example.md      ← a worked example
  skills/
    uxr/                 ← router — start here if unsure
    uxr-clean/           ← Phase 1  (+ reference/)
    uxr-csv/             ← Phase 2  (+ reference/)
    uxr-tag/             ← Phase 3  (+ reference/: guide, taxonomy.json, codes.json, taxonomy-setup)
    uxr-rq/              ← Phase 4  (+ reference/)
    uxr-coding-qa/       ← Phase 4.5 — coding QA checkpoint before findings
    uxr-findings/        ← Phase 5  (+ reference/: guide)
    uxr-report/          ← Phase 6  (+ reference/: guide)
    uxr-research-plan/   ← plan a study (standalone)
```

Each skill is **self-contained**: everything it needs is inside its own folder. See `README.md` for install steps.
