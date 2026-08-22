# Core — UXR Synthesis Pipeline

Eight skills that take a research transcript from raw text to a finished report. **No setup, no accounts, no connectors** — everything runs on files.

## Read first
- **`WORKFLOW.md`** — the six phases, how to start a session, the shared rules.
- **`config-template.md`** — fill in once, paste at the top of every session.
- **`config-example.md`** — a worked example.

## The skills

```
skills/
  uxr/                 router — start here if you're not sure which phase you need
  uxr-clean/           Phase 1 — clean a raw transcript
  uxr-csv/             Phase 2 — structure into a data-point CSV
  uxr-tag/             Phase 3 — tag with team taxonomy + codes
  uxr-rq/              Phase 4 — map data points to research questions
  uxr-findings/        Phase 5 — draft evidence-graded findings
  uxr-report/          Phase 6 — assemble a stakeholder report
  uxr-research-plan/   plan a study (standalone; used before a study runs)
```

Each folder is self-contained: a `SKILL.md` plus a `reference/` subfolder with its deep-dive guides and, for `uxr-tag`, the tag data (`taxonomy.json`, `codes.json`). Install whole folders.

## Install (Bob)

From this `core/` folder, either use the `skills` CLI:
```bash
npx skills add . -g -a bob -s '*' -y
```
or copy the folders in directly:
```bash
cp -R skills/* ~/.bob/skills/
```
Then **restart Bob**. (The same folders also load in Claude Code under `~/.claude/skills/`.)

## Quickstart

1. Install the skills.
2. Copy `config-template.md`, fill it in, save as your personal config.
3. Invoke `uxr` (or `uxr-clean` if you already have a transcript), paste your config, follow the prompts.
4. Say `continue` after each phase to chain to the next.

> **Guardrail:** don't run Phase 5 (findings) until Phases 2–4 are done. Findings need a complete, tagged, RQ-matched dataset. The skills will remind you.

## Airtable?

The core pipeline ends at a CSV. To push it into the team's Airtable base, or to query the base, add the **`../airtable-addon/`** (one-time setup — see its README).
