# Data Documentation (NHANES 2021–2023)

This document explains the official data sources, access date, and automated reconstruction steps.

## 1. Official Data Source
- **Source:** Centers for Disease Control and Prevention (CDC) / National Center for Health Statistics (NCHS) — National Health and Nutrition Examination Survey (NHANES), August 2021–August 2023 cycle.
- **Official Portal:** [CDC NHANES 2021–2023 Data Files](https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?Cycle=2021-2023)
- **Date Retrieved:** October 2026

## 2. Required Public-Use Files
The following five SAS Transport (`.xpt`) files from the 2021–2023 cycle are used:
1. `DEMO_L.xpt` — Demographic Variables and Sample Weights (`SEQN`, `RIDAGEYR`, `RIAGENDR`, `WTMEC2YR`)
2. `BMX_L.xpt` — Body Measures (`SEQN`, `BMXBMI`)
3. `BPXO_L.xpt` — Blood Pressure - Oscillometric Measurements (`SEQN`, `BPXOSY1`)
4. `SLQ_L.xpt` — Sleep Disorders (`SEQN`, `SLD012`)
5. `PAQ_L.xpt` — Physical Activity (`SEQN`, `PAD680`)

Direct download base URL:
`https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/`

## 3. Reconstructing the Analytical Dataset
You do not need to download the files manually. Running either `src/nhanes.py` or `notebooks/phase1.ipynb` will automatically:
1. Create the `data/` directory if it does not exist and download all 5 `.xpt` files directly from the CDC server.
2. Inner-join the 5 tables on the unique participant identifier `SEQN` ($11,933 \rightarrow 6,337$ participants).
3. Recode special NHANES missing/refused codes (`7777`, `9999` in `PAD680`) to `NaN`.
4. Filter to adults aged $\ge 20$ years ($6,064$ participants) and remove records with missing values on the core analytical variables, yielding the final analytical dataset of **$N = 5,714$** adult participants.
