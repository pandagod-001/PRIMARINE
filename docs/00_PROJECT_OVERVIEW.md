# PRIMARINE — Project Overview & Master Summary

**System Version:** 1.0.0 (Consolidated Release)  
**Classification:** Research, Engineering Blueprint, and Interactive Demonstrator  
**Authors:** PRIMARINE Core Team (SIH PS26006)

---

## 1. Executive Summary

**PRIMARINE** is an **Uncertainty-Aware Maritime Freight Decision Intelligence Platform** engineered to solve a multi-billion dollar blind spot in global bulk commodity shipping: *the downstream failure of point-forecasts in high-stakes procurement under rigid physical port and vessel constraints.*

In traditional maritime logistics, procurement managers rely on point-forecast price projections to decide when and where to charter vessels. However, maritime freight rates (e.g., Baltic Dry Index) exhibit non-stationary jumps, fat-tailed volatility, and geopolitical shocks. When an uncalibrated point forecast predicts a price drop that fails to materialize (a *false breakout*), procurement teams lock in sub-optimal charters, incur catastrophic demurrage fees, or face stockouts.

PRIMARINE reconciles this problem through a multi-stage architecture:
1. **Calibrated Predictive Intelligence:** LightGBM-based regime inflection detection coupled with **Split Conformalized Quantile Regression (Split-CQR)** to provide finite-sample, distribution-free uncertainty intervals.
2. **Hard Physical Feasibility Filtering:** Strict operational filtering across berth draft, deadweight tonnage (DWT), beam, LOA, tidal windows, and cargo gear.
3. **Uncertainty-Gated Selective Prediction:** A pre-calibrated interval-width gating policy ($\tau = 1.35 \times \text{validation median width}$) that dynamically issues `ENTER`, `DEFER`, or `ABSTAIN` recommendations, effectively filtering out high-risk false breakouts before capital is committed.
4. **Adaptive Disruption Intelligence:** Graph-based disruption modeling and Value-of-Information (VoI) tracking to reroute cargo and reschedule chartering when corridors congest.

---

## 2. Core Architectural Pillars

PRIMARINE spans eight interconnected operational stages across its complete enterprise vision:

```
[ External Data Sources: Baltic, AIS, Weather, Port Queues, ERP ]
                            ↓
[ Stage 1: Ingestion & Security Gate (Data Quality / Outlier Guard) ]
                            ↓
[ Stage 2: Feature Store & Maritime Knowledge Graph (FalkorDB / TimescaleDB) ]
                            ↓
[ Stage 3: Predictive Intelligence (LightGBM Inflection + Split-CQR Bounds) ]
                            ↓
[ Stage 4: Physical Feasibility Engine (Draft, DWT, Beam, Berth Step-Functions) ]
                            ↓
[ Stage 5: Multi-Objective Optimization (Cost vs Transit vs Demurrage Risk) ]
                            ↓
[ Stage 6: Uncertainty Gating & Selective Abstention (ENTER / DEFER / ABSTAIN) ]
                            ↓
[ Stage 7: Human-in-the-Loop Approval & Immutable Audit Trail (SHA-256 Chain) ]
                            ↓
[ Stage 8: Dynamic Disruption Monitoring & Adaptive Re-Ranking (Graph Cascade) ]
```

---

## 3. The Four Reality States

To maintain strict scientific integrity and professional clarity, all components of PRIMARINE are classified into four distinct reality states:

| Reality State | Description | Current Repository Artifacts |
| :--- | :--- | :--- |
| **1. VALIDATED RESEARCH** | Scientifically proven hypotheses supported by reproducible code, statistical significance tests ($p < 0.01$), and empirical datasets. | [research/PRIMARINE_RESEARCH_PACKAGE/](file:///c:/Users/Abhijay/PRIMARINE/research/PRIMARINE_RESEARCH_PACKAGE/), [research/EVIDENCE_REGISTRY.csv](file:///c:/Users/Abhijay/PRIMARINE/research/EVIDENCE_REGISTRY.csv) |
| **2. PROTOTYPE IMPLEMENTATION** | Functional local vertical-slice software demonstrating the end-to-end user experience and decision workflows on curated fixtures. | [prototype/PRIMARINE-demo/](file:///c:/Users/Abhijay/PRIMARINE/prototype/README.md) (`index.html`, `app.js`, `engine.js`) |
| **3. PLANNED ENGINEERING** | Enterprise software architectures, database schemas, and external API adapter interfaces designed for production scale. | [docs/PRIMARINE_PRODUCT_BLUEPRINT/](file:///c:/Users/Abhijay/PRIMARINE/docs/PRIMARINE_PRODUCT_BLUEPRINT/), [docs/api/](file:///c:/Users/Abhijay/PRIMARINE/docs/api/) |
| **4. FUTURE RESEARCH** | Long-term scientific goals requiring multi-terabyte global data feeds and high-performance computing clusters. | Global real-AIS Spatio-Temporal Graph Neural Network (ST-GNN) |

---

## 4. Key Verified Research Discoveries

- **Point Forecasting vs Turning Points:** While LightGBM does not beat naive Persistence on raw point MAE (`0.4644` vs `0.4175`), it achieves superior 7-day turning-point inflection detection (**F1 = 59.51%** vs **0.00%** for Persistence and **27.18%** for AR-5 baselines).
- **Asymmetric Fragility:** Physical vessel-to-port allocation decisions remain invariant under rate uncertainty (**PDFR = 0.00%** on tested dry-bulk constraints), while procurement timing is acutely fragile (**TDFR = 50%–100%**).
- **Conformal Width as a Regime Risk Filter:** High calibrated CQR interval width is strongly associated with false-breakout exposure (Risk Difference = `+16.86 percentage points`, $p < 0.01$, $\text{AUC} = 0.6719$).
- **Selective Abstention:** Pre-calibrated width abstention ($\tau = 1.35\times$) **reduces observed false-breakout events by 52.33%** (from 86 to 41 events) on held-out scenarios at a nominal cost premium of `+$0.0334/MT` (`+0.453%`).
- **Downstream Significance:** Gated multi-stage procurement decisions significantly outperform unconstrained optimization (Paired Wilcoxon $W = 11530.0$, $p = 5.42 \times 10^{-11}$).
- **Negative Finding Preserved:** Point-to-interval boundary crossing is degenerate in daily freight trading ($\text{AUC} = 0.5025$, 99.65% crossing rate).

---

## 5. Repository Guide

- **[Master README](file:///c:/Users/Abhijay/PRIMARINE/README.md):** Main project entry point with quickstart and architecture diagrams.
- **[Research Package](file:///c:/Users/Abhijay/PRIMARINE/research/PRIMARINE_RESEARCH_PACKAGE/):** Authoritative frozen research papers, claims, and reproduction manifests.
- **[Product Blueprint](file:///c:/Users/Abhijay/PRIMARINE/docs/PRIMARINE_PRODUCT_BLUEPRINT/):** 16 comprehensive product, system design, and commercialization specs.
- **[Interactive Prototype](file:///c:/Users/Abhijay/PRIMARINE/prototype/PRIMARINE-demo/):** Fully functional offline decision intelligence demonstrator.
- **[Evidence Registry](file:///c:/Users/Abhijay/PRIMARINE/research/EVIDENCE_REGISTRY.csv):** Traceability matrix for every empirical claim and metric.
