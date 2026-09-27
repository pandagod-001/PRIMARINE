# PRIMARINE — SIH 2026 Product & Prototype Presentation Outline

**Document:** `docs/PRIMARINE_PRODUCT_BLUEPRINT/PRIMARINE_PRODUCT_PPT_OUTLINE.md`  
**Classification:** Product & Prototype Slide Deck Outline (16 Slides)  

---

## Slide-by-Slide Content & Visual Structure

### SLIDE 1: Title & Vision
- **Title:** PRIMARINE — Uncertainty-Aware Maritime Freight Decision Intelligence
- **Subtitle:** Solving Industrial Raw Material Procurement Fragility for Indian Steel & Power PSUs
- **Metadata:** SIH 2026 PS-26006 | Ministry of Steel, Government of India
- **Visual:** PRIMARINE Logo + Hero Decision Architecture badge.

### SLIDE 2: The Industrial Challenge
- **Problem:** Over 70M+ tonnes of coking coal imported annually; a single Capesize shipment involves $3.5M in freight.
- **Pain Point:** 48-hour timing errors or berth draft siltation at Paradip causes ₹1.5 Cr+ in demurrage and deadfreight.

### SLIDE 3: The Flaw in Existing Solutions
- **The Blind Spot:** Standard ML point forecasting operates in a silo—optimizing statistical accuracy (MAE) while ignoring physical port constraints and prediction uncertainty.

### SLIDE 4: The Original PRIMARINE Vision & Complete Architecture
- **8-Stage Processing Flow:** Multimodal Ingestion $\rightarrow$ Quality Control Plane $\rightarrow$ Maritime Knowledge Graph $\rightarrow$ Predictive Intelligence $\rightarrow$ Conformal Gating $\rightarrow$ Physical Feasibility $\rightarrow$ Multi-Objective Solver $\rightarrow$ Explainable Decision Center.
- **Visual:** Architecture diagram referencing `PRIMARINE_FULL_TECHNICAL_ARCHITECTURE.png`.

### SLIDE 5: Data Sources & Planned Integrations
- **12 Data Streams:** Freight Indices (Baltic), Vessel Specs (Clarksons), Satellite AIS (Spire), Port Telemetry (PCS 1x), Weather (NOAA), Commodity, FX, Bunker fuel, ERP Requisitions.
- **Engineering Principle:** Provider-Adapter Pattern (Static demo adapters today $\rightarrow$ Live commercial APIs post-selection).

### SLIDE 6: How PRIMARINE Makes a Decision
- **Sequential Logic:** Requisition Ingestion $\rightarrow$ Hard Physical Feasibility Filtering $\rightarrow$ Forward Point Forecast $\rightarrow$ Split-CQR Uncertainty Gating $\rightarrow$ Total Landed Cost Optimization $\rightarrow$ Human Approval.

### SLIDE 7: Where Our Research Fits
- **Core Contribution:** Investigated the mathematical coupling of Conformal Prediction Intervals (Split-CQR) with non-convex Physical Berth/Draft Constraints.

### SLIDE 8: What We Have Actually Validated
- **Empirical Evidence:** 
  - LightGBM Turning-Point F1 = 59.51% (+32.33 pp over AR(5)).
  - Split-CQR Coverage = 88.19%–95.83%.
  - Physical Allocation Stability = 0.00% Flip Rate (Drafts dominate).
  - Selective Abstention eliminates 52.33% of false breakout errors.

### SLIDE 9: What Has NOT Been Implemented Yet (Honest Reality)
- **Clear Demarcation:** No live Baltic Exchange API connected yet; no live satellite AIS stream yet; no production cloud cluster deployed yet. (All planned for post-selection build phase).

### SLIDE 10: Local Prototype Architecture
- **Tech Stack:** 100% self-contained Single-Page Application (HTML5 / Vanilla CSS / ES6+ JavaScript) running directly in-browser without external API keys.

### SLIDE 11: Prototype User Workflow
- **Interactive Flow:** Select Industrial Requisition $\rightarrow$ Automated Draft/LOA Validation $\rightarrow$ Live CQR Width Assessment $\rightarrow$ Action Synthesis (`ENTER_NOW`, `DEFER`, `ABSTAIN`).

### SLIDE 12: Prototype Decision Center & Explainable Rationale
- **Feature Highlight:** Transparent breakdown of landed costs ($/MT), draft safety margins, and macroeconomic volatility gating.

### SLIDE 13: Live Disruption & Adaptive Re-Planning Demo
- **Demonstration:** Paradip monsoon siltation (-1.2m draft) $\rightarrow$ Capesize automatically rejected $\rightarrow$ Re-routes to Visakhapatnam Deepwater Berth, recovering +$14.79/MT over forced transshipment.

### SLIDE 14: Research to Product Translation
- **Matrix:** How Asymmetric Fragility, CQR Gating, and Constraint Criticality directly power the commercial PRIMARINE UI.

### SLIDE 15: Post-Selection Implementation Roadmap
- **Timeline:** Month 1–2 (Static Expansion) $\rightarrow$ Month 3–4 (Open APIs) $\rightarrow$ Month 5–6 (Graph DB) $\rightarrow$ Month 7–8 (Satellite AIS) $\rightarrow$ Month 11–12 (PSU Pilot with SAIL/RINL).

### SLIDE 16: Final Vision & Summary
- **Closing Takeaway:** *"PRIMARINE bridges the gap between machine learning and maritime physics—protecting Indian public sector procurement from volatile markets and port disruptions."*
