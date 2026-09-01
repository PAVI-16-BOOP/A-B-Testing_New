# A/B Testing: Landing Page Conversion Experiment

An end-to-end A/B test analysis on an e-commerce landing page redesign — going beyond a basic z-test to include pre-experiment power analysis, Bayesian analysis, segment-level checks, and multiple-testing awareness.

---

## ❓ The Question

Does a new landing page convert more visitors into buyers than the old one?

---

## 🔄 Pipeline

* **Power Analysis & EDA:** Cleaned contaminated rows (users shown the wrong page, or both pages), calculated the sample size needed to trust the results, and checked for a novelty effect over time.
* **Frequentist Testing:** Two-proportion z-test, 95% confidence intervals, and effect size calculation.
* **Bayesian Analysis:** Modeled both groups as Beta distributions and ran a 100,000-sample Monte Carlo simulation to estimate the probability that the new page is better, along with a credible interval for the true lift.
* **Segment Analysis:** Re-ran the test across 8 sub-groups (time of day, weekday/weekend, early/late in the test) to check if the redesign worked for specific segments even though it didn't win overall.

---

## 💡 Key Findings

* **Data Cleaning:** Removed 5,789 contaminated rows (mismatched page/group or users who saw both pages) before running the analysis, reducing the dataset from **294,478 to 288,689 rows**.
* **Frequentist Result:** Control converted at **12.03%**, treatment at **11.88%** — no statistically significant difference ($p = 0.22$).
* **Bayesian Check:** Agrees with the frequentist result, showing only an **11% probability** that the new page outperforms the old one.
* **Segment Breakdown:** No segment showed a true win. The best-performing segment (Evening, +0.29pp) was not statistically significant ($p = 0.23$), proving it to be noise rather than a rollout signal.
* **Novelty Effect:** Daily conversion rates for both pages remained flat and overlapping throughout the entire 23-day experiment window.

> **Final Recommendation:** Do not roll out the redesign.

---

## 🛠️ Tools Used

* **Language:** Python
* **Data Processing:** Pandas, NumPy
* **Statistical Modeling & Analysis:** SciPy, Statsmodels
* **Data Visualization:** Matplotlib, Seaborn

---

## 🚀 How to Run

Run the notebooks in sequential order — each step builds directly on the cleaned outputs of the previous phase:

1. `01_power_analysis_and_eda.ipynb`
2. `02_frequentist_tests.ipynb`
3. `03_bayesian_analysis.ipynb`
4. `04_segment_and_revenue.ipynb`

---

## 📊 Dataset

* **Source:** [Kaggle: A/B Testing Dataset](https://www.kaggle.com/datasets/zhangluyuan/ab-testing)
* **Scope:** 294,478 raw rows of user-level visit and conversion data.
