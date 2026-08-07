# Margin Decline Root Cause Analysis

## Executive Summary

A retail business observed a contradiction on a full-year basis: from 2016 to 2017, Sales and Profit both increased, but Profit Margin declined. This project investigates why, using order-level transaction data.

Reproducing the underlying data confirmed the full-year pattern (Sales↑, Profit↑, Margin↓, 2016 vs 2017) and identified the specific quarter driving it: **Q4-2017 vs Q4-2016**. Within that specific quarter — the baseline used for every root-cause finding below — Sales increased but **Profit also declined** ($38,139.86 → $27,448.73), alongside Margin. The full-year growth in Profit was driven by the other three quarters; Q4 alone moved against that trend. This distinction matters because the root-cause findings below explain a Sales↑/Profit↓/Margin↓ quarter, not a Sales↑/Profit↑/Margin↓ one — the two framings are not interchangeable, and conflating them would overstate what this analysis explains.

The decline was not associated with product category mix, which moved in a margin-favorable direction (Mix Effect: +0.08pp). It was associated with margin-rate deterioration concentrated in two areas: a small, high-ticket transaction cluster in the **Binders** sub-category (8–10 transactions, 96.6% of the Binders-level decline, average discount rising from 12.5% to 38.0%), and the **Central region**, which recorded the largest margin deterioration of any region (-33.3pp) and showed a discount-margin relationship consistently stronger than other regions in **2 of 3 product categories** (Furniture and Office Supplies; not observed in Technology). A majority of the total profit decline (60.8%) traces to a small number of large, deeply discounted transactions.

**Recommended actions:** review discount governance for the identified product cluster and the Central region pricing process (specifically for Furniture and Office Supplies), and verify the approval workflow for large discounted transactions — before making any broad discount policy change. Category mix rebalancing is not recommended, as it is not associated with the decline.

The dataset does not include cost or freight data, so findings describe observed patterns in pricing and discounting, not confirmed financial causes.

---

## Dashboard Preview

<img width="1421" height="802" alt="image" src="https://github.com/user-attachments/assets/7f5fcce2-518f-4dd8-9f02-336129e37347" />


<img width="1420" height="802" alt="image" src="https://github.com/user-attachments/assets/17e2da33-c4fb-442c-a63b-53bcd047ffa4" />


<img width="1420" height="806" alt="image" src="https://github.com/user-attachments/assets/8106a699-48ef-4bed-92ba-8fe9bf61d227" />

<img width="1426" height="802" alt="image" src="https://github.com/user-attachments/assets/e32f64e6-e21a-444b-9176-4068eb6df274" />

<img width="1422" height="802" alt="image" src="https://github.com/user-attachments/assets/6bd7aa12-a8fc-4028-b934-05af542323fb" />

---

## Business Context

The business sells across three product categories (Furniture, Office Supplies, Technology) to three customer segments (Consumer, Corporate, Home Office) across four U.S. regions. A quarterly performance review flagged that Sales and Profit growth was accompanied by a decline in Profit Margin — the metric that reflects underlying pricing and discounting efficiency.

This matters because strong top-line growth can mask a weakening pricing structure. Acting on Sales and Profit figures alone, without understanding the margin decline, risks reinforcing the underlying issue rather than resolving it.

---

## Business Questions

1. Did Sales, Profit, and Margin actually move in different directions, and over what period?
2. Where in the business did the change occur?
3. Which business dimensions are associated with the change?
4. Which explanation is best supported by the data?
5. Which candidate explanations were tested and ruled out?
6. What should management do, and how confident can they be?

---

## Dataset Overview

- **Rows:** 9,994
- **Columns:** 21
- **Granularity:** One row per order line item (5,009 unique orders)
- **Time period:** January 2014 – December 2017
- **Entities:** Order, Customer, Product (Category / Sub-Category), Region, Customer Segment
- **Geographic coverage:** United States only
- **Data quality:** No missing values, no invalid Sales/Quantity/Discount values, no duplicate Row IDs
- **Overall dataset margin:** 12.47%; 18.72% of line items recorded negative profit

---

## Analytical Workflow

1. **Business Understanding** — defined the business problem and confirmed the reported pattern was real, identifying the exact period it held.
2. **Exploratory Data Analysis** — examined Sales, Profit, and Margin across time, product, region, and customer segment.
3. **Root Cause Analysis** — tested candidate explanations, including discount, product mix, regional mix, and customer segment mix, against the observed decline.
4. **Validation** — checked findings for consistency across different data views (e.g., with and without outlier transactions, at line-item vs order-level aggregation, within individual product categories) before treating them as reliable.
5. **Business Recommendations** — translated validated findings into prioritized, actionable recommendations.
6. **Dashboard** — built an executive-facing Power BI dashboard to communicate findings and recommendations.

