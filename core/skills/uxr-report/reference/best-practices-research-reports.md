# Best practices for research reports and readout decks

**Living document · Owner: watsonx.data UXR team**
**Version 2 · August 4, 2026**

---

## How to use this document

This is the standard for any UXR readout deck or findings report in this repo. Read it before drafting a deck, before restructuring one, and before reviewing one.

**If you are an agent:** follow the rules in Parts 1 through 6. Run the checklist in Part 8 before delivering. When a rule and a request conflict, do what the person asked and say which rule you set aside.

**How to update it:** add the rule, add the worked example that produced it, and add a line to the changelog. Rules earn their place by coming out of a real edit, a real review, or a real deck that worked. Keep the worked examples. They are what make a rule usable by someone who was not in the room.

**Changelog**

| Version | Date | What changed |
|---|---|---|
| 1 | Aug 3, 2026 | First draft. Derived from the watsonx.data value proposition deck and the edit pass on the Skills Phase 1 deck. |
| 2 | Aug 4, 2026 | Added the rules on numbers, sourcing notes, quote-to-argument fit, active voice, and appendix linking. Reframed "lead with the gain" as "state the point first." Promoted the claim-to-evidence map and reusable templates from open questions to standards. Deck length reframed as scaled to study size. |
| 2.1 | Aug 4, 2026 | Added rule 16 on verifying a number against the document that defines it, after a sourcing count contradicted a correct figure. Corrected the sourcing-note example. |
| 2.2 | Aug 4, 2026 | Added rule 26 on reserving the footer band, after a rebuild printed content over the footer on twelve slides across three QA rounds. |
| 2.3 | Aug 4, 2026 | Added rule 17 on tracing a claim about someone else's plan to its actual document, after a deck presented one background sentence from our own study plan as a committed roadmap. |

**Reference deck:** `watsonx.data-ValuePropResearch-Deck.pptx`, in the wx.data UXR Study 2026 final reports folder. 113 slides: about 23 of main deck, then a 90-slide appendix. That study ran three phases and 176 participants, so treat its length as proportional rather than as a target.

---

## Part 0 — The two jobs

A report proves a finding. A deck lands one. The same evidence has to sit differently in each.

Most rules below move proof somewhere it stays reachable without standing in front of the answer. The deck is also the better review surface: people mark up slides, and they skim documents.

---

## Part 1 — Architecture

### 1. The answer comes first

The reference deck opens with **THE TOP 3 INSIGHTS · "If you remember nothing else."** Three numbered insights, each with a one-line so-what and a quote. Slide 3 says what it means for the audience's own roadmap. Method arrives on slide 5, sample on slide 6.

Order the front:

