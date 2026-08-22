# Taxonomy Setup — Build or Import Your Tag Config
*Part of the UXR Synthesis Skill. Complete this once before your first synthesis session.*

---

## What you're building

A **tag config** — a list of the taxonomy tags and codes your AI assistant will use when tagging data in Phase 3. Once you have it, you paste or attach it at the start of every synthesis session.

You only set this up once per research program (or per team). After that, you maintain it: adding new tags after sessions that surfaced them, deprecating ones that stopped being useful.

---

## Choose your path

**→ [Path A](#path-a--i-already-have-a-tag-list):** I already have a tag list (Airtable export, JSON, spreadsheet)

**→ [Path B](#path-b--im-starting-from-scratch):** I'm starting from scratch

---

## Path A — I already have a tag list

If you have an Airtable export, a JSON file, or a spreadsheet:

Paste this at the start of a new AI session:

```
I have an existing tag list. Please reformat it into the UXR Synthesis Skill tag config format:

{
  "taxonomy_tags": [
    { "tag": "ExampleProduct", "type": "Tool/Software" }
  ],
  "codes": [
    { "tag": "frustration", "type": "Sentiment" }
  ]
}

Naming rules to apply while reformatting:
- Singular form only (metastore not metastores)
- Closed spellings (metastore not meta store, dataset not data set)
- Official product casing (watsonx.data lowercase, Databricks capitalized, Db2 not DB2)
- Full names over abbreviations unless the abbreviation is industry standard (SQL is fine)
- Mark any tag with Type = "Deprecated" in Airtable as deprecated: true — do not include it in the active list

Here is my existing list:
[paste or attach your file]
```

Save the output as `my_tags.json` in your project folder. That's your tag config.

---

## Path B — I'm starting from scratch

Paste this block into a new AI session. Answer the questions one section at a time. The AI will build the config as you go.

```
I'm setting up a tag taxonomy for UX research synthesis. Ask me the questions below one
section at a time and build a tag config from my answers. After each section, show me
what you've added and let me adjust before moving on.

At the end, output the config as JSON in this format:

{
  "taxonomy_tags": [
    { "tag": "ExampleProduct", "type": "Tool/Software" },
    { "tag": "data engineer", "type": "Role" }
  ],
  "codes": [
    { "tag": "frustration", "type": "Sentiment" },
    { "tag": "workaround", "type": "Behavior" }
  ]
}

Naming rules:
- Singular form only
- Closed spellings for technical terms
- Official product casing
- Full names over abbreviations unless industry standard
- No duplicates — if something close already exists, use that one

SECTION 1 — Products and tools
What products, tools, or platforms will participants in your studies mention?
Include both your own products AND competitors or alternatives they might reference.

SECTION 2 — User roles
What job titles or roles are the people you research?
Be specific — "data engineer" and "data analyst" are different tags.

SECTION 3 — Features and capabilities
What specific features, flows, or capabilities within your products will participants
interact with or discuss?

SECTION 4 — Behavior codes
What observable behaviors do you expect to see in the data?
Examples: workaround, comparison, habit, shortcut, abandonment, error recovery

SECTION 5 — Sentiment codes
What emotional or attitudinal signals are you listening for?
Examples: frustration, delight, uncertainty, trust, skepticism

SECTION 6 — Conceptual codes
What higher-level themes do you want to track across studies?
Examples: discoverability, mental model, onboarding friction, information architecture

SECTION 7 — Process codes
What process or workflow observations matter to you?
Examples: manual step, context switching, collaboration point, workaround
```

Save the final JSON output as `my_tags.json`. That's your tag config.

---

## Tag config format reference

```json
{
  "taxonomy_tags": [
    { "tag": "watsonx.data", "type": "Tool/Software" },
    { "tag": "Databricks", "type": "Tool/Software" },
    { "tag": "Snowflake", "type": "Competitor" },
    { "tag": "Milvus", "type": "Feature" },
    { "tag": "metastore", "type": "Feature" },
    { "tag": "RAG", "type": "Feature" },
    { "tag": "iceberg table", "type": "Feature" },
    { "tag": "data engineer", "type": "Role" },
    { "tag": "data steward", "type": "Role" },
    { "tag": "platform admin", "type": "Role" },
    { "tag": "SQL", "type": "Tool" }
  ],
  "codes": [
    { "tag": "frustration", "type": "Sentiment" },
    { "tag": "delight", "type": "Sentiment" },
    { "tag": "uncertainty", "type": "Sentiment" },
    { "tag": "trust", "type": "Sentiment" },
    { "tag": "workaround", "type": "Behavior" },
    { "tag": "comparison", "type": "Behavior" },
    { "tag": "abandonment", "type": "Behavior" },
    { "tag": "discoverability", "type": "Concept" },
    { "tag": "mental model", "type": "Concept" },
    { "tag": "onboarding friction", "type": "Concept" },
    { "tag": "manual step", "type": "Process" },
    { "tag": "context switching", "type": "Process" },
    { "tag": "error recovery", "type": "Process" }
  ]
}
```

---

## How to use your tag config in sessions

At the start of every synthesis session, paste or attach the config in the session config block:

> `Tag config: [paste my_tags.json here, or attach the file]`

The skill uses it in Phase 3. It will only propose new tags when something in the data genuinely doesn't fit — and it will flag those proposals for you to approve before adding them.

---

## Growing the taxonomy over time

After each synthesis session:
- Add any **new taxonomy tags** you approved during the session
- Add any **new codes** that emerged and you expect to use again
- Mark deprecated tags with `"deprecated": true` rather than deleting them — so you can trace why a tag was retired

The AI flags new tag proposals during Phase 3. You decide what becomes permanent.

---

## Troubleshooting

**"The AI keeps inventing tags not in my list."**
Add this line to your session config: *"Only use tags from the config I provided. Flag anything that doesn't fit as PROPOSED — do not add it silently."*

**"My list has hundreds of tags and it's too long to paste."**
Paste the 50–75 tags most relevant to this specific study. Attach the full list as a file if your tool supports attachments. Tell the AI: *"For tag lookup, prioritize the pasted list; fall back to the attached file."*

**"I'm not sure whether something is a taxonomy tag or a code."**
Taxonomy tags are proper nouns and stable technical terms — the kind of thing you'd search for by name. Codes are interpretive — the kind of thing you're concluding about what you heard. When in doubt: if it appears in a product spec or job description, it's a taxonomy tag. If it describes a human experience or behavior, it's a code.
