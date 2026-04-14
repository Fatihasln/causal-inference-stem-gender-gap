# causal-inference-stem-gender-gap

# Causal Inference: Financial Incentives and Female STEM Enrollment in Italy

[![SSRN](https://img.shields.io/badge/SSRN-6282579-blue)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6282579)
[![Python 3.9+](https://img.shields.io/badge/python-3.9%2B-blue)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Replication code for **"Paying for Progress? The Causal Effect of Financial Incentives on Female STEM Enrollment"** (Çiftaslan, 2026).

---

## What This Project Does

Italy's MUR Decree No. 1320 (2021) introduced a **20% scholarship bonus** for female STEM students starting AY 2022/23. I exploit a sharp discontinuity in eligibility rates — ~100% for international students vs ~18% for domestic students — to isolate the causal effect of financial incentives on enrollment decisions.

**Main finding:** A **+6.0 percentage point** increase in female Engineering enrollment among the highly-treated international cohort (p = 0.001), translating into ~209 additional female Engineering graduates over 2022–2024.

---

## Methods

- **Difference-in-Differences (DiD)** — STEM vs. Non-STEM fields, pre/post 2022
- **Heterogeneous treatment effects** — Engineering / ICT / Basic Sciences disaggregated
- **Domestic placebo test** — rules out cultural confounds via differential eligibility (5.6:1 ratio)
- **Permutation-based inference** — exact finite-sample p-values (500 iterations, p = 0.018)
- **Parallel trends validation** — pre-treatment linear trend test (2011–2021)
- **Weighted Least Squares (WLS)** — weighted by cell size for population representativeness

---

## Key Results

| Specification | β | SE | p |
|---|---|---|---|
| Engineering × Post (International) | **+0.060** | 0.017 | 0.001 |
| ICT × Post (International) | +0.030 | 0.037 | 0.424 |
| Basic Sciences × Post (International) | +0.037 | 0.029 | 0.201 |
| Engineering × Post (Domestic placebo) | −0.017 | 0.009 | 0.081 |

Permutation p-value: **0.018** (500 iterations) | Pre-treatment β₃: 0.0055 (p = 0.289) ✅

---

## Files

```
├── analysis.ipynb   # Full analysis with outputs (Tables 1–2, Figure 1)
├── ssrn-6282579.pdf     # Working paper
└── README.md
```

The notebook contains all outputs — tables, regression results, and figures are rendered directly on GitHub without needing to run anything.

---

## Data

Administrative records from the **Italian Ministry of University and Research (MUR)**, accessed via the [USTAT Open Data Portal](http://dati.ustat.miur.it/) — publicly available at no cost.

| File | Description |
|---|---|
| `11_laureatiinternazionalixclasse.csv` | International graduates by LM code, gender, year (2011–2024) |
| `05_laureatixclasse.csv` | Domestic graduates by LM code, gender, year (2011–2024) |

Data files are not tracked in this repository. Download directly from USTAT and place in the same directory as the notebook before running.

---

## Reproducing the Analysis

```bash
pip install pandas numpy statsmodels matplotlib seaborn
jupyter notebook analysis.ipynb
```

Update `FILE_INTL` and `FILE_DOM` at the top of the notebook to point to your local data files.

---

## Citation

```bibtex
@unpublished{ciftaslan2026paying,
  author = {Çiftaslan, Mehmet Fatih},
  title  = {Paying for Progress? The Causal Effect of Financial Incentives on Female {STEM} Enrollment},
  year   = {2026},
  note   = {SSRN Working Paper 6282579},
  url    = {https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6282579}
}
```

---

## Contact

**Mehmet Fatih Çiftaslan**  
📧 mehmetfatih.ciftaslan@studenti.unimi.it  
🏛️ Università degli Studi di Milano, Department of DEMM
