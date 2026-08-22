---
name: uxr-coding-qa
description: Use when the user wants to QA the coding/tagging before drafting findings — Phase 4.5 of the UXR synthesis workflow. A consistency + keyword-completeness checkpoint that makes sure the coding was done well before Findings. Trigger phrases — "coding QA", "check the coding", "did we code this well", "consistency pass", "backfill codes", "codes are uneven", "clean up the tags before findings".
---

# /uxr-coding-qa — Phase 4.5: Coding QA (checkpoint before Findings)

A quality gate between **Phase 4 (RQ)** and **Phase 5 (Findings)**. Findings are only as good as the coding underneath them: if a keyword is applied to some mentions but not others, every downstream filter, count, and pattern is wrong. This phase makes the coding **complete and consistent** before synthesis begins.

Guiding rule: **"More is better" for codes — tag every filterable keyword; quantity is good because you never know what someone will want to filter by. Quality is for Findings, not codes.** This phase acts on the **keyword layer only**. It never adds or edits analytical **Theme** codes — those are the researcher's synthesis layer.

> Relationship to Phase 3 (`/uxr-tag`): the 5–7-tags-per-row cap in `/uxr-tag` governs the *initial semantic-coding* pass (keeping the interpretive layer readable). This QA pass intentionally allows **more** keyword tags per row, because keywords are the filter layer and completeness beats brevity there.

## Input required

The coded dataset — normally the study's **Data points** in Airtable (post-import), or a fully tagged CSV. If working in Airtable, use the `airtable-uxr` skill's access rules: **Claude uses the Keychain token via REST, never the MCP connector**; introspect the target base first (peer bases differ — e.g. the Carbon base's tag field is `Codes` / primary `Code` / category `Type of code`). See the airtable-uxr add-on skill (base access + reference).

If neither is present, ask which study/base and pull the data points (id, text, current codes, session/participant) before starting.

## The six QA checks

**1. Keyword completeness & consistency — the core check ("uneven codes").**
For every keyword / tool / company / role / artifact code already in use, scan all data-point **text** for verbatim mentions (word-boundary match) that are **missing** the code, and backfill them. Tier the candidates before writing:
- **SAFE (auto-apply):** unambiguous named entities (tools, products, companies), all-caps acronyms matched **case-sensitively** (`MCP`, `IBM`, `CSS`, `UI`), and distinctive multi-word keywords (`design system`, `pull request`, `pair-programming`).
- **REVIEW (hold for the researcher):** ambiguous common words whose string also has a non-keyword sense in the corpus (`time`, `code`, `team`, `agent`, `model`, `table`, `button`, `skills`). Report counts + sample lines; apply only on the researcher's OK.
Always **merge** (union) with existing codes — never overwrite. Match is verbatim only; never infer a keyword that isn't in the text.

**2. Under-coded substantive rows.** List substantive participant rows with **0 codes**. These are coding gaps — flag them for a tagging pass (don't invent codes to fill silence).

**3. Catch-all / low-signal codes.** Flag `pain point` and similar meaningless catch-alls (see `/uxr-tag`), and propose the specific replacement code.

**4. Near-duplicate codes.** Find singular/plural and spelling variants pointing at one concept (`developer`/`developers`, `Carbon Element Styles`/`Carbon Elements Styles`). Propose a canonical spelling and merge.

**5. Moderator / interviewer rows coded by mistake.** By convention these stay uncoded. Flag any that carry codes.

**6. Theme-layer safety.** Confirm the pass added **no** Theme-typed codes. If a genuinely new *keyword* concept recurs, propose it (`PROPOSED: name — keyword — N rows`); the researcher decides. New analytical themes are out of scope here.

## Doing it at scale

For a large study (many sessions / >300 data points), fan out one tagger per session over the transcript text, but keep the **vocabulary controlled centrally**: give every tagger the existing code list to reuse by exact spelling, then aggregate, canonicalize new-code spelling, drop any stray Theme codes, validate every row id, and write centrally (create new codes once, then union links). Dry-run before any write. Preserve original code links so the pass is fully reversible.

## Output — the QA report

Report, then apply safe fixes:
- **Fixed automatically:** SAFE backfill links added (by code + count), rows enriched, new keyword codes created.
- **Held for you:** the REVIEW list (ambiguous codes + counts + samples), proposed merges, catch-all replacements, under-coded rows, mis-coded moderator rows.
- **Integrity:** existing codes preserved (0 overwritten), row ids validated, no Theme codes touched, reversible.

State the gate result plainly: **coding QA passed** (safe fixes applied, held items are optional) or **blocked** (list what needs a decision). Say `continue` to proceed to Phase 5 (Findings).

## Full reference

`/uxr-tag` (Phase 3 coding rules) · `airtable-uxr` skill (base access, token, attribution) · the airtable-uxr add-on skill (base access + reference)
