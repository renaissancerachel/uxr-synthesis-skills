# Phase 6 — Research Report
*Part of the UXR Synthesis workflow: Clean, CSV, Tag, RQ, Findings, Report.*

---

## What this phase does

Assembles the findings from Phase 5 — plus the study context, methodology, and evidence — into a structured research report. The output is written for PMs, designers, and stakeholders: people who need to act on the research, not people who will re-analyze the raw data.

**The report translates research into decisions.** It leads with what matters, backs every claim with evidence, and is honest about what the data doesn't yet support.

---

## Before writing

Confirm you have:
- [ ] Session config (study name, goal, RQs, participant roles, study type)
- [ ] Completed findings from Phase 5 with evidence strength labels
- [ ] The tagged CSV (for any quote pull or counts the report needs)
- [ ] RQ coverage report from Phase 4

---

## Report structure

### 1 — Study overview (1 short paragraph)
What was this study? One paragraph covering:
- Study name and date range
- What you were trying to learn (study goal)
- Who participated (N participants, roles, how recruited)
- Study type (moderated interview, usability test, tree test, etc.)

Do not editorialize here. This section is factual.

### 2 — Research questions
List each RQ as written in the session config. No elaboration needed — the findings section addresses them.

### 3 — Key findings

The main section. Present findings in priority order — lead with the strongest evidence, then moderate, then directional.

**For each finding:**
- Finding statement (the 5–15 word headline)
- Evidence strength label: **Strong** / **Moderate** / **Directional** / **Draft**
- Description with sub-theme bullets and direct quotes (from Phase 5)
- Closing section if applicable (Implications or Recommendation)
- Which RQ(s) it addresses

**Emergent findings** — findings outside the RQ scope — go in a separate subsection at the end of this section, labelled "Emergent findings." Do not bury them or omit them.

### 4 — Recommendations summary (if applicable)
If any findings produced Recommendation closing sections, consolidate them here as a numbered action list. This section exists so a PM or designer can quickly see all the actionable asks without reading through every finding.

Format:
```
1. [Verb phrase — specific action] → Finding [N]
2. [Verb phrase — specific action] → Finding [N]
```

If no findings produced recommendations (all used Implications or no closing section), omit this section entirely.

### 5 — Open questions and gaps

Three types of gaps belong here:

**RQ gaps** — RQs with thin evidence (from the Phase 4 coverage report). Be specific:
> *"RQ2 (how users make build-vs-buy decisions) had only 2 matching data points from 1 participant. This question was not well addressed by the study design. A follow-up study targeting procurement decision-makers would strengthen this."*

**Evidence gaps** — findings labeled Directional or Draft. These are real but unconfirmed:
> *"Finding 4 (data engineers prefer a validation preview immediately after ingestion) is directional — supported by 2 data points from 1 study. Needs triangulation from a second study before acting on it."*

**Emergent gaps** — things the data surfaced that the study wasn't designed to investigate:
> *"Three participants independently mentioned agent reliability in production environments as a top concern. This was out of scope for this study but appears frequently enough to warrant a dedicated RQ in future work."*

### 6 — Methodology note (brief)
One short paragraph on study limitations. Things to flag:
- Sample size and whether it supports the claims being made
- Recruitment constraints (e.g., all participants from regulated industries — findings may not generalize)
- Study type constraints (e.g., moderated interview = self-report, not observed behavior)
- Any known data quality issues (e.g., poor ASR quality on certain sessions, a session where the participant was distracted)

---

## Tone and style

**Write for the reader, not the researcher.** The audience is PMs and designers, not the person who ran the study.

**Lead with the finding, not the process.** Do not write "In this study, we found that..." — just state the finding.

**Be direct about uncertainty.** Never present a Directional finding as confirmed. Never omit an evidence strength label. A reader who acts on weak evidence without knowing it's weak will lose trust in the research program.

**Use the participant's language in quotes, not paraphrase.** The quotes are the evidence. Paraphrase in the description headers, quote in the bullets.

**No jargon in the recommendations.** If you write "MOVE the Jobs item under Operations," that's clear. "Optimize the information architecture for improved task flow" is not.

---

## Output

The report can be produced as:
- Markdown (default — paste into Notion, Confluence, GitHub, or any doc tool)
- Plain text (for tools that don't render markdown)

Ask the researcher which format they want before producing the output. Default to markdown if not specified.

The tagged CSV is not part of the report — it is the underlying data. Reference it (e.g., *"full data available in `study-name-data-points.csv`"*) but do not embed it.
