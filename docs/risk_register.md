# Risk Register

## Purpose

This register documents analytical, data-quality, interpretation, and documentation risks that could affect the reliability or correct interpretation of the Margin Decline Root Cause Analysis. A risk is recorded here because it describes something that *could go wrong* as a consequence of an existing uncertainty (documented in `assumption_register.md`) or a documentation choice (documented in `decision_log.md`) — it is distinct from both: an **assumption** is what is uncertain; a **decision** is what the project chose to do about it; a **risk** is what could go wrong if that uncertainty is misread or a decision is not carried through consistently.

The register preserves the project's Phase 0–Phase 9 terminology throughout. `proposal.md`'s Step 1–6 framework is a separate, high-level planning structure and is not remapped onto Phase 0–9 anywhere in this document.

---

## Risk Register

| ID | Risk | Category | Likelihood | Impact | Evidence / Basis | Mitigation | Related Decision / Assumption | Status |
|---|---|---|---|---|---|---|---|---|
| R-01 | Reader confuses the full-year 2016 vs 2017 pattern with the Q4-2016 vs Q4-2017 root-cause baseline. | Analytical Scope | Medium | High | Full-year comparison shows Profit increasing; within Q4 specifically, Profit declines (~$38.1K → $27.4K) alongside Margin — the two scopes describe opposite Profit directions. | Full-year figures explicitly labeled as baseline/context; Q4-2016 vs Q4-2017 explicitly labeled as the root-cause window in README, Notebook 02 §1, and Page 3 dashboard subtitle. | D-01, D-02 / assumption A-06 | Mitigated |
| R-02 | Binders finding (96.6%) is generalized from a small high-ticket cluster to the broader Binders sub-category. | Statistical / Robustness | Medium | High | Approximately 8–10 transactions account for 96.6% of the Binders-level decline (Notebook 02 §5–6). | 8–10 transaction qualifier required wherever 96.6% is cited; Page 5 KPI caption updated to include it (D-20, Locked). The Page 2 banner names the mechanism (a discount cluster in Binders) without citing the 96.6% figure directly, so it is not treated as a separate open item per `decision_log.md`. | D-04, D-20 / assumption A-09 | Mitigated |
| R-03 | Central region finding is read as applying uniformly across all product categories. | Interpretation | Medium | Medium-High | Central effect observed in Furniture and Office Supplies; not observed in Technology, where Central's margin was slightly higher than other regions (Notebook 03, Validation 6). | "Furniture and Office Supplies" qualifier retained in README and dashboard; Page 5 recommendation card corrected to state category scope. | D-05, D-19 / assumption A-08 | Mitigated |
| R-04 | Corporate segment finding (54.1%) is treated as a confirmed, independent driver because the associated figure is large. | Causal Inference | Medium | High | 54.1% of the apparent Corporate decline disappears once known outlier transactions are excluded (Phase 6 Finding 6; Notebook 03 Validation 4). | Corporate finding tiered as exploratory/monitor-only, not High Priority, in both README and dashboard. | D-06, D-10 / assumption A-10 | Mitigated |
| R-05 | Discount-margin association is read as proof that discounting caused the margin decline. | Causal Inference | Medium-High | High | No Cost, COGS, or Freight data exists in the dataset (Phase 0 schema review); an unobserved cost-side explanation cannot be ruled out for any discount-related finding. | Association language ("associated with," "concentrated in") used consistently; causal terms ("confirmed," "proven," "root cause") prohibited absent sufficient evidence tier. | D-03, D-09 / assumption A-13 | Monitoring — structural risk given no cost data exists; cannot be permanently resolved, only continuously guarded through wording |
| R-06 | Q4-wide average discount change (+1.19pp) is confused with the much larger discount change within the Binders cluster (12.5% → 38.0%). | Interpretation | Low-Medium | Medium | Notebook 02 §6–7 reports both figures as distinct, differently-scoped metrics. | Both figures presented with explicit scope labels (Q4-wide average vs. Binders cluster) wherever either appears. | D-07 | Mitigated |
| R-07 | Binders, Central, and Outlier contribution percentages are summed and read as the total percentage of the decline "explained." | Analytical Scope | Medium | High | The three views overlap at the transaction level (e.g., a transaction can be part of the Binders cluster, in the Central region, and flagged as a statistical outlier simultaneously) (Phase 7 Overlap Explanation). | Explicit non-additivity statement wherever multiple contributors are discussed together in README and Notebook 02. | D-08 / assumption A-11 | Monitoring — control exists in documentation, but the risk of a reader summing percentages independently cannot be fully eliminated |
| R-08 | Category-level product mix shift is inferred to be a contributor to the margin decline. | Interpretation | Low | Medium | Category-level Mix Effect = +0.08pp — a margin-favorable direction, not a decline-driving one (Phase 7; Notebook 02 §3). | Category mix rebalancing kept in the Not Recommended tier, with the direction of the effect stated explicitly. | D-11 | Mitigated |
| R-09 | A small number of large transactions disproportionately influence aggregate findings without this being recognized. | Statistical / Robustness | Medium | High | Excluding known outlier transactions materially changes the Corporate segment finding and reduces (but does not eliminate) the Binders effect specifically (Notebook 03, Validation 1). No equivalent outlier-exclusion test exists for Central region in the current notebook library; Central's robustness was instead assessed through category-mix cross-view consistency (Notebook 03, Validation 3). | Outlier sensitivity explicitly tested and documented for each affected finding; stable findings distinguished from fragile ones. | D-06, D-08 / assumption A-03 | Monitoring — inherent to any small-N transaction cluster; robustness checks reduce but do not eliminate this risk |
| R-10 | 16 rows sharing an identical (Order ID, Product ID) pair are read as confirmed duplicate data-entry errors. | Data Quality | Low | Low | No timestamp or line-sequence field exists to determine whether these are genuine repeat line items or erroneous duplicates; affects 0.16% of rows (Phase 0, Step 0.4). | Rows retained without removal; status documented as unresolved rather than resolved in either direction. | D-17 / assumption A-02 | Unresolved |
| R-11 | Product ID → Product Name ambiguity (32 IDs, 3.37% of rows) is cited as a fully validated finding. | Data Quality / Documentation Governance | Low | Medium | Identified during Phase 0 schema review, but not independently reproduced in `01_EDA.ipynb` and not itemized in `TRACEABILITY_MATRIX.md`. | Status documented as partially validated / unresolved; no major finding currently depends on a specifically affected Product ID. | D-18 / assumption A-01 | Unresolved |
| R-12 | The project's findings are read as a complete explanation of the observed margin decline's financial cause. | Causal Inference | High | High | No Cost, COGS, or Freight fields exist in the dataset; a meaningful portion of the total Q4 decline remains unattributed to any identified driver (Phase 7; assumption A-14). | Findings explicitly framed as observed pricing/discounting patterns and associations, not a complete financial causal mechanism; unexplained residual stated in README Limitations. | D-09 / assumption A-13, A-14 | Monitoring — structural, cannot be resolved without additional data |
| R-13 | A recommendation is assigned High Priority based on the size of its associated percentage rather than the strength of its underlying evidence. | Recommendation | Medium | High | Corporate segment (54.1%) is a large figure but a fragile one (R-04); it is tiered as monitor-only rather than High Priority. | Evidence-strength tiering framework (High / Medium / Not Recommended–Monitor) applied consistently, with tier determined by robustness, not magnitude. | D-06, D-10 | Mitigated |
| R-14 | The dashboard, README, notebooks, and governance documents (assumption register, decision log, this risk register) drift out of consistency with one another after later edits. | Documentation / Governance | Medium | High | A prior audit identified exactly this pattern: the Page 5 Central and Binders cards omitted qualifiers present in the README, later corrected via D-19 and D-20. | Notebooks treated as the analytical source of truth; periodic cross-document audit performed (as evidenced by the D-19/D-20 correction cycle itself). | D-01–D-20 (register-wide) | Monitoring — the correction cycle that produced D-19/D-20 demonstrates the risk is real and requires ongoing, not one-time, attention |

