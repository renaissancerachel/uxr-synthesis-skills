# UXR Synthesis Skills

A set of [Agent Skills](https://code.claude.com/docs/en/skills) that take qualitative UX research from a raw interview transcript all the way to a finished, stakeholder-ready report — one phase at a time, each phase its own skill.

Originally built for the **watsonx.data UXR team** and generalized here for anyone doing qualitative research synthesis with an AI assistant. The skills use the open Agent Skills format (a `SKILL.md` with `name` + `description` frontmatter and a Markdown body, plus any deep-dive references bundled alongside), so they load in Claude Code, Bob, or any Agent-Skills-compatible assistant. The pipeline was built tool-agnostic from the start.

## The pipeline

Six phases, chained. Start at `uxr` if you're not sure where you are.

| Skill | Phase | What it does |
|---|---|---|
| `uxr` | — | Router — orients you and points to the right phase |
| `uxr-clean` | 1 | Clean a raw transcript (remove filler, false starts, noise — preserve voice) |
| `uxr-csv` | 2 | Structure the transcript into a one-thought-per-row data-point CSV |
| `uxr-tag` | 3 | Tag every row with a taxonomy + semantic codes |
| `uxr-rq` | 4 | Map each data point to the study's research questions |
| `uxr-findings` | 5 | Draft evidence-graded findings with quotes and traceability |
| `uxr-report` | 6 | Assemble the executive summary, findings, methodology, and appendix |

Two extra skills round it out: **`uxr-coding-qa`** (a consistency checkpoint before findings) and **`uxr-research-plan`** (write a study plan *before* fieldwork — used standalone).

Everything in `core/` runs **entirely on files** — no accounts, no connectors, no external services.

## Getting started

Read [`core/WORKFLOW.md`](core/WORKFLOW.md) first — it walks the six phases, how to start a session, and the shared rules. Then:

1. Install the skills (see [`core/README.md`](core/README.md)).
2. Copy [`core/config-template.md`](core/config-template.md), fill it in once, and paste it at the top of each session.
3. Invoke `uxr` (or `uxr-clean` if you already have a transcript) and follow the prompts. Say `continue` to chain to the next phase.

Each skill folder is self-contained — a `SKILL.md` plus a `reference/` subfolder with its deep-dive guides and, for `uxr-tag`, the tag vocabulary (`taxonomy.json`, `codes.json`). **Install whole folders**; never split a skill from its `reference/`.

## Bring your own taxonomy

The tag vocabulary bundled with `uxr-tag` is a starting point. Swap in your own taxonomy and codes via the session config — the pipeline doesn't assume any particular product or domain.

## Airtable integration

An optional [Airtable add-on](airtable-addon/) connects the pipeline to a research base — **query** it ("what did people say about X?") and **push** a finished data-point CSV into it. It ships with a **copyable Airtable base template** so you set it up against *your own* base, and addresses every table and field by name (no base IDs or credentials in the repo — you bring your own access). See [`airtable-addon/README.md`](airtable-addon/README.md) and [`airtable-addon/SETUP.md`](airtable-addon/SETUP.md).

The template base includes one fully worked example study — *"The Base That Studies Itself"* — that teaches the workflow as you explore it.

## Provenance

Built by Rachel Miles for the watsonx.data UX research team. Shared as a reference implementation for AI-assisted qualitative synthesis.
