---
name: uxr-report
description: Use when the user wants to write a stakeholder-facing research report from completed findings — Phase 6 of the UXR synthesis workflow. Assembles executive summary, findings, methodology, and appendix.
---

# /uxr-report — Phase 6: Write the Research Report

Assemble a stakeholder-facing research report from the completed findings.

## Input required

Completed findings from Phase 5 — either in chat context or attached as a file. If missing, ask.

If the researcher has a preferred report template, use it. Otherwise use the structure below.

## Report structure

```
# [Study Name] — Research Findings
[Date] · [Researcher name(s)] · [Study type] · [N participants]

## Executive summary
3–5 sentences. What did we learn? What should the team do with it?
No citations or quotes — this is for stakeholders who will read nothing else.

## Research questions
List the research questions this study was designed to answer.

## Key findings
One section per finding. Use the finding statement as the section header.
Include description and closing section from the drafted finding.
Order: Strong findings first, then Moderate, Directional, Draft.

## Methodology
Brief: study type, participant criteria, session count, data collection method, synthesis method.

## Appendix (optional)
- Full data point CSV (link or attachment)
- Participant overview table
- Any emergent findings that don't fit the main narrative
```

## Tone

Stakeholder-facing: clear, direct, scannable. Avoid jargon the reader may not know. Spell out acronyms on first use.

Write for the reader who will act on this — name the implications clearly. Do not hedge findings that have Strong or Moderate evidence.

## Formatting

- Section headers in sentence case
- Finding statements as H3 headers
- Evidence bullets indented under each finding
- Evidence strength label visible on every finding
- Emergent findings flagged inline

## Output

Produce the full report in chat as formatted markdown. When the researcher asks, export as a `.md` or `.docx` file named `[study-name]-research-report.[ext]`.

## Full reference

`reference/06-report.md` · `reference/best-practices-research-reports.md`
