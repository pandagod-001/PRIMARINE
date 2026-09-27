# PRIMARINE — The Research & Development Journey

**Document Version:** 1.0.0 (Consolidated Chronology)  
**Status:** Canonical Reference  
**Audience:** Researchers, Evaluators, Technical Reviewers, and Engineers

---

## 1. Chronological Research Journey

The development of PRIMARINE followed a disciplined, hypothesis-driven trajectory from initial problem discovery to rigorous empirical validation and prototype implementation.

```
[ Phase 1: Problem Inception & Ideation ]
  Identify blind spots in commercial chartering: point-forecast failure & physical disconnect.
                    ↓
[ Phase 2: Predictive Modeling Benchmarks ]
  Train baselines on Baltic Dry Index (2018–2024). Discover point MAE parity but turning-point superiority.
                    ↓
[ Phase 3: Conformal Uncertainty Quantification ]
  Implement Split-CQR to provide finite-sample marginal coverage guarantees (88.19%–95.83%).
                    ↓
[ Phase 4: Downstream Fragility Discovery ]
  Generate multi-dimensional perturbation surfaces. Discover Asymmetric Fragility: PDFR=0% vs TDFR=50-100%.
                    ↓
[ Phase 5: Decision-Boundary & Negative Findings ]
  Test boundary-crossing filter (Degenerate: AUC 0.5025). Discover CQR width associates with false breakouts (AUC 0.6719).
                    ↓
[ Phase 6: Selective Abstention & Risk Frontiers ]
  Calibrate validation threshold (tau = 1.35x). Prove 52.33% false-breakout cut at +0.453% cost premium.
                    ↓
[ Phase 7: Research Package Freeze ]
  Lock all datasets, metrics, and scripts. Author formal publications, claims, and reproduction manifests.
                    ↓
[ Phase 8: Prototype & Blueprint Consolidation ]
  Build interactive local demonstrator (prototype/PRIMARINE-demo/) and specify enterprise architecture.
```

---

## 2. Detailed Phase Narrative

### Phase 1: Inception & Challenge
Commercial maritime freight contracts involve millions of dollars per fixture. Teams charter vessels based on single-point price estimates from econometric or deep learning models. When market shocks occur, these deterministic models break down, locking charterers into expensive contracts. PRIMARINE was conceived to unite hard physical shipping constraints with uncertainty-aware decision intelligence.

### Phase 2: Forecasting Benchmark Surprises
Initial experiments on Baltic Dry Index data revealed a critical insight: **LightGBM does not beat a simple random-walk Persistence baseline on single-step point MAE (0.4644 vs 0.4175).** However, evaluating macro turning points revealed that LightGBM captures 7-day rate shifts ($\ge \pm 4\%$) with **F1 = 59.51%**, outperforming AR(5) (27.18%) and Persistence (0.00%).

### Phase 3: Conformal Calibration
To provide rigorous uncertainty bounds, we integrated Split Conformalized Quantile Regression (Split-CQR). By calibrating non-conformity scores on held-out calibration splits ($q_{\text{calib}} = 0.8415$), PRIMARINE achieved empirical coverage of **88.19% to 95.83%** under normal market dynamics.

### Phase 4: The Discovery of Asymmetric Fragility
We evaluated how forecast uncertainty propagated into procurement decisions. On East Coast India dry-bulk fixtures (Paradip, Dhamra, Haldia), the **Physical Decision Flip Rate was 0.00%**—draft and deadweight hard limits strictly dictated valid vessel-port pairings regardless of rate uncertainty. Conversely, the **Timing Decision Flip Rate was 50%–100%**, proving that procurement timing is acutely vulnerable to forecast errors.

### Phase 5: Negative Findings and Boundary Refinement
We hypothesized that abstaining when the prediction interval crossed the current spot price would prevent timing errors. Rigorous testing revealed a **crucial negative result:** 99.65% of all intervals crossed the spot boundary, resulting in an $\text{AUC} = 0.5025$ (completely random). We preserved this negative result and refocused on interval width, discovering that high width acts as a reliable macro filter for false breakouts ($\text{AUC} = 0.6719, p < 0.01$).

### Phase 6: Selective Prediction & Downstream Proof
We established a pre-calibrated abstention threshold ($\tau = 1.35 \times \text{validation median width}$). At this threshold, PRIMARINE **reduced observed false-breakout events by 52.33% (from 86 to 41 events)** while maintaining 61.11% decision coverage. Paired Wilcoxon testing proved extreme statistical significance ($p = 5.42 \times 10^{-11}$).

### Phase 7 & 8: Research Freeze and Vertical Demonstrator
Having established rigorous empirical proof, we froze the scientific branch, locked the claims matrix, and built an interactive vertical-slice demonstrator (`prototype/PRIMARINE-demo/`) showcasing the complete end-to-end decision chain.
