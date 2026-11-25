# Raw data

Dataset: **Régularité mensuelle TGV par liaisons** (SNCF Voyageurs)
Page: https://www.data.gouv.fr/datasets/regularite-mensuelle-tgv-par-liaisons
Licence: Open Data Commons Open Database License (ODbL), as shown on the data.gouv.fr page.
CSV link (used by the notebook): https://www.data.gouv.fr/api/1/datasets/r/91fe399d-cafa-4e72-8ba3-56d8717fdad4

The notebook downloads the file automatically on first run and writes
`regularite-mensuelle-tgv-aqst.csv` and `download_info.txt` (source URL, date, size) in this folder.
If the download is blocked, save the CSV manually under the same file name.

The raw file is never modified. Cleaned outputs go to `../processed/`.
