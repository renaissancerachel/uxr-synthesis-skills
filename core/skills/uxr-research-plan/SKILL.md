---
name: uxr-research-plan
description: >-
  Use when the user wants to write or start a UX research plan. Guides
  researchers through the full plan including protocol, and guides
  non-researchers/requesters through the sections they can fill in, leaving
  researcher-only sections as blank templates. Trigger phrases - "research
  plan", "write a research plan", "start a research plan", "create a research
  plan", "UXR plan", "study plan".
---

# UXR Research Plan

Guide the user through creating a UX research plan. The plan has two paths depending on the user's role. Follow all steps in order.

---

## Step 1 — Identify the user's role

Ask the user:

> "Are you the researcher who will be running this study, or are you a stakeholder/requester who is asking for research to be done?"

- **Researcher** → follow the Researcher Path (Steps 2–8)
- **Requester / non-researcher** → follow the Requester Path (Steps 2–6, then Step 9)

---

## Step 2 — Collect RACI and project details

Ask the following, grouped into one message (or one at a time). Allow the user to skip any field by saying "skip" or "I don't know."

Collect:
- **Study / project name**
- **Last updated date** (default to today if not provided)
- **RACI** — define the RACI framework and ask for names/teams for the following roles:
  - Research
  - Product Management
  - Development
  - Design
  - Executive Stakeholders

---

## Step 3 — Collect background and investment

Ask (allow skips):

1. **Background:** How did this study come about? What drove the initiative? Why is this research being done?
2. **Hypotheses / Assumptions:** What does the team currently believe about this problem? What do you expect to find?
3. **Investment in Outcomes:** What is the promised investment in the research outcomes? Will development commit resources? Will product management incorporate findings into the roadmap?

> **Requester path note:** Investment in Outcomes is the stakeholder's section to own — push for a concrete answer here rather than deferring to the researcher.

---

## Step 4 — Collect target user, methodology, and study goals

Ask (allow skips):

1. **Target User / Persona:** Who is the intended participant or user persona for this study? Do you have any screening criteria or requirements for participants?
2. **PDLC Phase:** Is this research tied to a specific IBM Winning Products phase? (Discovery / Delivery / Growth / Not applicable)
3. **Research Method:** What type of study is this? (e.g., usability test, generative interviews, concept test, diary study, survey, benchmark)
4. **Study Goals:** What should this research accomplish? What decisions or outcomes will it support?

---

## Step 5 — Collect research questions

Ask:

> "What are your research questions — not the questions you'll ask participants, but the overall questions you want the study itself to answer?"

Allow multiple questions. Allow skips.

If the user is unsure how to write good research questions or asks for help, suggest:

> "You can use the `/research-question-generator` command to get structured help writing unbiased, well-scoped research questions. This skill is available via **Propel** — if you don't have it installed, you can get it at [propel.ibm.com](https://propel.ibm.com). Otherwise, I can help you draft them directly here."

---

## Step 6 — Collect timeline

Ask:

> "What is your estimated timeline? For each phase, provide a rough month range."

Collect estimates for:
- Study Planning
- Recruiting
- Conduct sessions
- Synthesize data
- Present findings

Allow the user to skip phases or provide approximate ranges (e.g. "Month 1–2").

---

## Step 7 — Researcher only: Tasks and Metrics

*Skip this step for requesters — go to Step 9.*

Ask:

1. **Tasks:** What are the high-level tasks participants will go through in the study?
2. **Metrics:** Metrics are **optional and methodology-dependent**. Use the research method collected in Step 4 to guide this:
   - **Usability / evaluative studies** → metrics are relevant. Suggest:
     - Ease of Use — Single Ease Question (SEQ)
     - Confidence
     - Time on task / time to failure
     - Post-test: System Usability Scale (SUS)
     - NPS
   - **Generative / discovery / interview studies** → metrics typically don't apply. Ask the researcher to confirm before including them.
   - If metrics don't apply, **omit the Metrics section entirely** from the output.

---

## Step 8 — Researcher only: Session Protocol

*Skip this step for requesters — go to Step 9.*

Ask the researcher:

> "For the session protocol, would you like me to guide you through it interactively (asking about each section), or would you prefer a blank template you fill in yourself?"

### Option A — Guided

Ask in sequence (allow skips at each):

1. **Intro script:** The study name, what the product does, and any special context. (Offer the standard IBM Cloud Data and AI intro script as a starting point — see template below.)
2. **Generative section:** Any high-level background questions to understand the participant's context before tasks begin?
3. **Scenario / context:** What scenario should participants bear in mind during the study?
4. For each task section (ask how many sections they need, then repeat):
   - Section/task name
   - Time estimate (minutes)
   - Questions and tasks for this section

