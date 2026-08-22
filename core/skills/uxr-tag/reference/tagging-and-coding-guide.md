# How We Tag and Code Data in Airtable
*A guide for the research team*

---

## Why this matters

Our Airtable system is only as useful as what we put into it. The whole point is that we can trace findings across studies — see a pattern emerge over six months, across different products, from different participants. Tags and codes are how that tracing works. If we're inconsistent about how we apply them, we lose the thread.

This guide exists so that anyone on the team can code data and have it be searchable and useful — not just to the person who did the study.

---

## Two types: Tags vs. Codes

We use both tags and codes in our system, and they serve different purposes. It's important not to mix them up.

### Taxonomy Tags
These are a controlled, stable list of proper nouns and terms the team will actively filter by. Think of them as the vocabulary of our product space.

**What goes here:**
- IBM product names (watsonx.data, Db2, DataStage, Manta, etc.)
- Competitor names (Snowflake, Databricks, Starburst, Dremio, etc.)
- Feature names (metastore, query engine, data catalog, iceberg tables, etc.)
- User roles (data engineer, data steward, data analyst, etc.)

**The rule:** If it's a proper noun or a specific technical term that the team would search for by name, it's a taxonomy tag.

Taxonomy tags are finite and maintained. We don't add new ones casually — if you think a new one is needed, flag it so we can add it intentionally.

---

### Codes
Codes are emergent. They're the concepts, patterns, and signals you're pulling out of a quote during synthesis. They grow with the research.

**What goes here:**
- Behavioral observations ("workaround," "confusion," "trust," "habit")
- Sentiment signals ("frustration," "delight," "uncertainty")
- Conceptual themes ("discoverability," "mental model," "onboarding friction")
- Process observations ("manual step," "context switching," "collaboration point")

**The rule:** If it's something you're *interpreting* from what a participant said, it's a code.

---

## How to apply them

When you're tagging a data point, ask yourself two questions:

1. **Are there any taxonomy tags that apply?** — Did the participant mention a specific product, competitor, feature, or role? Apply those tags.
2. **What's the concept in this quote?** — What is this person actually telling us? Apply codes for the themes and behaviors you're observing.

Most data points will have a mix of both. A quote about struggling to find data in watsonx.data might get the taxonomy tag `watsonx.data` and the codes `discoverability` and `frustration`.

---

## Naming rules (please follow these exactly)

Inconsistent naming breaks search. We've had tags like `metastore`, `metastores`, `meta store`, and `meta stores` all meaning the same thing. That's four tags that should be one.

**Always:**
- Use **singular form** (`metastore` not `metastores`, `workaround` not `workarounds`)
- Use the **closed/technical spelling** for technical terms (`metastore` not `meta store`)
- Match **official product styling** exactly (`watsonx.data` lowercase, `Db2` not `DB2`, `Snowflake` capitalized)
- Use **full names** over abbreviations unless the abbreviation is the industry standard (`SQL` is fine, `wxd` is not)

**When in doubt:** search the Tags table before creating a new one. If something close already exists, use that and note any variation in the description field.

---

## The Tags table fields

When you create or update a tag, here's what each field means:

- **Code** — The tag name itself. Follow the naming rules above.
- **Code description** — A brief note on what this tag means or when to apply it. Required for codes; helpful for taxonomy tags that might be ambiguous.
- **Type** — Select one: `Taxonomy`, `Code`, or `Deprecated`. This is required.
- **Data points** — The linked quotes. This populates automatically when you tag a data point.
- **Count** — How many data points use this tag. Populated automatically.

---

## Common mistakes

**Creating a new tag when one already exists.** Always search first.

**Using a taxonomy tag as a code.** If a participant mentioned Snowflake but the insight is really about competitive switching behavior, apply the `Snowflake` taxonomy tag *and* a `competitive switching` code. Both, not just one.

**Leaving Code description blank.** Especially for codes — a year from now, no one will remember what `friction` means in the context you coded it. A one-line description saves a lot of confusion.

**Not tagging at all.** An untagged data point is invisible in synthesis. If you're short on time, at least apply the taxonomy tags — they're the fastest to apply and the most searchable.

---

## Questions?

This system is still evolving. If you run into a situation the guide doesn't cover, flag it — it probably means we need a new rule or a new taxonomy tag, and that's useful information.

---
*Last updated: [DATE] | Maintained by: watsonx.data UXR team*
