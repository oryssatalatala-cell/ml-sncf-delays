# PROMPT_LOG (4 to 6 high-stakes prompts, at least 1 per student)

Only log prompts that really happened. A high-stakes prompt is one where you constrained the model with a schema, assumptions or leakage guardrails, and the output went into the project.
Be transparent about the tool used and about which parts of the code were AI-drafted and then verified by you.

## Entry template (copy for each prompt)

### Prompt N: (short title)
- **Student:**
- **Date and tool/model:**
- **Goal:** what you needed (e.g. "build lag features without leaking the future")
- **Prompt (verbatim):**
  ```
  paste it here
  ```
- **Constraints given to the model:**
  - Schema (columns, types):
  - Assumptions stated:
  - Leakage guardrails (e.g. "fit scalers on train only", "split by time"):
- **Output summary:** what the model returned
- **What you kept, changed or rejected:**
- **How you verified it:** (unit check, manual recomputation, comparison with raw data)
- **Link to AI_AUDIT.md entry, if a flaw was found:**

## Disclosure
AI assistance (Claude) was used to explore project topics and approaches, to draft the Week 2 notebook code, and to structure the report templates. The group reviewed, ran and verified the code on the real data and is responsible for all methodological choices.

## Entries

### Prompt 1: Week 2 pipeline (cleaning, split, baseline)
- **Student:** Oryssa Stella TALATALA, on behalf of the group
- **Date and tool/model:** 2026-11-25, Claude (Sonnet 5.5)
- **Goal:** get a Week 2 notebook (data preparation and baseline) for the TGV delay project, following the Lab 5 brief.
- **Prompt (verbatim, originally in French):**
  ```
  maintenant on doit faire la suite. Week2
  ```
  The Lab 5 PDF (LAB5-FullProject.pdf) was attached with this prompt.
- **Constraints given to the model:**
  - Schema (columns, types): none given in the prompt. The assistant could not read the real file and matched columns by keyword.
  - Assumptions stated: only those of the Lab 5 brief (clean data, analyse missing values and target, define splits, implement a baseline, evaluate).
  - Leakage guardrails: none given in the prompt. The temporal split, past-only lag features and train-only fitting were chosen by the assistant. The group must check them (see AI_AUDIT.md).
- **Output summary:** a notebook with cleaning log, EDA, leakage audit table, temporal split, five regression baselines (global mean, route mean, persistence, seasonal naive, Ridge) and a classification view.
- **What you kept, changed or rejected:** kept the structure; asked for a download step (see Prompt 2).
- **How you verified it:** the group ran the notebook on the real dataset (12,907 raw rows, 26 columns) without errors. The column mapping selected the expected columns, the built-in assertions on the temporal split and on the lag merge passed, and we reviewed the cleaning log (73 rows with no scheduled trains removed) and the results tables.
- **Link to AI_AUDIT.md entry:** entries 1 and 2.

### Prompt 2: data source and automatic download
- **Student:** Oryssa Stella TALATALA, on behalf of the group
- **Date and tool/model:** 2026-11-25, Claude (Sonnet 5.5)
- **Goal:** make the notebook fetch the dataset itself instead of assuming a local file.
- **Prompt (verbatim, originally in French):**
  ```
  Dans le notebook tu n'as pas mis l'url vers les données. Tu as mis un chemein à modifier en considérant que j'avais les fichiers en local dans mon pc. Or c'est toi tu m'as conseillé cette data base et du coup c'est toi tu dois trouver l'url et scrapper les données
  ```
- **Constraints given to the model:** the dataset had to be the one recommended earlier (SNCF TGV regularity); the URL had to be found by the assistant, not by the user.
- **Output summary:** a download cell using the official data.gouv.fr CSV link, with a check that the answer is a CSV, a stored `download_info.txt`, and a clear error message with manual instructions if the download fails.
- **What you kept, changed or rejected:** kept as is.
- **How you verified it:** the group ran the download on a normal connection. The file was downloaded automatically (2.9 MB) and loaded correctly with 12,907 rows and 26 columns.
- **Link to AI_AUDIT.md entry:** entry 1.

### Other members
All four members used the assistant in the same way. The two entries above cover the group's usage, so there are no separate member-specific prompts.

## Checklist for this milestone
- [ ] Each entry shows explicit constraints (schema, assumptions, leakage)
- [ ] Verification described for each entry
