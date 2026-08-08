# Assumption Register

## 1. Purpose

This register documents the assumptions, analytical premises, methodological
choices, and unresolved conditions that materially affect the validity,
scope, or interpretation of the profitability analysis.

The register preserves the project's internal analytical traceability
structure from **Phase 0 through Phase 9**.

The high-level `proposal.md` uses **Step 1–Step 6** as a simplified
planning structure. These Steps are not a replacement for the internal
Phase 0–Phase 9 analytical traceability structure.

The purpose of this register is not to create additional findings, but to
make explicit what the analysis assumes, what has been validated, what is
only valid under bounded conditions, and what remains unresolved because
the available data cannot establish it.

---

## 2. Status Definitions

| Status | Meaning |
|---|---|
| **Validated** | Supported by a direct data check, recomputation, robustness test, or cross-view comparison in the project evidence. |
| **Partially Validated** | The underlying finding is supported, but only under specific bounded conditions or with material interpretive limitations. |
| **Unresolved** | The assumption or claim cannot be fully confirmed from the currently available evidence. |
| **Rejected / Superseded** | An earlier premise or interpretation was tested and contradicted by the evidence and should no longer be used as the project's active interpretation. |

A finding may be numerically verified while its broader interpretation remains
only partially validated. These two dimensions should not be conflated.

---

## 3. Assumption Register

| ID | Assumption / Analytical Premise | Why It Matters | Validation / Evidence | Status | Scope / Caveat |
|---|---|---|---|---|---|
| **A-01** | Some Product IDs may map to multiple Product Names, creating potential SKU-level identity ambiguity. | Product-level aggregation and interpretation may be affected if a Product ID does not uniquely identify a product name. | An earlier project artifact reports **3.37% of records / 32 Product IDs** as affected. However, the original computation producing these figures is not traceable in the currently available analytical notebooks. | **Unresolved** | Do not treat the 3.37% / 32-ID figure as fully validated until its original computation is recovered. |
| **A-02** | Repeated `Order ID + Product ID` combinations may represent legitimate repeated line items rather than automatically being duplicate records. | Removing them without establishing their business meaning could incorrectly delete valid transactions and alter profitability results. | Notebook 01 identifies **16 rows** sharing an identical `(Order ID, Product ID)` combination. | **Validated** | The existence of repeated combinations is validated; their business meaning is not independently established. |
| **A-03** | The transaction dataset is suitable for profitability pattern analysis at the available order/line-item level. | The project depends on the dataset containing sufficient Sales, Profit, Margin, Product, Region, Segment, and Discount information to investigate the observed pattern. | Data structure and baseline analysis support the intended profitability and drill-down analysis. | **Validated** | Conclusions remain limited to variables actually available in the dataset. |
| **A-04** | The dataset does not provide sufficient cost-side information to establish full financial causation. | Without Cost, COGS, and Freight information, observed discount/profit relationships cannot be converted into confirmed cost or margin causation. | The available dataset does not contain the required cost-side fields. | **Unresolved** | Additional Cost/COGS/Freight data would be required to separate pricing, discount, and cost effects. |
| **A-05** | Full-year profitability and the narrower Q4 root-cause comparison represent different analytical scopes. | Mixing the two scopes could produce an internally inconsistent narrative. | Full-year 2016 vs 2017 establishes the initial profitability pattern; Q4-2016 vs Q4-2017 is used as the root-cause baseline. | **Validated** | Full-year and Q4 findings must not be treated as interchangeable. |
| **A-06** | Q4-2016 vs Q4-2017 is the appropriate root-cause comparison window for the observed decline. | All subsequent root-cause findings depend on using a consistent comparison baseline. | Q4 Profit declines from approximately **$38.1K to $27.4K**, identifying the specific period used for the root-cause investigation. | **Validated** | This is the root-cause baseline, not a replacement for the full-year 2016 vs 2017 observation. |
| **A-07** | Findings observed at line-item level do not automatically transfer to order-level analysis. | Aggregation can materially change the strength and direction of observed relationships. | The project explicitly tests aggregation-level sensitivity and identifies weaker consistency at order level for relevant findings. | **Partially Validated** | Line-item relationships should not be generalized to order-level conclusions without separate validation. |
| **A-08** | The Central-region margin deterioration is concentrated in Furniture and Office Supplies rather than applying uniformly across all categories. | A region-wide recommendation without category qualification would overgeneralize the evidence. | Central shows the largest margin deterioration, with the effect observed in **2 of 3 product categories: Furniture and Office Supplies**. The same effect is not observed in Technology. | **Validated** | The finding is category-bounded and must not be presented as a Technology or business-wide Central effect. |
| **A-09** | The Binders decline is driven disproportionately by a small high-ticket transaction cluster. | A small cluster can materially affect the aggregate result without representing a broad category-wide trend. | The identified Binders cluster contains approximately **8–10 transactions** and accounts for approximately **96.6% of the Binders-level profit decline**. | **Partially Validated** | The numerical contribution is supported, but the small transaction count limits generalization. It is a concentrated cluster finding, not evidence of a broad Binders trend. |
| **A-10** | The Corporate segment finding is sensitive to outlier treatment. | A finding that materially changes after outlier exclusion should not be treated as a stable independent driver. | The project reports that **54.1% of the apparent Corporate decline disappears when known large-transaction outliers are excluded**. | **Partially Validated** | This is a fragility/robustness finding, not evidence that Corporate is a confirmed causal driver. |
| **A-11** | Binders, Central, and outlier findings represent overlapping analytical lenses rather than independent additive contributions. | Adding their percentages together could double-count the same underlying transactions and falsely imply a complete decomposition of the decline. | The project explicitly identifies overlap between the transaction, product/sub-category, and regional lenses. | **Validated** | Contribution percentages must not be summed as though they were mutually exclusive components. |
| **A-12** | Category mix rebalancing is not sufficiently supported as a driver of the observed decline. | Acting on product-mix composition without evidence could redirect attention away from the concentrated transaction and regional findings. | Category-mix analysis does not support a meaningful category-mix explanation for the observed decline; the measured mix effect is approximately **+0.08 pp**. | **Validated** | Category mix is treated as Not Recommended based on current evidence, not as permanently irrelevant to the business. |
| **A-13** | The absence of Store-level identifiers limits geographic interpretation. | Region-level findings cannot automatically be translated into store-level operational conclusions. | The dataset provides geographic attributes such as Region/State/City but does not provide a Store-level identifier. | **Unresolved** | Additional store-level data would be required for store-specific diagnosis or action. |
| **A-14** | A meaningful portion of the observed decline remains unexplained by the identified contributors. | The analysis should not imply that the identified Binders, Central, outlier, or discount findings fully decompose the decline. | The project identifies overlapping contributors and explicitly retains an unexplained residual. | **Unresolved** | Further investigation and additional data are required to explain the remaining portion of the decline. |

