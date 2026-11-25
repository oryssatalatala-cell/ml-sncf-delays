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

## Entries

(none yet)

## Checklist for this milestone
- [ ] At least one entry per student
- [ ] Each entry shows explicit constraints (schema, assumptions, leakage)
- [ ] Verification described for each entry
