# Findings writing guide

A finding that takes more than a few seconds to parse has already failed. This guide covers what makes a statement work, how to structure the description, when to add a closing section, and what changes when the evidence comes from public sources. It applies whether you're a human researcher or an LLM working with the Findings table.

---

## Part 1: The finding statement

**Keep it to 5–15 words**
Count the words. Over 15, cut. Under 5, it's probably too vague to mean anything. Most strong statements land between 7–11 words.

> ✓ "Insufficient error details hinder effective troubleshooting" (7 words)
> ✗ "Rising product prices present significant challenges especially for small to mid sized companies and existing customers are concerned about shifting transparency around costs" (23 words)

**Use sentence case**
Capitalize the first word and proper nouns only. Title-casing is a common mistake here. Resist it.

Proper nouns in this context: product names (watsonx.data, Databricks, Snowflake), UI section labels (Operations, Governance, Admin Console), version names (Version A, Version B). Not proper nouns: "data engineers," "admin users," "notebooks," "catalogs."

> ✓ "Users expect Jobs to live under Operations, not Projects."
> ✗ "Users Expect Jobs To Live Under Operations, Not Projects."

**One observation per statement**
If you find yourself joining two ideas with "but," "and," or "however," that's two findings. Split them.

> ✓ "Catalog terminology is inconsistent and confuses users."
> ✗ "Catalog terminology is inconsistent and confuses users, but power users adapt quickly."

**State what you observed, not what should change**
The statement describes what users do, think, feel, or struggle with. It doesn't tell the team what to build.

> ✓ "Users can't find system health monitoring under 'Resource usage.'"
> ✗ "Move system health monitoring out of 'Resource usage' to improve discoverability."

Quick test: if the statement tells a designer or PM what to build, it's a recommendation. Move it to the closing section.

**Anchor it to something specific**
Anchor the finding to a feature, flow, label, or user type. Generic observations don't give the team anywhere to act.

> ✓ "A recurring chat pop-up requires users to close it multiple times."
> ✗ "Users find pop-ups annoying."

**Name the subject**
Passive constructions — "is considered," "is preferred," "is expected" — hide who's doing the considering, preferring, or expecting. A buyer evaluating platforms and a data engineer choosing a tool are two different findings. Name the actor.

> ✗ "Customization options are considered when selecting a data platform."
> ✓ "Buyers weigh customization and data source flexibility when evaluating platforms."

**Write a statement, not a question**
A finding is a claim derived from evidence. Research questions belong in the Research Questions table, not here.

> ✗ "In what ways do users integrate AI into their day-to-day workflows?"

**Synthesize; don't quote**
The statement is a synthesized observation. Quotes belong in the description as evidence.

**Answer the research question**
A finding is an answer. Read the research question, then the statement: the statement should read as a direct answer to the question or to one named part of it. If it reads as a topic ("Art requires a human and people debate whether a human directing AI counts"), it isn't a finding yet.

> ✓ RQ: "Where do the two camps share an underlying concern?" → "AI-art critics and many supporters agree that art needs a human maker"
> ✗ "Art requires a human and people debate whether a human directing AI counts"

**Make it stand alone in a library**
A finding is read next to findings from other studies. Give just enough context that a reader from another study knows *who* and *what* without opening it, usually by naming the actor with one qualifying word. Don't spend more than two or three words on it; the study's scope note carries the rest.

> ✓ "AI-art critics and supporters each dismiss the other's reasons as selfish"
> ✗ "Each side dismisses the other's reasons as cover for a selfish motive" (which sides? of what?)

*Added October 10, 2026: "Answer the research question" and "Make it stand alone in a library."*

---

## Part 2: The description (Details field)

**Structure the description as nested bullets — everything is a bullet**
Each supporting-detail bullet is a top-level bullet with a bold header. Its quotes are sub-bullets nested underneath, indented one level (4 spaces). Nothing in the description sits outside a bullet — no bare bold header lines, no unindented quotes.

> - **Users mistake the search bar for a filter**
>     - "OK, so the search is actually filter." — HU

**Back every bullet with at least one direct quote**
Paraphrase doesn't count here. The quote is the evidence. If you can't find one that supports the bullet, the bullet is speculative — cut it or go back to the data.

**Attribute every quote correctly**

Participant quotes carry the participant number, the role, and the organization. All three are required. The role and the organization are what let a reader weigh the quote — a senior strategist at a bank and a DevSecOps engineer at a software vendor are different evidence, and an attribution that hides which is which makes the reader do work they cannot do.

