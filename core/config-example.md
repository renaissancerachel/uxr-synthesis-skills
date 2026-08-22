# Session Config — Worked Example
*This is what a filled-in config looks like. It's an illustration — swap in your own study details, moderator label, and research questions. Copy `config-template.md` to make your own.*

---

```
--- SESSION CONFIG ---

Study name: watsonx.data — Ingestion Onboarding Study
Study goal: Learn where new users get stuck setting up their first ingestion job.
Research questions:
  RQ1: What does "standardization" look like in practice — who owns it, how is it enforced, and how does it break down?
  RQ2: Where do first-time users lose confidence during ingestion setup?
  RQ3: What would data stewards need to see before trusting an ingestion job someone else built?
Participant roles: 5 data engineers, 3 platform admins, 2 data analysts
Study type: moderated interview

Moderator name: J. Rivera        # ← replace with your own speaker label
Tag config: using team default (skills/uxr-tag/reference/taxonomy.json + codes.json)
Output file: research projects/ingestion-onboarding/ingestion-onboarding-data-points.csv

Attribution:
  UserTesting studies — use participant's UT username verbatim from the Speaker field.
    Do not alter even if it looks like a real name (e.g., allisfair777, Ryan@9739).
  Real-name studies — first initial + last initial only (e.g., RM).

Transcript input:
  If input is a raw VTT or DOCX → run Phase 1 (clean), then Phase 2 (CSV), then Phase 3 (tag).
  If input is a pre-cleaned transcript → skip to Phase 2.
  If input is a CSV from the Transcript App → skip to Phase 2; re-tag from scratch in Phase 3.
    Treat the app's Keywords column as candidates only — do not carry them forward as final tags.

Moderator rows:
  Include in Phase 1 and Phase 2 CSV for context. Do not tag in Phase 3. Do not use as
  evidence in Phase 5.

Tag rules:
  Keywords: no cap (more is better — tag every tool/company/role/artifact). Codes: keep tight (~5). Min 0 — many rows get no tags.
  Proposed new tags: flag as PROPOSED: [name] — [type] — [reason]. Do not add silently.
  Re-tag Transcript App output from scratch. Do not trust app-generated keywords as final.

ASR corrections:
  RAG → RAG
  Milvus → Milvus
  watsonx.data → watsonx.data
  Databricks → Databricks
  LangGraph → LangGraph
  LangChain → LangChain
  Snowflake → Snowflake
  Presto → Presto
  Jupyter → Jupyter
  Db2 → Db2
  DataStage → DataStage
  [add study-specific corrections here]

Export:
  Do not auto-export CSV at any phase. Wait until I say "export."

--- WORKFLOW MODE ---
Step-by-step
```
