# PRIMARINE — Master Project Status & Forensic Audit

**Document Version:** 1.0.0 (Consolidated Audit)  
**Status:** Authoritative Final Reference  
**Scope:** Complete 12-section project assessment across vision, research, prototype, engineering, and future roadmap.

---

## A. WHAT PRIMARINE IS

**PRIMARINE** is an **Uncertainty-Aware Maritime Freight Decision Intelligence System** designed to bridge the gap between volatile freight forecasting, hard physical vessel-port constraints, and multi-million dollar procurement chartering decisions. It introduces a distribution-free **Split Conformalized Quantile Regression (Split-CQR)** gating architecture to protect commercial chartering desks from costly false breakouts during volatile market regimes.

---

## B. WHAT WE ORIGINALLY PROPOSED

The original PRIMARINE enterprise vision proposed an 8-stage real-time autonomous maritime decision platform:
1. **Multi-Source Ingestion & Security Gate:** Live Baltic Exchange, Satellite AIS, ECMWF Weather, and Port Community Systems feeds.
2. **Feature Store & Maritime Knowledge Graph:** Attributed multigraph modeling global vessel traffic, ports, berths, and corridors.
3. **Predictive Intelligence Core:** Probabilistic freight rate forecasting.
4. **Physical Feasibility Engine:** Strict deterministic filtering across draft, deadweight, beam, LOA, and gear constraints.
5. **Multi-Objective Procurement Optimizer:** Balancing freight cost, transit days, demurrage risk, and carbon emissions.
6. **Uncertainty-Gated Selective Prediction:** Issuing automated `ENTER`, `DEFER`, and `ABSTAIN` recommendations.
7. **Human-in-the-Loop Cockpit & Cryptographic Audit:** SHA-256 hash-chained decision audit logs.
8. **Dynamic Disruption Monitoring:** Real-time graph cascade detection and adaptive rerouting.

---

## C. WHAT WE ACTUALLY RESEARCHED

The scientific research phase investigated a specific, fundamental uncertainty-to-decision question within this architecture:
- Evaluated point-forecasting and 7-day inflection detection ($\ge \pm 4\%$) across Baltic Dry Index data (2018–2024).
- Calibrated non-parametric finite-sample Split-CQR prediction intervals at nominal 90% coverage.
- Mapped multi-dimensional decision fragility surfaces across physical vessel-port assignment versus temporal procurement timing.
- Evaluated the relationship between calibrated interval width and false-breakout exposure during procurement timing.
- Assessed pre-calibrated selective prediction policies ($\tau = 1.35\times$) and downstream optimization divergence ($p < 0.01$).
- Tested and preserved negative hypotheses regarding spot boundary-crossing discrimination and directional sign error correlation.

---

## D. WHAT WE ACTUALLY FOUND

1. **Point Forecasting Reality:** LightGBM does not beat naive Persistence on raw single-step point MAE (`0.4644` vs `0.4175`).
2. **Turning-Point Skill:** LightGBM achieves **F1 = 59.51%** on 7-day rate inflections (+32.33 pp over AR-5 baseline).
3. **Finite-Sample Coverage:** Split-CQR delivers **88.19%–95.83%** empirical coverage on held-out splits ($q_{\text{calib}} = 0.8415$).
4. **Asymmetric Fragility:** Physical vessel-port allocation is completely invariant under rate uncertainty (**PDFR = 0.00%** on tested dry-bulk fixtures), whereas procurement timing is acutely fragile (**TDFR = 50%–100%**).
5. **False-Breakout Association:** Calibrated CQR width is strongly associated with false-breakout exposure ($\text{AUC} = \mathbf{0.6719}$, Risk Difference = `+16.86 pp`, $p < 0.01$).
6. **Selective Abstention:** Pre-calibrated width abstention ($\tau = 1.35\times$) **reduces observed false-breakout events by 52.33%** (86 $\rightarrow$ 41 events) while retaining 61.11% decision coverage at a nominal cost premium of `+$0.0334/MT` (+0.453%).
7. **Downstream Significance:** Gated multi-stage procurement decisions significantly outperform unconstrained optimization (Paired Wilcoxon $W = 11530.0$, $p = 5.42 \times 10^{-11}$).
8. **Negative Results Locked:** Spot boundary crossing is degenerate ($\text{AUC} = 0.5025$, 99.65% crossing rate); CQR width does not correlate with single-step directional sign errors ($\text{AUC} = 0.4487$).

