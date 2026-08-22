# How We Tag and Code Data in Airtable
*A guide for the research team*

---

## Why this matters

Our Airtable system is only as useful as what we put into it. The whole point is that we can trace findings across studies — see a pattern emerge over six months, across different products, from different participants. Tags and codes are how that tracing works. If we're inconsistent about how we apply them, we lose the thread.

This guide exists so that anyone on the team can code data and have it be searchable and useful — not just to the person who did the study.

---

## Two layers: keywords and codes

Every tag lives in the Tags/Codes table and is classified by a **`Type of code`** field. Those types fall into two layers that do different jobs. Don't mix them up — the whole system depends on the split.

### 1. Keywords — the filter layer  ·  *more is better*

Keywords are the concrete, searchable things a participant actually named or referred to. They are the layer you filter by later, so **quantity is the goal: tag every keyword that appears.** You never know what someone will want to filter on, and the cost of an extra keyword is basically zero. There is **no cap** on keywords per row.

`Type of code` values in this layer:
- **`Tool/Software/Company`** — products, tools, platforms, competitors, companies, orgs: `watsonx.data`, `Databricks`, `Figma`, `Claude Code`, `GitHub`, `Carbon MCP`, `Bob`, `Gilead`, `Power BI`.
- **`keyword`** — concrete artifacts, actions, and technical terms: `screenshots`, `video`, `pull request`, `wireframe`, `presentation`, `repo`, `terminal`, `grid`, `MCP`, `component`, `prototype`, `instructions file`, `slash command`, `compliance-as-code`, `oncology`, `FinOps`.
- **`Persona/Target User`** — roles and audiences: `data engineer`, `designer`, `UX engineer`, `developer`, `security engineer`, `VP`, `contractor`.

**The rule:** if a participant named it, referred to a specific artifact, or used a concrete term someone might filter by — tag it. Reach wide: tools, companies, roles, artifacts (files, screens, decks, PRs), concrete concepts, and domains all count, not just product and competitor names.

### 2. Codes — the interpretive layer  ·  *quality over quantity*

Codes are what you're *interpreting* from the quote — the behaviors, barriers, patterns, and signals you pull out during synthesis. These feed findings, so here **quality wins: apply a few meaningful ones, not a pile.** If you're regularly past ~5 interpretive codes on a row, you're over-interpreting — ask whether each one truly differentiates this row or just restates the study topic.

`Type of code` values in this layer:
- **`Theme`** — the analytic patterns you're naming (`terminal comfort`, `prototype fidelity`, `access friction`, `design-engineer convergence`). Themes are the researcher's synthesis layer.
- **`Feature/Capability`** and **`Workflow/Process`** — capability- or process-level observations (`multi-tenant`, `automation`, `administration`).

**The rule:** if you're interpreting rather than transcribing, it's a code. Keep it tight.

> Rule of thumb: **quantity for keywords, quality for codes and findings.**

---

## How to apply them

For each substantive data point, ask two questions:

1. **What keywords are in this row?** — Every product, tool, company, role, artifact, or concrete term named or clearly referred to. Apply them all. Be exhaustive.
2. **What is this row actually telling us?** — The behavior or pattern. Apply a few interpretive codes (Themes). Be selective.

Most rows get a mix: a quote about struggling to find data in watsonx.data might get keywords `watsonx.data`, `data catalog` and the Theme codes `discoverability`, `frustration`.

**Moderator / interviewer rows:** leave them uncoded. Always. (Unless a moderator row itself names a concrete keyword worth filtering — then the keyword layer may apply, but never interpretive codes.)

---

## Completeness and consistency

More is better only works if it's applied *evenly*. A keyword that's on some mentions but not others is worse than useless — it makes counts and filters lie.

- **Apply a keyword to every quote where it appears**, not just the first.
- **Reuse before you create** — search the Tags/Codes table first; use the existing spelling rather than making a near-duplicate.
- Before drafting findings, run the **Coding QA checkpoint (`/uxr-coding-qa`, Phase 4.5)**. It sweeps for uneven keywords, backfills the ones applied inconsistently, merges near-duplicates, and flags under-coded rows — so findings rest on complete, consistent coding. It never touches Theme codes; those stay yours.

---

## Naming rules (please follow these exactly)

Inconsistent naming breaks search. We've had `metastore`, `metastores`, `meta store`, and `meta stores` all meaning the same thing — four tags that should be one.

**Always:**
- Use **singular form** (`metastore` not `metastores`, `workaround` not `workarounds`)
- Use the **closed/technical spelling** for technical terms (`metastore` not `meta store`)
- Match **official product styling** exactly (`watsonx.data` lowercase, `Db2` not `DB2`, `Snowflake` capitalized)
- Use **full names** over abbreviations unless the abbreviation is the industry standard (`SQL` and `MCP` are fine, `wxd` is not)

**When in doubt:** search the Tags/Codes table before creating a new one. If something close already exists, use it and note any variation in the description.

---

## The Tags/Codes table fields

- **Code** — the tag name itself. Follow the naming rules above.
- **Details / description** — a brief note on what it means or when to apply it. Required for interpretive codes and Themes; helpful for any keyword that could be ambiguous.
- **`Type of code`** — the classification, from the two layers above: `Tool/Software/Company`, `keyword`, `Persona/Target User` (keyword layer); `Theme`, `Feature/Capability`, `Workflow/Process` (interpretive layer). Set this when you create a code — don't leave new keywords blank; an untyped keyword is hard to filter and hard to maintain.
- **Data points** — the linked quotes; populates automatically.
- **# of data points** — the count; populates automatically.

*(Different bases name this field slightly differently — the Carbon base uses `Type of code`, the watsonx.data base uses `Type of tag` — but the values and the two-layer logic are the same. Introspect the base you're in before writing.)*

---

## Common mistakes

**Under-tagging keywords.** The most common one now. If a tool, artifact, role, or company is named and you didn't tag it, the row is invisible to that filter. When in doubt, tag it — more is better for keywords.

**Applying a keyword unevenly.** Tagging `Figma` on three of the eight rows that mention it. Apply it to all eight (or let `/uxr-coding-qa` catch it).

**Over-coding the interpretive layer.** Eight Theme codes on one row isn't thorough, it's noise. A few sharp codes beat a pile of vague ones. Quality lives here.

**Creating a near-duplicate.** `developer` and `developers`, `Carbon Element Styles` and `Carbon Elements Styles`. Search first; reuse the existing spelling.

**Leaving `Type of code` blank on a new tag.** It should carry a type so it's filterable and maintainable.

**Leaving a description blank on an interpretive code.** A year from now no one will remember what `friction` meant in the context you coded it. One line saves a lot of confusion.

---

## Questions?

This system is still evolving. If you run into a situation the guide doesn't cover, flag it — it probably means we need a new rule or a new keyword, and that's useful information.

---
*Last updated: 2026-08-22 | Maintained by: watsonx.data UXR team*
