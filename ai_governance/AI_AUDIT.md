# AI_AUDIT (at least 4 concrete flaws caught in AI outputs, at least 1 per student)

Rule from the lab: claiming that the AI made zero errors scores 0/5. Log only flaws you really found, with the evidence.

| # | Student | Where (file / notebook cell) | What the AI output said or did | Why it is wrong or risky | How you detected it | Fix applied |
|---|---------|------------------------------|--------------------------------|--------------------------|---------------------|-------------|
| 1 | Oryssa Stella TALATALA | Notebook section 1 (load) | First version read the data from a local path (`../data/raw/...csv`) and gave no source URL, although the assistant had recommended the dataset | The notebook was not reproducible and pushed the data collection onto the user | Noticed by Stella when reading the notebook | Added `DATA_URL`, an automatic download with checks and `download_info.txt`, and a clear error with manual instructions |
| 2 | Oryssa Stella TALATALA (found by the AI during its own testing) | Notebook section 2 (cleaning) | Rows with station `0` were relabelled `UNKNOWN` and kept; duplicate-key aggregation then summed rows of different real routes into one fake route | Corrupts route identity and the lag features built per route | The cleaning log showed "rows involved in duplicated keys (aggregated)" greater than 0 on test data | Rows with an unusable station are now dropped and counted in the cleaning log |


## Where to look in the Week 2 notebook (things the group must verify itself)
These are open points in the AI-drafted code, not findings. Check each against the real file and write up what you actually observe.

1. **Column names.** The mapping in section 1.1 matches columns by keyword. Does it select the right "late arrivals" column in the real CSV? Check the printed mapping against the raw header.
2. **Target definition.** `late_rate = late arrivals / (scheduled - cancelled)`. Is this the right denominator for this dataset? Compare with the dataset description and a few rows computed by hand.
3. **Station `0` rows.** How many rows are dropped, and are they concentrated in some months or routes?
4. **COVID months.** Do 2020-2021 rows distort the baselines? Is dropping them better or worse on validation?
5. **Persistence vs Ridge.** If Ridge barely beats persistence, is the "baseline" strong enough to matter for Week 3?
6. **Leakage.** Re-derive `lag1` for three random rows by hand from the raw data.