### Option B — Blank template

Output the protocol section as a blank template (see output format below) — the researcher fills it in after.

---

## Step 9 — Assemble and output the plan

Assemble the full research plan document using the template below. Fill in every field the user provided. For any field the user skipped:
- In the **Requester path**: leave the placeholder text and add a `> ⚠️ **Needs researcher to complete**` blockquote immediately below the section heading.
- In the **Researcher path**: leave the placeholder text only (no warning callout).

### Output format

At the end, ask:

> "Would you like me to save this as a Markdown file, or display it here in chat for you to copy?"

- **Save to file**: save a Markdown file named `research-plan-[study-name].md` in the current workspace directory. Use kebab-case for the filename.
- **Display in chat**: output the full plan as a fenced Markdown block.

---

## Research Plan Template

Use this exact structure. Replace bracketed placeholders with collected answers.

```markdown
# Research Plan: [Study Name]

**Last Updated:** [Date]

## Team (RACI)

| Role | Name / Team |
|------|-------------|
| Research | [value or TBD] |
| Product Management | [value or TBD] |
| Development | [value or TBD] |
| Design | [value or TBD] |
| Executive Stakeholders | [value or TBD] |

---

## Project Details

**PDLC Phase:** [Discovery / Delivery / Growth / Not applicable]
**Research Method:** [e.g., Usability test, Generative interviews, Concept test, Diary study, Survey, Benchmark]

[Any additional high-level details about the scope of the study]

---

## Background

[How did this study come about? What drove the initiative? Why is this research being done?]

**Hypotheses / Assumptions:** [What does the team currently believe about this problem? What do you expect to find?]

---

## Investment in Outcomes

[What is the promised investment in the outcomes of the research? Will development commit resources? Will product management incorporate findings into the roadmap?]

---

## Target User

[Persona / role of intended participants]

**Screening criteria:** [Any requirements or screener notes for recruiting]

---

## Study Goals

[Goals of what this research should accomplish and help with]

---

## Research Questions

*Note: these are not questions to ask participants, but overall questions the study should answer.*
*Need help writing research questions? Use the `/research-question-generator` command (requires Propel — [propel.ibm.com](https://propel.ibm.com)).*

[Research questions]

---

## Tasks

[High-level tasks participants will go through]

---

## Metrics *(include only if applicable to the study methodology)*

- Ease of Use — Single Ease Question (SEQ)
- Confidence
- Time on task / time to failure
- Post-test questions:
  - System Usability Scale (SUS)
  - NPS

[Add or remove metrics as appropriate, or remove this section entirely for generative/discovery studies]

---

## Timeline

| Phase | Estimated Dates |
|-------|----------------|
| Study Planning | [Month X – Month X] |
| Recruiting | [Month X – Month X] |
| Conduct sessions | [Month X – Month X] |
| Synthesize data | [Month X – Month X] |
| Present findings | [Month X – Month X] |

---

## Session Protocol

> **Note:** Adapt the intro script and section structure to match your study's method and context.

### Intro Script

Hi, I support the IBM Cloud Data and AI portfolio and I'm evaluating a design for [XXX]. This design does [XXX]. I also have some colleagues on the line to help take notes.

I did not design or develop this product, so anything you say will not hurt my feelings.

First, I have some preliminary questions to help the team better understand your role and process, and then I want to test some workflows to learn about what works and what doesn't.

Before I get started, I wanted to confirm that you are okay with this session being recorded? When you finished the screener questions in Respondent, you accepted an agreement to non-disclosure of any designs and concepts you might see today. As a reminder, the agreement states that you will not share what we show you today.

---

### Optional Generative Section

[Insert high-level background questions to understand the participant's context]

---

### Scenario / Context

[What scenario should participants bear in mind? What questions do you have?]

---

### SECTION/TASK 1 [X minutes]

[Questions and tasks to complete — write based on your research questions]

---

### SECTION/TASK 2 [X minutes]

[Questions and tasks to complete]

---

### SECTION/TASK 3 [X minutes]

[Questions and tasks to complete]

---

### SECTION/TASK 4 [X minutes]

[Questions and tasks to complete]

---

*For IBM Winning Products research guidance, see the [Winning Products W3 site](https://w3.ibm.com/w3publisher/winning-products/) — search for "user research" for relevant pages.*
```
