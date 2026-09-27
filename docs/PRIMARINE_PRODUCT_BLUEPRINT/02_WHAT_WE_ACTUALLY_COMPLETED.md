# PRIMARINE — Completed Research & Validated Proofs-of-Concept

**Document:** `docs/PRIMARINE_PRODUCT_BLUEPRINT/02_WHAT_WE_ACTUALLY_COMPLETED.md`  
**Status:** Frozen Research Package Reference  

---

## 1. Executive Summary of Completed Research

During the research phase, we conducted an exhaustive, multi-tier experimental evaluation on the decision-intelligence layers of PRIMARINE. 

We preserved strict scientific boundaries across three tiers:
1. **Validated Empirical Core:** Evaluated on 1,920 authentic daily financial and commodity market observations (2018–2025).
2. **Controlled Computational Experiments:** Evaluated on held-out test splits ($N=288$) and 2D constraint tightness perturbation grids ($N=360$).
3. **Controlled Proof-of-Concept Simulations:** Spatial shock propagation evaluated over an authentic 8-node, 11-corridor maritime graph.

---

## 2. Quantitative Experimental Milestones

### A. Freight Rate & Turning-Point Point Forecasting [VALIDATED EMPIRICAL]
- **Target:** 7-day cumulative forward freight rate direction and inflection ($\ge \pm 4.0\%$).
- **Point Forecasting MAE:**
  - Naive Persistence Baseline: $\text{MAE} = \mathbf{0.4175}$
  - LightGBM Regressor (10-seed average): $\text{MAE} = \mathbf{0.4644}$
- **7-Day Inflection Detection ($\ge \pm 4.0\%$ Movements):**
  - Naive Persistence: $\text{F1} = \mathbf{0.00\%}$ (Completely blind to turns)
  - Econometric AR(5) Baseline: $\text{F1} = \mathbf{27.18\%}$
  - Technical 5-Day SMA: $\text{F1} = \mathbf{26.47\%}$
  - LightGBM Inflection Engine: $\text{F1} = \mathbf{59.51\%}$ (**$+32.33\text{ pp}$ over AR(5)**)
- **5-Day Directional Movement Accuracy:**
  - 5-Day SMA: $\mathbf{50.70\%}$ (Random-walk level)
  - LightGBM: $\mathbf{59.15\%}$
  - XGBoost: $\mathbf{60.56\%}$

---

### B. Conformal Uncertainty Quantification (Split-CQR) [VALIDATED EMPIRICAL]
- **Calibration Method:** Non-parametric Split Conformalized Quantile Regression ($q_{\text{calib}} = 0.8415$).
- **Test Set Coverage:** **$88.19\%$ to $95.83\%$** observed coverage under a nominal $90.0\%$ target.
- **Mean Interval Width ($W$):** $\mathbf{5.76\text{ to }7.62\ \$/\text{MT}}$ across held-out test scenarios.
- **COVID-19 Stress Test:** Observed coverage dropped to $\mathbf{50.59\%}$ during the March 2020 crash, proving that conformal intervals dynamically flag extreme regime shifts.

---

### C. Asymmetric Decision Fragility Surface [CONTROLLED COMPUTATIONAL EXPERIMENT]
Evaluated across $360$ scenario evaluations (6 uncertainty scales $\times$ 3 constraint tightness regimes):
- **Physical Allocation Flip Rate (PDFR):** **$0.00\%$**  
  *Finding:* Discrete physical constraints (e.g. Paradip $17.1\text{m}$ draft vs Haldia $11.5\text{m}$ draft) strictly bound vessel/port selection, making physical allocations robust against continuous freight variations under tested fixtures.
- **Timing Decision Flip Rate (TDFR):** **$50.00\% \text{ to } 100.00\%$**  
  *Finding:* Procurement timing is acutely vulnerable to uncertainty, flipping actions between `ENTER_NOW` and `DEFER`.
- **Baseline-Plan Feasibility Retention (BPFR):** **$1.00$ ($100.0\%$)** across all tested perturbations.

---

### D. Selective Abstention & Risk-Cost Trade-Off [CONTROLLED HELD-OUT EXPERIMENT]
Evaluated on $288$ held-out test scenarios:
- **Macro-Regime Volatility Signal:** High CQR interval width ($W > \tau$) strongly predicted severe false-breakout capital commitments ($\text{AUC} = \mathbf{0.6719}$, High Width rate $= 40.25\%$ vs Low Width $= 23.39\%$, Risk Diff $= \mathbf{+16.86\text{ pp}}$ $[6.14, 28.52]$, $p < 0.01$).
- **False Breakout Elimination:** Pre-calibrated width abstention ($\tau = 1.35 \times \text{Val Median}$) **reduced false breakouts by $52.33\%$** (from $86$ forced errors down to $41$).
- **Decision Coverage:** **$61.11\%$** ($38.89\%$ abstention rate).
- **Nominal Landed Cost Trade-Off:** $+\$0.0334/\text{MT}$ ($+0.453\%$), representing an operational downside insurance premium.
- **Downstream Optimization (E5 vs E2):** Full adaptive pipeline achieved statistically significant cost reduction over unconstrained point forecasts (Paired Wilcoxon $W = 11530.0$, $\mathbf{p = 5.42 \times 10^{-11}}$).

---

### E. Explicit Negative Results Preserved [SCIENTIFIC INTEGRITY]
1. **Decision-Boundary Crossing ($\text{AUC} = 0.5025$):** $99.65\%$ of $90\%$ CQR bands crossed the spot price because interval width exceeds weekly rate shifts. Local boundary crossing is uninformative in shipping.
2. **Width vs Binary Direction Error ($\text{AUC} = 0.4487$):** Interval width reflects macro volatility, not pointwise sign correctness.
3. **Normalized Decision Margin ($\text{AUC} \approx 0.51$):** Margin distance is secondary to macro interval width.

---

### F. Spatial Disruption Simulation (ST-GNN) [CONTROLLED PROOF-OF-CONCEPT]
- Evaluated over an authentic 8-node, 11-edge maritime network connecting Australian/Indonesian coal origins to Indian East Coast discharge ports.
- **Spatial Shock Routing:** Demonstrates proactive corridor re-routing, saving an estimated **$\$0.49/\text{MT}$** in congestion demurrage.
- **Adaptive Disruption Recovery:** Re-routing during port draft cuts (D3) recovered **$+\$14.79/\text{MT}$** over static commitment.
- **Negative Finding:** ST-GNN does *not* beat LightGBM in univariate rate forecasting ($\text{MAE} \approx 0.46$ vs $0.42$); its value is strictly spatial delay propagation.
