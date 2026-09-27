# PRIMARINE — Current Implementation & Project Status

**Document Version:** 1.0.0 (Consolidated Status)  
**Status:** Canonical Reference  
**Audit Date:** September 2026

---

## 1. System Implementation Matrix

The table below provides a transparent audit of all components across the PRIMARINE ecosystem, categorized by reality state:

| Component / Subsystem | Implementation Reality State | Current Repository Location | Status & Verification |
| :--- | :--- | :--- | :--- |
| **Baseline Point Forecasting** | `1. VALIDATED RESEARCH` | `scripts/experiments/01_baseline_forecasting.py` | LightGBM, XGBoost, AR, SMA evaluated on Baltic Dry Index (2018–2024). |
| **Inflection Point Detection** | `1. VALIDATED RESEARCH` | `results/tables/inflection_metrics.csv` | 59.51% F1 verified (+32.33 pp over AR baseline). |
| **Split-CQR Uncertainty Engine** | `1. VALIDATED RESEARCH` | `scripts/experiments/02_cqr_calibration.py` | Nominal 90% coverage verified (88.19%–95.83% empirical test coverage). |
| **Physical Feasibility Invariance** | `1. VALIDATED RESEARCH` | `scripts/experiments/03_feasibility_invariance.py` | PDFR = 0.00% verified across Paradip, Dhamra, Haldia dry-bulk fixtures. |
| **Asymmetric Fragility Surface** | `1. VALIDATED RESEARCH` | `scripts/experiments/08_fragility_surface.py` | Multi-dimensional perturbation surfaces generated (TDFR = 50%–100%). |
| **False-Breakout Risk Correlation** | `1. CONTROLLED EXPERIMENT` | `research/experiments/10_timing_flip_threshold.py` | High vs Low width risk difference verified (+16.86 pp, AUC = 0.6719, $p < 0.01$). |
| **Selective Abstention Policy** | `1. CONTROLLED EXPERIMENT` | `research/experiments/09_abstention_vs_forced.py` | 52.33% false breakout reduction verified at $\tau = 1.35\times$ ($p = 5.42 \times 10^{-11}$). |
| **Negative Results Preservation** | `1. NEGATIVE RESULT` | `research/experiments/13_boundary_proximity.py` | Boundary crossing degeneracy (AUC = 0.5025) and sign error non-correlation locked. |
| **Interactive UI Cockpit** | `2. PROTOTYPE IMPLEMENTATION` | `prototype/PRIMARINE-demo/` | Functional local HTML5/CSS3/JS demonstrator with dark-mode glassmorphic UI. |
| **Client Decision Engine** | `2. PROTOTYPE IMPLEMENTATION` | `prototype/PRIMARINE-demo/js/engine.js` | Client-side execution of Split-CQR uncertainty gating and multi-objective ranking. |
| **Curated Demo Fixtures** | `2. PROTOTYPE IMPLEMENTATION` | `prototype/PRIMARINE-demo/data/fixtures.json` | 8 Indian Ocean ports, 5 vessel classes, 3 disruption scenarios, market series. |
| **Synthetic ST-GNN Engine** | `2. PROOF OF CONCEPT` | `scripts/experiments/07_stgnn_poc.py` | 8-node synthetic graph disruption cascade simulator (Pearson $r = 0.842$). |
| **Provider Adapter Architecture** | `3. PLANNED ENGINEERING` | `docs/api/PROVIDER_ADAPTER_ARCHITECTURE.md` | Abstract Python adapter interfaces for Baltic, MarineTraffic, ERA5, PCS. |
| **Production Cloud Backend** | `3. PLANNED ENGINEERING` | `docs/PRIMARINE_PRODUCT_BLUEPRINT/03_ENTERPRISE_SYSTEM_ARCHITECTURE.md` | FastAPI microservices, TimescaleDB, FalkorDB Knowledge Graph schemas. |
| **Enterprise RBAC & Auth** | `3. PLANNED ENGINEERING` | `docs/PRIMARINE_PRODUCT_BLUEPRINT/13_SECURITY_COMPLIANCE_AND_ENTERPRISE_GOVERNANCE.md` | OAuth2 / OIDC authentication and role-based access control architecture. |
| **Global Real-AIS ST-GNN** | `4. FUTURE RESEARCH` | `assets/architecture/real_ais_stgnn_blueprint.png` | Distributed ST-GNN architecture on multi-billion message AIS streams. |

---

## 2. Integrity Verification Check

- [x] **No Phantom Implementations:** No planned API is claimed as live-connected.
- [x] **No Metric Fabrication:** All metrics originate from reproducible script executions.
- [x] **No Narrative Smoothing:** All negative results and stress degradations are prominently displayed.
- [x] **Four-Reality Separation Enforced:** Code, blueprints, prototypes, and future hypotheses are strictly separated.