---

## E. WHAT IS VALIDATED (VALIDATED RESEARCH)

- Point MAE and Turning-Point Inflection metrics on Baltic Dry Index (2018–2024).
- Split-CQR non-parametric marginal calibration ($q_{\text{calib}} = 0.8415$).
- Physical feasibility invariance (PDFR = 0.00%) on standard East Coast India dry-bulk fixtures (Paradip, Dhamra, Haldia).
- Multi-dimensional timing fragility divergence (TDFR = 50%–100%).
- Downstream optimization statistical significance ($p = 5.42 \times 10^{-11}$).
- Untouched historical procurement backtest (+1.04% to +2.95% cost efficiency).

---

## F. WHAT IS PROTOTYPED (PROTOTYPE IMPLEMENTATION)

- Standalone interactive local demonstrator cockpit (`prototype/PRIMARINE-demo/`).
- Dynamic Indian Ocean port-vessel routing map visualization.
- Real-time client-side execution of Split-CQR uncertainty gating (`ENTER`, `DEFER`, `ABSTAIN`).
- Hard physical feasibility filtering across 8 ports, 24 berths, and 5 dry-bulk vessel classes.
- Scenario-based disruption simulator (Red Sea closure, Cyclone warning, Port strike).
- SHA-256 cryptographic audit drawer logging all procurement decisions.
- Synthetic 8-node Spatio-Temporal Graph disruption simulator (`scripts/experiments/07_stgnn_poc.py`).

---

## G. WHAT IS NOT IMPLEMENTED

- Live production WebSocket connections to commercial AIS satellite streaming providers.
- Live API subscriptions to Baltic Exchange or Clarksons Research.
- Live automated Port Community System (PCS) berth queue webhooks.
- Multi-tenant cloud hosting on distributed Kubernetes clusters.

---

## H. WHAT IS PLANNED (PLANNED ENGINEERING)

- Provider Adapter Ingestion Layer implementing abstract interfaces (`IFreightMarketAdapter`, `IVesselTelemetryAdapter`, `IPortOperationsAdapter`).
- Enterprise backend services built on FastAPI, TimescaleDB, and FalkorDB Maritime Knowledge Graph.
- Enterprise Single Sign-On (SSO) with OAuth2 / OIDC and Role-Based Access Control (RBAC).
- Automated daily rolling conformal recalibration pipeline.

---

## I. WHAT IS FUTURE RESEARCH (FUTURE RESEARCH)

- Real-world Global Spatio-Temporal Graph Neural Network (ST-GNN) trained on multi-terabyte satellite AIS telemetry streams for global choke-point delay propagation.
- End-to-end multi-commodity transfer learning across Clean Tankers, LNG, and Container Liner networks.

---

## J. CURRENT RESEARCH CONTRIBUTION

> *"PRIMARINE investigates conformal uncertainty-gated decision support for maritime freight procurement, demonstrating that calibrated forecast-interval width can serve as a regime-level signal for false-breakout exposure and support selective abstention under hard physical vessel-port feasibility constraints."*

---

## K. CURRENT PRODUCT STATUS

PRIMARINE currently exists as a **fully functional local vertical-slice prototype** (`prototype/PRIMARINE-demo/`) validated on curated real-world fixtures and historical market series. It provides a complete, tangible user experience demonstrating all operational stages without external cloud dependencies.

---

## L. NEXT ENGINEERING PHASE

The immediate next engineering phase will focus on:
1. Deploying the FastAPI backend services and TimescaleDB store.
2. Connecting live sandbox feeds for Baltic Exchange and AIS data via the Provider Adapter layer.
3. Conducting pilot trials with commercial chartering desks to validate the selective abstention policy in live trading environments.