Format: `"quote text" — P#, role, organization`

> ✓ `"the work has come to a standstill right now." — P1, senior strategist, TD Bank`
> ✗ `"the work has come to a standstill right now." — P1`
> ✗ `"the work has come to a standstill right now." — KS`
> ✗ `"the work has come to a standstill right now." — rec3Sa9OmxQJdVc5C`

Whether the organization is named is settled at consent, per study, before writing starts — not per quote while drafting. If a study cannot name it, substitute the sector at the same level of specificity for every quote in that study (`— P1, senior strategist, retail bank`). Never mix named and unnamed organizations inside one report.

Public-source quotes take the handle, the community, and whatever signal the platform gives, plus a link to the thread:

> ✓ `— u/zohar275, r/devops, 105 pts · [view thread](url)`

Never use a record ID or a session date as the identifier in either form.

*Changed August 4, 2026. This rule previously required initials only and forbade role and company. Reports written before that date carry the old form; leave them alone rather than back-filling details that were never collected.*

**Merge consecutive quotes from the same participant**
Don't list two separate attributed lines back-to-back for the same person. Either combine them into one continuous quote (using a bracket for observed behavior) or select the stronger one.

> ✗ "No, I don't want to have a tour." — A.
> ✗ [closed pop-up immediately without reading] — A.

> ✓ "No, I don't want to have a tour. [Closed pop-up immediately without reading.]" — A.

**Populate the description, even if evidence is thin**
A finding with no description is an unverified claim. Either populate it or leave the finding as a draft. One data point and one quote is still a valid (if weak) description. Write it.

**Write for scannability, not narrative**
Prose hides the evidence structure. A reader should be able to scan the description in 10 seconds and locate the key patterns and quotes without reading every word.

> ✗ "Users were generally confused by the catalog terminology and found it inconsistent with their mental models. Several mentioned that the term 'catalog' had different meanings in different contexts, and one participant compared it to connectors."

> ✓ - **Terminology maps to different concepts by user type**
>     - "The catalog is the interface… sort of like a connector in the sense of Presto." — GW
>     - "I find them confusing… I don't intrinsically know why there's a Hive catalog." — JW

**Make each bullet a claim, not a category**
A bullet header is a short sentence with a verb, and it says something that supports the statement. Its quotes prove that sentence. A header that only names a group or a topic ("Estrangement inside the family," "Pro-AI users") makes the reader do the interpreting.

> ✓ **Critics feel unheard when relatives embrace AI**
> ✗ **Estrangement inside the family**

Test: cover the quotes. Do the headers alone still argue for the statement?

**Write in plain language**
Write for a smart reader outside the field. In the statement, headers, and closing, use everyday words; no internet slang, community in-jokes, or codebook labels. When choosing quotes, prefer the plain one when two make the same point. When a quote's slang is essential, gloss it once in square brackets inside the quote: "the micro-commission economy [artists who sell small paid commissions]".

**Use American spelling and punctuation**
In everything you write (statement, headers, closing): American spelling ("organized," "centers," "behavior"), the serial comma, and double quotation marks. Quotes from sources stay exactly as written.

**Start with evidence, not repetition**
The description adds evidence, not restatement. Open with your first evidence bullet — don't echo the finding statement in the opening line.

*Added October 10, 2026: "Make each bullet a claim, not a category," "Write in plain language," and "Use American spelling and punctuation."*

---

## Part 3: The closing section (optional)

The closing section — Implications, Recommendation, or both — is **optional**. Don't write one just to complete a template. You can include both headings, just one, or neither, depending on what the evidence supports. A weak implication is worse than none.

**Only write a closing section if it adds something**
Ask: does this help the team know what to do with this finding, or does it just restate the obvious? If the latter, leave it out.

Cases where a closing section is usually not needed:
- Very specific bug-like findings ("Username appears under Presto but not Milvus") — the action is self-evident
- Purely contextual background findings with no clear product implication
- Findings where you genuinely don't yet have enough context to say anything useful

**Use "Implications" when you see a direction but don't own the decision**
Implications are tentative. They might point to a pattern across studies, flag a tension the team needs to resolve, or pose a question. They open a conversation rather than close one.

