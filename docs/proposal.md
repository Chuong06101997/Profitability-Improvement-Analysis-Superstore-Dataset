# Project Proposal

## 1. Project Context

A retail business selling across multiple product categories, customer segments, and geographic regions has observed a quarterly profitability pattern worth investigating: top-line indicators (Sales, Profit) can move favorably while Profit Margin — the ratio reflecting underlying pricing and discounting efficiency — moves unfavorably in the same period. Profit Margin provides a complementary view of profitability beyond absolute Sales and Profit, helping identify situations where revenue or profit growth may coexist with weaker profitability efficiency.

Before any pricing, promotion, or product-mix decision is made in response to this pattern, the business needs to understand whether the decline is broad-based across the entire business, or concentrated in specific products, regions, customer segments, or transactions. These two scenarios call for very different management responses, and acting on the wrong assumption risks reinforcing the underlying issue rather than resolving it.

## 2. Business Problem

Management has flagged a period in which Profit Margin appears to move against the trend suggested by Sales and Profit. The business problem, as an investigation, is:

> Is the observed margin movement real, and if so, what — if anything — explains it, at a level of confidence sufficient to justify a business action?

At this stage, the cause is unknown. It is not yet established whether the movement reflects a genuine structural issue, a temporary or narrow effect, or an artifact of how the comparison period is defined. The investigation is scoped to determine this before any recommendation is made.

## 3. Analytical Objective

This analysis is intended to:

- Establish and verify the profitability baseline (Revenue, Profit, Margin) and confirm whether the reported pattern is reproducible in the underlying transaction data, and over what specific comparison period.
- Identify where — by product category, sub-category, region, and customer segment — any margin decline is concentrated, as opposed to being uniformly distributed across the business.
- Investigate potential contributing factors (pricing, discount behavior, product mix, geographic mix, customer mix, and transaction-level concentration) as candidate explanations, without assuming any one factor in advance.
- Determine which findings are sufficiently supported by the data — and which are not — to distinguish evidence strong enough to act on from findings that are exploratory or require further data.

## 4. Key Analytical Questions

1. How did profitability (Revenue, Profit, Margin) actually change between the relevant comparison periods, and is the reported pattern reproducible in the data?
2. Is any margin decline broad-based across the business, or concentrated in specific regions, product categories/sub-categories, or transactions?
3. Which contributors, if any, account for a disproportionate share of the decline relative to their size?
4. What role does discount behavior appear to play, and does its relationship with margin hold consistently across different segments of the business?
5. Are apparent contributing factors robust once outlier or highly concentrated transactions are accounted for, or do they depend heavily on a small number of transactions?
6. Which findings are strong enough, in terms of evidence and robustness, to support a business recommendation — and which should be treated as exploratory only?
7. Where does the available data fall short of what is needed to fully explain the observed pattern, and what additional data would be required before further action?

## 5. Scope

- **Data source:** order-level transaction data for a U.S. retail business, covering Order, Customer, Product (Category / Sub-Category), Region, and Customer Segment attributes, as documented in the project's dataset overview.
- **Analysis period:** transaction data spanning January 2014 – December 2017.
- **Full-year observation:** an initial check of the reported profitability pattern will be made on a full-year (year-over-year) basis, to confirm whether the pattern holds at that level of aggregation.
- **Root-cause comparison window:** where the full-year check identifies a specific period driving the pattern, that period will become the defined baseline for all subsequent root-cause investigation (Steps 2–6). Full-year observations and the narrower root-cause comparison window will be explicitly distinguished throughout the analysis and are not treated as interchangeable.
- **Dimensions to be investigated:** product category and sub-category, geographic region, customer segment, discount depth and frequency, and transaction-level concentration (including outlier transactions).
- **Out of scope at proposal stage:** any business factor for which the dataset does not contain a corresponding field (to be formally assessed and documented during the analysis, not assumed here).

## 6. Analytical Methodology

### Step 1 — Establish Baseline
Verify Revenue, Profit, and Margin over time and confirm whether the reported profitability pattern is reproducible in the data, identifying the exact comparison period it holds over.

### Step 2 — Localize the Decline
Drill down by product category/sub-category, region, and customer segment to determine where any change in profitability is concentrated, rather than assuming it is evenly distributed.

### Step 3 — Investigate Concentration
Identify whether specific products, regions, or transaction clusters contribute disproportionately to the observed change, relative to their overall size in the business.

### Step 4 — Outlier Analysis
Assess whether a small number of extreme, high-value, or heavily discounted transactions materially affect the observed result, and whether findings hold when such transactions are excluded.

### Step 5 — Discount Analysis
Evaluate discount depth and frequency, and their observed relationship with profitability, including whether this relationship is consistent across product categories, regions, and transaction sizes, or concentrated in specific segments of the business.

### Step 6 — Recommendation Assessment
Separate findings into evidence-strength tiers and determine which are supported strongly enough to justify a business recommendation, which require further validation, and which should not be prioritized based on current evidence.

## 7. Expected Outputs

- Analytical notebooks documenting each stage of the investigation, from data quality assessment through root-cause analysis and validation.
- A set of root-cause findings, each stated with its corresponding evidence strength.
- A recommendation framework that translates supported findings into prioritized business actions.
- A Power BI dashboard summarizing findings and recommendations for a business audience.
- Project documentation (README and supporting materials) describing the investigation and its conclusions.

This proposal does not claim or guarantee any specific financial improvement; expected outputs are analytical deliverables, not projected business outcomes.

## 8. Decision Framework

Findings will be translated into recommendations using an evidence-strength tiering approach:

- **High Priority** — findings supported by consistent evidence across multiple checks, with a clear, actionable business action.
- **Medium** — findings that are directionally supported but do not justify a specific, quantified action without further validation.
- **Not Recommended / Monitor** — findings where current evidence does not justify prioritizing an action. This does not mean the underlying business issue can never matter — it means the evidence available at this stage does not support treating it as a priority, and it should be revisited if additional data becomes available or the pattern persists.

## 9. Data & Analytical Limitations

The following limitations are anticipated based on the dataset as documented and are expected to shape what the analysis can and cannot conclude:

- The transaction data provides order- and product-level context but limited detail beyond what is captured in the dataset's fields (e.g., no store-level identifier).
- Cost, COGS, and freight information is not expected to be present in the dataset; where relevant, findings will describe observed pricing and discounting patterns rather than confirmed financial cause and effect.
- Where a finding is driven by a small cluster of transactions, this will be explicitly noted rather than generalized to a broader trend.
- Some contributing factors may overlap (e.g., a discount effect concentrated in a specific region or product cluster), and the analysis may not be able to fully separate their individual contributions.
- Some portion of any observed decline may remain unexplained by the factors investigated, given the scope of available data.

## 10. Success Criteria

This project will be considered successful if it:

- Establishes a defensible, reproducible profitability baseline and confirms the exact period the reported pattern holds over.
- Identifies concentrated contributors to any decline where the evidence supports doing so, rather than defaulting to broad or uniform explanations.
- Clearly distinguishes findings backed by strong, robust evidence from those that are exploratory or weakly supported.
- Produces business recommendations that are appropriately qualified by their evidence strength, rather than overstated relative to what the data supports.
- Clearly communicates the limitations of the dataset and the analysis, including any business questions that cannot be answered with the available data.
