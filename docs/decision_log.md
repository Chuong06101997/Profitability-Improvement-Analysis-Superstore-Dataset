# Decision Log

## Purpose

This log records material decisions that affected the analytical scope, methodology, interpretation, recommendations, dashboard design, and documentation architecture of the Margin Decline Root Cause Analysis. It is not a project summary and not a retrospective narrative — its purpose is to preserve why a particular analytical or communication path was chosen, so that later documents (README, dashboard, assumption register, risk register) do not silently drift from decisions already made.

Where a decision's exact date is not recorded in the available project materials, this log states "Date: Not recorded" rather than inventing one. Where a decision emerged progressively across the analysis rather than at a single point, this log states "Timing: Iterative / during analysis."

---

## Decision Register

| ID | Decision | Rationale | Evidence / Basis | Impact | Status |
|---|---|---|---|---|---|
| D-01 | Distinguish the full-year (2016 vs 2017) profitability pattern from the Q4-2016 vs Q4-2017 root-cause baseline; treat the two as non-interchangeable scopes. | The full-year comparison and the Q4-specific comparison show different directions for Profit (up on a full-year basis, down within Q4), so conflating them would misstate what the root-cause analysis explains. | Phase 1 KPI Verification; reconfirmed during Notebook 02 §1 reproduction, where the discrepancy was explicitly logged rather than silently corrected. | All root-cause findings (Binders, Central, outlier contribution, discount relationship) are scoped to the Q4-2016 vs Q4-2017 window, not the full-year trend. | Locked |
| D-02 | Establish Q4-2016 vs Q4-2017 as the root-cause comparison baseline. | This is the specific period over which the reported Sales-up/Margin-down pattern is reproducible in the underlying data. | Phase 1 KPI Verification. | Defines the transaction window used throughout Phase 3–9 analysis. | Locked |
| D-03 | Adopt an evidence-strength discipline: observed association is not confirmed causation; recommendations must be proportional to evidence strength; fragile findings must not be presented as confirmed drivers. | Stated as a governing analytical principle from the start of the project and enforced through explicit language rules at each phase (e.g., prohibition on terms like "confirmed driver," "root cause," "proven" absent sufficient evidence tier). | Phase 0 Analytical Principles; reinforced in Phase 6 (Bias, Robustness & Sensitivity), Phase 7, Phase 8 wording rules. | Shapes the wording of every finding and recommendation across README, dashboard, and notebooks. | Locked |
| D-04 | Describe the Binders finding as a concentrated high-ticket transaction cluster (approximately 8–10 transactions, 96.6% of the Binders-level decline), not as a broad Binders-category effect. | The underlying transactions were traced to a small, identifiable cluster; generalizing this to "Binders" as a whole would overstate what the data supports. | Phase 4 drill-down (Notebook 02 §5–6); Phase 5 interaction analysis; Phase 6 robustness check. | Constrains how the Binders finding may be cited in the README, dashboard, and recommendations — as a cluster-level finding, not a category-wide trend. | Locked |
| D-05 | Scope the Central region finding specifically to Furniture and Office Supplies; explicitly exclude Technology, where the effect was not observed. | A within-category check found Central's margin lower than other regions in two of three categories, but not in Technology (where Central's margin was slightly higher). | Phase 9 / Notebook 03 Validation 6. | The Central region recommendation is scoped to Furniture and Office Supplies in the README and in the Phase 3 dashboard banner/subtitle. | Locked |
| D-06 | Treat the Corporate segment finding as a robustness/fragility result, not a confirmed driver. | A direct test showed that 54.1% of the apparent Corporate segment decline disappears once known large-transaction outliers are excluded, indicating the original finding is not stable across checks. | Phase 6 Finding 6; Notebook 03 Validation 4. | The Corporate finding ("Corporate Risk 54.1%") is presented on the dashboard and in the README as a fragility indicator, not as an independent, confirmed driver, and receives no High-Priority recommendation. | Locked |
| D-07 | Distinguish the overall Q4 average discount-depth change (+1.19 pp) from the substantially sharper discount change observed specifically within the Binders high-ticket cluster (12.5% → 38.0%). | Reporting only the average Q4 figure would understate how concentrated the discount escalation actually was; reporting only the cluster figure would misrepresent it as dataset-wide. | Notebook 02 §6–7. | Both figures are retained and kept clearly separate across the README, dashboard KPI cards, and decision documentation. | Locked |
| D-08 | Treat the Binders cluster, Central region, and outlier-transaction contributions as overlapping, non-additive views of the same total decline, rather than mutually exclusive components. | Some transactions belong simultaneously to more than one of these categories (e.g., a transaction can be both part of the Binders cluster and flagged as a statistical outlier); summing their individual percentage contributions would double-count. | Phase 7 Driver Contribution Analysis, Overlap Explanation. | Percentage/dollar contributions from these three drivers are never presented as summing to 100% of the decline; this is stated explicitly wherever they are reported together. | Locked |
| D-09 | Treat the absence of Cost, COGS, and Freight data as a standing limitation that prevents confirming a complete financial causal mechanism. | The dataset's 21-column schema does not include any cost-related field; without it, no discount-margin relationship in this project can be confirmed as a financial cause rather than an observed pattern. | Phase 0 Data Sufficiency Assessment (schema review). | Every discount-related finding in the README, dashboard, and notebooks is qualified as an observed association, not a confirmed cause. | Locked |
| D-10 | Adopt a three-tier recommendation framework (High Priority / Medium / Not Recommended–Monitor), with tier assignment proportional to evidence strength rather than to business impact size alone. | Ensures that a recommendation's prominence reflects how well-supported it is by the analysis, not merely how large its apparent dollar impact appears. | Phase 8 Business Recommendations. | Structures both the README's Business Recommendations section and the Page 5 dashboard recommendation panel. | Locked |
| D-11 | Reject product category mix shift as a contributor to the margin decline. | A price–volume–mix decomposition found the category-level Mix Effect to be slightly positive, meaning the mix shift moved in a margin-favorable direction — opposite to what a "category mix caused the decline" hypothesis would require. | Phase 7 Driver Contribution Analysis (Category Mix Effect, +0.08pp); Notebook 02 §3. | Category-level mix rebalancing is placed in the "Not Recommended" tier in both the README and the Page 5 dashboard. | Locked |
| D-12 | Rebuild Page 5 of the dashboard from its earlier simulation-oriented design (a discount-cap what-if scenario) into a diagnostic/root-cause summary, discarding the earlier simulation content entirely rather than preserving it for backward compatibility. | The original Page 5 content predated the Phase 0–9 methodology and was never validated through it, unlike the content on the other four pages. | Explicit project instruction during dashboard rebuild: rebuild Page 5 entirely from Phase 0–9 verified outputs; do not preserve unvalidated content. | The final Page 5 dashboard content (5 diagnostic KPI cards, 6 recommendation cards) is fully traceable to Notebook 02 and the README's Business Recommendations, replacing all prior discount-cap simulation figures. | Locked |
| D-13 | Remove the "DiscountCap" slicer from Page 5. | The slicer controlled the discount-cap simulation that was removed under D-12; retaining it would have no function once the simulation content was removed. | Direct consequence of D-12. | Page 5 no longer exposes any simulation control. | Locked |
| D-14 | Use five diagnostic KPI cards on the rebuilt Page 5 (Binders Share, Central Margin, Outlier Share, Corporate Risk, Discount Depth), each paired with a short caption preserving its scope/qualifier, in place of sparkline/MoM formatting used elsewhere on the dashboard. | These five figures were identified as the most decision-relevant, already-verified diagnostic figures from Notebook 02; a caption line was used to carry the qualifier that a sparkline could not. | Notebook 02 §6–10; dashboard implementation and review process. | Establishes the specific figures and captions shown on Page 5; any future change to these five metrics or their captions should be treated as a revision to this decision, not a routine edit. | Locked |
| D-15 | Organize the Page 5 recommendation panel by evidence tier (High Priority / Medium / Not Recommended), using consistent card height and border color coding, rather than sizing cards to fill available space. | Preserves visual proportionality to evidence strength rather than to available layout space; avoids implying that a lower-tier recommendation carries equal analytical weight to a High Priority one. | Dashboard layout validation and implementation review for Page 5. | Fixes the structure of the Page 5 recommendation panel (2 rows of 3 cards); tier-to-column/row assignment should not be altered without revisiting this decision. | Locked |
| D-16 | Distinguish "Steps 1–6" (used in `proposal.md` as a high-level planning structure) from "Phase 0–Phase 9" (the project's detailed internal analytical workflow); do not treat the two as equivalent or attempt to map one onto the other. | `proposal.md` serves a different documentation purpose (pre-analysis planning) than the detailed Phase 0–9 workflow used throughout the actual investigation; conflating the two risks implying a false one-to-one correspondence between planning steps and executed phases. | Explicit instruction during the `proposal.md` revision: rename the proposal's six methodology items from "Phase" to "Step," and preserve Phase 0–9 terminology everywhere else in the project. | `proposal.md` uses Step 1–6 exclusively; all other project documents (notebooks, README, assumption register, this log) retain Phase 0–9 terminology without alteration. | Locked |
| D-17 | Retain the 16 rows sharing an identical (Order ID, Product ID) pair without removal, and do not classify them as confirmed data-entry errors. | Insufficient evidence (no timestamp or line-sequence field) exists to determine whether these rows represent genuine repeat line items or duplicate entries. | Phase 0 data quality assessment (Step 0.4). | These rows remain in the dataset used throughout the analysis; no finding in this project depends on resolving their status, given their small share of total rows (0.16%). | Unresolved |
| D-18 | Treat the Product ID → Product Name ambiguity (32 Product IDs, 3.37% of rows) as a documented, partially validated data-quality caveat rather than a fully resolved or fully unverified item. | The inconsistency was identified during Phase 0 schema review, but the specific check has not been independently reproduced within `01_EDA.ipynb` or itemized in `TRACEABILITY_MATRIX.md`. | Phase 0 data quality assessment (Step 0.4). Source not sufficient to establish this as fully reproduced in the current notebook library — see Consistency Issues below. | Any SKU-level finding touching one of the 32 affected Product IDs should be read with this caveat; no major finding in this project currently depends on one of these specific IDs. | Unresolved |
| D-19 | Update the Page 5 Central recommendation card to explicitly scope the recommendation to Furniture and Office Supplies. | The earlier card version omitted a category qualifier that was required by the underlying finding and by the README. | Direct dashboard revision following consistency review. | Page 5 now states the Central pricing review applies to Furniture and Office Supplies, matching the README wording. | Locked |
| D-20 | Update the Page 5 "Binders Share" KPI caption to include the small-sample qualifier of approximately 8–10 transactions. | The 96.6% figure describes a concentrated transaction cluster and should not be presented without its sample-size context. | Direct dashboard revision following consistency review. | Page 5 now preserves the 8–10 transaction qualifier alongside the 96.6% figure. | Locked |

---

## Detailed Decisions

### D-01 — Distinguish full-year pattern from Q4 root-cause baseline

**Decision:** The full-year (2016 vs 2017) Sales-up/Profit-up/Margin-down pattern and the Q4-2016 vs Q4-2017 root-cause comparison are treated as distinct analytical scopes and are never presented interchangeably.

**Rationale:** Within the Q4-specific window, Profit itself declines ($38,139.86 → $27,448.73) alongside Margin — a different pattern from the full-year framing that initially motivated the investigation. Presenting the two as the same pattern would misstate what the Q4 root-cause findings actually explain.

**Evidence / Basis:** Phase 1 KPI Verification; independently reproduced and explicitly logged as a discrepancy during Notebook 02 §1 (rather than silently reconciled).

**Analytical consequence:** Every subsequent root-cause finding (Phases 3–9) is scoped to the Q4 window; full-year figures are used only for baseline/context purposes (e.g., the Page 1 dashboard KPI row).

**Documentation consequence:** README Executive Summary, Notebook 02 §1, and the Page 1/Page 3 dashboard content must remain consistent with this distinction; any future edit that blurs the two scopes should be treated as a regression.

**Status:** Locked

---

### D-02 — Q4-2016 vs Q4-2017 as root-cause baseline

**Decision:** Q4-2016 vs Q4-2017 is adopted as the fixed comparison window for all root-cause investigation.

**Rationale:** This is the period identified, during baseline verification, as the one over which the reported profitability pattern actually reproduces.

**Evidence / Basis:** Phase 1 KPI Verification.

**Analytical consequence:** All downstream figures (Binders, Central, outlier share, discount depth) are computed within this window and are not directly comparable to full-year or other-quarter figures without re-stating scope.

**Documentation consequence:** Notebook 02, README, and dashboard Pages 2–5 must state this baseline wherever a root-cause figure is presented.

**Status:** Locked

---

### D-03 — Evidence-strength discipline

**Decision:** The project adopts, as a governing rule, that observed association does not constitute confirmed causation, that recommendations must be proportional to evidence strength, and that fragile findings must not be described as confirmed drivers.

**Rationale:** Without this discipline, concentrated or statistically suggestive patterns risk being overstated as confirmed business causes, particularly given the absence of cost data (see D-09).

**Evidence / Basis:** Phase 0 Analytical Principles; explicit wording restrictions applied from Phase 6 onward (e.g., disallowing "confirmed," "proven," "root cause," "true driver" absent sufficient evidence).

**Analytical consequence:** Findings are consistently reported with qualifiers (e.g., "associated with," "concentrated in," "fragile") rather than unqualified causal language.

**Documentation consequence:** README, summary.md, proposal.md, this decision log, and the dashboard must all conform to this language discipline.

**Status:** Locked

---

### D-04 — Binders finding scoped to a concentrated cluster

**Decision:** The Binders finding is documented as a concentrated cluster of approximately 8–10 high-ticket transactions accounting for 96.6% of the Binders-level profit decline — not as a broad, category-wide Binders effect.

**Rationale:** The magnitude of the decline traces almost entirely to a small, identifiable transaction group; describing it as a general Binders trend would misrepresent the underlying concentration.

**Evidence / Basis:** Phase 4 drill-down (Notebook 02 §5–6); confirmed via Phase 5 interaction analysis and Phase 6 robustness testing (fragile at order-level aggregation, robust at line-item level).

**Analytical consequence:** The finding is not generalized to other Binders transactions outside the identified cluster.

**Documentation consequence:** README, Notebook 02, and the Page 2/Page 5 dashboard content must retain the "8–10 transactions" / small-sample qualifier wherever the 96.6% figure appears.

**Status:** Locked

---

### D-05 — Central region finding scoped to Furniture and Office Supplies

**Decision:** The Central region discount-margin finding is scoped specifically to Furniture and Office Supplies; it is explicitly not extended to Technology.

**Rationale:** A within-category check found Central's margin lower than other regions in Furniture and Office Supplies, but not in Technology, where Central's average margin was slightly higher than other regions.

**Evidence / Basis:** Phase 9 / Notebook 03 Validation 6.

**Analytical consequence:** The Central region recommendation and finding are not presented as applying uniformly across all product categories.

**Documentation consequence:** README, Notebook 03, and the Page 3 dashboard banner/subtitle carry this qualifier explicitly. (Note: the Page 5 recommendation card for Central region pricing does not currently restate this category scope — see Consistency Issues.)

**Status:** Locked

---

### D-06 — Corporate segment treated as fragility finding

**Decision:** The Corporate segment finding is documented as a robustness/fragility result, not as a confirmed, independent driver of the margin decline.

**Rationale:** 54.1% of the apparent Corporate segment decline disappears once known large-transaction outliers are excluded, indicating the original observation is not stable across checks.

**Evidence / Basis:** Phase 6 Finding 6; Notebook 03 Validation 4.

**Analytical consequence:** No High-Priority recommendation is attached to the Corporate segment finding; it is treated as exploratory / monitor-only in the README's recommendation hierarchy.

**Documentation consequence:** README, dashboard ("Corporate Risk" KPI card, not a recommendation card), and this log must not describe this finding using confirmed-driver language.

**Status:** Locked

---

### D-07 — Discount depth: overall Q4 average vs Binders cluster

**Decision:** The overall Q4 average discount-depth change (+1.19 pp) is documented and reported separately from the much sharper discount change within the Binders high-ticket cluster specifically (12.5% → 38.0%).

**Rationale:** Reporting only the Q4-wide average would obscure how concentrated the discount escalation actually was; reporting only the cluster-level figure would misrepresent it as a dataset-wide shift.

**Evidence / Basis:** Notebook 02 §6–7.

**Analytical consequence:** Two distinct discount figures exist in the project and must not be conflated or substituted for one another.

**Documentation consequence:** README, Notebook 02, and the Page 5 "Discount Depth" KPI card must each clearly indicate which of the two figures is being shown.

**Status:** Locked

---

### D-08 — Overlapping, non-additive contributors

**Decision:** The Binders cluster, Central region, and outlier-transaction findings are treated as overlapping views of the same underlying decline, not as separable components whose contributions can be summed.

**Rationale:** Some transactions belong to more than one of these groups simultaneously (e.g., a transaction can be part of the Binders cluster, located in the Central region, and flagged as a statistical outlier at once); summing their reported percentage contributions would double-count the total decline.

**Evidence / Basis:** Phase 7 Driver Contribution Analysis, Overlap Explanation.

**Analytical consequence:** No claim in the project states or implies that these three factors sum to 100% of the decline.

**Documentation consequence:** README, Notebook 02 §5/§8/§9, and the assumption register (A-11) must preserve this non-additivity explicitly wherever multiple contributors are discussed together.

**Status:** Locked

---

### D-09 — Missing cost data as a standing limitation

**Decision:** The absence of Cost, COGS, and Freight data in the dataset is treated as a standing limitation on what the project can conclude, rather than resolved by proxy or silently assumed away.

**Rationale:** Without cost-side data, no discount-margin relationship documented in this project can be confirmed as a financial cause; an unobserved cost-side explanation cannot be ruled out for any of the findings.

**Evidence / Basis:** Phase 0 Data Sufficiency Assessment (schema review of the 21-column dataset).

**Analytical consequence:** All discount-related findings in this project are described using association language, not causal language.

**Documentation consequence:** README Limitations, assumption register (A-13), and this log must retain this limitation; it should not be dropped from any condensed summary of the project (e.g., `summary.md`).

**Status:** Locked

---

### D-10 — Three-tier, evidence-proportional recommendation framework

**Decision:** Recommendations are organized into High Priority, Medium, and Not Recommended/Monitor tiers, with tier assignment based on evidence strength rather than apparent dollar impact alone.

**Rationale:** Ensures a recommendation's prominence reflects how well the underlying finding is supported, preventing a large but fragile or unverified figure from being presented with the same confidence as a robust one.

**Evidence / Basis:** Phase 8 Business Recommendations.

**Analytical consequence:** The Corporate segment finding, despite a large associated percentage (54.1%), receives no High-Priority recommendation, consistent with D-06.

**Documentation consequence:** README Business Recommendations section and the Page 5 dashboard recommendation panel must remain structured around these three tiers.

**Status:** Locked

---

### D-11 — Category mix rejected as a decline driver

**Decision:** Product category mix shift is documented as not associated with the margin decline and is placed in the "Not Recommended" tier for any rebalancing action.

**Rationale:** The category-level Mix Effect, computed via price–volume–mix decomposition, is slightly positive (+0.08pp) — meaning the mix shift moved in a margin-favorable direction, the opposite of what a mix-driven decline hypothesis would require.

**Evidence / Basis:** Phase 7 Driver Contribution Analysis; Notebook 02 §3.

**Analytical consequence:** Category mix is explicitly excluded from the set of findings used to justify any recommendation.

**Documentation consequence:** README and the Page 5 "Not Recommended" card must retain this finding and its direction.

**Status:** Locked

---

### D-12 — Full rebuild of dashboard Page 5

**Decision:** Page 5 of the dashboard was rebuilt entirely, replacing its earlier discount-cap simulation content with a diagnostic/root-cause summary derived from verified Phase 0–9 outputs. The earlier simulation figures were not preserved for backward compatibility.

**Rationale:** The original Page 5 content predated the Phase 0–9 methodology and had not been validated through it, unlike the content on Pages 1–4.

**Evidence / Basis:** Explicit project direction to rebuild Page 5 entirely from verified outputs rather than retain unvalidated legacy content.

**Analytical consequence:** No figure from the original Page 5 (e.g., the prior simulated discount-cap outcomes) appears anywhere in the final project documentation.

**Documentation consequence:** README, Notebook 02, and Page 5 dashboard content must remain mutually consistent going forward; any reintroduction of simulation-style content on Page 5 would require a new, explicit decision.

**Status:** Locked

---

### D-13 — Removal of DiscountCap slicer

**Decision:** The "DiscountCap" slicer was removed from Page 5.

**Rationale:** Direct consequence of D-12; the control had no remaining function once the simulation content it governed was removed.

**Evidence / Basis:** Dashboard implementation record for Page 5.

**Analytical consequence:** None beyond removal of a now-nonfunctional control.

**Documentation consequence:** Page 5 dashboard documentation should not reference a discount-cap control going forward.

**Status:** Locked

---

### D-14 — Five diagnostic KPI cards on Page 5

**Decision:** Page 5 displays five diagnostic KPI cards (Binders Share, Central Margin, Outlier Share, Corporate Risk, Discount Depth), each with a short caption preserving the figure's scope or qualifier.

**Rationale:** These five figures were judged the most decision-relevant, already-verified diagnostics available from the analysis; captions were added specifically to avoid presenting an isolated number without its qualifying context.

**Evidence / Basis:** Notebook 02 §6–10; dashboard implementation and review.

**Analytical consequence:** None beyond the presentation format.

**Documentation consequence:** Any future change to which five metrics are shown, or removal of their captions, should be treated as a revision to this decision.

**Status:** Locked

---

### D-15 — Evidence-tiered recommendation panel layout

**Decision:** The Page 5 recommendation panel is organized as two rows of three cards (High Priority row; Medium/Medium/Not Recommended row), with fixed card height regardless of text length, and border color coding by tier.

**Rationale:** Preserves visual proportionality to evidence strength and avoids implying that a lower-tier recommendation carries equal weight to a higher-tier one; avoids stretching cards to fill space, which would misrepresent shorter recommendations as less substantial.

**Evidence / Basis:** Dashboard layout validation for Page 5 (KPI label fit, column balance, and text-fit review).

**Analytical consequence:** None; presentation-only.

**Documentation consequence:** Future edits to the recommendation panel should preserve the 2-row/3-column structure and tier-based color coding established here.

**Status:** Locked

---

### D-16 — "Steps 1–6" (proposal) vs "Phase 0–9" (project) terminology

**Decision:** `proposal.md` uses "Step 1" through "Step 6" for its high-level methodology; this is explicitly distinct from, and not mapped onto, the project's detailed "Phase 0" through "Phase 9" workflow used everywhere else.

**Rationale:** `proposal.md` serves a different documentation purpose (pre-analysis planning) than the executed Phase 0–9 workflow; using the same "Phase" terminology in both would risk implying a false one-to-one correspondence between the two.

**Evidence / Basis:** Explicit revision instruction for `proposal.md`.

**Analytical consequence:** None; terminology/documentation-only.

**Documentation consequence:** `proposal.md` must not reintroduce "Phase" numbering for its six steps; all other project documents must continue using "Phase 0–9" without alteration.

**Status:** Locked

---

### D-17 — Retention of 16 rows with identical (Order ID, Product ID)

**Decision:** 16 rows sharing an identical (Order ID, Product ID) pair are retained in the dataset without removal, and are not classified as confirmed duplicate-entry errors.

**Rationale:** No timestamp or line-sequence field exists to determine whether these represent genuine repeat line items or erroneous duplicate entries.

**Evidence / Basis:** Phase 0 data quality assessment (Step 0.4).

**Analytical consequence:** These rows remain part of every downstream calculation; given their small share (0.16% of rows), no finding in this project is materially sensitive to their status.

**Documentation consequence:** Assumption register (A-02) and this log retain this as an unresolved data-quality note, not a confirmed error.

**Status:** Unresolved

---

### D-18 — Product ID / Product Name ambiguity status

**Decision:** The Product ID → Product Name ambiguity (32 Product IDs, 3.37% of rows) is documented as a partially validated, unresolved data-quality caveat.

**Rationale:** While the inconsistency was identified during Phase 0 schema review, it has not been independently reproduced within the current `01_EDA.ipynb` notebook or itemized as a line item in `TRACEABILITY_MATRIX.md`.

**Evidence / Basis:** Phase 0 data quality assessment (Step 0.4). Source not sufficient to establish full reproduction within the current notebook library.

**Analytical consequence:** No major finding in this project currently depends on resolving the identity of a specific affected Product ID; the caveat is precautionary.

**Documentation consequence:** Should this item be cited elsewhere as "validated," that claim would exceed what the current notebook library supports — see Consistency Issues below.

**Status:** Unresolved

---

### D-19 — Add category scope to Central recommendation card

**Decision:** The Page 5 Central recommendation card was updated to explicitly scope the recommendation to Furniture and Office Supplies.

**Rationale:** The earlier version omitted a category qualifier that was required by the underlying finding and README.

**Evidence / Basis:** Direct dashboard revision following consistency review.

**Analytical consequence:** None. The underlying finding remains unchanged.

**Documentation consequence:** Page 5 now explicitly states that the Central pricing review applies to Furniture and Office Supplies, resolving the inconsistency previously logged against D-05.

**Status:** Locked

---

### D-20 — Add sample-size qualifier to Binders KPI

**Decision:** The Page 5 Binders Share KPI caption was updated to include the small-sample qualifier of approximately 8–10 transactions.

**Rationale:** The 96.6% figure describes a concentrated transaction cluster and should not be presented without its sample-size context.

**Evidence / Basis:** Direct dashboard revision following consistency review.

**Analytical consequence:** None. The underlying Binders finding remains unchanged.

**Documentation consequence:** Page 5 now preserves the 8–10 transaction qualifier alongside the 96.6% figure, resolving the inconsistency previously logged against D-04.

**Status:** Locked

---

## Consistency Issues

| Issue | Conflicting Statements | Source Documents | Recommended Resolution | Status |
|---|---|---|---|---|
| A-01 / D-18 traceability gap | Phase 0 project history records the Product ID → Product Name ambiguity (32 IDs, 3.37% of rows) as an established data-quality finding, but this specific check does not appear as a reproducible calculation in `01_EDA.ipynb`, and no corresponding line item exists in `TRACEABILITY_MATRIX.md`. | Phase 0 record (via `assumption_register.md` A-01); `01_EDA.ipynb`; `TRACEABILITY_MATRIX.md` | Either add a reproducible check for this figure to `01_EDA.ipynb` and a corresponding Traceability Matrix entry, or explicitly label the 3.37%/32-ID figure in all documents as "Phase 0 record, not independently reproduced in the current notebook library." | **Open** |
| Central region recommendation card omits category scope | README's High Priority recommendation states the Central region review should be "focused on Furniture and Office Supplies specifically — the discount-margin relationship was not observed in Technology." The Page 5 dashboard recommendation card previously read only "Review the regional pricing and discount approval process for the Central region," without the category qualifier. | `README.md` (Business Recommendations, High Priority); Page 5 dashboard, recommendation card 2 | Add the Furniture/Office Supplies qualifier to the dashboard card text. | **Resolved by D-19** |
| Binders sample-size qualifier present in README, absent from dashboard KPI/banner | README explicitly requires the "8–10 transactions" small-sample qualifier be preserved wherever the 96.6% figure is cited. The Page 2 banner and Page 5 "Binders Share" KPI card previously displayed 96.6%/96.60% without this qualifier. | `README.md` (Key Findings, Limitations); Page 2 dashboard banner; Page 5 dashboard KPI card | Add a caption noting the small transaction count to the dashboard. | **Resolved by D-20 (Page 5 only — see note below)** |

**Note on partial resolution:** D-20 resolves the qualifier gap on the Page 5 KPI card specifically. The Page 2 banner ("Furniture and Office Supplies show the weakest profitability, driven mainly by a high-ticket discount cluster in Binders...") was not addressed by D-19/D-20 and does not itself state the transaction count. This is not logged as a new open issue, since the Page 2 banner names the mechanism (a discount cluster) without citing the 96.6% figure directly — the strict qualifier requirement applies most directly to the KPI figure itself (now resolved) rather than to every mention of Binders on the dashboard. If this distinction is not acceptable, the Page 2 banner should be reviewed as a further follow-up.
