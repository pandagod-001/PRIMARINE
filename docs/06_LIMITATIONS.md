# PRIMARINE — Known Limitations & Research Boundaries

**Document Version:** 1.0.0 (Frozen Consolidation)  
**Status:** Canonical Reference  
**Purpose:** Explicit disclosure of methodological constraints, dataset limitations, and operational boundaries.

---

## 1. Experimental & Methodological Limitations

### Limitation L-01: Exchangeability and Macroeconomic Regime Breaks
- **Constraint:** Split-CQR finite-sample coverage guarantees depend mathematically on the assumption of exchangeability between calibration and test data.
- **Observed Impact:** Under catastrophic structural breaks (e.g., the March 2020 COVID-19 pandemic shock), empirical coverage degraded to **50.59%**.
- **Operational Rule:** System must trigger automatic recalibration or fallback to conservative expert rules when macroeconomic volatility breaks historical bounds.

### Limitation L-02: Specificity of Physical Feasibility Testbed
- **Constraint:** The finding of zero physical decision flips (**PDFR = 0.00%**) was evaluated on a curated testbed of East Coast India dry-bulk ports (Paradip, Dhamra, Haldia) across Capesize, Panamax, and Supramax vessel classes with standard coal/iron ore deadweight envelopes.
- **Boundary:** This invariance **CANNOT** be generalized unconditionally to all maritime segments (e.g., container liner networks with dynamic transshipment flexibility, or liquid chemicals with parceling flexibility).

### Limitation L-03: Pre-Calibrated Threshold Generalization
- **Constraint:** The selective abstention threshold $\tau = 1.35 \times \text{validation median width}$ was pre-calibrated on the validation split of the Baltic Dry Index series.
- **Boundary:** $\tau = 1.35\times$ is **NOT** an analytically optimal universal constant. Deploying on new trade routes (e.g., clean tanker Baltic Clean Index or LNG carrier rates) requires route-specific quantile re-calibration.

### Limitation L-04: ST-GNN Synthetic Validation Scope
- **Constraint:** The Spatio-Temporal Graph Neural Network (ST-GNN) disruption cascade engine was evaluated on an 8-node synthetic graph topology with simulated delay injections.
- **Boundary:** It has **NOT** been validated on multi-gigabyte real-world satellite AIS feeds. Global real-AIS validation remains classified as `FUTURE RESEARCH`.

---

## 2. Technical & Data Limitations

### Limitation L-05: Prototype Offline Data Fixtures
- **Constraint:** The interactive demonstrator (`prototype/PRIMARINE-demo/`) uses curated static JSON fixtures (`fixtures.json`) to allow standalone offline execution without live paid enterprise subscriptions.
- **Boundary:** It does not stream live API data in its current local demonstrator form.

### Limitation L-06: Directional Movement Signal Bounds
- **Constraint:** Directional classification accuracy of tree-based models is capped at approximately **59%–60%**.
- **Boundary:** Models cannot reliably forecast daily binary price fluctuations on noisy spot series; uncertainty gating must be used to mitigate false commitments.

---

## 3. Scientific Integrity Statement

PRIMARINE does not claim:
- Universal Point-Forecast Superiority (Persistence wins on point MAE: 0.4175 vs 0.4644).
- Flawless Market Directional Prediction (AUC = 0.4487 for sign errors).
- Spot Boundary-Crossing Discrimination (AUC = 0.5025; degenerate mechanism).
- Connected Production APIs in the Local Prototype.
- Real-AIS ST-GNN Validation.
