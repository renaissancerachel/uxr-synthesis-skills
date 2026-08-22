# Airtable add-on (optional)

Two skills that connect the [core synthesis pipeline](../core/) to an Airtable research base — so your work doesn't die in a CSV. Query the base to answer questions from real evidence, and push a finished data-point CSV back into it.

| Skill | Purpose |
|---|---|
| `airtable-uxr` | **Read** — pull quotes for a topic, check findings, answer "what did people say about X?" from actual records only |
| `uxr-airtable-import` | **Write** — push a tagged data-point CSV into the base; resolves or creates Project / Participant / Session, then writes Data points and links their Tags + Research Questions |

Use these **after** the core pipeline produces a tagged CSV (Phases 1–4), or any time you want to read from the base.

> **This add-on is optional and connector-agnostic.** The core pipeline runs entirely on files with zero setup. Add this only if you keep your research in Airtable. It's aimed at assistants that reach Airtable through a connector/MCP.

---

## 🧱 It ships with a copyable base template

You run these skills against **your own copy** of a ready-made Airtable base — the same structure the skills expect, pre-loaded with one fully worked example study ("The Base That Studies Itself") that teaches the model as you explore it.

👉 **Copy the template base:** <!-- TODO: paste your Airtable "Copy base" share link here -->

Then follow **[SETUP.md](SETUP.md)** to connect your access and point the skills at your copy. Full walkthrough there; the short version is below.

---

## 🔒 You bring your own access — no credentials ship here

These skills contain **no base ID, no table/field IDs, and no token.** They address every table and field **by name**, so they work against any copy of the template base — including yours, which gets brand-new internal IDs the moment you duplicate it.

To use the add-on:

1. **Copy the template base** into your own Airtable workspace (link above).
2. **Create a Personal Access Token in _your own_ Airtable account** (Airtable → Builder hub → Personal access tokens), scoped to your copy with `data.records:read` — plus `data.records:write` and `schema.bases:read` if you'll run the import skill.
3. **Give that token to your assistant's Airtable connector/MCP — never to these files.** The skills call the connector; they never see the raw token.
4. **Put your base ID in your session config** (see [config-template.md](config-template.md)). That's the only base-specific value the skills need, and it lives with _you_, not in the repo.

Rotate or revoke the token in your Airtable account anytime — nothing in this add-on changes.

---

## What the skills expect from your connector

The instructions reference record operations by common names — `list_records_for_table`, `create_records_for_table`, `search_records`. Any Airtable integration that offers equivalent read/create operations works; if yours names them differently, the steps read as plain actions you can map to your tools. Most Airtable connectors accept a **table name** wherever an ID is expected, which is why these name-based skills are portable.

- **`airtable-uxr`** needs **read** access.
- **`uxr-airtable-import`** needs **read + write**. It creates records, so run it deliberately — it confirms Project / Participant / Session matches with you before writing Data points.

Both share one field map: [`reference/base-reference.md`](reference/base-reference.md).

---

## Install

Install the **whole `airtable-addon/` folder** (the two skills share `reference/base-reference.md`).

**Claude Code / Agent-Skills assistants** — copy the skill folders into your skills directory:
```bash
cp -R skills/* ~/.claude/skills/
```
**Or via the skills CLI:**
```bash
npx skills add . -g -s '*' -y
```
Then restart your assistant and connect Airtable (PAT via your connector/MCP) per [SETUP.md](SETUP.md) before using either skill.

---

## Safety notes

- The import skill **never writes PII** (email, real names beyond an initial, demographics) unless you explicitly provide it and ask.
- Both skills keep Airtable record IDs out of any user-facing output.
- The import skill writes in batches and reports exactly what it created, skipped, and couldn't match — review that summary.
- The read skill answers **from records only** — it never fills gaps with general knowledge.
