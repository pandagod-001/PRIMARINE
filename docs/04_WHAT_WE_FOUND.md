# PRIMARINE — Empirical Research Findings Summary

**Document Version:** 1.0.0 (Frozen Consolidation)  
**Status:** Canonical Reference  
**Scope:** Consolidated summary of all positive, negative, and controlled research findings.

---

## 1. Master Findings Summary Table

| Research Area | Metric / Hypothesis | Benchmark Baseline | PRIMARINE Finding | Evidence Status | Impact / Interpretation |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Point Forecasting** | Step-ahead Point MAE | Persistence: **0.4175** | LightGBM: **0.4644** | VALIDATED | LightGBM does not beat Persistence on raw point MAE; freight prices resemble random-walk step levels. |
| **Inflection Detection** | 7-Day Turning Point F1 ($\ge \pm 4\%$) | Persistence: **0.00%**<br>AR(5): **27.18%** | LightGBM: **59.51%** (+32.33 pp) | VALIDATED | Model captures macro-regime turning points and cyclical trends effectively. |
| **Directional Accuracy** | Daily Sign Movement | 5-Day SMA: **50.70%** | LightGBM: **59.15%**<br>XGBoost: **60.56%** | VALIDATED | Moderate directional signal; valuable as feature input but insufficient alone for automated execution. |
| **Uncertainty Calibration** | Split-CQR 90% Coverage | Target: **90.00%** | Observed: **88.19%–95.83%** ($q_{\text{calib}} = 0.8415$) | VALIDATED | Non-asymptotic, distribution-free marginal finite-sample validity under exchangeability. |
| **Stress Coverage** | COVID-19 Covariate Shift | Target: **90.00%** | Observed: **50.59%** | VALIDATED | Calibration degrades under catastrophic structural macroeconomic breaks. |
| **Physical Feasibility** | Decision Flip Rate (PDFR) | Baseline: N/A | **0.00%** (Tested Dry-Bulk) | VALIDATED | Draft, DWT, and berth constraints enforce hard, invariant physical boundaries. |
| **Timing Fragility** | Decision Flip Rate (TDFR) | Baseline: N/A | **50.00%–100.00%** | VALIDATED | Demonstrates Asymmetric Fragility: physical choices are robust; timing choices are fragile. |
| **False-Breakout Signal** | CQR Width vs False Breakouts | Random: 0.5000 | $\text{AUC} = \mathbf{0.6719}$ ($p < 0.01$)<br>High W = **40.25%** vs Low W = **23.39%** | CONTROLLED | Calibrated interval width serves as a valid macro risk and false-breakout exposure signal. |
| **Boundary Crossing** | Spot Delta Discrimination | Target: $\text{AUC} > 0.70$ | Observed: $\text{AUC} = \mathbf{0.5025}$ (99.65% cross) | NEGATIVE RESULT | Degenerate mechanism. Naive boundary crossing cannot serve as an operational filter. |
| **Directional Error Correlation** | Sign Error vs CQR Width | Target: Positive Corr | Observed: $\text{AUC} = \mathbf{0.4487}$ | NEGATIVE RESULT | CQR width reflects volatility and epistemic spread, NOT single-step directional sign correctness. |
| **Selective Abstention** | False-Breakout Event Reduction | Forced: 86 events | Gated ($\tau = 1.35\times$): **41 events** (**-52.33%**) | CONTROLLED | Pre-calibrated threshold cuts false breakouts by half; retains 61.11% decision coverage. |
| **Economic Trade-off** | Nominal Freight Premium | Baseline: $0.00 | Gated: **+$0.0334 / MT** (**+0.453%**) | CONTROLLED | Acts as a low-cost insurance premium against catastrophic demurrage and bad locks. |
| **Downstream Significance** | E5 Gated vs E2 Baseline | Null Hypothesis ($p \ge 0.05$) | Paired Wilcoxon: $\mathbf{p = 5.42 \times 10^{-11}}$ ($W = 11530.0$) | VALIDATED | Statistically confirms downstream decision divergence from unconstrained baselines. |

---

## 2. Definitive Research Contribution

> *"PRIMARINE investigates conformal uncertainty-gated decision support for maritime freight procurement, demonstrating that calibrated forecast-interval width can serve as a regime-level signal for false-breakout exposure and support selective abstention under hard physical vessel-port feasibility constraints."*
