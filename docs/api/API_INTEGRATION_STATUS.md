# PRIMARINE — External API Integration Status & Roadmap

**Document Version:** 1.0.0 (Consolidated Audit)  
**Status:** Canonical Reference  
**Audit Date:** September 2026

---

## 1. Executive Summary & Integration Principles

To ensure scientific honesty and operational transparency, PRIMARINE strictly distinguishes between:
1. **Curated Local Data Fixtures** (Used in the offline research scripts and prototype demonstrator).
2. **Planned Enterprise API Integrations** (Fully architected provider interfaces designed for cloud deployment).

> **CRITICAL SCIENTIFIC RULE:** PRIMARINE currently operates as an **offline research package and standalone local prototype**. Live third-party enterprise APIs are **NOT** connected to this repository, avoiding dependency on paid commercial credentials.

---

## 2. Comprehensive API Provider Status Matrix

| Data Domain | Target Commercial Provider(s) | Protocol / Ingestion Format | Prototype Status | Enterprise Implementation Status | Mock Fixture Location |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Freight Market Rates** | Baltic Exchange API / Clarksons Research | REST API / JSON (Daily Spot Indices) | **MOCK / FIXTURE** | **PLANNED** (Phase 2 Cloud) | `prototype/PRIMARINE-demo/data/fixtures.json` (`market_data`) |
| **Vessel AIS Telemetry** | Spire Maritime / MarineTraffic / ExactEarth | WebSocket / JSON Streaming + REST Historical | **MOCK / FIXTURE** | **PLANNED** (Phase 2 Cloud) | `prototype/PRIMARINE-demo/data/fixtures.json` (`vessels`) |
| **Marine Weather & Waves** | ECMWF ERA5 / Copernicus Marine / NOAA GFS | GRIB2 / NetCDF4 / REST API (6-hour cycles) | **MOCK / FIXTURE** | **PLANNED** (Phase 2 Cloud) | `prototype/PRIMARINE-demo/data/fixtures.json` (`disruptions`) |
| **Port & Berth Telemetry** | Port Community Systems (PCS) / PortXchange | REST API / Webhooks (Berth lineups, delays) | **MOCK / FIXTURE** | **PLANNED** (Phase 2 Cloud) | `prototype/PRIMARINE-demo/data/fixtures.json` (`ports`) |
| **Enterprise ERP / Cargo** | SAP S/4HANA / Oracle SCM / CargoSmart | RFC / REST / OData (Purchase orders, laycans) | **MOCK / FIXTURE** | **PLANNED** (Phase 2 Cloud) | `prototype/PRIMARINE-demo/data/fixtures.json` (`cargo_requests`) |
| **Geopolitical Disruption** | Lloyd's List Intelligence / Maritime Security Feeds | RSS / Webhooks / NLP Event Extraction | **MOCK / FIXTURE** | **PLANNED** (Phase 3 Cloud) | `prototype/PRIMARINE-demo/data/fixtures.json` (`disruptions`) |

---

## 3. Provider Adapter Implementation Roadmap

```
[ Phase 1: Local Prototype & Research ]  <-- CURRENT STATE
  - Curated JSON fixtures and static benchmark datasets.
  - Deterministic replay for reproducible demonstration.
                    ↓
[ Phase 2: Staging Sandbox & Cloud Ingestion ]
  - Implement ProviderAdapter abstract base classes.
  - Connect sandbox test feeds for Baltic Exchange & Spire AIS.
  - Deploy Kafka ingestion streams and TimescaleDB store.
                    ↓
[ Phase 3: Production Live Feeds ]
  - Commercial enterprise subscriptions activated.
  - End-to-end automated retraining and live real-time decision gating.
```
