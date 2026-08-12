# Apex Swing System — Architecture

## 1. Overview

Apex Swing System is designed as a modular TradingView technical-analysis system.

The architecture separates market calculations, signal generation, trade-level management, visualization and alerts.

The primary objective is to make the system easy to maintain and extend as new versions are developed.

---

## 2. Current Architecture

```text
Market Data
     │
     ▼
Indicator Calculations
     │
     ├── SMA 200
     ├── RSI
     └── Ichimoku Cloud
     │
     ▼
Trend Engine
     │
     ▼
Momentum Engine
     │
     ▼
Confirmation Engine
     │
     ▼
Signal Engine
     │
     ├── Bullish Setup
     └── Bearish Setup
     │
     ▼
Trade-Level Engine
     │
     ├── Entry
     ├── Stop Loss
     ├── Target 1
     ├── Target 2
     └── Target 3
     │
     ▼
Risk Engine
     │
     └── Risk / Reward
     │
     ├───────────────┐
     ▼               ▼
Visualization      Alerts
```

---

## 3. Core Components

### Indicator Engine

Calculates the technical indicators required by the system.

Current components:

* SMA 200
* RSI
* Ichimoku Cloud

---

### Trend Engine

Determines the broad market direction using the configured trend conditions.

Possible states:

```text
BULLISH
BEARISH
NEUTRAL
```

---

### Momentum Engine

Evaluates momentum conditions using RSI and related confirmation logic.

---

### Confirmation Engine

Combines multiple conditions before allowing a trade setup.

The purpose is to reduce signals generated from a single indicator.

---

### Signal Engine

Converts confirmed conditions into:

```text
BUY
SELL
NO SIGNAL
```

---

### Trade-Level Engine

Creates the trade plan after a valid setup is confirmed.

The trade plan contains:

```text
Entry
Stop Loss
Target 1
Target 2
Target 3
```

---

### Trade State

The system maintains the state of an active setup.

Conceptually:

```text
IDLE
 ↓
SIGNAL CONFIRMED
 ↓
ACTIVE
 ↓
TARGET / STOP / INVALIDATION
 ↓
COMPLETED
 ↓
IDLE
```

---

## 4. Fixed-Level Principle

When a setup is confirmed, its trade levels should remain stable while the setup is active.

The system should avoid continuously recalculating:

* Entry
* Stop Loss
* Target 1
* Target 2
* Target 3

unless the setup has been closed and a new setup is generated.

---

## 5. Visualization Layer

The visualization layer displays:

* Market direction
* Buy/Sell signals
* Entry
* Stop Loss
* Targets
* Dashboard
* Trade status

Visual elements should communicate information rather than create unnecessary chart clutter.

---

## 6. Alert Layer

Alerts are separated from the signal-generation logic.

This allows TradingView users to receive notifications for important system events without changing the underlying signal calculations.

---

## 7. Future Architecture

Future versions may expand the architecture:

```text
                    APEX ENGINE
                         │
       ┌─────────────────┼─────────────────┐
       │                 │                 │
   Swing Engine      Scalp Engine     Intraday Engine
       │                 │                 │
       └─────────────────┼─────────────────┘
                         │
                    AI Analysis
                         │
                    Risk Engine
                         │
                  Target Engine
                         │
                  User Dashboard
```

These components are future development goals and are not represented as current v1 functionality.

---

## 8. Design Principles

Apex development prioritizes:

1. Deterministic logic
2. Clear signals
3. Stable trade levels
4. Non-repainting design
5. Efficient Pine Script
6. Readable code
7. Testability
8. Minimal chart clutter
9. Mobile-friendly visualization
10. Incremental development

---

## 9. Important Limitation

TradingView Pine Script is designed for chart-based scripting and has limitations compared with a full backend application.

Future external AI functionality may require an architecture involving:

```text
TradingView
     ↓
Alert / API
     ↓
Backend
     ↓
AI Analysis
     ↓
Dashboard
```

The Pine Script indicator should remain independently useful even if external AI functionality is introduced.
