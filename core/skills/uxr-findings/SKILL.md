---
name: uxr-findings
description: Use when the user wants to identify patterns and draft research findings from a tagged CSV — Phase 5 of the UXR synthesis workflow. Produces evidence-graded finding statements with quotes and RQ traceability.
---

# /uxr-findings — Phase 5: Draft Findings

Identify patterns across the complete tagged dataset and draft actionable findings.

## Gate check

Before starting, confirm:
- Phase 2 (CSV) complete — structured data points exist
- Phase 3 (Tags) complete — Tags column populated
- Phase 4 (RQ) complete — Research Question(s) column populated
- Phase 4.5 (Coding QA, `/uxr-coding-qa`) passed — coding is complete and consistent (keyword backfill done, near-duplicates merged)

If any phase is incomplete, stop and say which phase to finish first.

## Input required

Complete tagged CSV with `Timestamp, Speaker, Data point, Tags, Research Question(s)` columns. If missing, ask.

If there is a prior findings list (from an earlier session, Airtable, or attached file): scan it first. Match candidates against existing findings before drafting new ones.

## Pattern threshold

A pattern qualifies as a finding when:
- At least 2–3 data points support it
- Those data points come from at least 2 different participants

One participant saying the same thing twice is an observation, not a finding.

## Discovery — run in order

**1. RQ-anchored (primary)**
For each research question, gather all matched rows, read them across participants, and identify what multiple participants keep saying. These are the primary deliverables.

**2. Tag-cluster (secondary)**
Find high-frequency codes and taxonomy tags. Pull all rows per code and check whether they cluster around one shared observation. If yes, check RQ overlap — it may extend an existing finding or be emergent.

**3. Emergent**
Patterns outside any research question scope. Draft them; flag with `[EMERGENT — outside RQ scope]`. Emergent findings reveal gaps in the research plan — surface them, don't suppress.

## Prior findings

If a match to an existing finding exists: note the prior finding ID and the new data points to add — do not draft a duplicate.
If the pattern extends an existing finding: flag as "extends finding [ID]."
If the pattern contradicts an existing finding: flag both — contradictions are as valuable as confirmations.

## Finding format

```
---
Finding [N]  [STRONG / MODERATE / DIRECTIONAL / DRAFT]  [EMERGENT if applicable]

Statement: [5–15 words, sentence case, single observation]

- **[Sub-theme header]**
    - "[exact quote]" — [Participant ID]
    - "[exact quote]" — [Participant ID]
- **[Sub-theme header]**
    - "[exact quote]" — [Participant ID]

**Implications** OR **Recommendation**   ← closing section; include when it adds something (see rules below)
[one short paragraph]

Supporting data points: [row timestamps or numbers]
Matched RQs: [RQ numbers]
Tags driving this finding: [tags that clustered here]
---
```

**Statement rules:**
- Sentence case — capitalize first word and proper nouns only
- One observation — no "and/but/however" joining two ideas; split those into two findings
- Observation only — not a recommendation ("Add a validation step" is a recommendation; move to closing section)
- Named actor — "data engineers," "users," "buyers"; no passive constructions
- Specific anchor — a feature, flow, label, or user type; not a generic topic
- Synthesized — not a verbatim quote

**Description rules (Details field):**
- Everything is a bullet. Each sub-theme is a **top-level bullet with a bold header**; its quotes are **sub-bullets nested one level under it (4-space indent)**. No bare bold-header lines, no unindented quotes.
- Opens with the first evidence bullet — never restates the statement.
- 1–3 sub-theme bullets; every one backed by ≥1 direct quote (paraphrase doesn't count — the quote is the evidence).
- Attribute every quote. **Default house form: first+last initials, no periods (`— VC`)**, or the verbatim username for UserTesting. (The shareable-report standard is `— P#, role, organization`; confirm which form a study uses before writing — internal studies of named colleagues use initials.)
- Scannable structure, not prose paragraphs.

**Closing section (Implications / Recommendation) — optional, but expected wherever it adds something:**
- Skip it only when the action is self-evident (a bug-like finding) or the finding is pure context. A weak, generic closing ("improve this area") is worse than none.
- **Implications** — tentative: use when you see a direction but don't own the decision (a cross-study pattern, a tension to resolve, a question to open).
- **Recommendation** — a specific action with a verb (KEEP / MOVE / RENAME / SPLIT / ADD / REMOVE / SUPPRESS), grounded in the evidence. Use only when you understand the constraint space; otherwise use Implications.
- Name role differences when the evidence supports them, rather than treating "users" as a monolith.

**Evidence strength:**

| Label | Criteria |
|---|---|
| Strong | 3+ data points, 3+ participants, consistent across dataset |
| Moderate | 2–3 data points, 2+ participants, consistent within a subgroup |
| Directional | 2+ data points but 1 study or 1 participant type — needs more data |
| Draft | 1–2 data points — worth noting, not publishable without more evidence |

## Run the improvement checklist before finalizing

Full checklist: `reference/05-findings.md` — Improvement checklist section.

## Output

All findings in the format above, then a summary:
- Total findings: N
- Strong / Moderate / Directional / Draft counts
- RQs with no supporting findings
- Emergent findings flagged
- Proposed new tags from this phase

Say `continue` to proceed to Phase 6.

## Full reference

The load-bearing rules are inlined above, so this skill stands alone even when installed
outside the repo. For depth and worked examples, the full guides live **in the repo** (they
are not bundled into the installed skill): `reference/findings-writing-guide.md` and
`reference/05-findings.md` (improvement checklist). When working in the repo, read
the findings-writing guide before finalizing.
