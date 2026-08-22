# Airtable add-on — setup

Five steps, ~10 minutes. You do this once.

---

## 1. Copy the template base

Open the template and duplicate it into your own Airtable workspace:

👉 <!-- TODO: paste your Airtable "Copy base" share link here -->

Click **Copy base** (top-right) → pick your workspace. You now own a private copy with the right structure and one worked example study inside it. Explore that study first — follow the 🎓 TOUR comments — then delete the example records when you're ready for real work. (Deleting records keeps the empty structure; that's your template.)

> **Why a copy?** These skills address tables and fields by name, not by ID. Your copy gets new internal IDs, but the **names stay the same**, so the skills just work. If you rename a table or field, update the name in your session config (below).

---

## 2. Get your base ID

Open your copy and look at the URL:

```
https://airtable.com/appXXXXXXXXXXXXXX/tbl.../viw...
                     └──────┬──────┘
                        your base ID
```

The `app…` segment is your base ID. Copy it.

---

## 3. Create a Personal Access Token (in your own account)

Airtable → **Builder hub → Personal access tokens → Create token**:

- **Scopes:** `data.records:read` (required). Add `data.records:write` and `schema.bases:read` if you'll run the import skill.
- **Access:** add *your copy of the base*.
- Copy the token — you'll paste it into your connector, **not** into any file here.

---

## 4. Connect Airtable to your assistant

Give the token to your assistant's Airtable connector or MCP server (it stores the secret in your OS keychain or the connector's own vault). The skills call the connector; they never see the raw token.

> If your assistant already has a native Airtable connector authenticated to the account that owns your copy, you can skip the token entirely — just make sure it can reach your base.

---

## 5. Tell the skills which base to use

Add the Airtable block from [config-template.md](config-template.md) to your session config, filled in with your base ID:

```
--- AIRTABLE ---
Base ID: appXXXXXXXXXXXXXX        # your copy, from step 2
Table names: defaults (Projects, Participants, Sessions, Data points,
             Tags/Codes, Findings, Research Questions, Screens)
```

Paste that block at the start of any session where you'll read from or write to the base. See [config-example.md](config-example.md) for a filled-in version.

---

## Verify it works

Ask your assistant something like:

> Using the airtable-uxr skill, what are the top findings in my base?

If it comes back with the example study's findings (and their supporting quotes), you're connected. 🎉
