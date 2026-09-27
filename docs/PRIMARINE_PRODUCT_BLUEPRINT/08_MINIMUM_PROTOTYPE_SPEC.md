# PRIMARINE — Minimum Viable Prototype Specification

**Document:** `docs/PRIMARINE_PRODUCT_BLUEPRINT/08_MINIMUM_PROTOTYPE_SPEC.md`  
**Classification:** Prototype Product Specification & Deliverable Scope  

---

## 1. Prototype Objective & Guiding Principles

The objective of the prototype is to deliver a **fully functional, interactive vertical slice** of PRIMARINE that demonstrates the complete decision chain locally **without requiring live external APIs, cloud credentials, or synthetic fake random data**.

### Core Guiding Principles:
1. **Deterministic Curated Scenarios:** Uses authentic maritime fixtures (e.g., Australian Coking Coal to Paradip, Indonesian Thermal Coal to Visakhapatnam, US Metallurgical Coal to Haldia).
2. **Transparent Algorithmic Visibility:** The user can clearly see how physical feasibility, point forecasting, CQR uncertainty width, and disruption events interact to produce recommendations.
3. **No Placeholders or Broken Links:** Every button, scenario selector, filter, and chart must work deterministically.

---

## 2. Mandatory Prototype Feature Set

The prototype includes 8 core interactive views:

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│ 1. PRIMARINE OPERATIONAL DASHBOARD & METRICS OVERVIEW                                    │
│    • Key indicators: Spot Freight Index, Volatility Regime, Monitored Shipments        │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ 2. SHIPMENT REQUISITION & SCENARIO SELECTOR                                            │
│    • Choose from 3 Curated Industrial Scenarios (Heavy Bulk, Thermal Coal, Met Coal)   │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ 3. CANDIDATE FLEET & PHYSICAL FEASIBILITY AUDIT PANEL                                  │
│    • Real-time validation matrix: Draft, LOA, Beam, and DWT clearance per vessel       │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ 4. FORWARD MARKET FORECAST & SPLIT-CQR UNCERTAINTY PANEL                               │
│    • 7-day rate forecast + Conformal prediction interval + Interval width metric       │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ 5. EXPLAINABLE DECISION CENTER                                                         │
│    • Recommendation: ENTER_NOW, DEFER, or ABSTAIN                                      │
│    • Detailed justification breakdown (Freight trend vs Draft safety vs Landed cost)   │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ 6. MULTI-OBJECTIVE PLAN RANKING TABLE                                                  │
│    • Plan A (Primary), Plan B (Alternative), Plan C (Fallback) with $/MT breakdown     │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ 7. INTERACTIVE DISRUPTION SIMULATION WORKBENCH                                         │
│    • Triggers: Port Siltation (-1.2m), Cyclone Corridor Closure, Severe Berth Dwell    │
│    • Visual Before vs After comparison with recovery delta (+$14.79/MT savings)        │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ 8. DECISION AUDIT TRAIL & LOG RECORDER                                                 │
│    • Complete immutable record of charter decisions, rationale, and timestamps         │
└────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Curated Prototype Scenarios (Deterministic Static Data)

### Scenario 1: Heavy Bulk Import (SAIL Coking Coal)
- **Cargo:** Australian Hard Coking Coal ($120,000\text{ MT}$).
- **Origin:** Hay Point Terminal, Australia $\longrightarrow$ **Destination:** Paradip Port, India.
- **Normal Conditions:** Paradip Max Draft = $17.1\text{m}$.
- **Baseline Recommendation:** `ENTER_NOW` with *V2 Capesize Standard* ($15.2\text{m}$ draft) at **$\$19.34/\text{MT}$**.
- **Disruption:** Monsoon siltation drops Paradip draft to $13.0\text{m}$ (Capesize infeasible).
- **Adaptive Recovery:** Automatically re-routes to *Visakhapatnam Deepwater Berth* ($16.5\text{m}$ draft) at **$\$19.55/\text{MT}$**, avoiding a $\$15.00/\text{MT}$ demurrage/deadfreight penalty.

### Scenario 2: High-Volatility Market Expansion (NTPC Thermal Coal)
- **Cargo:** Indonesian Steam Coal ($75,000\text{ MT}$).
- **Origin:** Samarinda Port, Indonesia $\longrightarrow$ **Destination:** Visakhapatnam Port, India.
- **Market State:** Extreme volatility ($W = \$8.20/\text{MT} > \tau = \$5.95/\text{MT}$).
- **Recommendation:** `ABSTAIN` (Volatile Market Regime — Defer commitment to neutral spot rate to avoid false breakout).

### Scenario 3: Draft-Constricted Riverine Discharge (Haldia Met Coal)
- **Cargo:** US Low-Volatile Metallurgical Coal ($50,000\text{ MT}$).
- **Origin:** Newcastle, Australia $\longrightarrow$ **Destination:** Haldia Dock Complex, India ($11.5\text{m}$ max draft).
- **Feasibility:** Capesize ($16.8\text{m}$) and Panamax ($13.8\text{m}$) strictly **REJECTED**; only *V5 Supramax Geared* ($11.2\text{m}$ draft) is physically permitted.
- **Recommendation:** `DEFER` (Soft market ahead, locking Supramax fixture).
