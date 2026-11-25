# Predicting monthly delay rates of French TGV routes

ESILV, Data and AI major, Machine Learning project (Lab 4 and 5).
Dataset: *Régularité mensuelle TGV par liaisons* (SNCF Voyageurs, ODbL),
https://www.data.gouv.fr/datasets/regularite-mensuelle-tgv-par-liaisons

**Question:** can we predict the share of late TGV arrivals on a route for a given month, using only information known before that month, and do we beat simple baselines?

## Structure
- `notebooks/02_week2_data_prep_baseline.ipynb`: cleaning, features, temporal split, baselines (Week 2)
- `data/raw/`: the notebook downloads the CSV here (not versioned)
- `data/processed/`: clean dataset and results produced by the notebook
- `report/`: final report and figures
- `ai_governance/`: CONTRIBUTIONS.md, PROMPT_LOG.md, AI_AUDIT.md

## Run
```bash
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute notebooks/02_week2_data_prep_baseline.ipynb --inplace
```
Or open the notebook in Jupyter or VS Code and run all cells.

## Team
See `ai_governance/CONTRIBUTIONS.md`.
