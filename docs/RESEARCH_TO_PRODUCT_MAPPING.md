# PRIMARINE — Research-to-Product Mapping Matrix

**Document Version:** 1.0.0 (Consolidated Blueprint)  
**Status:** Canonical Reference  
**Purpose:** Direct mapping between verified research discoveries, enterprise product capabilities, current prototype implementation, and future production requirements.

---

## 1. Master Research-to-Product Traceability Matrix

| Research Finding & Artifact | Corresponding Product Feature | Prototype Demonstrator Status (`prototype/PRIMARINE-demo/`) | Enterprise Production Requirement (`docs/PRIMARINE_PRODUCT_BLUEPRINT/`) |
| :--- | :--- | :--- | :--- |
| **LightGBM Turning-Point Inflection (F1 = 59.51%)**<br>`EV-002` | **Macro Market Regime Detector**<br>Identifies multi-day freight rate surges/drops for strategic chartering windows. | **IMPLEMENTED**<br>Simulated forward 7-day rate curves with turning point indicators in chart UI. | **PRODUCTION PLANNED**<br>Daily automated retraining pipeline with multi-route Baltic Exchange feed. |
| **Split-CQR 90% Conformal Calibration**<br>`EV-004` | **Distribution-Free Uncertainty Bounds**<br>Computes non-parametric $[\hat{y}_{\text{low}}, \hat{y}_{\text{high}}]$ risk bands. | **IMPLEMENTED**<br>Interactive slider adjusting quantile bounds and rendering confidence envelopes dynamically. | **PRODUCTION PLANNED**<br>Rolling online conformal calibration worker running every 24 hours. |
| **Physical Feasibility Invariance (PDFR = 0.00%)**<br>`EV-005` | **Hard Operational Vessel-Port Gate**<br>Filters vessels by Draft, DWT, Beam, LOA, and berth equipment before pricing. | **IMPLEMENTED**<br>Strict rule-engine filtering 5 vessel classes against 8 Indian Ocean ports in real-time. | **PRODUCTION PLANNED**<br>Integration with Port Community Systems (PCS) and dynamic tidal bathymetry feeds. |
| **Conformal Width vs False Breakouts (AUC = 0.6719)**<br>`EV-007` | **False-Breakout Exposure Warning**<br>Alerts chartering teams when high model dispersion signals risky false dips. | **IMPLEMENTED**<br>Real-time risk scoring and visual alerts on high-dispersion procurement cycles. | **PRODUCTION PLANNED**<br>Streaming Kafka alert pipeline notifying chartering desks via WebSockets/Slack. |
| **Pre-Calibrated Selective Abstention ($\tau = 1.35\times$)**<br>`EV-010` | **Three-Tier Decision Gate (ENTER / DEFER / ABSTAIN)**<br>Automates optimal action based on width threshold and physical buffers. | **IMPLEMENTED**<br>Full client-side decision engine outputting color-coded `ENTER`, `DEFER`, and `ABSTAIN` cards. | **PRODUCTION PLANNED**<br>Configurable enterprise policy engine allowing procurement heads to adjust risk tolerance. |
| **Cryptographic Auditability & Governance**<br>`Claim P-01` | **Immutable Decision Audit Chain**<br>Logs inputs, bounds, constraints, and approvals for compliance and post-voyage review. | **IMPLEMENTED**<br>SHA-256 hash-chained transaction log visible in the prototype Cockpit audit drawer. | **PRODUCTION PLANNED**<br>Enterprise PostgreSQL audit table with cryptographic ledger verification. |
| **Graph-Based Disruption Propagation**<br>`EV-013` | **Dynamic Rerouting & Feasibility Re-ranking**<br>Calculates delay cascades and re-ranks alternative vessels/ports. | **IMPLEMENTED**<br>Interactive scenario buttons (e.g. Red Sea Disruption, Cyclone) triggering rerouting. | **PRODUCTION PLANNED**<br>Real-time graph analytics engine powered by FalkorDB and live AIS telemetry. |
| **Negative Results (Degenerate Boundary Crossing)**<br>`EV-008`, `EV-009` | **Architectural Guardrail / Anti-Patterns**<br>Prevents implementation of naive threshold-crossing triggers in core engines. | **ENFORCED**<br>Prototype uses interval width exclusively for gating; naive spot crossing is omitted. | **ENFORCED**<br>System design documentation explicitly forbids point-crossing triggers. |

---

## 2. Decision Flow Architecture

```
[ Ingested Market & Port Data ]
              ↓
[ LightGBM Regime Detection + Split-CQR Bounds ]
              ↓
[ Hard Physical Feasibility Filter (Draft / DWT) ]
              ↓
       { Interval Width <= tau? }
       ├── YES: Recommend ENTER (Commit Charter)
       └── NO: Check Physical Laycan Buffer
              ├── Buffer Available: Recommend DEFER (Wait for Clarity)
              └── No Buffer: Recommend ABSTAIN (Escalate to Human Desk)
              ↓
[ Immutable Audit Logging (SHA-256 Chain) ]
```
