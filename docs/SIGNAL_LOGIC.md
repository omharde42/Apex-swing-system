# Apex Swing System — Signal Logic

## 1. Purpose

This document describes the conceptual signal-generation framework used by Apex Swing System.

The exact thresholds and conditions may change between releases and should always be checked against the current Pine Script implementation.

---

## 2. Signal Philosophy

Apex does not rely on a single indicator.

The system combines:

```text
Trend
+
Momentum
+
Ichimoku Confirmation
=
Potential Setup
```

The objective is to create a structured setup rather than a standalone indicator signal.

---

## 3. Bullish Framework

A bullish setup requires the configured bullish conditions to be satisfied.

The system evaluates:

* SMA 200 trend relationship
* RSI momentum
* Ichimoku confirmation
* Overall market direction

Conceptually:

```text
Bullish Trend
      +
Bullish Momentum
      +
Ichimoku Confirmation
      ↓
Bullish Setup
```

---

## 4. Bearish Framework

A bearish setup follows the opposite framework.

The system evaluates:

* SMA 200 trend relationship
* RSI momentum
* Ichimoku confirmation
* Overall market direction

Conceptually:

```text
Bearish Trend
      +
Bearish Momentum
      +
Ichimoku Confirmation
      ↓
Bearish Setup
```

---

## 5. Neutral Condition

If the required confirmation conditions are not satisfied, the system should avoid forcing a trade signal.

```text
Insufficient Confirmation
          ↓
        NEUTRAL
```

No signal is not a failure.

Avoiding low-quality setups is an important part of the system design.

---

## 6. Signal Lifecycle

```text
NO SETUP
   ↓
CONDITIONS DEVELOP
   ↓
CONFIRMATION
   ↓
SIGNAL
   ↓
TRADE PLAN CREATED
   ↓
LEVELS LOCKED
   ↓
ACTIVE SETUP
   ↓
TARGET / STOP / INVALIDATION
   ↓
SETUP CLOSED
```

---

## 7. Signal Direction

The system supports:

```text
BUY
SELL
NEUTRAL
```

A new setup should not unnecessarily overwrite an existing active setup.

---

## 8. Repainting Considerations

Apex should be developed with non-repainting behavior as a priority.

Signals should preferably be confirmed using completed bars when appropriate.

Users should always test the current implementation and understand how TradingView processes realtime bars.

---

## 9. Signal Quality

Future releases may introduce a numerical setup-quality score.

Example concept:

```text
Trend       30%
Momentum    25%
Ichimoku    25%
Volatility  20%
```

This is a future design concept and does not represent the exact v1 algorithm.

---

## 10. Future Signal Engine

Future versions may include:

* Multi-timeframe confirmation
* Volatility filtering
* Trend-strength measurement
* Market-regime detection
* Pattern classification
* Setup scoring
* AI-assisted analysis

These features should be added only after testing and validation.
