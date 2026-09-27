# PRIMARINE / PRIMARINE — Final Release Manifest

**Project Identity:** PRIMARINE  
**System Type:** Uncertainty-Aware Maritime Freight Decision Intelligence Platform  
**Research Title:** Conformal Uncertainty-Gated Decision Support for Maritime Freight Procurement  
**Audit Status:** 100% Validated (Release Gate Approved)  
**Date:** September 2026

---

## 1. Distribution Repositories

- **Research Repository:** `https://github.com/pandagod-001/PRIMARINE_Research-.git`
- **Product Repository:** `https://github.com/pandagod-001/PRIMARINE.git`
- **Google Drive Package:** Local directory `PRIMARINE_GOOGLE_DRIVE_PACKAGE/` and archives.

---

## 2. Verified Research Ground Truth

- **Point MAE:** Persistence (`0.4175`) vs LightGBM (`0.4644`) — LightGBM does not beat Persistence on raw point MAE.
- **7-Day Inflection Detection:** LightGBM **F1 = 59.51%** (+32.33 pp over AR-5 baseline: 27.18%).
- **Split-CQR Coverage:** Nominal 90% coverage $\rightarrow$ **88.19% to 95.83%** empirical held-out test coverage ($q_{\text{calib}} = 0.8415$).
- **Pandemic Stress Coverage:** **50.59%** under COVID-19 macroeconomic shock.
- **Physical Feasibility Invariance:** **PDFR = 0.00%** on tested dry-bulk constraints.
- **Timing Fragility:** **TDFR = 50%–100%** across tested perturbation envelopes.
- **False-Breakout Risk Association:** High W = 40.25% vs Low W = 23.39% ($\text{AUC} = \mathbf{0.6719}$, $p < 0.01$).
- **Selective Abstention:** **52.33% reduction in observed false breakouts** ($86 \rightarrow 41$) at $\tau = 1.35\times$ with 61.11% coverage (+0.453% cost premium).
- **Downstream Optimization Divergence:** Paired Wilcoxon $W = 11530.0$, $\mathbf{p = 5.42 \times 10^{-11}}$.
- **Negative Results Preserved:** Boundary crossing is degenerate ($\text{AUC} = 0.5025$); directional sign error does not correlate with CQR width ($\text{AUC} = 0.4487$).

---

## 3. Reality State Taxonomy

1. `VALIDATED RESEARCH` — Empirically verified models, CQR calibration, fragility surfaces, and Wilcoxon significance.
2. `CONTROLLED / PROOF-OF-CONCEPT` — Synthetic 8-node ST-GNN cascade simulator, synthetic scenario injections.
3. `PROTOTYPE IMPLEMENTATION` — Standalone local vertical-slice demonstrator (`prototype/PRIMARINE-demo/`).
4. `PLANNED / FUTURE WORK` — Live Baltic/AIS/PCS provider adapters, global real-AIS ST-GNN.
