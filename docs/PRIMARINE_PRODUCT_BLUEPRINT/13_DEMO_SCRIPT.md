# PRIMARINE — 3-Minute Live Interactive Demo Script

**Document:** `docs/PRIMARINE_PRODUCT_BLUEPRINT/13_DEMO_SCRIPT.md`  
**Target Audience:** SIH Evaluators, Industrial Procurement Directors, Academic Evaluators  
**Duration:** Exactly 3 Minutes  

---

## 1. Demo Setup & Requirements
- **URL:** Open `prototype/PRIMARINE-demo/index.html` in Chrome/Edge/Firefox.
- **Dependency:** 100% self-contained local prototype. Zero external API keys or internet connection required.

---

## 2. Step-by-Step 3-Minute Presentation Flow

### [0:00 – 0:45] Step 1: Normal Operations & Physical Feasibility Filtering
1. **Action:** Open dashboard. Select **Scenario 1: SAIL Coking Coal Import (120,000 MT)**.
2. **Talking Point:** 
   > *"Judges, here we have a 120,000 MT coking coal requirement from Hay Point to Paradip. Notice how PRIMARINE instantly evaluates the entire fleet against Paradip's 17.1m draft and berth limits. Panamax and Supramax vessels are automatically REJECTED due to capacity mismatch. The system selects MV Pacific Trader (Capesize, 15.2m draft) at a total landed cost of $19.34/MT."*
3. **Point out:** Green **ENTER NOW** banner. 7-day forecast indicates a rising market, and interval width ($5.76/MT) is stable.

---

### [0:45 – 1:45] Step 2: Live Operational Shock & Adaptive Re-Routing
1. **Action:** Click the red button: **⚠️ TRIGGER OPERATIONAL SHOCK** in the Disruption Simulator panel.
2. **Talking Point:**
   > *"Now, imagine a real-world monsoon siltation event occurs at Paradip, reducing allowable draft to 13.0m. Watch the screen: PRIMARINE immediately detects that the Capesize draft (15.2m) now violates the new draft limit. Instead of failing or forcing costly transshipment, PRIMARINE automatically executes adaptive re-routing. It selects Visakhapatnam Deepwater Berth (16.5m draft) at $19.55/MT, recovering over $14.79/MT compared to forced deadfreight penalties."*
3. **Point out:** The blue **RE-ROUTED** badge and updated landed cost.

---

### [1:45 – 2:30] Step 3: Conformal Uncertainty Gating & Selective Abstention
1. **Action:** Click **Scenario 2: NTPC Thermal Coal (High Volatility)**.
2. **Talking Point:**
   > *"Now observe what happens in an erratic, high-volatility market. The point forecast predicts freight is going up. A naive ML system would tell you to buy now. But look at our Conformal 90% Band Width: it has surged to $9.60/MT, exceeding our pre-calibrated stability threshold ($5.95/MT).*
   > 
   > *PRIMARINE issues a purple ABSTAIN signal. Our empirical research proved that in high-width regimes, false breakouts surge to 40.25%. By selectively abstaining, PRIMARINE prevents the charterer from locking in at the peak of a false breakout, saving millions in procurement capital."*

---

### [2:30 – 3:00] Step 4: Strict Physical Port Constraints (Haldia) & Audit Trail
1. **Action:** Click **Scenario 3: Riverine Met Coal Discharge (Haldia)**.
2. **Talking Point:**
   > *"Finally, for shallow riverine ports like Haldia (11.5m draft), PRIMARINE physically blocks all Capesize and Panamax ships regardless of market rates, selecting the only feasible Supramax vessel. Notice on the right, every decision, rationale, and timestamp is logged into an immutable Decision Audit Trail for enterprise compliance."*
3. **Closing Line:**
   > *"PRIMARINE bridges the gap between machine learning and maritime physics—protecting Indian public sector procurement from volatile markets and port disruptions."*
