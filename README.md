# ARCeH-Environmental-Health
# 🌏 Household Air Pollution × Childhood Respiratory Infection — Southeast Asia
 
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![statsmodels](https://img.shields.io/badge/statsmodels-4051B5?style=for-the-badge)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge)
![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)
 
> A survey-weighted analysis of **44,650 children under five** across **Cambodia, Indonesia, Myanmar, the Philippines and Timor-Leste**, testing a widely held assumption: that cooking with polluting fuel drives childhood acute respiratory infection (ARI). Within each country, it does — until household wealth enters the model.
>
> **Built for ARCeH (Advancing Research for Children's Health – Environmental Health) via Extern · Advised by Dr. William Suk, ARCeH Board Member**
 
![Practitioner chart](images/practitioner_chart_final.png)
 
---
 
## 🎯 The Problem
 
Pneumonia remains a leading killer of children under five, and household smoke from wood, charcoal and kerosene is routinely named as a cause. In Cambodia, Myanmar and Timor-Leste, **more than 80% of children** live in homes that cook with polluting fuel.
 
Environmental health practitioners have limited budgets for children's respiratory health. Before shifting money toward or away from clean-cooking programs, they need to know one thing:
 
> **Does cooking fuel reliably identify which children get sick?**
 
| The Assumption | What This Analysis Tested |
|---|---|
| Polluting fuel raises ARI risk | Whether the link holds across 5 countries in one harmonized model |
| Fuel is the driver | Whether poverty explains the link instead |
| Pooled regional data tells the story | Whether pooling hides what happens inside each country |
| A null result means "no harm" | Whether the null survives a deliberate stress test |
 
---
 
## 🔬 The Investigation
 
### 1. The pooled data showed nothing
 
I built the dataset from **Demographic and Health Survey (DHS) microdata via IPUMS-DHS**: 47,600 children, each row linking a mother-reported symptom to the household's stove, kitchen and wealth. After decoding the codebook, filtering to usual-resident children and resolving missing values, **44,650 children** remained.
 
The first comparison was flat:
 
| Fuel Type | ARI Prevalence |
|---|---|
| Clean fuel | 3.27% |
| Polluting fuel | 3.28% |
 
Either the hypothesis was wrong, or the data was hiding something.
 
### 2. Inside each country, the pattern appeared
 
Split by country, biomass homes had more ARI in Indonesia (5.4% vs 4.0%), Myanmar (3.3% vs 2.6%) and the Philippines — where the rate **doubled** (1.6% vs 0.8%).
 
Indonesia was the reason the pooled number was flat. It was the largest sample, mostly clean-fuel, and high in ARI overall — enough to cancel the gaps everywhere else. That's **Simpson's paradox**, and it set the design rule for the rest of the project: compare children **within** the same country.
 
With country fixed effects, survey weights and clustered standard errors, the link was clear: **26% higher odds of ARI** in polluting-fuel homes (OR 1.26, p = 0.012).
 
### 3. Then wealth erased it
 
I added covariates one group at a time to see what moved the estimate.
 
| Model | Fuel Odds Ratio | Result |
|---|---|---|
| All countries pooled | 1.00 | ❌ No link |
| Within country | **1.26** | ✅ Clear link |
| + Household wealth | 0.92 | ❌ Link gone |
| All covariates *except* wealth | 1.21 | ✅ Link holds |
| **Full model** | **0.97** (95% CI 0.79–1.20) | ❌ **No detectable link** |
 
Mother's education, smoking, kitchen location, breastfeeding and household size barely moved it. **Wealth alone switched the fuel effect on and off.** Poorer households cook with polluting fuel — and their children get sick more often for many other reasons.
 
Four independent methods confirmed it, including a Mantel-Haenszel cross-check, propensity score overlap weighting (RR 0.89) and a Cochran–Armitage trend test.
 
### 4. Stress-testing the null
 
A null result can be wrong too. I wrote a structured prompt asking AI to attack my interpretation — with two rules: **don't rewrite my work, and don't suggest ways to make the fuel effect significant.**
 
It found the weak point: **the DHS wealth index is partly built from cooking fuel itself.** Adjusting for wealth might erase a real smoke effect.
 
I tested it directly. Measuring family circumstances *without* the wealth index — mother's education and urban/rural residence — brought the fuel link back: **22% higher odds** (p = 0.038).
 
That changed the conclusion:
 
| Before Stress Test | After Stress Test |
|---|---|
| "Rules out" more than a 20% increase | **Does not rule out** a modest effect |
| Wealth overlap was a closing caveat | Wealth overlap is **the** main limitation |
| Borderline results reported as findings | Labeled as **leads** — ~35 comparisons were run |
 
---
 
## 📊 Key Findings
 
| Finding | Evidence | Verdict |
|---|---|---|
| Pooled data hides the fuel link | 3.27% vs 3.28% pooled; gaps within 3 countries | ⚠️ Simpson's paradox |
| Fuel predicts ARI within countries | OR 1.26, p = 0.012 | ✅ Before wealth |
| Fuel predicts ARI after full adjustment | OR 0.97, p = 0.81 | ❌ Not detectable |
| Wealth is the strongest household predictor | Richest fifth OR 0.55 (half the odds) | ✅ Steady gradient |
| A modest fuel effect is ruled out | Fuel-free adjustment: OR 1.22, p = 0.038 | ❌ Can't be ruled out |
| Cooking indoors without a separate kitchen | OR 1.28, p = 0.023 | 🔍 Lead to confirm |
 
> **Note on the null:** Mother-reported symptoms and "main fuel" exposure both pull estimates toward no difference. This result means **no clear association** — not that cooking smoke is harmless.
 
---
 
## 💡 Recommendation & Impact
 
The findings were delivered as a **practitioner's brief** and **slide deck** built around one decision: should DHS cooking-fuel data shift resources toward or away from clean-cooking programs?
 
**Recommendation:** Maintain current allocations and commission a targeted re-analysis that rebuilds the wealth index **without cooking fuel**, adds child age and uses newer survey rounds — **no new data collection required.**
 
- If the fuel effect survives → the case for clean-cooking investment gets **stronger**
- If it doesn't → household **poverty** becomes the more defensible target
Until then, the data does not support cutting clean-cooking programs — or targeting children by fuel type or wealth alone.
 
---
 
## 🧰 Tech Stack
 
| Category | Tools |
|---|---|
| **Data wrangling** | pandas, NumPy |
| **Modeling** | statsmodels — survey-weighted logistic regression, cluster-robust SEs, Wald tests |
| **Robustness** | Propensity score weighting, cluster bootstrap, Mantel-Haenszel, Cochran–Armitage |
| **Visualization** | Matplotlib, Seaborn |
| **Runtime** | Google Colab |
 
---
 
## ⚠️ Limitations
 
1. **Wealth vs fuel overlap** — the wealth index partly contains cooking fuel
2. **No exact child age** in the extract — birth order used as a proxy
3. **Cross-sectional, self-reported** — association, not causation
4. **Limited overlap** — 47% of children have a near-certain fuel type, so the poorest rural homes have no clean-fuel comparison
---
 
## 📁 Repository Structure
 
```
├── notebooks/
│   ├── Exploratory_Data_Analysis.ipynb   # Cleaning, feature engineering, weighted EDA
│   └── Statistical_Analysis.ipynb        # Regression, sensitivity checks, charts
├── reports/
│   ├── Practitioners_Brief.pdf
│   └── Slide_Deck.pdf
├── images/
└── README.md
```
 
*Data: DHS Program via IPUMS-DHS (University of Minnesota). Raw data is not redistributed — request the extract at [idhsdata.org](https://www.idhsdata.org).*
 
---