---

## 4. Critical Unresolved Assumptions

### A-01 — Product ID ambiguity provenance

An earlier project artifact reports that approximately **3.37% of records**
and **32 Product IDs** involve Product ID → Product Name ambiguity.

However, the original calculation cannot currently be traced to the available
analytical notebooks.

Therefore:

- The existence of the historical claim is documented.
- The numerical value is **not treated as fully validated**.
- The figure should not be used as a verified quantitative data-quality KPI
  until the original calculation or source artifact is recovered.

### A-04 — Missing Cost / COGS / Freight data

The dataset does not contain sufficient cost-side information to determine
whether observed profitability changes are caused by:

- discounting,
- underlying product cost,
- freight,
- COGS,
- or another cost-side mechanism.

Therefore the analysis can identify observed relationships and concentrations,
but cannot establish complete financial causation.

Additional cost-side data would be required for a stronger causal assessment.

### A-07 — Aggregation-level sensitivity

Some relationships observed at the line-item level weaken when aggregated to
the order level.

Therefore:

- line-item evidence should remain line-item scoped;
- order-level conclusions require separate validation;
- aggregation should not be treated as a purely technical transformation
  with no analytical consequence.

### A-14 — Unexplained residual

The identified contributors do not constitute a mutually exclusive,
complete decomposition of the total decline.

The project therefore retains an unexplained residual rather than assigning
it to an unsupported cause.

Additional data and further investigation would be required to explain the
remaining portion.

---

## 5. Implications for Interpretation

The following rules should be applied when interpreting the project's
findings.

