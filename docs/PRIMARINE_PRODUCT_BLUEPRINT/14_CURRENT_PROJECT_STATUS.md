# PRIMARINE — Current Project Status Report

**Document:** `docs/PRIMARINE_PRODUCT_BLUEPRINT/14_CURRENT_PROJECT_STATUS.md`  
**Classification:** Executive Project Health & Status Audit  
**Date:** 2026-09-26  

---

## 1. What was the Original Idea?
An end-to-end Maritime Freight Decision Intelligence Platform for Indian bulk importers (SAIL, NTPC, RINL) that unifies forward market forecasting, physical port-vessel feasibility, conformal uncertainty estimation, and multi-objective chartering optimization into an explainable decision center with adaptive disruption re-planning.

---

## 2. What did we Actually Research?
We investigated the fundamental hypothesis:
> *"Forecast uncertainty should not be evaluated only at the prediction layer. When propagated through physical maritime constraints and downstream optimization, uncertainty may alter the feasible solution space, induce asymmetric decision fragility, and govern selective procurement abstention."*

---

## 3. What did we Find?
1. **Asymmetric Decision Fragility:** Port depth and vessel deadweight act as rigid non-linear boundaries that insulate physical vessel and port selection from freight uncertainty ($\text{PDFR} = 0.00\%$), while procurement timing is acutely fragile ($\text{TDFR} = 50\%\text{--}100\%$).
2. **CQR Interval Width Flags Macro Risk:** Conformal prediction band width strongly predicts severe false-breakout positioning mistakes ($\text{AUC} = 0.6719$, $p < 0.01$).
3. **Selective Abstention Works:** Gating decisions on calibrated interval width ($\tau = 1.35\times$) eliminates **$52.33\%$ of false-breakout chartering errors** ($86 \rightarrow 41$) at $61.11\%$ decision coverage.
4. **Boundary Crossing is Degenerate:** In $99.65\%$ of test cases, CQR intervals span spot rates, proving local boundary crossing is uninformative in bulk freight.

---

## 4. What is Validated vs Proof-of-Concept?
- **Validated Empirical Core:** LightGBM turning-point inflections ($\text{F1} = 59.51\%$), Split-CQR finite-sample coverage ($88.19\%\text{--}95.83\%$), and held-out selective abstention error reduction ($52.33\%$).
- **Controlled Computational Experiment:** 2D Fragility Surface ($N=360$), Negative Control sanity checks, and Paired Wilcoxon landed cost comparisons ($p = 5.42\times 10^{-11}$).
- **Controlled Simulation / POC:** ST-GNN 8-node corridor delay propagation, synthetic port draft siltation cuts, and adaptive port re-routing.

---

## 5. What is NOT Implemented?
- No live commercial Baltic Exchange API subscription.
- No real-time satellite AIS WebSocket stream (Spire/MarineTraffic).
- No live Port Community System (PCS 1x) electronic data interchange.
- No live weather radar scrapers.
- No production cloud database (PostgreSQL/TimescaleDB) or graph DB (FalkorDB/Neo4j).
- No enterprise SSO/RBAC user authentication.

---

## 6. What are we Demonstrating Right Now?
A self-contained, fully interactive local prototype (`prototype/PRIMARINE-demo/index.html`) demonstrating:
- Real-time physical feasibility checking against authentic vessel and port specifications.
- Split-CQR uncertainty gating triggering `ENTER_NOW`, `DEFER`, and `ABSTAIN` states.
- Multi-objective total landed cost calculation per metric tonne.
- Live interactive disruption simulation (Paradip draft cut $\rightarrow$ automated re-routing to Visakhapatnam with $+14.79\text{ \$/MT}$ recovery).
- Immutable decision audit trail logging.
