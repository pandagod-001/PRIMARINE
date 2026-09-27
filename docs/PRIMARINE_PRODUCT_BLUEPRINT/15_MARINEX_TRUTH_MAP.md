# PRIMARINE — Definitive Project Truth Map

**Document:** `docs/PRIMARINE_PRODUCT_BLUEPRINT/15_PRIMARINE_TRUTH_MAP.md`  
**Classification:** Absolute Forensic Truth Map  
**Date:** 2026-09-26  

---

## 1. WHAT WE KNOW (Scientifically & Empirically Grounded)

1. **Point forecasting alone causes procurement failures:** Minimizing statistical error ($L_2$ loss) does not prevent severe chartering mistakes because unconstrained forecasts over-commit during volatile rate expansions.
2. **Physical feasibility dominates freight noise:** Physical port drafts ($17.1\text{m}$ vs $11.5\text{m}$) and vessel deadweights strictly constrain ship selection ($\text{PDFR} = 0.00\%$), while procurement timing is acutely fragile to uncertainty ($\text{TDFR} = 50\%\text{--}100\%$).
3. **Conformal interval width flags tail risk:** Higher CQR interval width indicates volatile market expansions where false breakouts surge to $40.25\%$ ($\text{AUC} = 0.6719$, $p < 0.01$).
4. **Selective abstention reduces false breakout commitments:** Gating charter decisions on calibrated interval width ($\tau = 1.35\times$) eliminates $52.33\%$ of false breakout entries at $61.11\%$ decision coverage.
5. **Boundary crossing is uninformative:** In $99.65\%$ of test cases, CQR intervals span spot rates, making local boundary crossing degenerate ($\text{AUC} = 0.5025$).
6. **Abstention is an insurance trade-off:** Accepts a $+0.453\%$ ($+\$0.0334/\text{MT}$) nominal cost difference to protect against adverse false-breakout positioning.

---

## 2. WHAT WE BUILT (Implemented & Runnable in Workspace)

1. **Validated Algorithmic Pipeline:** Python scripts ingesting 1,920 daily market rows, training LightGBM turning-point models, and calibrating Split-CQR intervals.
2. **Comprehensive Research & Audit Package:** `research/PRIMARINE_RESEARCH_PACKAGE/` containing frozen reports, claim matrices, prior art reviews, and 10 publication charts.
3. **Interactive Local Decision Cockpit:** `prototype/PRIMARINE-demo/index.html` executing real-time feasibility checking, CQR gating, landed cost optimization, and live disruption re-routing.
4. **Controlled Simulation Testbeds:** 2D Fragility Surface ($N=360$), Negative Control sanity checks, and 8-node ST-GNN spatial shock models.

---

## 3. WHAT WE ARE BUILDING (Near-Term Prototype Refinements)

1. **Expanded Deterministic Scenario Catalog:** Adding 25 global ports, 50 bulk shipping corridors, and 100 historical shipment fixtures to the prototype data store.
2. **Interactive Parameter Controls:** Adding user-adjustable risk tolerance sliders ($\tau$ multiplier) directly in the decision cockpit.
3. **Counterfactual Dredging Sandbox:** Allowing users to simulate the cost impact of dredging a specific berth by $+1.0\text{m}$.

---

## 4. WHAT WE PLAN TO BUILD (Post-Selection Production System)

1. **Live External API Connectors:** Baltic Exchange commercial API, Spire Maritime Satellite AIS WebSocket streams, NOAA/Open-Meteo weather radar, and Port Community System (PCS 1x) gateways.
2. **Enterprise Persistence & Graph Database:** PostgreSQL/TimescaleDB time-series storage paired with FalkorDB / Neo4j maritime topology graphs.
3. **Multi-Vessel Combinatorial Fleet Solver:** Mixed-Integer Linear Programming (MILP) solving simultaneous multi-vessel assignments across annual procurement laycans.
4. **Production Security & Enterprise SSO:** Multi-tenant OAuth2/JWT authentication with Role-Based Access Control (RBAC) and automated webhook alerts.
