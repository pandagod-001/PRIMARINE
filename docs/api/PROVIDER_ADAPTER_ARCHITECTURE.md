# PRIMARINE — Provider Adapter Architecture

**Document Version:** 1.0.0 (Consolidated Blueprint)  
**Status:** Canonical Reference  
**Scope:** Specification of the extensible data adapter interface isolating external commercial APIs from core decision and uncertainty engines.

---

## 1. Architectural Motivation & Design Pattern

In production maritime logistics, external data providers change frequently (e.g. switching from MarineTraffic to Spire Maritime, or migrating from NOAA GFS to ECMWF ERA5). 

To prevent vendor lock-in and decouple core predictive models from third-party schemas, PRIMARINE implements the **Provider Adapter Pattern**. All external data streams must implement standardized abstract interfaces, outputting strictly validated Pydantic data schemas before reaching the Feature Store or Decision Engine.

```mermaid
graph TD
    subgraph External Commercial Providers
        P1[Baltic Exchange API]
        P2[Spire Maritime AIS]
        P3[ECMWF ERA5 Weather]
        P4[Port Community System]
    end

    subgraph Provider Adapter Layer (Abstract Interfaces)
        A1[FreightMarketAdapter]
        A2[VesselTelemetryAdapter]
        A3[WeatherGridAdapter]
        A4[PortOperationsAdapter]
    end

    subgraph Core Ingestion & Validation
        B[Data Quality & Security Gate]
        C[(Feature Store / TimescaleDB)]
    end

    subgraph PRIMARINE Decision Engines
        D[Uncertainty & Feasibility Pipeline]
    end

    P1 --> A1
    P2 --> A2
    P3 --> A3
    P4 --> A4

    A1 & A2 & A3 & A4 --> B
    B --> C
    C --> D
```

---

## 2. Standardized Adapter Interface Specifications

### 2.1. Freight Market Rate Adapter (`IFreightMarketAdapter`)

```python
from abc import ABC, abstractmethod
from datetime import datetime
from typing import List, Optional
from pydantic import BaseModel, Field

class FreightSpotQuote(BaseModel):
    route_code: str = Field(..., description="Standard Baltic route code, e.g. C5TC, P4TC")
    vessel_class: str = Field(..., description="Capesize, Panamax, Supramax, Handysize")
    spot_rate_usd: float = Field(..., description="Rate in USD/day or USD/metric ton")
    timestamp: datetime = Field(..., description="Timestamp of quote publication")
    provider: str = Field(..., description="Name of data source provider")
    confidence_score: float = Field(default=1.0, ge=0.0, le=1.0)

class IFreightMarketAdapter(ABC):
    @abstractmethod
    def fetch_spot_rates(self, route_codes: List[str], date: datetime) -> List[FreightSpotQuote]:
        """Fetch historical or real-time freight spot quotes."""
        pass

    @abstractmethod
    def fetch_forward_curves(self, route_code: str) -> List[dict]:
        """Fetch Forward Freight Agreement (FFA) curve data."""
        pass
```

### 2.2. Vessel AIS Telemetry Adapter (`IVesselTelemetryAdapter`)

```python
class VesselTelemetryRecord(BaseModel):
    mmsi: int = Field(..., description="Maritime Mobile Service Identity")
    imo: int = Field(..., description="International Maritime Organization number")
    vessel_name: str
    vessel_class: str
    latitude: float = Field(..., ge=-90.0, le=90.0)
    longitude: float = Field(..., ge=-180.0, le=180.0)
    speed_over_ground_knots: float = Field(..., ge=0.0)
    course_over_ground_deg: float = Field(..., ge=0.0, le=360.0)
    current_draft_meters: float = Field(..., ge=0.0)
    destination_port: Optional[str] = None
    estimated_arrival_utc: Optional[datetime] = None
    timestamp: datetime

class IVesselTelemetryAdapter(ABC):
    @abstractmethod
    def stream_vessel_positions(self, bounding_box: dict) -> List[VesselTelemetryRecord]:
        """Stream live AIS telemetry for vessels in a geographic bounding box."""
        pass

    @abstractmethod
    def get_vessel_particulars(self, imo: int) -> dict:
        """Fetch static particulars: DWT, Beam, LOA, Crane Outreach."""
        pass
```

### 2.3. Port Operations & Queue Adapter (`IPortOperationsAdapter`)

```python
class BerthStatus(BaseModel):
    port_id: str
    berth_id: str
    max_draft_meters: float
    max_dwt: float
    max_beam_meters: float
    is_occupied: bool
    current_vessel_imo: Optional[int] = None
    estimated_clearing_time: Optional[datetime] = None
    queue_vessels_waiting: int = 0
    average_waiting_hours: float = 0.0

class IPortOperationsAdapter(ABC):
    @abstractmethod
    def get_port_congestion(self, port_id: str) -> dict:
        """Fetch current anchorage waiting times and queue depth."""
        pass

    @abstractmethod
    def get_berth_constraints(self, port_id: str) -> List[BerthStatus]:
        """Fetch physical constraints and occupancy for all berths."""
        pass
```

---

## 3. Mock Adapter Implementation for Standalone Execution

For testing and prototype demonstration, PRIMARINE provides mock implementations (`MockFreightAdapter`, `MockAISAdapter`, `MockPortAdapter`) that replay verified historical fixtures from `data/fixtures/` and `prototype/PRIMARINE-demo/data/fixtures.json`. This guarantees 100% offline reproducibility without external network dependencies.
