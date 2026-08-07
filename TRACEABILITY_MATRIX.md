# Traceability Matrix

Maps every quantitative and business claim in `README.md` to the notebook section, output table, and reproduction status that supports it. This matrix is the evidence map connecting the README, the notebooks, and the Power BI dashboard.

| # | README Claim | Notebook | Section | Output | Status |
|---|---|---|---|---|---|
| 1 | Dataset: 9,994 rows, 21 columns, one row per order line item | `01_EDA.ipynb` | 1. Data Loading & Schema | `df.shape`, unique Order ID count | Reproduced |
| 2 | No missing values; no invalid Sales/Quantity/Discount values | `01_EDA.ipynb` | 2. Data Quality Assessment | Missing-value table, invalid-value checks | Reproduced |
| 3 | Time period: January 2014 – December 2017 | `01_EDA.ipynb` | 3. Time Coverage | Order Date min/max | Reproduced |
| 4 | 3 Categories, 4 Regions, 3 Segments, United States only | `01_EDA.ipynb` | 8. Entity Overview | Unique-value printout | Reproduced |
| 5 | Sales↑, Profit↑, Margin↓ pattern (full-year framing) | `02_Root_Cause_Analysis.ipynb` | 1. Q4-2016 vs Q4-2017 Comparison | `yearly` table | Reproduced (full-year basis) |
| 6 | Pattern holds only for Q4-2016 vs Q4-2017, not the full 2014–2017 trend | `02_Root_Cause_Analysis.ipynb` | 1. Q4-2016 vs Q4-2017 Comparison | `full_trend` table | Reproduced |
| 7 | Within the Q4-specific baseline used for the rest of the analysis, Profit does not increase (it decreases) | `02_Root_Cause_Analysis.ipynb` | 1. Q4-2016 vs Q4-2017 Comparison | `comparison` table + discrepancy note | **Discrepancy — reported, not corrected.** See note below. |
| 8 | Revenue growth alone would have increased profit; the decline is attributable to margin-rate deterioration | `02_Root_Cause_Analysis.ipynb` | 2. Revenue Effect vs Margin-Rate Effect | `bridge` table | Reproduced |
| 9 | Category-level product mix is not associated with the decline (moved in a margin-favorable direction) | `02_Root_Cause_Analysis.ipynb` | 3. Category Mix Analysis | `category_bridge` table (Mix Effect = +0.08pp) | Reproduced |
| 10 | Region revenue-share mix made a measurable negative contribution to margin | `02_Root_Cause_Analysis.ipynb` | 4. Region Mix Analysis | `region_bridge` table (Mix Effect = −2.08pp) | Reproduced |
| 11 | Binders sub-category accounts for the majority of the sub-category-level profit decline | `02_Root_Cause_Analysis.ipynb` | 5. Binders Analysis | `subcat_delta` table | Reproduced |
| 12 | A small cluster of high-ticket transactions drives the Binders decline; discount depth rose sharply on this cluster | `02_Root_Cause_Analysis.ipynb` | 6. High-Ticket Transaction Analysis | `binders_cluster` table (96.6% of Binders decline; discount 12.5%→38.0%) | Reproduced |
| 13 | Discount depth increased between the two periods; higher discount is associated with lower margin | `02_Root_Cause_Analysis.ipynb` | 7. Discount Analysis | `discount_margin_table` | Reproduced |
| 14 | Central region shows the largest margin deterioration among all four regions | `02_Root_Cause_Analysis.ipynb` | 8. Central Region Analysis | `central_summary` table | Reproduced |
| 15 | A majority of the total profit decline traces to a small number of large, deeply discounted transactions | `02_Root_Cause_Analysis.ipynb` | 9. Outlier Contribution | `outlier_table` (majority share) | Reproduced |
| 16 | The Corporate segment margin decline is not consistent — most disappears once outlier transactions are excluded | `02_Root_Cause_Analysis.ipynb` | 10. Customer Segment Investigation | `segment_table` (54.1% attributable to outliers) | Reproduced |
| 17 | Binders decline persists (direction) after removing known outlier transactions | `03_Validation.ipynb` | Validation 1 — Outlier Sensitivity | `validation_1` table | Reproduced |
| 18 | Binders discount-margin relationship is fragile at order-level aggregation, robust at line-item level | `03_Validation.ipynb` | Validation 2 — Aggregation-Level Comparison | `validation_2` table | Reproduced |
| 19 | Central region effect is not explained by product category composition differences across regions | `03_Validation.ipynb` | Validation 3 — Cross-View Consistency | `region_category_mix` table (max spread 5.0pp) | Reproduced |
| 20 | Corporate segment decline is majority-attributable to outlier transactions | `03_Validation.ipynb` | Validation 4 — Customer Segment Validation | Corporate ProfitDelta gross vs excl. outliers | Reproduced |
| 21 | Binders finding is associated with discount depth, not discount frequency | `03_Validation.ipynb` | Validation 5 — Discount Depth vs Frequency | `validation_5` table | Reproduced |
| 22 | Central region finding "held after accounting for product category" | `03_Validation.ipynb` | Validation 6 — Regional Finding Robustness | `within_category_df` table | **Discrepancy — reported, not corrected.** See note below. |

---

## Discrepancies Identified During Reproduction

Two claims did not fully reproduce as originally worded. Per the traceability requirement, these are reported here rather than silently corrected or replaced with alternative analysis.

### Discrepancy 1 — Profit direction within the Q4-specific baseline (Item 7)

The Executive Summary's "Sales↑ Profit↑ Margin↓" framing holds on a full-year (2016 vs 2017) basis. However, every downstream root-cause finding in this project (Binders, Central region, outlier contribution, etc.) is built on the **Q4-2016 vs Q4-2017** comparison specifically. Within that specific slice, Profit decreases ($38,139.86 → $27,448.73) alongside Margin, while only Sales increases. The README's opening framing should be understood as describing the full-year pattern that motivated the investigation, not the exact quarterly baseline used to explain it.

**Recommended README adjustment:** clarify that the Q4-specific analysis explains a Sales↑/Profit↓/Margin↓ quarter, distinct from the full-year Sales↑/Profit↑/Margin↓ pattern that initially prompted the investigation.

### Discrepancy 2 — Central region effect not uniform across all categories (Item 22)

The Central region shows lower average margin than other regions in Furniture and Office Supplies, but not in Technology (where Central's average margin is slightly higher than other regions). The finding is real and holds in 2 of 3 categories, but does not hold universally "within every category" as a category-blind statement might imply.

**Recommended README adjustment:** qualify the Central region finding as holding in Furniture and Office Supplies specifically, rather than as a category-independent statement.

---

## Summary

- **20 of 22** README claims reproduced without qualification.
- **2 of 22** claims reproduced with a documented nuance that narrows the original wording; both are flagged above rather than corrected, per the project's traceability requirement.
- No claim was found to be entirely unreproducible or unsupported by the dataset.
