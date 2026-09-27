# PRIMARINE — Master Component Status & Reality Matrix

**Document:** `docs/PRIMARINE_PRODUCT_BLUEPRINT/12_MASTER_STATUS_MATRIX.md`  
**Classification:** Transparent Component Status Audit  

---

## 1. Master System Status Matrix

| Major Component | Original Product Vision | Research Validation Status | Prototype Status | Production Status | Next Action |
|---|---|---|---|---|---|
| **Freight Market Forecasting** | 7-day forward freight index & turning points ($\ge \pm 4\%$) | **VALIDATED** (LightGBM $\text{F1}=59.51\%$, $+32\text{ pp}$ over AR(5)) | **IMPLEMENTED** (Badge & 7-day metric) | Local Model Checkpoint | Expand training to multi-corridor Baltic fixtures |
| **Conformal Uncertainty Layer** | Distribution-free prediction intervals (Split-CQR) | **VALIDATED** ($88.19\%\text{--}95.83\%$ coverage, $q_{\text{calib}}=0.8415$) | **IMPLEMENTED** (CQR interval width display) | Local Calibration Array | Implement online dynamic re-calibration |
| **Physical Feasibility Engine** | Automated validation of draft, LOA, beam & DWT | **VALIDATED** ($\text{PDFR}=0.00\%$, $\text{BPFR}=1.0$) | **IMPLEMENTED** (Interactive feasibility matrix) | Python Validation Logic | Connect to Port Authority Berth Master APIs |
| **Selective Abstention Gate** | Gating commitments during extreme market volatility | **VALIDATED** ($52.33\%$ False Breakout Cut, $\text{AUC}=0.6719$) | **IMPLEMENTED** (`ABSTAIN` state & rationale) | Pre-Calibrated $\tau=1.35\times$ Rule | Add user-adjustable risk tolerance slider |
| **Multi-Objective Cost Solver** | Total landed cost optimization ($/MT) | **VALIDATED** (Paired Wilcoxon $p=5.42\times 10^{-11}$) | **IMPLEMENTED** (Live landed cost calculation) | Deterministic Cost Function | Add CII Carbon Intensity penalty weights |
| **Adaptive Disruption Re-Planning**| Dynamic re-routing during port bottlenecks | **CONTROLLED SIMULATION** (+$3.90/MT average recovery) | **IMPLEMENTED** (Interactive disruption simulator) | Re-Routing Rule Engine | Connect live storm & port congestion feeds |
| **Spatio-Temporal GNN (ST-GNN)** | Network-level shock propagation across shipping lanes | **CONTROLLED POC** (8 Nodes / 11 Corridors) | **NOT INCLUDED IN LOCAL UI** | Controlled Python Script | Scale graph to global container/bulk nodes |
| **Maritime Knowledge Graph** | Graph topology of ports, berths, and corridors | **STATIC PYTHON CATALOG** | **IMPLEMENTED** (`PRIMARINE_DATA` store) | Hardcoded JavaScript/Python | Deploy FalkorDB / Neo4j Graph DB |
| **Satellite AIS Stream** | Live Capesize/Panamax vessel trajectory tracking | **NOT IMPLEMENTED** | **STATIC SIMULATION** | Not Connected | Provision Spire Maritime WebSocket stream |
| **Port EDI Telemetry (PCS 1x)** | Live port queues and draft notices | **NOT IMPLEMENTED** | **STATIC PRESETS** | Not Connected | Formalize API gateway with Indian Major Ports |
| **Enterprise Authentication & RBAC**| Multi-tenant SSO for steel/power procurement teams | **NOT IMPLEMENTED** | **NOT INCLUDED** | Not Implemented | Deploy OAuth2 / JWT Auth Gateway |
