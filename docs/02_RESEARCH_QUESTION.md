# PRIMARINE — The Scientific Research Question

**Document Version:** 1.0.0 (Frozen Consolidation)  
**Status:** Canonical Reference  
**Classification:** Core Research Methodology

---

## 1. Context & Motivation

While the complete PRIMARINE enterprise platform addresses end-to-end maritime logistics, the scientific research phase was designed to answer a fundamental, unaddressed question at the intersection of machine learning, conformal prediction, and operations research:

> *"When machine learning models generate probabilistic freight forecasts, how does forecast uncertainty propagate into downstream discrete procurement decisions, and can distribution-free prediction intervals serve as an effective risk gate to prevent costly decision failures under rigid physical constraints?"*

---

## 2. Formal Research Questions (RQ)

The PRIMARINE experimental program formulated four explicit, falsifiable research questions:

### RQ 1: Inflection Detection vs Point Forecasting
- *Can machine learning models overcome the random-walk nature of freight rate levels to accurately detect macro-regime inflection points ($\ge \pm 4\%$ 7-day rate shifts)?*
- **Empirical Answer:** **YES.** While LightGBM does not beat Persistence on raw point MAE (`0.4644` vs `0.4175`), it achieves **F1 = 59.51%** on turning points compared to **0.00%** for Persistence and **27.18%** for AR(5) (+32.33 percentage point improvement).

### RQ 2: Asymmetric Decision Fragility
- *Do physical vessel-port feasibility constraints and temporal procurement timing decisions exhibit symmetric sensitivity to forecast uncertainty?*
- **Empirical Answer:** **NO (Asymmetric Fragility).** Physical feasibility decisions are invariant (**PDFR = 0.00%** on tested dry-bulk constraints), whereas procurement timing decisions are acutely fragile (**TDFR = 50%–100%** under uncertainty perturbations).

### RQ 3: Conformal Interval Width as a Decision Gate
- *Does the width of a Split-CQR prediction interval correlate with decision risk and false-breakout exposure during procurement timing?*
- **Empirical Answer:** **YES.** High interval width is observationally associated with greater false-breakout exposure (Risk Difference = `+16.86 percentage points`, $p < 0.01$, $\text{AUC} = 0.6719$).
- **Boundary / Negative Finding:** CQR width **DOES NOT** predict binary single-step directional sign errors ($\text{AUC} = 0.4487$), and spot boundary crossing is degenerate ($\text{AUC} = 0.5025$).

### RQ 4: Selective Abstention Risk Trade-off
- *Can a pre-calibrated interval-width threshold systematically reduce false-breakout events in procurement execution without unacceptable cost inflation?*
- **Empirical Answer:** **YES.** A pre-calibrated threshold ($\tau = 1.35 \times \text{validation median width}$) **reduces observed false-breakout events by 52.33%** (from 86 to 41 events) with 61.11% decision coverage at a nominal cost premium of `+$0.0334/MT` (`+0.453%`). Downstream optimization significance is verified at $p = 5.42 \times 10^{-11}$.

---

## 3. Position Within the Broader PRIMARINE System

```
[ Complete PRIMARINE Platform ]
       ├── Data Ingestion & Live AIS Streams (Planned Engineering)
       ├── Maritime Knowledge Graph (Planned Engineering)
       ├── [ SCIENTIFIC RESEARCH INVESTIGATION ]  <-- FROZEN RESEARCH CORE
       │      ├── LightGBM Turning-Point Dynamics (RQ1)
       │      ├── Split-CQR Finite-Sample Calibration
       │      ├── Asymmetric Fragility (PDFR vs TDFR) (RQ2)
       │      ├── Conformal False-Breakout Filter (RQ3)
       │      └── Selective Abstention Policy (RQ4)
       ├── User Interface Cockpit (Prototype Demonstrator)
       └── Global Real-AIS ST-GNN (Future Research)
```
