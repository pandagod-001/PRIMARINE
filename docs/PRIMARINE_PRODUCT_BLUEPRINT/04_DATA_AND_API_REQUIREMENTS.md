# PRIMARINE — Complete Data & API Integration Requirements Map

**Document:** `docs/PRIMARINE_PRODUCT_BLUEPRINT/04_DATA_AND_API_REQUIREMENTS.md`  
**Classification:** Technical Data Architecture Specification  

---

## 1. Executive Summary

To transition PRIMARINE from a validated algorithmic decision engine into a fully operational production platform, **12 distinct data streams** must be integrated. 

This document defines the exact requirements for each stream, including:
- Why PRIMARINE needs the data.
- Candidate providers and commercial licensing requirements.
- Current prototype substitute.
- Eventual production integration strategy.

> **Absolute Rule:**  
> We explicitly state whether each provider is connected or not. In the current prototype phase, **no commercial live APIs are connected**; all data is supplied via curated deterministic static fixtures.

---

## 2. Exhaustive Data Source & API Integration Matrix

| # | Data Category | Specific Information Required | Expected Frequency | Candidate Providers / APIs | Auth / Licensing Required | Current Prototype Substitute | Production Integration Status |
|---|---|---|---|---|---|---|---|
| **1** | **Freight Market Benchmarks** | Spot freight indices: BDI, BCI, BPI, BSI, Capesize 5TC, Panamax 4TC, forward FFA curves. | Daily / Real-time | Baltic Exchange API, Clarksons SIN, Dalian Commodity Exchange, BDRY ETF proxy. | Yes (Commercial subscription $\approx \$15\text{k}+/\text{yr}$) | Historical daily CSV (`target_bdry_BDRY.csv`) | **TO BE SELECTED / NOT CONNECTED** |
| **2** | **Vessel Register & Specs** | DWT, Draft (Laden/Ballast), LOA, Beam, Crane outreach, Daily fuel burn (TPD), CII Carbon rating, Daily hire base. | Static / Weekly updates | Clarksons Sea/net, IHS Markit / S&P Maritime, Equasis. | Yes (API key & Commercial license) | Curated 5-vessel fleet catalog (`vessel_fleet` dict) | **TO BE CONNECTED** |
| **3** | **Satellite AIS Telemetry** | MMSI, Lat/Lon, SOG, COG, Draught, Destination, ETA, Navigation status. | Streaming (1–5 min intervals) | Spire Maritime, MarineTraffic / Kpler, AISHub, exactEarth. | Yes (Enterprise WebSocket / REST) | Static deterministic corridor coordinates | **NOT CONNECTED** |
| **4** | **Port & Berth Master Data** | Max allowable draft, Max LOA, Max Beam, Handling charges per tonne, Berth count, Crane outreach limits. | Monthly / Regulatory notices | Major Port Trusts (Paradip, Vizag, Haldia), IPA (Indian Ports Association). | Free / Public Port Gazette | Curated 3-port specifications dictionary | **TO BE FORMALIZED** |
| **5** | **Port Congestion & Dwell** | Vessel queue count, Average turnaround time, Anchorage dwell hours, Berth occupancy rate. | Hourly / Daily | Port Community System (PCS 1x), MarineTraffic Port Congestion API. | Yes (Port Authority credentials) | Static historical average dwell priors | **NOT CONNECTED** |
| **6** | **Weather & Sea State** | Tropical cyclone tracks, Significant wave height, Gale warnings, Monsoon wind vectors. | 3–6 Hour updates | NOAA GFS / ECMWF, Bureau of Meteorology (BOM) Australia, Open-Meteo REST. | Free tier / Open API | Static seasonal storm risk penalty | **TO BE INTEGRATED (Open-Meteo)** |
| **7** | **Commodity Prices** | Coking coal spot (FOB Australia), Iron ore 62% Fe (CFR China), Thermal coal (FOB Newcastle). | Daily | S&P Global Platts, Fastmarkets, Metal Bulletin. | Yes (Enterprise license) | Miner equities proxy (BHP, Vale CSVs) | **TO BE CONNECTED** |
| **8** | **Foreign Exchange (FX)** | USD/INR, AUD/USD, USD/CNY exchange rates for landed rupee conversions. | Real-time / Daily close | Reserve Bank of India (RBI), Open Exchange Rates, Yahoo Finance. | Free / Low-cost API key | Historical daily CSV (`macro_usdinr_INR_X.csv`) | **TO BE INTEGRATED** |
| **9** | **Bunker Fuel Benchmarks** | VLSFO (0.5% Sulphur), MGO, IFO 380 spot prices at Singapore, Fujairah, Rotterdam. | Daily | BunkerIndex, Ship & Bunker, ICE Brent Futures (`BZ=F`). | Yes (Commercial / Free proxy) | Historical Brent crude CSV proxy | **TO BE INTEGRATED** |
| **10** | **Shipment Cargo Requisitions** | Cargo grade, Volume (MT), Laycan window, Plant destination, Quality tolerances. | Per procurement event | Enterprise ERP (SAP MM, Oracle SCM, SAIL ERP). | Enterprise SAML / OAuth | User-input scenario selector | **INTERNAL ERP ADAPTER** |
| **11** | **Maritime Disruptions** | Canal blockages, Port strikes, Navigational warnings, Geopolitical sanctions. | Event-driven (Webhooks) | Lloyd's List Intelligence, NAVTEX broadcasts, Dryad Global. | Yes (Subscription API) | Controlled synthetic disruption fixtures (D1–D6) | **NOT CONNECTED** |
| **12** | **Navigable Sea Routes** | Waypoints, Sea distances (nautical miles), Canal transit fees, Piracy High Risk Areas (HRA). | Static / Quarterly | Admiralty Distance Tables, SeaRates / Netpas Distance API. | Yes (Low-cost REST) | Static nautical distance matrix | **TO BE INTEGRATED** |

---

## 3. Modular Architecture: Provider-Adapter Pattern

To ensure PRIMARINE can run locally today while seamlessly connecting to live APIs tomorrow, the backend utilizes an abstract **Provider-Adapter Pattern**:

```python
# Conceptual Architecture Interface
class IMarketDataProvider(ABC):
    @abstractmethod
    def get_forward_freight_curve(self, corridor_id: str) -> FreightCurve:
        pass

# Current Implementation (Prototype)
class StaticInstanceMarketProvider(IMarketDataProvider):
    def get_forward_freight_curve(self, corridor_id: str) -> FreightCurve:
        return load_curated_fixture(corridor_id)

# Future Production Implementation (Post-Selection)
class BalticExchangeLiveMarketProvider(IMarketDataProvider):
    def __init__(self, api_key: str):
        self.api_key = api_key
    def get_forward_freight_curve(self, corridor_id: str) -> FreightCurve:
        return query_baltic_rest_api(self.api_key, corridor_id)
```

This guarantees zero rewrites of the core optimization and feasibility logic when commercial API keys are provisioned.
