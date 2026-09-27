# PRIMARINE — Unimplemented Capabilities & Engineering Gaps

**Document:** `docs/PRIMARINE_PRODUCT_BLUEPRINT/03_WHAT_IS_NOT_IMPLEMENTED.md`  
**Classification:** Forensic Project Reality Check  

---

## 1. Executive Summary

To maintain complete credibility with SIH evaluators, academic peer-reviewers, and industrial stakeholders, this document provides an honest, rigorous audit of **what PRIMARINE has NOT implemented yet**.

We do NOT claim that a system capability exists simply because it appears in our architectural blueprint. Below is the complete catalog of engineering components that remain planned for post-selection implementation.

---

## 2. Layer-by-Layer Inventory of Unimplemented Features

```
┌──────────────────────────────────────────────────────────────────────────────────┐
│  CAPABILITY CATEGORY         │ CURRENT REALITY         │ PLANNED IMPLEMENTATION │
├──────────────────────────────┼─────────────────────────┼────────────────────────┤
│ 1. Live Freight APIs         │ Static CSV / BDRY Proxy │ Baltic Exchange / Dalian│
│ 2. Live AIS Satellite Stream │ Static / Synthetic POC  │ Spire / AISHub Stream  │
│ 3. Port EDI Telemetry        │ Static Port Catalog     │ PCS / Major Port APIs  │
│ 4. Weather Radar Ingestion   │ Static Historical Priors│ NOAA / Open-Meteo REST │
│ 5. Commodity & FX Live Feeds │ Static Yahoo Finance CSV│ Bloomberg / Refinitiv  │
│ 6. Production Database       │ Local CSV / JSON files  │ PostgreSQL / Timescale │
│ 7. Production Knowledge Graph│ Static Python Dicts     │ FalkorDB / Neo4j Graph │
│ 8. Real-time ST-GNN Model    │ Controlled 8-Node POC   │ Scaled Multi-Port GNN  │
│ 9. User Authentication & RBAC│ None (Local Script)     │ OAuth2 / JWT Security  │
│ 10. Multi-Vessel Fleet Solver│ Single Fixture Scenarios│ MIP Fleet Repositioning│
└──────────────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Detailed Forensic Breakdown

### A. Real-Time Data Ingestion & Live APIs [NOT IMPLEMENTED]
- **Current State:** All market data is read from local static CSV files (`data/processed/freight_features_dataset.csv`).
- **What is Missing:**
  - No active WebSocket listeners or streaming TCP sockets.
  - No live Baltic Exchange API integration (due to commercial subscription costs $\approx \$15\text{k}+/\text{year}$).
  - No live AIS receiver feeds (Spire Maritime / MarineTraffic).
  - No live weather radar or storm trajectory scrapers (NOAA / BOM Australia).
  - No Port Community System (PCS 1x) electronic data interchange (EDI) connections with Indian Major Ports.

---

### B. Production Knowledge Graph & Databases [NOT IMPLEMENTED]
- **Current State:** Vessel deadweights, drafts, LOA, beam, and port handling limits are hardcoded into Python dictionaries (`ports = {...}`, `vessel_fleet = [...]`).
- **What is Missing:**
  - No deployed FalkorDB or Neo4j instance running in the workspace.
  - No Cypher/GraphQL query pipeline traversing graph relations dynamically.
  - No persistent time-series database (TimescaleDB / InfluxDB).

---

### C. Industrial-Scale ST-GNN & Fleet Optimization [NOT IMPLEMENTED]
- **Current State:** The ST-GNN is implemented as an 8-node, 11-corridor controlled proof-of-concept simulation using synthetic spatial shock matrices (`research/experiments/07_stgnn_decision_comparison.py`).
- **What is Missing:**
  - Not trained on real historical AIS global vessel trajectories (due to multi-terabyte proprietary AIS requirements).
  - Multi-vessel combinatorial fleet repositioning (solving simultaneously for 50+ steel plant shipments across a 6-month laycan) is not yet integrated into a production Mixed-Integer Linear Program (MILP).

---

### D. Production Security, Authentication & Deployment [NOT IMPLEMENTED]
- **Current State:** Local Python research scripts and a React SVG architecture viewer.
- **What is Missing:**
  - No multi-tenant user authentication (OAuth2, SAML, JWT).
  - No Role-Based Access Control (RBAC) distinguishing Chartering Managers, Fleet Planners, and Read-Only Auditors.
  - No cloud Kubernetes cluster (EKS/GKE), Docker container registry, or CI/CD deployment pipelines.
  - No automated alert dispatch (SMS/Email/Slack webhooks) for disruption triggers.

---

## 4. Conclusion & Scientific Positioning

The fact that these production features are not yet implemented is **standard and expected for an SIH ideation/prototype submission**.

*The validated strength of PRIMARINE lies in its proven algorithmic decision logic, conformal uncertainty gating, and physical constraint mathematics.* The remaining infrastructure constitutes straightforward software engineering to be executed during the build phase.
