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

Remove:
- Filler and discourse markers: *yeah, yep, nah, oh, okay, sure, right, exactly, absolutely, totally, great, perfect, got it, mm-hmm, uh-huh, hmm* and repeated forms
- Verbal sounds: *um, uh, er, ah*
- Throat-clearing: *I mean, you know, like* (as filler), *sort of, kind of, basically, literally, actually* (when meaningless)
- False starts — abandoned phrasing before the speaker restarts
- Consecutive word repeats: *"the the"* → *"the"*
- Moderator prompts that leaked into a participant block

Preserve:
- Every word the participant chose, including informal language
- Hesitations that carry meaning (*"I'm not sure… maybe it was under Settings?"* — the uncertainty is the data)
- Technical terms — never remove them; apply ASR corrections instead (see guide)

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
