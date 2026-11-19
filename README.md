# 🌏 Does Cooking Smoke Make Children Sick? Household Air Pollution in Southeast Asia
 
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![statsmodels](https://img.shields.io/badge/statsmodels-4051B5?style=for-the-badge)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge)
![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)
 
> An analysis of **44,650 children under five** in **Cambodia, Indonesia, Myanmar, the Philippines and Timor-Leste**, testing a common belief: that children in homes cooking with wood, charcoal or kerosene get more chest infections. They do — but once family wealth is taken into account, the difference disappears.
>
> **Built for ARCeH (Advancing Research for Children's Health – Environmental Health) via Extern · Mentored by Dr. Bill Suk and Will Suk, ARCeH Board**
 
---
 
## 📦 Final Deliverables
 
| Deliverable | Audience | What It Answers |
|---|---|---|
| 📄 [Practitioner's Brief](deliverables/ARCeH_Practitioners_Brief.pdf) | Environmental health practitioners | Should survey data shift money toward or away from clean-cooking programs? |
| 📊 [Slide Deck](deliverables/ARCeH_Slide_Deck.pdf) | ARCeH Board | Which children's respiratory research should ARCeH back next? |
| 📓 [Analysis Notebooks](notebooks/) | Data reviewers | How the data was cleaned, analyzed and stress-tested |
| 🧭 [Process Documents](process/) | Hiring managers and mentors | How the dataset, research question and stress test were developed |
 
---
 
## 🎯 The Problem
 
Pneumonia is one of the leading causes of death in children under five, and the World Health Organization links about half of those deaths to smoke from household cooking. In Cambodia, Myanmar and Timor-Leste, **more than 80% of children** live in homes that cook with wood, charcoal, kerosene or similar fuels.
 
Health organizations have limited budgets. Before they invest in clean-cooking programs — or move money away from them — they need a clear answer to one question:
 
> **Does the type of cooking fuel tell us which children are more likely to get sick?**
 
---
 
## 🔬 The Investigation
 
### 1. At first, fuel seemed to make no difference
 
I used **Demographic and Health Surveys (DHS)**, large national household surveys, accessed through IPUMS-DHS. Each record links one child to their mother's report of recent symptoms and to the household's cooking fuel, kitchen and living conditions. After cleaning the data, **44,650 children** remained, including **1,583 with chest infection symptoms** in the two weeks before the survey.
 
Across all five countries, the rates were almost identical:
 
| Cooking Fuel | Children With Chest Infection Symptoms |
|---|---|
| Clean (gas, electricity) | 3.27% |
| Polluting (wood, charcoal, kerosene) | 3.28% |
 
Either the belief was wrong, or something in the data was hiding the pattern.
 
### 2. Looking inside each country revealed a link
 
When I looked at each country separately, children in wood- and charcoal-burning homes **did** get sick more often in 3 of the 5 countries. In the Philippines, the rate was **twice as high** (1.6% vs 0.8%).
 
So why did the combined numbers look flat? **Indonesia.** It was the largest group, most of its homes cook with clean fuel, and it has a high rate of chest infections overall. Mixing it with the other countries cancelled out the differences inside them.
 
From then on, I compared children **only with other children in the same country**. On that basis, children in polluting-fuel homes were about **26% more likely** to have chest infection symptoms.
 
### 3. Then family wealth made the link disappear
 
Poorer families are more likely to cook with wood and charcoal. Their children also tend to get sick more often for other reasons, such as poorer nutrition, crowded homes and less access to healthcare. So I checked whether fuel still mattered when comparing **families of similar wealth**.
 
I added one family factor at a time and watched how the result changed:
 
| What I Accounted For | Polluting-Fuel Homes vs Clean-Fuel Homes |
|---|---|
| Nothing (all countries combined) | No difference |
| Same country | ✅ **26% more likely** to be sick |
| Same country + similar wealth | ❌ No difference |
| Same country + every other family factor **except** wealth | ⚠️ 21% more likely (borderline) |
| **Same country + all family factors** | ❌ **No difference** |
 
Mother's education, smoking at home, breastfeeding and household size barely changed the result. **Wealth was the only factor that made the link disappear.** I re-ran the analysis with three other methods, and all of them reached the same answer.
 
### 4. Testing my own conclusion
 
A "no difference" result can be wrong too, so I tried to find holes in my own conclusion. I asked an AI to critique my interpretation, with two rules: **don't rewrite my work, and don't suggest ways to force a positive result.**
 
The critique pushed me on an issue I had noted but underplayed. The survey's **wealth score is partly calculated from the type of cooking fuel a home uses.** So adjusting for wealth may quietly remove part of the very effect I was testing — like asking whether exercise helps fitness while scoring fitness partly by minutes of exercise.
 
To test this, I measured family background **without** the wealth score, using the mother's education, city or rural home and the child's birth order instead. The link came back: children in polluting-fuel homes were about **22% more likely** to be sick.
 
That changed how I described the result:
 
| My First Conclusion | My Final Conclusion |
|---|---|
| Cooking fuel has no meaningful effect | A **small effect can't be ruled out** |
| The wealth score issue was a footnote | It is the **main limitation** of the study |
| Borderline results reported as findings | Treated as **leads to confirm**, since I ran many comparisons |
 
---
 
## 📊 Key Findings
 
| Finding | What It Means |
|---|---|
| ⚠️ Combining all five countries hid the pattern | Regional averages can be misleading; compare within each country |
| ✅ Within each country, polluting fuel was linked to **26% more** chest infections | The common belief holds — at first |
| ❌ After accounting for wealth, the link **disappeared** | Poverty explains most of the difference |
| ✅ Children in the wealthiest fifth of homes were **about half as likely** to be sick as the poorest fifth | Wealth was the strongest household factor |
| ⚠️ Measured without the wealth score, fuel was linked to **22% more** infections | A small fuel effect is still possible |
| 🔍 Cooking indoors without a separate kitchen was linked to **28% more** infections, whatever the fuel | A lead worth confirming |
| ❌ No single country showed a clear fuel effect on its own | Each country had too few cases to tell |
 
> **What "no difference" does and doesn't mean:** The survey records only a household's *main* fuel, not the stove, ventilation or how close a child sits to the fire, and symptoms are reported from mothers' memory. Both make real differences harder to detect. This result means **no clear link was found** — not that cooking smoke is harmless.
 
---
 
## 💡 Recommendations
 
I delivered the findings in two formats, each built around a different decision.
 
**📄 Practitioner's Brief — for environmental health practitioners**
*Should this survey data shift money toward or away from clean-cooking programs?*
 
**Keep current funding in place** and commission a low-cost re-analysis that rebuilds the wealth score **without cooking fuel**, adds each child's exact age and uses newer survey data. **No new data collection is needed.**
 
- If the fuel link holds up → the case for clean-cooking programs gets **stronger**
- If it doesn't → **household poverty** is the better target
Until then, the data does not support cutting clean-cooking programs, or choosing which children to help based on fuel type or wealth alone.
 
**📊 Slide Deck — for ARCeH**
*Which children's respiratory health research should ARCeH support next in Southeast Asia?*
 
Back a **follow-up study** that separates household wealth from cooking fuel:
 
- Fund an early-career researcher to lead it
- Collect direct exposure data: kitchen setup, ventilation, stove type and child age
- Connect researchers across the five countries
- Present fuel-only survey results with caution
---
 
<details>
<summary><b>🔧 Technical Details (for statisticians and data reviewers)</b></summary>
| Area | Approach |
|---|---|
| **Data** | IPUMS-DHS microdata: Cambodia 2014, Myanmar 2015, Timor-Leste 2016, Indonesia 2017, Philippines 2017 |
| **Sample** | 47,600 children → 44,650 surviving, usual-resident children with complete data; 1,583 ARI cases |
| **Outcome** | Standard DHS ARI indicator: cough + short, rapid chest-related breathing in the past 2 weeks |
| **Exposure** | Polluting (wood, charcoal, biomass, kerosene) vs clean fuel, per WHO 2014 |
| **Main model** | Survey-weighted logistic regression, country fixed effects, standard errors clustered on 4,710 survey clusters |
| **Main result** | Fuel OR 1.26 (95% CI 1.05–1.50, p = 0.012) within country → OR 0.97 (0.79–1.20, p = 0.81) fully adjusted |
| **Robustness** | Unweighted model (OR 1.00), propensity score overlap weighting (RR 0.89), adjusted Cochran–Armitage trend (p = 0.20), Mantel-Haenszel cross-check (OR 1.29), kerosene split, per-country models, fuel × country interaction (p = 0.23) |
| **Wealth question** | Fuel-free adjustment (education + urban + birth-order proxy): OR 1.22 (1.01–1.48, p = 0.038) |
| **Model fit** | AUC 0.67; well calibrated across risk deciles |
| **Pattern noted** | Pooled vs within-country disagreement is Simpson's paradox, driven by Indonesia's sample size and fuel mix |
 
</details>
---
 
## 🧰 Tech Stack
 
| Category | Tools |
|---|---|
| **Data cleaning** | pandas, NumPy |
| **Statistical modeling** | statsmodels |
| **Robustness checks** | Propensity score weighting, bootstrapping, trend tests |
| **Visualization** | Matplotlib, Seaborn |
| **Environment** | Google Colab |
 
---
 
## ⚠️ Limitations
 
1. **Wealth and fuel overlap** — the survey's wealth score is partly built from cooking fuel, so the two are hard to separate
2. **Fuel isn't the same as smoke exposure** — the survey doesn't record stove type, ventilation or time near the fire
3. **No exact child age** — younger children get sick more often; birth order was used as a stand-in
4. **One-time, self-reported survey** — shows links, not cause and effect, and relies on mothers' memory
5. **Few poor clean-fuel homes** — in most countries, nearly all of the poorest families cook with polluting fuel, so there's little to compare against
---
 
## 📁 Repository Structure
 
```
ARCeH-Environmental-Health/
├── README.md
├── requirements.txt
├── deliverables/                          # Final outputs (open these first)
│   ├── ARCeH_Practitioners_Brief.pdf
│   └── ARCeH_Slide_Deck.pdf
├── notebooks/                             # Code, run in order
│   ├── 01_Exploratory_Data_Analysis.ipynb
│   ├── 02_Statistical_Analysis.ipynb
├── data/
│   ├── README.md                          # Which IPUMS-DHS samples and variables to request
│   └── Codebook_Key_Variables.csv
└── images/
    └── practitioner_chart_final.png
```
 
*Developed during the ARCeH Environmental Health Research Externship (Extern, 2026) by [Sriram Srinivasan](https://www.linkedin.com/in/sriram-srinivasan00/).*
 
