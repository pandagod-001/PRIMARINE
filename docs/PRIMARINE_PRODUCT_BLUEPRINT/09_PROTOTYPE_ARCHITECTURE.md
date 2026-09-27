# PRIMARINE — Local Prototype Architecture & Implementation Plan

**Document:** `docs/PRIMARINE_PRODUCT_BLUEPRINT/09_PROTOTYPE_ARCHITECTURE.md`  
**Classification:** Prototype Technical Blueprint  

---

## 1. Prototype Architectural Philosophy

The prototype architecture is engineered to be **self-contained, zero-dependency, and instantly runnable** in any modern web browser or standard Node/Python environment.

```text
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                               PROTOTYPE PRESENTATION LAYER                              │
│         Single-Page Application (HTML5 / Vanilla CSS3 / Modern JavaScript ES6+)         │
│         • Rich Glassmorphic Navy-Slate Theme                                           │
│         • Zero external API key dependencies                                           │
│         • Responsive Multi-Panel Decision Cockpit                                      │
├────────────────────────────────────────────────────────────────────────────────────────┤
│                               LOCAL PRIMARINE DECISION CORE                              │
│         • Physical Feasibility Matrix Validator (Draft, LOA, Beam, DWT)                │
│         • Split-CQR Conformal Volatility Gating Engine (tau = 1.35x)                   │
│         • Multi-Objective Landed Cost Calculator ($/MT Breakdown)                      │
│         • Adaptive Disruption Re-Planning Engine                                       │
├────────────────────────────────────────────────────────────────────────────────────────┤
│                           STATIC DETERMINISTIC FIXTURE STORE                           │
│         • Authentic Vessel Fleet Catalog (Capesize, Panamax, Supramax)                 │
│         • Authentic Port Catalog (Paradip, Visakhapatnam, Haldia)                      │
│         • Curated Industrial Shipment Scenarios (SAIL, NTPC, Haldia)                   │
└────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 2. Directory Structure of Prototype (`prototype/PRIMARINE-demo/`)

```
prototype/PRIMARINE-demo/
├── index.html               # Main Interactive Prototype Cockpit
├── css/
│   └── styles.css           # Premium Dark/Navy Marine Design System
├── js/
│   ├── data.js              # Deterministic Scenarios, Ports & Vessel Fleet
│   ├── engine.js            # Feasibility, CQR Gating & Optimization Core
│   └── app.js               # UI Event Controller, Disruption Workbench & Audit Log
└── README.md                # 1-Click Launch Instructions
```

---

## 3. Technology Stack Choice & Rationale

- **Core:** Pure HTML5, CSS3, and ES6+ JavaScript.
- **Styling:** Custom CSS design system utilizing CSS Grid, Flexbox, glassmorphism (`backdrop-filter`), and CSS custom properties (variables) for high visual polish without bulky framework overhead.
- **Portability:** Can be opened directly via `file:///` or served via any lightweight local server (`python -m http.server 3000` or `npx serve`).