> **Implications**
> This pattern appeared across three separate studies, suggesting it reflects a persistent mental model gap rather than study-specific friction. Worth discussing whether the label, the placement, or both are contributing — and whether quant metrics (directness rate, task success) can help the team prioritize.

**Use "Recommendation" when you can propose a specific action**
A recommendation includes an action verb and enough specificity that a designer or PM could act on it. Only write one when you understand the constraint space well enough to be useful. If you're not sure, use Implications instead.

Useful action verbs: KEEP, MOVE, RENAME, SPLIT, COMBINE, ADD, REMOVE, SUPPRESS.

> **Recommendation**
> Suppress the chat widget after first dismissal. Do not re-surface until the user explicitly opens the help menu.

> ✗ **Recommendation**
> Make the chat pop-up less annoying for users.

**Keep codebook mechanics out of the prose**
Don't put code names or raw counts ("motive imputation appears in 618 points from 485 authors") in a closing. Prevalence is shown by the evidence-strength grade; if a closing needs scale, say it in words ("common across both camps"). *(Added October 10, 2026.)*

**Name role differences when evidence supports them**
If engineers and business users (or admins and consumers, or sellers and buyers) behave differently, say so explicitly rather than treating "users" as a monolith.

> **Implications**
> Admin-background users consistently navigate to Governance as a top-level destination; data consumers treat it as subordinate to Data. A single IA may not serve both groups equally well.

---

## Part 4: Findings from public sources (social listening)

Interview findings describe participants you recruited. Public-source findings describe people who chose to post, which changes what a finding can claim.

**Name who is talking, honestly**
Name the actor as the community or role the evidence comes from ("AI-art critics," "commenters in AI-art debate forums," "GitHub issue reporters"), not "users" or a whole profession ("artists").

**Write a scope note for every public-source study**
State, once per study: where the data came from (platforms and communities), the date range, who it over- and under-represents, and what it can show. Statements then stay short.

**It's what people say, not what they do**
Public posts are claims, arguments, and stories told to an audience, often to win a point. Write findings about what people say, argue, or report. Don't turn them into findings about behavior or outcomes ("artists are losing income") without other evidence.

**Common in the debate, not common among people**
Prevalence describes the share of the *conversation*, not of a population. "Common in the debate" is fine; "most artists" is not. The loudest, most committed voices are over-represented by design.

**Check for bait, satire, and repeats**
Public data contains trolling, satire, and the same post in several communities. Drop or flag a quote that reads as bait, and never let one person's cross-posts count as several voices.

*Added October 10, 2026.*

---

## Part 5: Improvement checklist

Run any finding through this list to assess and improve it.

**Statement**
- [ ] 5–15 words?
- [ ] Sentence case (first word + proper nouns only)?
- [ ] Single observation (no "but/and/however" joining two ideas)?
- [ ] Observation only — no recommendation baked in?
- [ ] Specific to a feature, flow, label, or user type?
- [ ] Subject named — no passive constructions hiding the actor?
- [ ] A statement, not a question?
- [ ] Synthesized, not a verbatim quote?
- [ ] Reads as a direct answer to the research question (or one named part of it)?
- [ ] Stands alone: a reader from another study knows who and what?

**Description**
- [ ] Details field is populated?
- [ ] 1–3 bold-headed bullets at the top level, quotes nested as sub-bullets underneath?
- [ ] Every bullet has at least one direct quote?
- [ ] Every quote is attributed in the correct format (`"quote" — P#, role, organization`, or handle + community + link for public sources)?
- [ ] Scannable structure (not prose paragraphs)?
- [ ] Description adds evidence rather than restating the statement?
- [ ] Every bullet header is a claim (a sentence with a verb), not a group or topic?
- [ ] Plain language; any essential slang glossed in [brackets]?
- [ ] American spelling, the serial comma, and double quotation marks (source quotes untouched)?
- [ ] No codebook names or raw counts in the prose?

**Closing section**
- [ ] If present, does it add something beyond what the finding already says?
- [ ] If using Implications: tentative framing, opens a conversation?
- [ ] If using Recommendation: specific action verb, grounded in evidence?
- [ ] Role differences named if evidence supports them?

**Public sources**
- [ ] Actor named as the community or role, not "users" or a whole profession?
- [ ] The study has a scope note?
- [ ] Claims stay at "say," not "do"; prevalence framed as "in the debate"?
- [ ] Bait, satire, and cross-posted repeats dropped or flagged?

---

## Part 6: Where findings go wrong

