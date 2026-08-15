# A-B-Tasty

This project evaluates an A/B test conducted for the company **Eniac** to optimize the Click-Through Rate (CTR) on their website's homepage. The experiment focused on testing two key design variables across four homepage versions. It was carried out as part of a practical data analytics case study project during a bootcamp at WBS Coding School.
> Optimizing Click-Through Rate (CTR) through data-driven homepage design decisions.

## Project Overview

- **Button color** — White vs. Red
- **Call-to-action text** — "SHOP NOW" vs. "SEE DEALS"

| Version | Button color | CTA text  |
| ------- | ------------ | --------- |
| A       | White        | SHOP NOW  |
| B       | Red          | SHOP NOW  |
| C       | White        | SEE DEALS |
| D       | Red          | SEE DEALS |

## Data

Raw click/visit data for each homepage version lives in `Data/`:

- `eniac_a.csv`, `eniac_b.csv`, `eniac_c.csv`, `eniac_d.csv` — one file per version above, each containing element-level click counts and visit snapshot info scraped from the live pages.

## Hypotheses

- **H₀ (Null): All four versions have the same CTR.**
- **H₁ (Alternative): At least one version has a statistically significant difference in CTR.**
- **Significance Level: α = 0.05 (95% confidence)**

## Statistical Findings

A chi-squared test of independence was run on the clicks/visits contingency table across all four versions, followed by a Bonferroni-corrected pairwise post-hoc test to identify the true winner.

- **Overall test: χ² = 224.02, p ≈ 2.7 × 10⁻⁴⁸ → reject H₀.** The design variations have a statistically significant impact on CTR.

| Version | CTR   |
| ------- | ----- |
| C       | 2.12% |
| A       | 2.02% |
| B       | 1.14% |
| D       | 0.76% |

- **Pairwise post-hoc (α = 0.05 / 6 comparisons):** A vs. C is the only non-significant pair (p = 0.465) — every other pair is significant.

**Recommendation** — Use a **white button**. Versions A and C (both white) statistically tie for the highest CTR and significantly outperform both red versions (B and D), while the CTA text ("SHOP NOW" vs. "SEE DEALS") makes no significant difference. Button color, not copy, drives the CTR gain here.

## How to Reproduce

1. Install dependencies: `pandas`, `numpy`, `scipy`, `seaborn`, `matplotlib`.
2. Run [`NoteBook/01_main_analysis.ipynb`](NoteBook/01_main_analysis.ipynb) for the full hypothesis test, pairwise post-hoc analysis, and CTR plots.
3. See [`NoteBook/02_mail.analysis.ipynb`](NoteBook/02_mail.analysis.ipynb) for the supplementary analysis.
4. Generated plots are saved to `outputs/` (e.g. [`03_CTR_performance_plot.png`](outputs/03_CTR_performance_plot.png), [`01_pair_wise_tests_plot.pdf`](outputs/01_pair_wise_tests_plot.pdf)).

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=flat&logo=scipy&logoColor=white)

- **Python** — Core analysis language
- **Pandas** — Data manipulation and aggregation
- **SciPy** — Chi-squared statistical testing

---
