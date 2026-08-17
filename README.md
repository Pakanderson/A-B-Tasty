
# Eniac Homepage A/B Testing & CTR Optimization

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=flat&logo=scipy&logoColor=white)

> Evaluated 4 homepage design variations using Chi-Squared hypothesis testing and Bonferroni-corrected post-hoc analysis to identify conversion drivers for Eniac.

---

## 🎯 Executive Summary & Recommendations

* **Key Driver:** Button color is the primary driver of CTR performance. **White buttons significantly outperformed red buttons.**
* **Copy Impact:** Text copy ("SHOP NOW" vs. "SEE DEALS") showed no statistically significant difference in user conversion.
* **Final Recommendation:** **Deploy Version C or Version A (White Button).** Both versions tie for the highest performance (~2.02%–2.12% CTR) and statistically outperform red button alternatives by up to **2.7x**.

---

## 🧪 Experiment Architecture

To test the impact of design elements on conversion rates, a $2 \times 2$ factorial experiment was deployed across four distinct homepage versions:

| Version             | Button Color | CTA Text  | CTR (%)         | Statistical Rank       |
| :------------------ | :----------- | :-------- | :-------------- | :--------------------- |
| **Version C** | White        | SEE DEALS | **2.12%** | 🥇 Winner (Tied for#1) |
| **Version A** | White        | SHOP NOW  | **2.02%** | 🥇 Winner (Tied for#1) |
| **Version B** | Red          | SHOP NOW  | **1.14%** | 🥈 Underperformed      |
| **Version D** | Red          | SEE DEALS | **0.76%** | 🥉 Lowest Performing   |

---

## 📊 Statistical Analysis & Methodology

### 1. Hypothesis Definition

* **$H_0$ (Null):** $CTR_A = CTR_B = CTR_C = CTR_D$ (Design variations have no effect on CTR)
* **$H_1$ (Alternative):** At least one version has a statistically significant difference in CTR.
* **Significance Threshold ($\alpha$):** 0.05 (95% Confidence Interval)

### 2. Overall Significance (Omnibus Test)

A **Chi-Squared ($\chi^2$) Test of Independence** was conducted across the aggregated clicks/visits contingency matrix:

* **$\chi^2$ Statistic:** 224.02
* **p-value:** $2.7 \times 10^{-48}$ ($p < 0.05$)
* **Conclusion:** Reject $H_0$. Design variations have a highly significant impact on user behavior.

### 3. Pairwise Post-Hoc Analysis

To isolate which specific variables drove the difference while controlling for **Type I error inflation**, a post-hoc analysis was executed using the **Bonferroni Correction** ($\alpha_{adjusted} = 0.05 / 6 \approx 0.0083$):

* **A vs. C ($p = 0.465$):** **Not significant.** Confirming copy choice does not meaningfully shift conversion.
* **All other pairwise comparisons ($p < 0.0083$):** **Statistically significant.** Confirming white buttons systematically beat red buttons regardless of copy.

---

## 📁 Repository Structure

```text
├── Data/                   # Raw visit and click-level CSV exports
│   ├── eniac_a.csv
│   ├── eniac_b.csv
│   ├── eniac_c.csv
│   └── eniac_d.csv
├── NoteBook/               # Jupyter Notebooks containing execution steps
│   ├── 01_main_analysis.ipynb   # Primary hypothesis testing & post-hoc execution
├── outputs/                # High-resolution data visualizations & export files
│   ├── 01_pair_wise_tests_plot.pdf
│   └── 03_CTR_performance_plot.png
└── README.md
```