| Problem | Example | Fix |
|---|---|---|
| Statement too long | "Rising product prices present significant challenges especially for small to mid sized companies..." | Cut to the core claim. Split remaining ideas into separate findings. |
| Recommendation in statement | "Improve demo experiences to help clients quickly grasp product value" | Rewrite as observation: "Clients can't grasp product value quickly from current demo experiences." Move the fix to the closing section. |
| Not sentence case | "Users Expect Notebooks To Be Collaborative" | Lowercase everything except first word and proper nouns. |
| Empty description | *(empty)* | Populate it, or mark the finding as a draft — don't publish without evidence. |
| Prose description | "Users were confused by..." | Convert to bold-headed top-level bullets with quotes nested as sub-bullets. |
| Quote without attribution | `"I had trouble finding it."` | Add participant number, role, and organization: `"I had trouble finding it." — P2, omni-channel activation lead, Gilead Sciences` |
| Attribution missing role or organization | `"I had trouble finding it." — P2` | A bare P# tells the reader nothing about whose judgment this is. Add both: `— P2, omni-channel activation lead, Gilead Sciences` |
| Description restates the statement | Description opens with "Users were confused by catalog terminology, which is inconsistent..." | Cut the restatement. Start with the first evidence bullet. |
| Two observations in one statement | "Catalog terminology is inconsistent, but power users adapt" | Split into two findings. |
| Question as statement | "In what ways do users integrate AI?" | Either answer it (write the finding) or delete the record. |
| Passive voice | "Customization options are considered when selecting a data platform." | Name the actor: buyers? data engineers? Rewrite with the subject doing the action. |
| Weak or forced closing section | "Recommendation: improve this area" | Either write something specific and grounded, or leave the closing section out. |
| Consecutive same-participant quotes | `"No, I don't want a tour." — A.` followed by `[closed pop-up] — A.` | Merge into one: `"No, I don't want a tour. [Closed pop-up immediately.]" — A.` |

---

## Part 7: Examples

Three examples across different categories, each illustrating a different closing section choice.

*The attributions in these examples predate the August 4, 2026 rule change and show initials only. Read them for description structure, not for attribution format — new work uses `— P#, role, organization`.*

---

### No closing section — Usability / error states

The gap is specific, well-evidenced, and self-explanatory. A closing section here would just say "fix the error messages" — adding nothing the team doesn't already know.

---

**Insufficient error details hinder effective troubleshooting**

- **Error messages identify that something failed, not where or why**
    - "I had no luck. Cannot create a project. Wrong project type. What is a wrong project type? What type am I? What type should I be?" — JQ
    - "Insufficient error messages and missing logs make debugging impossible." — CoE team
- **Log detail view surfaces status labels, not diagnostic information**
    - "If I go into this job, I see: runs completed, one; runs failed, zero; status: completed with errors. It failed successfully." — HU
    - "There's no document sets because the flow failed. That's not so helpful." — HU

---

### With Recommendation — UI / interaction pattern

The fix is specific, low-ambiguity, and well within the researcher's line of sight. No implementation uncertainty warrants hedging it as an implication.

---

**A recurring chat pop-up requires users to close it multiple times.**

- **Persistent overlay interrupts task flow immediately upon landing**
    - "Had to click x to close 'let's talk' pop up." — R.
    - "No, I don't want to have a tour. [Closed pop-up immediately without reading.]" — A.

**Recommendation**
Suppress the chat widget and product tour prompt after first dismissal. Do not re-surface until the user explicitly opens the help menu.

---

### With Implication — Information architecture / user type differentiation

The researcher can name the tension clearly and point to what's at stake, but resolving it requires trade-offs the product and design team are better positioned to weigh.

---

**Admins want standalone Governance; data engineers want it nested.**

- **Admin and regulated-org users treat Governance as a top-level destination**
    - "For bigger organizations they will go with version A; for small ones, version B." — pztnakro
    - "I see Governance as a dedicated category with its own subcategories." — MagicMouseTech
- **Data engineers expect Governance nested within their working context**
    - "The catalog should be invisible… unless this is admin… only in troubleshooting do we care." — GW
    - "As a consumer I'd expect not to see manage access or governance at all." — GW

**Implications**
These two groups have fundamentally different mental models of where Governance belongs. A single IA may not serve both well. Worth discussing whether role-based navigation is feasible, or whether the primary user type for this view should drive the default structure.
