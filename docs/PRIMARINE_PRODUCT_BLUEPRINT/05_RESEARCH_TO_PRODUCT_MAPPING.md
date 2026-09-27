# PRIMARINE — Research to Product Capability Mapping

**Document:** `docs/PRIMARINE_PRODUCT_BLUEPRINT/05_RESEARCH_TO_PRODUCT_MAPPING.md`  
**Classification:** Research $\longrightarrow$ Production Translation Matrix  

---

## 1. Executive Summary

This document connects every scientific finding established during our research phase to its corresponding commercial feature in the larger PRIMARINE product architecture.

> **Key Principle:**  
> A research finding validates an algorithmic principle; it does not automatically mean the commercial UI/microservice is fully deployed. This table outlines the exact translation path.

---

## 2. Comprehensive Research-to-Product Translation Matrix

| # | Validated Research Finding | Corresponding PRIMARINE Product Feature | Why It Matters Industrially | Research Status | Product / Prototype Status |
|---|---|---|---|---|---|
| **1** | **Physical Allocation Stability ($\text{PDFR} = 0.00\%$)** | **Feasibility-First Decision Engine** | Draft, LOA, and deadweight limits are physical walls. Eliminating infeasible ships first saves compute and prevents illegal fixtures. | **VALIDATED (Empirical & Simulation)** | **PROTOTYPE IMPLEMENTED** (Hard-coded filter in local solver) |
| **2** | **Procurement Timing Fragility ($\text{TDFR} = 50\%\text{--}100\%$)** | **Market-Entry Timing Risk Advisor** | Prevents charterers from entering the market 3 days too early during volatile rate expansions, avoiding ₹1.5 Cr+ freight premiums. | **VALIDATED (Held-Out Test)** | **PROTOTYPE IMPLEMENTED** (`ENTER` vs `DEFER` indicator) |
| **3** | **CQR Interval Width vs False-Breakout ($\text{AUC} = 0.6719$)** | **Macro-Regime Volatility Gate** | Prediction band width flags dangerous macro volatility regimes where point forecasts are likely to trigger false breakouts. | **VALIDATED (Held-Out Test, $p < 0.01$)** | **PROTOTYPE IMPLEMENTED** (Pre-calibrated $\tau = 1.35\times$ threshold) |
| **4** | **Selective Abstention ($52.33\%$ Error Cut)** | **Deterministic `ABSTAIN` Recommendation** | When market noise is extreme, PRIMARINE advises staying neutral (dollar-cost averaging) rather than gambling on a forecast. | **VALIDATED (Held-Out Test)** | **PROTOTYPE IMPLEMENTED** (`ABSTAIN` UI state with explanation) |
| **5** | **Boundary-Crossing Degeneracy ($\text{AUC} = 0.5025$)** | **Rejection of Local Heuristics** | Proved that local boundary crossing is uninformative in shipping because macro intervals naturally span spot rates. | **NEGATIVE RESULT PRESERVED** | **EXCLUDED FROM PRODUCT** (Avoids bad heuristics) |
| **6** | **Turning-Point Inflection Skill ($\text{F1} = 59.51\%$)** | **Forward Rate Turning-Point Detector** | Alerts procurement managers when a 7-day rate inflection ($\ge \pm 4\%$) is forming, providing a $+32\text{ pp}$ edge over AR(5). | **VALIDATED (1,920 Market Rows)** | **PROTOTYPE IMPLEMENTED** (LightGBM forecast badge) |
| **7** | **Downstream Landed Savings ($p = 5.42\times 10^{-11}$)** | **Multi-Objective Landed Cost Optimizer** | Optimizes total landed USD/MT (Charter hire + Fuel burn + Port dues + Demurrage) rather than raw spot freight alone. | **VALIDATED (Paired Wilcoxon)** | **PROTOTYPE IMPLEMENTED** (Cost optimizer across candidate fleet) |
| **8** | **Adaptive Disruption Recovery (+$3.90/MT Average)** | **Adaptive Disruption Re-Planning Engine** | When a port is silted or congested, PRIMARINE dynamically re-ranks alternative discharge ports and routes. | **CONTROLLED SIMULATION** | **PROTOTYPE IMPLEMENTED** (Interactive disruption trigger) |
| **9** | **ST-GNN Disruption Propagation (+$0.49/MT POC)** | **Network-Aware Congestion Forecasting** | Models how typhoons or Singapore Strait jams propagate delays across connected maritime corridors. | **CONTROLLED POC (8 Nodes)** | **PLANNED FOR EXPANSION** (Global graph expansion post-selection) |
| **10** | **Constraint Criticality Scoring (Capacity 52%, Draft 3%)** | **Counterfactual "What-If" Analysis Engine** | Shows charterers exactly what would happen if a port berth were dredged $+1\text{m}$ or parcel volume split. | **VALIDATED (63 Permutations)** | **PLANNED FOR PHASE 3** (Interactive scenario sandbox) |
