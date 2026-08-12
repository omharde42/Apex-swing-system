# Apex Swing System — Risk Management

## 1. Purpose

Apex Swing System provides analytical Entry, Stop Loss and Target levels.

These levels are not guarantees.

Risk management remains the responsibility of the user.

---

## 2. Trade Structure

Each active setup can contain:

```text
ENTRY
STOP LOSS
TARGET 1
TARGET 2
TARGET 3
```

---

## 3. Risk

For a long setup:

```text
Risk = Entry - Stop Loss
```

For a short setup:

```text
Risk = Stop Loss - Entry
```

The system should ensure that the calculated risk is meaningful and non-zero.

---

## 4. Reward

For a long setup:

```text
Reward = Target - Entry
```

For a short setup:

```text
Reward = Entry - Target
```

---

## 5. Risk / Reward

Conceptually:

```text
R:R = Potential Reward / Potential Risk
```

Example:

```text
Risk = ₹5
Reward = ₹15

R:R = 1:3
```

A higher theoretical R:R does not guarantee a higher probability of success.

---

## 6. Fixed Levels

After a setup is confirmed:

```text
Entry      → LOCKED
Stop Loss  → LOCKED
Target 1   → LOCKED
Target 2   → LOCKED
Target 3   → LOCKED
```

The system should not continuously move these levels merely because the market price changes.

---

## 7. Setup Completion

A setup can be considered complete when one of the configured termination conditions occurs.

Possible events:

* Stop Loss reached
* Final target reached
* Setup invalidated
* Opposite setup according to configured logic
* Manual reset

The exact implementation depends on the current Pine Script version.

---

## 8. Position Sizing

Apex does not determine a user's personal position size.

Users should consider:

* Account size
* Maximum acceptable loss
* Instrument volatility
* Stop distance
* Liquidity
* Transaction costs

---

## 9. Risk Warning

No indicator can guarantee:

* Profit
* Target achievement
* Prediction accuracy
* Market direction
* Win rate

Historical performance does not guarantee future results.

Apex is an analytical tool, not financial advice.

---

## 10. Future Risk Engine

Future versions may introduce:

* ATR-based risk modelling
* Volatility-adjusted stops
* Adaptive targets
* Position-size calculators
* Portfolio-level risk
* Maximum daily risk controls
* Market-regime-dependent risk parameters

These features are planned and should not be considered part of v1.