---

## Highest-Priority Risks

**1. R-01 — Full-year vs Q4 scope confusion.** This risk sits upstream of every other finding in the project: if a reader does not register that the root-cause analysis explains a Q4-specific Sales-up/Profit-down/Margin-down quarter — not the full-year Sales-up/Profit-up/Margin-down pattern that originally motivated the investigation — every downstream finding (Binders, Central, outlier share) risks being read against the wrong baseline narrative.

**2. R-02 — Binders small-sample concentration.** The single largest sub-category contributor to the Q4 decline is traceable to roughly 8–10 transactions. Dropping this qualifier converts a bounded, cluster-level finding into an implied category-wide trend, which is precisely the kind of overstatement the project's evidence-strength discipline (D-03) is designed to prevent.

**3. R-05 / R-12 — Causal interpretation without cost-side data.** Every discount-margin relationship in this project is an association, not a confirmed cause, because no Cost, COGS, or Freight field exists in the dataset. This is the most consequential and most permanent limitation in the project (assumption A-13) — it cannot be resolved by further analysis of the existing dataset, only by acquiring new data.

**4. R-04 — Corporate segment fragility / outlier sensitivity.** More than half of the apparent Corporate segment decline is attributable to a small number of outlier transactions rather than a systematic pattern. This is the clearest example in the project of a finding that is large in magnitude but weak in robustness — treating it as a confirmed driver would directly contradict the evidence-strength framework the project otherwise applies consistently.

