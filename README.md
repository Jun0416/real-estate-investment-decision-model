# U.S. Real Estate Investment Score Model

> A data-driven support model to identify high-potential residential real estate investment opportunities across all U.S. states using publicly available housing and economic data.

---

## Overview

This project analyzes zip-code-level real estate data across all 50 U.S. states to generate a composite **Investment Score**. The score integrates rental yield, income demographics, and property price to help investors identify zip codes with strong return potential relative to risk.

---

## Business Insights

By combining ROI, income stability, and price accessibility into a single score, this model enables the following actionable conclusions:

- **High-ROI zip codes are not always the best investment** — areas with low median income may signal tenant instability or high vacancy risk. The model accounts for this by incorporating income as a positive weight.
- **After adjusting for mortgage interest costs (6.5% rate)**, many nominally high-ROI markets show negative cash flow, revealing hidden risk not visible from gross yield alone.
- **Lower-priced markets with strong rental income and solid median incomes** consistently rank highest — pointing to secondary cities and suburban markets as overlooked opportunities.
- Zip codes scoring above the **80th percentile** on the Investment Score represent the most favorable balance of yield, demand, and affordability.

---

## Data Sources

| Dataset | Source | Description |
|---|---|---|
| Property Prices | Zillow (ZHVI) | Median home value by zip code |
| Rental Rates | Zillow (ZORI) | Median rent by zip code |
| Median Household Income | U.S. Census Bureau (ACS) | B19013 variable, zip-level income |
| Mortgage Rate | Assumed (Fixed) | 6.5% annual rate applied uniformly |

---

## Methodology

For each zip code, the following metrics were calculated and standardized using z-scores before combining into a final Investment Score:

| Metric | Formula | Weight |
|---|---|---|
| Gross ROI | (Annual Rent / Property Price) × 100 | — |
| Annual Mortgage Interest | Property Price × 6.5% | — |
| Cash Flow | Annual Rent − Annual Mortgage Interest | — |
| ROI After Interest | Cash Flow / Property Price | +0.5 |
| Median Income | From Census ACS B19013 | +0.3 |
| Property Price | From Zillow ZHVI | −0.2 |

---

## Investment Score Formula

```
Investment Score = (0.5 × z_ROI_after_interest) + (0.3 × z_median_income) − (0.2 × z_price)
```

Where each variable is standardized as:
```
z(x) = (x − mean) / std
```

A higher Investment Score indicates a zip code with strong rental returns after financing costs, stable income demographics, and relatively affordable property prices — representing the most attractive conditions for residential real estate investment.

---

## Tools & Technologies

- **Python (Pandas)** — data cleaning, merging, and score calculation
- **Jupyter Notebook** — exploratory analysis and modeling
- **Tableau** — interactive zip-code-level visualization across all states

  
## Interactive Dashboard

View the interactive Tableau dashboard:

🔗[View the Dashboard](https://public.tableau.com/app/profile/junyong.seong/viz/RealEstateInvestmentModel/1_1)
