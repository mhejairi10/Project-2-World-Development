# Hollow Growth: Targeting the $100M Intervention Fund
### World Development Statistics (Gapminder) — Exploratory Data Analysis

---

## Problem Statement

A Policy Steering Committee has $100M to fund countries with stalled human development, but rising GNI per capita doesn't always mean people are living longer, healthier lives. This project analyzes population, GNI per capita, and life expectancy trends from 1960-2020 to identify "hollow growth" countries — places where income grew strongly but life expectancy gains badly lagged — so the fund can be targeted where it's actually needed.

## Executive Summary

[Fill this in yourself once your analysis is final — 2-3 paragraphs covering your process, key findings, conclusions, and recommendations. A suggested structure below; replace the bracketed prompts with your own words.]

[Paragraph 1 — Process: Briefly describe what you did. E.g., "We cleaned and merged three Gapminder datasets — population, GNI per capita, and life expectancy — into a single country-year panel covering 1960-2020. For each country, we measured how much its income grew and how much its life expectancy improved over that 60-year window, then flagged countries where income grew well above average but life expectancy gains lagged well below average."]

[Paragraph 2 — Findings: State your biggest results in plain language. E.g., "Of the 184 countries with complete data, X were flagged as 'hollow growth' candidates. [Name your standout examples] stood out most clearly, with strong economic growth but among the smallest gains in life expectancy of any country in the dataset."]

[Paragraph 3 — Conclusions & Recommendations: State your recommendation. E.g., "We recommend the Committee prioritize [countries] for the $100M fund, since their data shows income growth is not the binding constraint — a different kind of intervention (e.g., health system investment) is likely needed. This is a first-pass screen, not a final answer; country-level review is recommended before funds are committed."]

## File Directory

| File / Folder | Description |
|:---|:---|
| `README.md` | Project overview, executive summary, and findings (this file) |
| `Data/population.csv` | Original population data by country, 1800-2100 |
| `Data/life_expectancy.csv` | Original life expectancy data by country, 1800-2100 |
| `Data/gni_per_cap_atlas_method_con2021.csv` | Original GNI per capita data by country, 1800-2100 (Atlas method, constant 2021 USD) |
| `Code/World_Development_EDA_Data_Checking.ipynb` | Main EDA notebook: data cleaning, merging, and initial checks |
| `Code/03_EDA_WorldDevelopment.ipynb` | Full EDA notebook: analysis, hollow-growth flagging, and visualizations |
| `Presentation/Hollow_Growth_Presentation.pptx` | Slide deck summarizing the project for a 5-minute presentation |
| `Presentation/viz1_hollow_growth_scatter.png` | Scatter chart: GNI growth vs. life expectancy gain, by country |
| `Presentation/viz2_top10_shortlist.png` | Bar chart: top 10 hollow-growth candidate countries |

## Data & Data Dictionary

Data sourced from the [Gapminder Foundation](https://www.gapminder.org/about/), covering population, GNI per capita (Atlas method, constant 2021 USD), and life expectancy at birth for nearly 200 countries, 1800-2100. This analysis restricts the data to **1960-2020** per the problem statement.

| Feature / Column | Data Type | Source | Description |
|:---|:---|:---|:---|
| `country` | string | Original | Country name |
| `year` | int | Original | Calendar year, restricted to 1960-2020 |
| `population` | float | Original (cleaned) | Total national population; converted from Gapminder shorthand (`k`/`M`/`B`) to a numeric value |
| `gni` / `gni_per_capita` | float | Original (cleaned) | GNI per capita, Atlas method, constant 2021 USD; converted from Gapminder shorthand to a numeric value |
| `life_expectancy` | float | Original | Life expectancy at birth, in years |
| `gni_cagr_pct` | float | Engineered | Compound annual growth rate of GNI per capita, 1960-2020 |
| `pop_cagr_pct` | float | Engineered | Compound annual growth rate of population, 1960-2020 |
| `life_exp_change_years` | float | Engineered | Change in life expectancy, 1960-2020 |
| `hollow_growth_flag` | boolean | Engineered | True if a country has above-median GNI growth AND below-median life expectancy gain |

## Important Visualizations

**GNI Growth vs. Life Expectancy Gains** — each dot is a country; countries in red were flagged as hollow-growth candidates (above-median income growth, below-median life expectancy gain).

![Hollow growth scatter plot](Presentation/viz1_hollow_growth_scatter.png)

**Top 10 Hollow Growth Candidates** — the ten flagged countries with the smallest life expectancy gains despite above-median income growth.

![Top 10 hollow growth candidates](Presentation/viz2_top10_shortlist.png)

## Conclusions & Recommendations

[Fill this in yourself — pull directly from Section 5 of your EDA notebook once it's finalized.]

* **Key conclusion:** [e.g., "Income growth alone does not guarantee a population lives longer, healthier lives — X of 184 countries analyzed show a real, measurable gap."]
* **Recommendation:** [Which specific countries would you prioritize for the $100M fund, and why?]

## Areas for Further Research

* This analysis only compares two snapshot years (1960 and 2020) — it doesn't capture what happened in between (a country could have dipped badly mid-period and fully recovered by 2020, and this method wouldn't show that).
* The median-split flag doesn't account for a country's starting life expectancy, so some flagged countries may simply have less room left to grow rather than a genuine problem.
* [Add your own additional idea for further research here.]

## Sources

* Population, GNI per capita (Atlas method, constant 2021 USD), and Life Expectancy datasets — [Gapminder Foundation](https://www.gapminder.org/about/)