**5. R-07 — Overlapping contributor double-counting.** Because the Binders cluster, Central region, and outlier-transaction findings share transactions, summing their reported percentages would misstate what fraction of the decline the analysis actually explains. This risk is easy for a reader to fall into precisely because each individual percentage (96.6%, contribution shares tied to Central, 60.8%) is accurately reported on its own.

---

## Risk Control Map

| Risk | Primary Control | Where Controlled |
|---|---|---|
| R-01 | Explicit full-year vs Q4 scope labeling | README, Notebook 02 §1, Page 3 dashboard subtitle |
| R-02 | 8–10 transaction qualifier | README, Notebook 02 §6, Page 5 dashboard KPI caption |
| R-03 | "Furniture and Office Supplies" scope qualifier | README, Notebook 03 Validation 6, Page 3 dashboard banner, Page 5 recommendation card |
| R-04 | Evidence-tiered recommendation framework | README Business Recommendations, Decision Log (D-06, D-10), Page 5 dashboard (no High Priority card for Corporate) |
| R-05 | Association-only language discipline | Phase 0 Analytical Principles, README, Decision Log (D-03) |
| R-06 | Explicit dual-figure labeling | Notebook 02 §6–7, README, Page 5 dashboard KPI caption |
| R-07 | Explicit overlap/non-additivity statement | Phase 7 Driver Contribution Analysis, README, Assumption Register (A-11) |
| R-08 | Not Recommended tier assignment | README, Decision Log (D-11), Page 5 dashboard | 
| R-09 | Documented robustness/outlier-sensitivity checks | Phase 6, Notebook 03 | 
| R-10 | Retention without error classification | Phase 0 (Step 0.4), Assumption Register (A-02), Decision Log (D-17) |
| R-11 | Partially-validated status flag | Assumption Register (A-01), Decision Log (D-18), this Risk Register |
| R-12 | Explicit causal-limit statement | README Limitations, Assumption Register (A-13, A-14) |
| R-13 | Evidence-strength tiering framework | Phase 8, README Business Recommendations, Decision Log (D-10) |
| R-14 | Periodic cross-document audit against the notebooks as source of truth | Traceability Matrix, Decision Log (D-19, D-20 as evidence the audit cycle functions) |

---

## Consistency Notes

- Phase 0–Phase 9 remains the executed analytical workflow referenced throughout this register; no phase has been renumbered, merged, or reinterpreted here.
- `proposal.md` uses Step 1–6 as a separate, high-level planning framework and is not remapped onto Phase 0–9 anywhere in this document.
- D-19 and D-20, as recorded in `decision_log.md` (Status: Locked), represent dashboard qualifier corrections already applied to the current dashboard: the Page 5 Central recommendation card now states the Furniture/Office Supplies scope, and the Page 5 Binders Share KPI caption now states the 8–10 transaction qualifier. These are reflected as **Mitigated** in this register (R-02, R-03), not as open or monitoring items, consistent with `decision_log.md`'s own resolution of these two issues.
- A-01 / D-18 (Product ID / Product Name ambiguity) remains **Unresolved** in this register, consistent with its status in `assumption_register.md` and `decision_log.md`. It is not upgraded to "validated" here, since no reproducible source has been added to `01_EDA.ipynb` or `TRACEABILITY_MATRIX.md`.
- No risk in this register silently upgrades an unresolved assumption into a validated fact, or a fragile finding into a confirmed driver. Where a risk's underlying uncertainty is structural (e.g., R-05, R-09, R-12, R-14), its status is recorded as **Monitoring** rather than **Mitigated**, since these risks are actively managed but not eliminable with the current dataset or a one-time correction.
