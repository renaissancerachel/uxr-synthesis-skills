# Session Config Template
*Copy this file. Rename it `my-synthesis-config-[yourname].md`. Fill in every field.*
*This is the block you paste at the top of every synthesis session.*
*See `WORKFLOW.md` for the full workflow, and the taxonomy-setup guide bundled with the `uxr-tag` skill (`skills/uxr-tag/reference/taxonomy-setup.md`) to build your tag config.*

---

## Step 1 — Fill in your standing settings (do this once)

These don't change between studies. Fill them in now and leave them.

**Moderator name:** the exact speaker label that appears in your transcripts for your own turns.
> e.g., `Moderator`, `Interviewer`, or your name exactly as the transcript renders it

**Attribution rules:** how you identify participants in findings and reports.
> UserTesting studies: UT username verbatim (e.g., `allisfair777`)
> Real-name studies: first initial + last initial (e.g., `RM`)
> If unsure — check how participants are labelled in your recruiting tool and use that consistently.

**Tag config:** where your team's tag files live.
> The watsonx.data team default ships with the `uxr-tag` skill: `skills/uxr-tag/reference/taxonomy.json` + `codes.json`. Attach or paste them at session start.
> Building your own? Complete the taxonomy-setup guide (`skills/uxr-tag/reference/taxonomy-setup.md`) first.

**Workflow mode:** how you want the assistant to proceed between phases.
> `Step-by-step` — shows output after each phase and waits for you to say "continue"
> `Auto-chain` — runs Phases 1–4 automatically, pauses before Phase 5

---

## Step 2 — Save your config block

Replace every `[FILL IN]` with your standing settings. Leave the study-specific fields as blanks — you fill those in at the start of each session.

```
--- SESSION CONFIG ---

Study name: [fill in each session — must match your project tracker name exactly]
Study goal: [fill in each session — one sentence]
Research questions:
  RQ1: [fill in each session]
  RQ2: [fill in each session]
  RQ3: [fill in each session — add or remove RQs as needed]
Participant roles: [fill in each session — e.g., 5 data engineers, 3 platform admins]
Study type: [fill in each session — moderated interview / usability test / tree test / card sort]

Moderator name: [FILL IN — your speaker label as it appears in transcripts]
Tag config: [FILL IN — "using team default (uxr-tag reference)" or path to your own tag files]
Output file: [FILL IN — folder convention, e.g., research projects/[study name]/[study-name]-data-points.csv]

Attribution:
  [FILL IN — e.g., "UserTesting studies: UT username verbatim. Real-name studies: first + last initial."]

Transcript input:
  If raw VTT or DOCX → run Phase 1 (clean), then Phase 2 (CSV), then Phase 3 (tag).
  If pre-cleaned transcript → skip to Phase 2.
  If CSV from Transcript App → skip to Phase 2; re-tag from scratch in Phase 3.
    Treat app Keywords column as candidates only — do not carry forward as final tags.

Moderator rows:
  Include in Phase 1 and Phase 2 CSV for context. Do not tag in Phase 3. Do not use
  as evidence in Phase 5.

Tag rules:
  Max [FILL IN — default 5–7] tags per row. Min 0.
  Proposed new tags: flag as PROPOSED: [name] — [type] — [reason]. Do not add silently.

ASR corrections:
  [FILL IN — list the technical terms that get mis-transcribed in your research domain]
  e.g.:
  ProductName → ProductName
  FeatureName → FeatureName

Export:
  Do not auto-export CSV at any phase. Wait until I say "export."

--- WORKFLOW MODE ---
[FILL IN — Step-by-step or Auto-chain]
```

---

## Step 3 — Notes for your team context

Add any team-specific context a new researcher joining your team would need — things that don't belong in the config block but affect how the workflow runs.

**Examples of what to put here:**
- Where your project folder lives and how it's organized
- Which Airtable base/tables map to which phases (if you use the Airtable add-on)
- How your attribution rules work for your specific recruiting tool
- Study types your team runs that have special handling (e.g., comparative tree tests with version-label conventions)
- How to get Airtable access if write-back is part of your workflow (see the Airtable add-on README — you supply your own access; no credentials ship with these skills)

*Delete this section if you're not handing this off to a teammate.*
