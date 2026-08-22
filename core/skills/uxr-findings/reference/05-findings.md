# Phase 5 — Draft Findings
*Part of the UXR Synthesis workflow: Clean, CSV, Tag, RQ, Findings, Report.*

> **Do not start this phase until Phases 2–4 are complete.** Findings require looking across a complete, tagged, RQ-matched dataset. Running this phase on partial data produces speculative findings, not evidence-grounded ones.

---

## What this phase does

Reads the complete tagged CSV and identifies patterns — recurring themes across multiple participants that rise to the level of a finding. Then drafts each finding in a format that is actionable, scannable, and directly tied to evidence.

---

## What makes a pattern a finding

A pattern qualifies as a finding when:
- At least **2–3 data points** support it
- Those data points come from at least **2 different participants** (one participant saying something twice is an observation, not a pattern)
- The data points share a specific, nameable observation — not just a general topic area

A data point from one participant is worth noting. It is not a finding.

---

## Three discovery methods (in priority order)

### Method 1 — RQ-anchored (primary)
Start here. For each research question in the session config:
1. Gather all rows matching that RQ from the Research Questions column
2. Read them end-to-end across all participants
3. Ask: what do multiple participants keep saying or experiencing in relation to this question?
4. If a pattern meets the threshold (2–3 rows, 2+ participants), it is a candidate finding

RQ-anchored findings are the primary deliverable of most studies. Prioritize these.

### Method 2 — Tag-cluster patterns (secondary)
Look at which codes and taxonomy tags appear most frequently across the dataset. For each high-frequency code:
1. Pull all rows with that code
2. Check whether they cluster around a shared observation or represent unrelated uses of the same tag
3. If they cluster, check whether the pattern overlaps with any RQ
4. If it doesn't overlap: it may be a finding that informs an RQ indirectly, or it may be an emergent finding (see Method 3)

### Method 3 — Emergent patterns (flag, don't suppress)
Patterns that fall outside the scope of any research question. These are valid findings — the research surfaced something the study wasn't designed to ask about. Draft them, but flag them explicitly:

> `[EMERGENT — outside RQ scope]`

Emergent findings often point to a gap in the research plan. Surfacing them is part of the researcher's job.

---

## Before drafting: check for existing findings

If you have a prior findings list (from earlier synthesis sessions, from Airtable, or attached as a file):

1. Scan the prior list for findings that match any candidate pattern
2. If a match exists: note the prior finding ID and the data points that should be added to it — do not draft a new finding
3. If a pattern partially matches an existing finding: flag it as "extends existing finding" and draft the extension separately
4. If a pattern contradicts an existing finding: flag both explicitly — contradictions are as valuable as confirmations

---

## Finding format

Each finding has three parts. See `guides/findings-writing-guide.md` for the complete reference with examples.

### Part 1 — Statement (required)
5–15 words. Sentence case. One observation only.

**Rules:**
- Capitalize only the first word and proper nouns (product names, UI labels, version names)
- One observation — no "and," "but," or "however" joining two ideas; split those into two findings
- State what you observed, not what should change — if the statement tells a designer what to build, it's a recommendation; move it to the closing section
- Name the actor — "users," "data engineers," "buyers" — no passive constructions hiding who's doing what
- Anchor to something specific: a feature, flow, label, or user type — not a generic observation
- A statement, not a question
- Synthesized, not a verbatim quote

> ✅ *"Data engineers manually validate ingestion results before any transformation."*
> ❌ *"Users do validation."*
> ❌ *"Add a validation step to the ingestion flow."* (that's a recommendation)
> ❌ *"Validation is considered important by users."* (passive, no named actor)

### Part 2 — Description (required)
The evidence layer. Structure with 1–3 bold-headed bullets. Each bullet names a sub-theme. Each bullet must have at least one direct quote underneath it.

```
**[Sub-theme label]**
- "[exact participant quote]" — [Participant ID]
- "[exact participant quote]" — [Participant ID]

**[Sub-theme label]**
- "[exact participant quote]" — [Participant ID]
```

**Attribution rules:**
- Username (from UserTesting or similar): use verbatim, exactly as it appears
- Real name on record: first initial + last initial only (e.g., `RM`)
- Never include record IDs, session dates, companies, or roles in the attribution
- If two consecutive quotes are from the same participant, merge them into one attributed line

**Scannability:** a reader should be able to scan the description in 10 seconds. Use bullets, not prose paragraphs.

**No restatement:** the description opens with the first evidence bullet, not a repeat of the finding statement.

### Part 3 — Closing section (optional)
Only write this if it adds something the finding doesn't already say. Leave it out entirely if the finding is self-explanatory or evidence is thin.

**Implications** — use when you see a direction but don't own the decision. Opens a conversation.
**Recommendation** — use when you can name a specific action with a verb: KEEP, MOVE, RENAME, SPLIT, COMBINE, ADD, REMOVE, SUPPRESS.

If engineers and business users behave differently, say so explicitly in the closing section — don't average them into one "users."

---

## Evidence strength labels

Attach one of these to every draft finding:

| Label | Criteria |
|---|---|
| **Strong** | 3+ data points, 3+ participants, consistent across the dataset |
| **Moderate** | 2–3 data points, 2+ participants, consistent within a subgroup |
| **Directional** | 2+ data points but only 1 study, or only 1 participant type; pattern is real but needs more data |
| **Draft** | 1–2 data points; worth noting but not publishable without more evidence |

Always report the evidence strength alongside the finding. Do not present Directional or Draft findings as confirmed.

---

## Improvement checklist

Run every finding through this before finalizing:

**Statement**
- [ ] 5–15 words?
- [ ] Sentence case?
- [ ] Single observation — no "but/and/however"?
- [ ] Observation only — no recommendation baked in?
- [ ] Specific to a feature, flow, label, or user type?
- [ ] Subject named — no passive voice?
- [ ] A statement, not a question?
- [ ] Synthesized — not a verbatim quote?

**Description**
- [ ] Populated?
- [ ] 1–3 bold-headed bullets?
- [ ] Every bullet has at least one direct quote?
- [ ] Every quote attributed correctly?
- [ ] Scannable — not prose paragraphs?
- [ ] Opens with evidence, not restatement?

**Closing section**
- [ ] Adds something new (if present)?
- [ ] Implications: tentative framing, opens a conversation?
- [ ] Recommendation: specific action verb, grounded in evidence?
- [ ] Role differences named if evidence supports?

---

## Output

For each finding, produce:

```
---
Finding [N] [EVIDENCE STRENGTH] [EMERGENT if applicable]

Statement: [5–15 words]

**[Sub-theme]**
- "[quote]" — [ID]

**[Sub-theme]**
- "[quote]" — [ID]

[Implications / Recommendation — if applicable]

Supporting data points: [row numbers or timestamps from CSV]
Matched RQs: [RQ numbers]
Tags driving this finding: [the codes/tags that clustered here]
---
```

After all findings, produce a summary:
- Total findings drafted: N
- Strong/Moderate/Directional/Draft counts
- RQs with no supporting findings (if any)
- Emergent findings flagged
- Proposed new tags from this phase (if any)