1. Title
2. If you remember nothing else: the top 3 to 5
3. What this means for [the audience's actual decision]
4. What's in this deck
5. How we ran it
6. Who we heard from

Someone who leaves after three minutes leaves with the finding.

### 2. One file, two decks

Main deck, then a hard break into an appendix with its own title slide, its own overview, and lettered sections.

The split keeps the main deck short while every finding stays in the file. Nothing gets cut for length. It moves.

**Length scales with the study.** A three-phase study with 176 participants earns 23 main plus 90 appendix. A four-session qualitative study earns something closer to 18 main plus 35 appendix. The rule that holds at any size: every finding lives on a slide somewhere in the file.

### 3. Map the deck, and say the appendix exists

The overview slide lists the numbered sections with a one-line description each, then names the appendix sections in a single line:

> The main part of the deck (outlined above) is only the tip of the iceberg. The appendix has more: A Study design · B Demographics · C Phase 1 · D Phase 2 · E Phase 3 · F Voice of the user · G Methods · H Limitations · I Provenance · J External references

The appendix gets its own overview slide when it starts.

### 4. Persistent wayfinding

Every content slide in the reference deck carries the same section strip, with the current section marked. In a forty-minute readout people lose their place. Use the section names the audience would use.

### 5. Close on the calls

The reference deck ends: **THE BOTTOM LINE** → **RECOMMENDATIONS**, grouped by owning workstream → **WHAT'S NEXT** → a statement slide → acknowledgements for partners and participants.

**Recommendations sit in two places, and both earn their spot.** Each finding carries its own implication inline, because that is where the reader has the context to judge it. The closing recommendations slide consolidates them and groups by the team that owns each one. A flat list of implications at the end, with no owner, moves nothing.

---

## Part 2 — Headlines and language

### 6. The kicker names the slide's job

A small label above the headline: WHERE THE OPPORTUNITY IS, WHO WE HEARD FROM, HOW WE KNOW. In the appendix, precise: APPENDIX C · PHASE 1 FINDING 07.

The reader knows the slide type before reading a word of content.

> **Worked example.** "How to read this" became **"Research overview."** "One failure, end to end" became **"Example scenario: One failure, end to end."** Both changes name the slide type. Rhetorical framing was doing that job badly.

### 7. The headline is the finding. So is every subheading.

*Security, governance, and compliance are the non-negotiable floor.* *Preparing enterprise data for agents is an emerging, unowned job.* *Proof beats claims: buyers require proof on their real data.*

Someone who reads only the headlines gets the whole study. That is the test, and it applies to card headings and section labels inside a slide too, not just the top line.

Topic labels ("The trust problem," "Capability value") belong in the kicker. The headline states what the research found.

### 8. Write in active voice, with the real subject

Passive construction hides who did the thing, and in research writing the who is usually the finding.

> **Worked example.** "The safeguard being removed is human hesitation" became **"Skills remove the human hesitation safeguard."** Same claim. The second version names the actor, and a product team reads it as being about them.

> **Worked example.** "That is a real control, and today it is holding" became **"Humans always remain in the loop behind the skills."** The hedge moved into the body. The headline states the finding.

### 9. Say the point in the first sentence

The most common failure in a deck written from a report: the subheading arrives at the point three clauses late, or leaves the subject implied.

> **Worked example.** "Not one of the four runs unattended. A steward reads a number and knows it is wrong. A steward contacts another team…" became **"Even though using skills with agents speeds things up, none of our participants run them unattended. A human reviewer: reads a number and knows it is wrong, contacts another team to find out whether a rule applies, reinstalls a skill by hand to get the update."**
>
> Two fixes in one edit. The subject arrives immediately, and the sentence grants the benefit before naming the gap. The original made the reader assemble the point from four parallel sentences.

### 10. End the slide by saying what each source shows

> **Worked example.** "The sessions show the safeguard working, manually, four times out of four. The public research shows what the same procedures look like once nobody is performing it" became **"Our participants highlighted the need for manual human safeguards. / The Reddit forums show what happens when nobody performs checks."**
>
> One sentence per source, each saying plainly what that source shows. The rewritten version survives being read aloud.

### 11. Use the word the audience uses

**"Steward"** became **"human reviewer"** and **"practitioner."** **"The public research"** became **"Reddit"** and **"the Reddit forums."**

A term of art defined at the front of a report works, because the reader can page back. In a room they cannot, so they carry a small confusion for the rest of the session.

Keep the formal term where it does formal work. Evidence labels like *Established*, *Promising*, and *Public discussion only* stay in the footers, because a definition sits behind them. The narrative above them says "Reddit."

### 12. Keep "we" for the research team and "they" for participants

> **Worked example.** "This is the control we have today" became **"This is the control they have today."** The control belongs to the participants.

---

## Part 3 — Evidence on the slide

### 13. Quotes have to visibly carry the argument on the slide

A quote earns its place when a reader can see, without help, how it supports the headline above it. A quote that needs the speaker to explain the connection has failed.

> **Worked example.** A slide headed "…and a person caught it" carried two quotes: one about the participant's testing habits, one about being nervous over a monthly report. Neither shows anyone catching anything. The slide got hidden in review, and the note was: *"the message on the slide is unclear and the quotes are unclear as well."*
>
> Two ways out. Find the quote where the thing in the headline happens. Or change the headline to the claim these quotes do support.

Test each quote against its headline before the deck ships. Where the best available quote only half supports the point, say the narrower thing.

### 14. Every number on a slide is a number you will defend later

Executives repeat numbers. A figure that goes on a slide leaves the room without its caveat and comes back as a quoted fact.

Bar for a headline number:

- **Say what produced it.** One measurement, an estimate, a count, a rate.
- **Give it its denominator.** *16/20*, *n=151*, *3 of 4*, *13 of 22*.
- **Mark measurement against estimate,** beside the number, in the same eyeline.
- **Give it a slide of its own only when it can carry the weight.** A number that needs a paragraph of qualification is a finding, not a stat.

> **Worked example.** A "two numbers worth carrying" slide paired 80% (one diff, one project, run once) with 15-to-2 days (the participant's own guess, with "maybe" in the transcript). The review note was: *"made no sense to me and didn't seem very well supported by data… EXECS LOVE them and we need to make sure we can back them up."*
>
> The slide labeled both figures Measured and Estimated, and it still failed, because a stat slide reads as *these are the headline numbers* whatever the labels say. The fix: keep the well-supported figure in the finding slide where its context lives, and drop the stat treatment.

The reference deck's opportunity chart marks reliability on the data points themselves: *● solid = n ≥ 24 (reliable) ○ hollow = n < 15 (directional).* Copy that habit.

### 15. Every evidence base gets a sourcing note, at the same specificity

The participant table names each participant, their role, their organization, what they run, and how mature it is. Any second evidence base gets the same treatment on the same slide.

> **Worked example.** A research-overview slide said "we scraped various Reddit forums looking for what the community says about developer skills" and stopped there. The review note: *"should have a list of the subreddits we looked at… I want that to be some kind of sourcing evidence note there at the bottom, like how the participants slide showed participant details."*

A sourcing note carries: what the corpus is, how you gathered it, the named sources, the size of each, and the composition caveat a reader would want.

Writing it often finds a problem. In this case, counting the corpus surfaced that the agent panel holds 81% of the posts while the operations panel that supplied the strongest evidence holds 3.5%, and that the evidence line pairs an archive-wide post count with a panel-scoped community count. Both belong on the slide.

It also finds a problem in the other direction. The first pass at this note read one file, found 25 communities, and reported the study's "twelve" as an error. The twelve came from the secondary research report's own panel table and was right. **Check the document that defines a number before calling it wrong.**

### 16. Check a number against the document that defines it

Counting a source file tells you what is in that file. It does not tell you what a figure in the report was counting.

> **Worked example.** A Phase 1 report said the secondary corpus covered "twelve communities." Counting the fetch archive found 25, and the first pass reported the report as wrong. The secondary research report's own "Method and sample" section defines three named panels holding twelve communities between them. Twelve was right. The 25 was the tool's whole fetch archive, a wider set that the analysis never used.

Before contradicting a figure: find the document that produced it, read the section that defines it, and confirm you are counting the same set. Where two real numbers describe two real sets, say which is which rather than picking one.

### 17. Trace a claim about somebody else's plan to the document that states it

A research deck earns its authority by being checkable. That extends to any claim about a roadmap, a strategy, or a commitment the research did not itself produce.

> **Worked example.** A slide read "All four parts of the committed roadmap hold up," with four rows marked Confirmed and a footer reading "Every verdict rests on Established evidence." Asked where the roadmap came from, the trail ran: slide → the report's roadmap section → one sentence in the Background of our own study plan. The same plan's Investment section says "Further investment commitments (development, roadmap) TBD," and lists Product Management and Development as TBD in its RACI. Splitting that sentence into four testable claims was the analysis's own move. And one of the four rows rested on two Promising findings from a single participant, so the footer was false.

Three habits:

- **Name the file and the section on the slide**, the same way an appendix finding names its source. A claim about a roadmap that cannot name where the roadmap is written down is a claim about a conversation.
- **Say when the decomposition is yours.** Turning one sentence into four testable parts is analysis. It reads as the plan's own structure unless you say otherwise.
- **Label each row, not the table.** A summary footer that generalizes across rows will be wrong the moment one row is weaker than the others, and that is the row a stakeholder will pick.

Where the claim is about someone else's commitment, "supported by" is the honest verb. "Confirmed" implies the study set out to test it.

### 18. Answer the obvious objection in small type, where it happens

> Satisfaction was asked about each person's #1 priority; "Turn unstructured into usable" is omitted — no one named it their top priority.

The person who was going to raise their hand now does not have to.

---

## Part 4 — Navigation

### 19. Section references become links to the appendix

A report cross-reference like "§2.3" tells a document reader where to turn. On a slide it points at nothing, and the reader has no way to follow it.

> **Worked example.** A caption read "P1 believes this works; he has not verified it (§2.3)." The reference got cut, and the review note was: *"§2.3 goes… where? That's what's unclear in the deck format now. It needs to be a link to the part in the appendix or something."*

Every reference converts one of three ways:

| Reference | Becomes |
|---|---|
| Supports a claim a reader may challenge | A hyperlink on the claim, to the appendix slide that carries the evidence |
| Context the presenter needs | Speaker notes |
| Provenance for the record | The slide footer, or the claim-to-evidence map |

Use PowerPoint's internal slide links, and give the linked text a visible affordance so a reader knows it goes somewhere. Add the reverse link on the appendix slide back to the main-deck slide it supports.

Doing this by hand across a deck is slow, which is an argument for generating it.

---

## Part 5 — The appendix

### 20. One slide per finding, and all of the findings

Appendix C of the reference deck gives each of the 17 Phase 1 findings its own slide on one template: numbered kicker, full-sentence finding title, two bullets, a cross-method note where another phase agrees, two attributed quotes, and a source line.

Nothing gets dropped for being less interesting. The main deck carries what changes a decision; every finding exists in the file with its evidence attached.

This is also what makes a deck reusable. Six months later somebody needs finding 11, and it is a slide, not a paragraph in a document nobody opens.

### 21. Keep dissent visible on purpose

Appendix F carries **TENSIONS & DISSENT — "Counter-evidence we keep visible,"** subtitled *"Quotes that complicate the headline findings — shown on purpose, so the story stays honest."* A table: what the quote challenges, who said it, and the quote.

A readout that includes the strongest disagreement is harder to attack than one that hides it, and it is the one thing a stakeholder cannot get from a summary.

### 22. Put each limit beside the finding it limits

Appendix H is "What this study does not establish," and it names its own sampling gap first. The sample slide carries its caveats inline: *"sample skews tech (IT & software ≈ 45%),"* *"Buyer sample was kept small this round (n=4 depth interviews); a fuller buyer read comes next."*

A caveat the reader meets an hour after the claim does different work than one in the same eyeline.

### 23. Ship a claim-to-evidence map

Two artifacts from Appendix I, both standard from here:

- **Provenance index.** One row per appendix section, naming the primary source file, so any figure traces back.
- **Claim → evidence map.** Every headline claim in the main deck, with the phase or method behind it, the evidence, and the appendix slide where it lives.

The claim map answers "how do you know that" for every sentence in the readout, in one table. It also doubles as the link target list for rule 19.

### 24. Show the instrument as participants saw it

Screens of the card sort, the pairwise, the survey, with exact question wording: *"the context questions, verbatim."* A stakeholder who sees the question can judge the answer.

### 25. Name the source file

Every appendix finding slide ends with a source line naming the synthesis file and the finding ID. That makes the deck auditable by someone who is not the author, which is the condition for the work outliving the person who did it.

### 26. Reserve the footer band, and size blocks to fit it

Every deck has a band at the bottom holding the footer and the page number. Nothing else may enter it.

> **Worked example.** A 61-slide rebuild printed live text over the footer on twelve slides. Three QA rounds and four rounds of per-slide fixes did not clear it, because each fix adjusted one slide's numbers while the underlying estimate stayed optimistic. What fixed it was making the layout derive block heights *from the space available* rather than computing a height and hoping it fit: `available = floor − footer − gap − contentTop`, then shrink the type until the block fits `available`.

Two habits that make this hold:

- **Size from the floor down, not the content up.** Compute what room a block has, then fit the content into it. A block that computes its own height will eventually exceed the slide.
- **Check it mechanically, not by eye.** A script that scans the rendered slide images for ink below the footer line catches this in seconds and does not get tired at slide 40.

Text-fit estimates should be deliberately pessimistic. A block that reserves too much leaves a gap; a block that reserves too little prints on top of something.

---

## Part 6 — What goes where

| Content | Main deck | Appendix |
|---|---|---|
| The top 3 to 5 insights | Slide 2 | — |
| What it means for the audience's roadmap | Slide 3 | — |
| Method and sample | One slide each, headline level, with sourcing notes | Full design, screeners, instruments, rosters |
| Evidence-labeling scheme | Named in footers | Its own slide, with the calculation behind each label |
| Coverage or support matrix | — | Full page, its own slide |
| Findings that change a decision | One slide each, implication inline | Also in the catalog |
| Every other finding | — | One slide each, same template |
| The illustrative story | One or two slides | The rest of the incident |
| Counter-evidence and dissent | The strongest one or two | All of it, as a table |
| Limitations | The one that changes how to read the headline | All of them |
| Quote bank | — | Themed, in full |
| Provenance and claim-to-evidence map | — | Yes |
| Glossary | — | Yes |

Test for the main deck: **would a reader act differently if this slide were missing?** If not, move it to the appendix, where it still counts as delivered.

---

## Part 7 — Reusable templates

These slides repeat across every study, so build them once:

| Template | Carries |
|---|---|
| **Finding slide** | Numbered kicker · finding as a full sentence · 2 bullets · cross-method note · 2 attributed quotes · implication · source line · link back to the main deck |
| **Participant / sample slide** | One card per participant: role, organization, what they run, maturity · composition caveat inline |
| **Sourcing note** | Corpus size · how gathered · named sources with per-source counts · composition caveat |
| **If you remember nothing else** | 3 to 5 numbered insights · one so-what line each · one quote each |
| **Dissent table** | What it challenges · voice · the quote |
| **Provenance index** | Appendix section · primary source file |
| **Claim → evidence map** | Claim · method · evidence · appendix slide (hyperlinked) |
| **Limitations** | What this study does not establish, one line each |

Build them as a starter `.pptx` in the house template, or as a generator that fills them from the findings file. A generator also solves rule 19, because internal links across 60 slides are not worth hand-maintaining.

---

## Part 8 — Build checklist

**Structure**

- [ ] Slide 2 is the answer, not the method
- [ ] Slide 3 says what it means for this audience's decisions
- [ ] An overview slide maps the deck and names the appendix sections
- [ ] Section wayfinding on every content slide
- [ ] Findings carry their implication inline; recommendations at the end group by owning team
- [ ] The appendix has its own title slide and its own overview

**Headlines and language**

- [ ] Every headline states a finding as a full sentence
- [ ] Every subheading and card heading does the same
- [ ] Active voice, with the real subject named
- [ ] The point arrives in the first sentence
- [ ] Each slide ends by saying what its evidence shows
- [ ] The audience's words, not the report's terms of art
- [ ] "We" for the team, "they" for participants

**Evidence**

- [ ] Every quote visibly supports the headline above it
- [ ] Every number names what produced it and carries its denominator
- [ ] Measurement and estimate marked apart, beside the number
- [ ] No stat slide for a figure that needs a paragraph of qualification
- [ ] Every evidence base has a sourcing note as specific as the participant table
- [ ] Small type answers the obvious objection where it happens

**Navigation and rigor**

- [ ] Every section reference is a link, a speaker note, or a footer entry
- [ ] Links run both ways between main deck and appendix
- [ ] Every finding exists on a slide somewhere in the file
- [ ] Counter-evidence has its own page
- [ ] Limits sit beside the findings they limit
- [ ] A claim-to-evidence map covers every main-deck claim
- [ ] Instruments shown as participants saw them
- [ ] Every appendix section names its source file

---

## Open questions

1. **Wayfinding strip.** Worth the build cost on every deck, or only past some length?
2. **Link affordance.** What should a link to the appendix look like on an IBM Plex slide so a reader knows it is clickable without it reading as decoration?
3. **Where the templates live.** A starter `.pptx` that a person copies, a generator that builds from a findings file, or both.
4. **Whether this becomes a skill.** The rules are stable enough to enforce automatically. The worked examples are what make them teachable, and a skill would need to carry both.