### 5.1 Association is not causation

Observed relationships between discounting and profitability describe
patterns in the available data.

They do not establish that discounting alone caused the observed financial
decline.

The absence of Cost, COGS, and Freight data is a material limitation.

### 5.2 Binders is a bounded concentration finding

The Binders result is driven by a small high-ticket cluster of approximately
8–10 transactions.

The **96.6%** figure therefore describes the contribution of that identified
cluster to the Binders-level decline.

It should not be interpreted as evidence that the entire Binders sub-category
experienced a uniform structural deterioration.

### 5.3 Central is a category-bounded regional finding

The Central-region margin deterioration is concentrated in:

- Furniture
- Office Supplies

The same pattern is not observed in Technology.

Therefore the finding should not be generalized to all Central-region
transactions or all product categories.

### 5.4 Corporate is a fragility finding

The **54.1%** Corporate result reflects sensitivity to the removal of known
large-transaction outliers.

It should therefore be described as a robustness/fragility finding rather
than a confirmed independent driver.

### 5.5 Contribution percentages are not additive

The Binders, Central, and outlier findings overlap.

Their percentages must not be added together to produce a claimed total
share of the decline.

The same underlying transactions can appear through multiple analytical
lenses.

### 5.6 Category mix is not currently supported as a priority driver

The category-mix analysis does not provide sufficient evidence to justify
category-level product-mix rebalancing as a response to the observed decline.

This is an evidence-based prioritization decision, not a claim that product
mix can never affect profitability.

### 5.7 Full-year and Q4 findings are different scopes

The project begins with the full-year 2016 vs 2017 profitability pattern.

The root-cause investigation then uses Q4-2016 vs Q4-2017 as the defined
comparison window.

These scopes must remain explicitly separated in the README, dashboard,
proposal, notebooks, and supporting documentation.

### 5.8 Missing cost-side data limits causal interpretation

The project can identify:

- where the decline is concentrated;
- which transactions or groups contribute disproportionately;
- observed discount and margin relationships;
- robustness and sensitivity of findings.

It cannot fully determine the underlying financial cause without cost-side
data.

### 5.9 The analysis does not explain 100% of the decline

The project intentionally retains an unexplained residual.

This is a limitation of the available evidence, not an analytical failure.

A stronger conclusion would require additional variables and/or further
investigation.

---

## 6. Phase Traceability

The assumption register should be interpreted alongside the project's
internal Phase 0–Phase 9 analytical structure.

The high-level proposal's Step 1–Step 6 terminology is intentionally
different and should not be used to relabel the internal analytical phases.

| Internal Phase | Relevant Assumption / Interpretation |
|---|---|
| **Phase 0** | Initial assumptions, data-quality premises, and evidence constraints are recorded and tested rather than automatically accepted. |
| **Phase 1** | Baseline profitability and comparison-period assumptions are established and verified. |
| **Phase 2** | Product, region, and segment localization assumptions are tested. |
| **Phase 3** | Concentration and disproportionate-contribution assumptions are investigated. |
| **Phase 4** | Outlier influence and robustness assumptions are evaluated. |
| **Phase 5** | Discount depth/frequency relationships are evaluated without assuming causality. |
| **Phase 6** | Evidence strength is assessed before converting findings into recommendations. |
| **Phase 7** | Overlap between analytical lenses is explicitly considered to avoid double-counting. |
| **Phase 8** | Remaining evidence gaps and interpretation limitations are preserved. |
| **Phase 9** | Final validation and consistency checks determine which claims can remain in the final analytical narrative. |

---

## 7. Documentation Rule

Any future change to a material assumption should be reflected consistently
across the relevant project documentation.

In particular:

- A validated numerical claim should have traceable evidence.
- A bounded finding should retain its qualifier wherever it is presented.
- An unresolved assumption should not silently become a validated claim.
- A rejected or superseded interpretation should not reappear in later
  documentation as though it were still active.
- Phase 0–Phase 9 terminology should remain reserved for the project's
  internal analytical traceability.
- Step 1–Step 6 terminology should remain reserved for the high-level
  proposal structure.

The purpose of this register is to preserve analytical discipline and
traceability, not to imply a level of certainty greater than the available
evidence supports.
