---
name: uxr-clean
description: Use when the user wants to clean a raw interview transcript — Phase 1 of the UXR synthesis workflow. Removes filler, false starts, and noise while preserving meaning and participant voice.
---

# /uxr-clean — Phase 1: Clean the Transcript

Clean a raw transcript. Remove noise. Preserve meaning exactly.

## Before starting

You need two things. If either is missing, ask:
1. **Transcript** — VTT or DOCX, pasted or attached
2. **Moderator label** — exact speaker name as it appears in the transcript (from session config, or ask)

If the researcher has a CSV from the Transcript App, stop and redirect: use `/uxr-tag` instead — Phase 1 is already done.

## Pilot first

Before cleaning the full transcript, show 5 examples as before/after pairs:
- 2 moderator turns
- 2 substantive participant turns
- 1 short or fragmented participant turn

Wait for approval. Clean the full transcript only after the researcher approves the pilot.

## Clean

**The cardinal rule: participant words are data. When in doubt, keep it.**

### Moderator turns — clean freely
Remove filler, false starts, redundant phrasing, and discourse markers from
moderator turns. The moderator's exact wording is not research data.

### Participant turns — remove only the clearest filler sounds
Only remove:
- Pure verbal sounds: *um, uh, er, ah*
- Consecutive word repeats: *"the the"* → *"the"*
- A false start where the speaker **explicitly restarts** the same sentence
  (abandoned fragment only — keep everything from the restart onward)

Do **not** remove from participant turns:
- *like, you know, I mean, sort of, kind of, basically* — these often carry
  hedging, uncertainty, or emphasis that is research data
- Hesitations, trailing thoughts, or unfinished sentences — uncertainty is data
  (*"I'm not sure… maybe it was under Settings?"* stays verbatim)
- Informal or imprecise language — the participant's own words are the record
- Anything that could qualify, soften, or add nuance to a statement

**If removing a word would change the meaning or texture of what the participant
said, do not remove it.**

Also remove from all turns:
- Moderator prompts that leaked into a participant block

Apply ASR corrections from `reference/01-transcript-clean.md` Step 3, plus any study-specific corrections from the session config.

## Merge

Merge consecutive turns from the same speaker when they are one interrupted thought (broken by a timestamp boundary or a brief moderator acknowledgment like "mm-hmm"). Do not merge across a meaningful moderator question.

## Include moderator turns

Keep all moderator lines. They provide context for participant responses. Phase 3 excludes them from tagging.

## Drop

Remove rows that are only:
- Single-word acknowledgments with no research value
- Punctuation only
- Greetings or farewells with no content

Short but substantive rows stay: *"I'd never use that."* is one complete observation.

## Output format

```
[HH:MM:SS] Speaker: Text of the turn.

[HH:MM:SS] Speaker: Text of the turn.
```

Show in chat as plain text. Produce a file only when the researcher asks. Researcher reviews, then says `continue` to proceed to Phase 2.

## Encoding

When producing any file output, write in UTF-8. Never substitute ASCII approximations for Unicode punctuation:
- Em-dash `—` stays `—` (U+2014). Do not write `--`, `ÄîÂ`, or any other stand-in.
- En-dash `–` stays `–` (U+2013). Do not write `-`.
- Curly quotes `"` `"` `'` `'` stay as-is.

If the source transcript contains garbled characters (e.g. `ÄîÂ` where a dash should be), correct them to the proper Unicode character during cleaning.

## Full reference

`reference/01-transcript-clean.md`
