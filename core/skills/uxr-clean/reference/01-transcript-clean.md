# Phase 1 — Clean the Transcript
*Part of the UXR Synthesis workflow: Clean, CSV, Tag, RQ, Findings, Report.*

---

## What this phase does

Removes noise from the raw transcript while preserving the participant's meaning exactly. The output is clean, readable text — not structured data yet. Structuring happens in Phase 2.

**This phase is about signal preservation, not summarization.** Never shorten, paraphrase, combine ideas across speaker turns, or "improve" a participant's phrasing. Only remove the noise that gets in the way of the words.

---

## Choose your input path

### Path A — Raw transcript (VTT or DOCX pasted in chat, or attached)
Run the full Phase 1 cleaning rules below.

### Path B — Pre-cleaned transcript
The researcher has already cleaned the transcript in another tool or session. Skip to Phase 2 with a quick validation pass: confirm speaker labels are consistent, no one-word/punctuation-only rows remain, no obvious ASR errors in technical terms.

### Path C — CSV from Transcript App or Figma Make tool
The transcript has already been parsed and partially processed. **Do not re-run Phase 1.** Go directly to Phase 2 for structural validation, then Phase 3 for full re-tagging. Treat the Keywords column from the app as candidate tags only — they will be reviewed and replaced in Phase 3.

---

## Phase 1 rules (Path A only)

### Step 1 — Pilot first
Before cleaning the full transcript, show the researcher 5 representative examples:
- 2 moderator turns
- 2 substantive participant turns
- 1 short or fragmented participant turn

Show each as a before/after pair. Wait for approval before running the full transcript.

---

### Step 2 — Remove noise

**Remove these filler words and discourse markers:**
- Standalone interjections: *Yeah, Yep, Nah, Oh, OK, Okay, Sure, Right, Exactly, Absolutely, Totally, Great, Perfect, Got it, Mm-hmm, Uh-huh, Hmm*
- Repeated acknowledgments: *Yeah yeah, OK OK, Okay okay, Right right*
- Verbal thinking sounds: *um, uh, er, ah, uhh, umm*
- Throat-clearing phrases: *"I mean," "you know," "like" (when used as a filler, not comparatively), "sort of," "kind of," "basically," "literally," "actually"* (when they add no meaning)
- False starts: where the speaker abandons a phrasing and immediately restarts — remove the abandoned fragment
  > *"I- I went to the dashboard"* → *"I went to the dashboard"*
- Consecutive word repeats: *"the the data"* → *"the data"*
- Interviewer prompts that leaked into a participant block

**Do not remove:**
- Hesitations that carry meaning (e.g., "I'm not sure... maybe it was under Settings?" — the uncertainty is the data)
- Any of the participant's actual word choices, even informal ones
- Technical acronyms — these are preserved as-is (see ASR fixes below)

---

### Step 3 — Apply ASR corrections

Speech-to-text systems commonly mis-transcribe technical terms. Apply these corrections:

| Mis-transcribed as | Correct form |
|---|---|
| rag, R.A.G., retrieval augmented generation (when clearly the acronym is intended) | RAG |
| milvus, mil vus, mil-vus | Milvus |
| python (when clearly referring to the language) | Python |
| node.js, nodejs, node J.S. | Node.js |
| elasticsearch, elastic search | Elasticsearch |
| langchain, lang chain | LangChain |
| langraph, lang graph | LangGraph |
| jupyter, jubiter, joop iter | Jupyter |
| databricks, data bricks | Databricks |
| watsonx.data, watson x data, watson x dot data | watsonx.data |

Add study-specific corrections at the start of your session config. Any term in the researcher's override list takes precedence over this default list.

---

### Step 4 — Merge fragments

If consecutive turns from the same speaker are clearly one interrupted thought (e.g., broken by a timestamp boundary mid-sentence, or interrupted by a brief moderator acknowledgment like "Mm-hmm"), merge them into a single block.

Do not merge across a meaningful moderator question — that marks a new topic.

---

### Step 5 — Drop empty rows

Remove rows that contain only:
- A single word with no research value (*"Yeah," "Right," "Okay"*)
- Punctuation only (*"..."*, *"–"*)
- A greeting or farewell with no content (*"Hi, thanks for joining"*)

Keep rows that are short but substantive. *"I'd never use that."* is one sentence and one complete observation — keep it.

---

### Step 6 — Combine incomplete thoughts

If a speaker's thought is syntactically incomplete (cut off mid-sentence, sentence fragment) but the meaning is recoverable from context, combine it with the immediately adjacent turn from the same speaker to form a complete thought.

Do this only when:
- The meaning of the incomplete fragment is clear
- The combination preserves the original meaning without adding interpretation
- Both fragments are from the same speaker

Do not combine turns that express different ideas, even if they're adjacent.

---

### Step 7 — Include moderator turns

Include moderator lines in the cleaned transcript. They provide essential context for reading participant responses — a response only makes sense if you know what question it answers. Moderator lines will be excluded from tagging and findings later, but they stay in the clean text for now.

---

## What the output looks like

Show the cleaned transcript in chat as plain text — not a file, not a table. Format:

```
[HH:MM:SS] Speaker: Text of the turn.

[HH:MM:SS] Speaker: Text of the turn.
```

**Do not auto-export to CSV.** Do not produce a downloadable file at the end of Phase 1. The researcher reviews the clean text in chat first, then says "proceed to Phase 2" when ready.

---

## Common mistakes in Phase 1

**Paraphrasing.** Changing *"I couldn't figure out where the heck that was"* to *"the user found the navigation confusing"* destroys the quote. The participant's actual language is the evidence.

**Over-merging.** Combining turns that express different ideas because they're adjacent. One topic per block.

**Removing technical terms.** *"RAG"*, *"LangGraph"*, *"metastore"* are not filler words. Do not remove them.

**Cleaning moderator lines away.** They stay. Phase 3 excludes them from tagging; Phase 1 preserves them.

**Summarizing long responses.** A 10-sentence response gets cleaned, not summarized. If it contains multiple distinct ideas, note it for Phase 2 (splitting), but don't compress it here.
