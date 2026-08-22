# Airtable config block

Append this block to your core session config (see [`../core/config-template.md`](../core/config-template.md)) whenever you'll read from or write to your Airtable base. It's the only base-specific information the skills need.

```
--- AIRTABLE ---

Base ID: [FILL IN — the app… segment of your base URL, e.g. appXXXXXXXXXXXXXX]

Table names: [defaults — only change a line if you renamed that table in your copy]
  Projects:            Projects
  Participants:        Participants
  Sessions:            Sessions
  Data points:         Data points
  Tags/Codes:          Tags/Codes
  Findings:            Findings
  Research Questions:  Research Questions
  Screens:             Screens

Attribution: [FILL IN — how to identify participants in output]
  e.g. "Real names: first initial + last initial (RM). Panel usernames: verbatim."

Write policy: [FILL IN — for the import skill]
  Never write PII (email, full real name, demographics) unless I provide it and ask.
  Confirm Project / Participant / Session matches before writing Data points.
```

---

## Notes

- **You never put a token here.** Access comes from your assistant's Airtable connector/MCP — see [SETUP.md](SETUP.md).
- The skills address tables and fields **by name**. If you left the template's names alone, the defaults above are correct and you only need to fill in the Base ID.
- Field names in the **Projects** table end with a 🌎 emoji (e.g. `Project Name 🌎`) and the Sessions date is `Date ✅` — those exact strings come from the template; leave them as-is unless you renamed them.
