# PRIMARINE — Complete System Architecture Specification

**Document:** `docs/PRIMARINE_PRODUCT_BLUEPRINT/06_COMPLETE_SYSTEM_ARCHITECTURE.md`  
**Classification:** Enterprise System Architecture Blueprint  

---

## 1. High-Level Architectural Schema

The complete intended PRIMARINE platform is an enterprise-grade, event-driven decision intelligence system. 

It connects real-world maritime data inputs with downstream human chartering workflows through a continuous **8-Stage Processing Pipeline**:

```
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│                           STAGE 1: MULTIMODAL INGESTION LAYER                           │
│  Baltic Freight APIs │ Satellite AIS │ NOAA Weather │ Port EDI (PCS 1x) │ ERP Ingestion │
└────────────────────────────────────────────┬────────────────────────────────────────────┘
                                             │
                                             ▼
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│                         STAGE 2: CONTROL PLANE & QUALITY GATE                           │
│   Schema Validation │ Unit Standardization │ Z-Score Outlier Filter │ Holiday Forward-Fill│
└────────────────────────────────────────────┬────────────────────────────────────────────┘
                                             │
                                             ▼
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│                    STAGE 3: MARITIME KNOWLEDGE GRAPH & FEATURE STORE                    │
│   Graph Topology (Ports, Berths, Corridors) │ FalkorDB / Neo4j │ TimescaleDB Feature Store│
└────────────────────────────────────────────┬────────────────────────────────────────────┘
                                             │
                                             ▼
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│                  STAGE 4: PREDICTIVE INTELLIGENCE & CONFORMAL GATING                    │
│   LightGBM Turning-Point Regressor (F1=59.51%) │ Split-CQR Prediction Intervals (90%)   │
│   Macro-Regime Volatility Gate (tau = 1.35x)   │ Selective Abstention Engine (52% Cut)  │
└────────────────────────────────────────────┬────────────────────────────────────────────┘
                                             │
                                             ▼
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│                        STAGE 5: PHYSICAL FEASIBILITY ENGINE                             │
│   Draft Validator (Laden/Tidal) │ LOA & Beam Clearance │ Parcel Deadweight (DWT) Match  │
└────────────────────────────────────────────┬────────────────────────────────────────────┘
                                             │
                                             ▼
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│                   STAGE 6: MULTI-OBJECTIVE CHARTER OPTIMIZATION                         │
│   Total Landed Cost ($/MT) │ Turnaround Duration │ Demurrage Exposure │ CII Carbon Score │
└────────────────────────────────────────────┬────────────────────────────────────────────┘
                                             │
                                             ▼
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│                     STAGE 7: EXPLAINABLE DECISION CENTER & UI                           │
│   Transparent Rationale │ Trade-Off Curves │ Counterfactual Sandbox │ Human-in-the-Loop │
└────────────────────────────────────────────┬────────────────────────────────────────────┘
                                             │
                                             ▼
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│                    STAGE 8: DISRUPTION DETECTION & ADAPTIVE RE-PLANNING                 │
│   ST-GNN Network Propagation │ Port Siltation Shocks │ Cyclone Re-Routing (+3.90 $/MT)  │
└─────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 2. Microservice Topology & Technical Stack

```text
+-----------------------------------------------------------------------------------------+
| PRESENTATION LAYER (Web SPA)                                                            |
| React 19 + TypeScript + Tailwind CSS / Vanilla CSS + Vite + Lucide Icons + Recharts    |
+-----------------------------------------------------------------------------------------+
                                             │ (REST / WebSocket / JSON)
                                             ▼
+-----------------------------------------------------------------------------------------+
| APPLICATION & API GATEWAY                                                               |
| FastAPI (Python 3.11+) / Go Gateway + OAuth2 JWT Security + Redis Cache                 |
+-----------------------------------------------------------------------------------------+
                                             │
                      ┌──────────────────────┴──────────────────────┐
                      ▼                                             ▼
+------------------------------------------+  +------------------------------------------+
| CORE DECISION INTELLIGENCE SERVICE       |  | INGESTION & DATA QUALITY WORKERS         |
| • LightGBM Turning-Point Engine          |  | • Celery / Redis Queue Async Workers     |
| • Split-CQR Conformal Calibration        |  | • Anomaly Detection & Time Alignment     |
| • Physical Feasibility Matrix            |  | • Provider-Adapter Ingestion Interfaces  |
| • Multi-Objective Pareto Solver          |  | • Synthetic / Static Fixture Providers   |
+------------------------------------------+  +------------------------------------------+
                      │                                             │
                      └──────────────────────┬──────────────────────┘
                                             ▼
+-----------------------------------------------------------------------------------------+
| DATA PERSISTENCE & KNOWLEDGE GRAPH LAYER                                                |
| • PostgreSQL / TimescaleDB (Time-series freight, bunker, FX, macro metrics)             |
| • FalkorDB / Neo4j (Maritime Graph: Ports, Berths, Canals, Corridors, Vessels)          |
| • MinIO / S3 (Audit logs, model checkpoints, raw payload archive)                       |
+-----------------------------------------------------------------------------------------+
```

---

## 3. Position of Research within the System

The research findings completed in the previous phase integrate directly into **Stage 4, Stage 5, and Stage 8**:
- **Stage 4:** The calibrated conformal uncertainty interval ($W$) gates decisions into `ENTER_NOW`, `DEFER`, or `ABSTAIN`.
- **Stage 5:** The verified physical feasibility matrix filters all candidate combinations before optimization.
- **Stage 8:** The adaptive disruption engine recalculates optimal alternatives during unforeseen operational shocks.
