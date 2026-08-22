# Airtable config — worked example

What a filled-in Airtable block looks like. Swap in your own base ID and rules.

```
--- AIRTABLE ---

Base ID: appXXXXXXXXXXXXXX          # ← your own copy of the template base

Table names: defaults (Projects, Participants, Sessions, Data points,
             Tags/Codes, Findings, Research Questions, Screens)

Attribution:
  Real-name studies — first initial + last initial only (e.g. RM).
  Panel/usability-tool usernames — use the username verbatim from the Speaker
    field; do not alter it even if it looks like a real name.
  Never include Airtable record IDs in output.

Write policy:
  Never write PII (email, full real name, demographics) unless I provide it and ask.
  Confirm the Project / Participant / Session match with me before writing Data points.
  Default new Project status to "Conducting".
```

This pairs with the core session config — see [`../core/config-example.md`](../core/config-example.md) for the transcript/tagging side.
