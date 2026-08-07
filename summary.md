# Project Summary

## 1. Project Summary

This project investigates a retail business's profitability pattern: on a full-year basis (2016 vs 2017), Sales and Profit both increased while Profit Margin declined. The analytical objective was to determine whether this decline was broad-based or concentrated, and to identify which contributing factors were sufficiently supported by evidence to inform a business recommendation. The approach combined baseline verification, drill-down by business dimension, outlier and robustness testing, and evidence-tiered recommendations. The main takeaway: the decline is not broad or uniform — it is concentrated in a small transaction cluster, one product sub-category, and one region, and roughly a third of the total decline remains unexplained by the drivers identified.

## 2. Business Problem

Management observed that Sales and Profit growth (full-year, 2016 vs 2017) was accompanied by a decline in Profit Margin — the metric reflecting underlying pricing and discounting efficiency. Aggregate Sales and Profit figures alone did not explain this divergence, and acting on top-line growth without understanding the margin movement risked reinforcing whatever was actually driving it. The pattern required deeper investigation to determine where it originated and whether it reflected a structural issue or a narrow, isolated effect.

## 3. Analytical Question

Two distinct analytical scopes are addressed, and are not interchangeable:

- **Full-year pattern:** Did Sales, Profit, and Margin move in different directions between 2016 and 2017?
- **Root-cause investigation:** Within the specific quarter that drove this pattern (Q4-2016 vs Q4-2017), what explains the margin decline? Within this quarter specifically, Profit itself declined ($38.1K → $27.4K) alongside Margin — a different pattern from the full-year Sales↑/Profit↑/Margin↓ framing that motivated the investigation.

## 4. Analytical Approach

1. Established the full-year profitability pattern.
2. Identified the period where the decline was concentrated.
3. Compared Q4-2016 vs Q4-2017 as the root-cause baseline.
4. Drilled down by product category/sub-category, region, and customer segment.
5. Investigated concentrated contributors relative to their size in the business.
6. Investigated outliers and transaction concentration.
7. Evaluated discount depth and frequency against profitability.
8. Assessed the robustness of apparent findings (outlier exclusion, aggregation level, within-category checks).
9. Translated sufficiently supported findings into prioritized recommendations.

## 5. Key Findings

- **Q4 profit: $38.1K → $27.4K.** Within the Q4-2016 vs Q4-2017 root-cause baseline, Profit declined alongside Margin — distinct from the full-year trend where Profit increased.
- **Binders Share: 96.6%.** A small high-ticket transaction cluster (approximately 8–10 transactions) in the Binders sub-category accounts for 96.6% of the Binders-level profit decline. Given the small transaction count, this is a concentrated cluster effect, not evidence of a broad category-wide trend.
- **Central Margin: -33.3 pp.** The Central region recorded the largest margin deterioration of any region. This effect is concentrated in Furniture and Office Supplies specifically — it was not observed in Technology, where Central's average margin was slightly higher than other regions.
- **Outlier Share: 60.8%.** A majority of the total profit decline traces to a small number of large, deeply discounted transactions rather than a broad, uniform pattern.
- **Corporate Risk: 54.1%.** This is a robustness/fragility finding, not a confirmed driver: 54.1% of the apparent Corporate segment margin decline disappears once known large-transaction outliers are excluded, indicating the original finding is not consistent across checks.
- **Discount Depth: +1.19 pp.** Average discount increased by 1.19 percentage points within the Q4 baseline — a modest average-level change, distinct from the much sharper discount increase (12.5% → 38.0%) observed specifically within the Binders high-ticket cluster.

## 6. Root-Cause Interpretation

The evidence supports:
- **Concentration:** the decline is disproportionately attributable to a small transaction cluster, one sub-category, and one region, not spread evenly across the business.
- **Association:** discount depth is associated with lower margin at the individual transaction level; this association weakens when data is aggregated to the order level.
- **Contributing factors, appropriately scoped:** the Binders cluster and Central region findings are contributing factors within specific, bounded conditions (a small transaction group; two of three product categories) — not category- or business-wide effects.
- **Robustness/sensitivity:** the Corporate segment finding is sensitive to outlier exclusion and should be treated as fragile rather than reliable.

The evidence does **not** support a single, confirmed causal mechanism. The dataset lacks cost, COGS, and freight data, so findings describe observed pricing and discounting patterns rather than confirmed financial cause and effect. A meaningful portion of the total decline remains unexplained by the drivers identified.

## 7. Recommendations

**High Priority**
- Review discount governance for the identified high-ticket cluster in the Binders sub-category.
- Review the regional pricing and discount approval process for the Central region, focused on Furniture and Office Supplies.
- Review the approval workflow for large, deeply discounted transactions.

**Medium**
- Review overall discount policy direction (no specific reduction target is supported by current evidence).
- Begin collecting cost and freight data to distinguish discount effects from cost effects in future analysis.

**Not Recommended**
- Category-level product mix rebalancing — not associated with the margin decline.

**Exploratory / Monitor only:** The Customer Segment finding (Corporate) is noted as fragile and is treated as an exploratory monitoring point in the underlying analysis — it is not one of the six prioritized recommendation items above.

## 8. Limitations

- The Binders high-ticket cluster finding is based on a small sample (approximately 8–10 transactions); direction and magnitude should be treated with corresponding caution.
- The Binders finding is less consistent when aggregated at the order level versus the line-item level.
- The Central region finding holds in Furniture and Office Supplies specifically and does not hold in Technology.
- No cost, COGS, or freight data exists in the dataset — findings reflect observed patterns, not confirmed financial causes.
- The Binders cluster, Central region, and large-transaction findings overlap partially and could not be fully separated.
- A meaningful portion of the total profit decline remains unexplained by the drivers identified.
- The full-year profitability pattern and the Q4 root-cause baseline are distinct analytical scopes and should not be conflated.

## 9. Business Value

This project demonstrates structured problem framing under ambiguity, systematic drill-down and concentration analysis, robustness and sensitivity testing before treating a finding as reliable, and the ability to distinguish signal from noise (e.g., separating a small fragile finding from a robust one). It shows evidence-based prioritization — translating findings into recommendations proportional to their evidence strength, including explicit "not recommended" and "monitor only" categories — and clear communication of uncertainty and data limitations to a non-technical audience.

This project demonstrates analytical decision support. It does not claim that recommendations were implemented or that any financial outcome was realized.

## 10. Tools

| Category | Tools |
|---|---|
| Data Analysis | Python (pandas, statsmodels) |
| Data Source | Microsoft Excel |
| Visualization | Microsoft Power BI, DAX |