Every quantitative claim below is reproducible: see `TRACEABILITY_MATRIX.md` for the full mapping of each claim to its supporting notebook cell and output.

---

## Key Findings

- The full-year Sales↑/Profit↑/Margin↓ pattern (2016 vs 2017) is confirmed. It does **not** describe the Q4-2016-vs-Q4-2017 quarter used as the baseline for the analysis below — within that specific quarter, Profit **declined** alongside Sales↑ and Margin↓.
- Revenue growth alone would have increased profit on a full-year basis; the margin decline is associated with a drop in margin rate, not with weaker sales.
- Product category mix is **not associated** with the decline — the mix shift moved in a margin-favorable direction (+0.08pp Mix Effect).
- Regional mix shift made a measurable negative contribution to margin (-2.08pp Mix Effect), separate from the within-region rate effect described below.
- A small cluster of 8–10 high-ticket transactions in the **Binders** sub-category, where average discount rose from 12.5% to 38.0%, accounts for 96.6% of the Binders-level profit decline. Given the small transaction count, this finding should be read as a concentrated cluster effect, not a broad category trend.
- The **Central region** recorded the largest margin deterioration of any region (-33.3pp) and the largest revenue-share decline (-12.4pp) between the two periods.
- Central's discount-margin relationship is consistently stronger than other regions' **in Furniture and Office Supplies** specifically; in Technology, Central's average margin was slightly *higher* than other regions. The finding should be scoped to these two categories rather than stated as category-independent.
- A majority of the total profit decline (60.8%) is traceable to a small number of large, deeply discounted transactions rather than a broad, uniform trend.
- The apparent margin decline in the Corporate customer segment is not consistent across checks — 54.1% of it disappears once known large-transaction outliers are excluded.
- A consistent relationship between discount depth and margin was observed at the individual transaction (line-item) level; this relationship weakens when data is aggregated to the order level.

---

## Business Recommendations

**High Priority**
- Review the regional pricing and discount approval process for the Central region, focused on Furniture and Office Supplies specifically — the discount-margin relationship was not observed in Technology.
- Review discount governance for the identified high-ticket product cluster in the Binders sub-category (8–10 transactions; small sample, high dollar impact).
- Review the approval workflow for large, deeply discounted transactions across the business.

**Medium Priority**
- Review overall discount policy direction; the data does not support a specific discount-reduction target.
- Begin collecting cost and freight data to enable future analysis to distinguish discount effects from cost effects.

**Not Recommended**
- Do not prioritize category-level product mix rebalancing — it is not associated with the margin decline.
- Treat the Customer Segment finding as exploratory only; monitor rather than act, pending additional data.

---

## Repository Structure

```
├── data/                      # Raw and processed dataset files
├── notebooks/
│   ├── 01_EDA.ipynb                     # Dataset structure, quality, schema
│   ├── 02_Root_Cause_Analysis.ipynb     # Hypothesis testing, driver decomposition
│   └── 03_Validation.ipynb              # Robustness checks, cross-view consistency
├── dashboard/                 # Power BI dashboard file
├── images/                    # Dashboard screenshots and visual assets
├── TRACEABILITY_MATRIX.md     # Maps every README claim to its notebook source
└── README.md                  # Project documentation
```

---

## Technologies

| Category | Tools |
|---|---|
| Data Analysis | Python (pandas, statsmodels) |
| Data Source | Microsoft Excel |
| Visualization | Microsoft Power BI, DAX |

---

## Limitations

- The dataset does not include Cost, COGS, or Freight data, so findings reflect observed pricing and discounting patterns, not confirmed financial cause and effect.
- The Binders high-ticket cluster is based on 8–10 transactions — a small sample. The direction and magnitude of this finding should be treated with corresponding caution.
- The Binders sub-category finding is less consistent when transactions are aggregated at the order level rather than the line-item level.
- The Central region finding holds in 2 of 3 product categories (Furniture, Office Supplies) and does not hold in Technology; it should not be read as a category-independent effect.
- The dataset does not include store-level detail, limiting how precisely the regional finding can be localized beyond city and state.
- The Binders cluster, Central region, and large-transaction findings overlap partially and could not be fully separated from one another.
- A meaningful portion of the total profit decline remains unexplained by the drivers identified in this analysis.
- The dataset does not include customer contract or pricing-agreement data, limiting the ability to confirm the customer segment finding.

---

## Contact

*[Name]Tràn Văn Thành Chương* 

*[Email] tranchuong06101997@gmail.com*

*[LinkedIn]*

*[Portfolio link] *
