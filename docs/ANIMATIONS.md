# Apex Swing System — Animation & Visual Workflow

## 1. Purpose

Apex uses visual feedback to make important market events easier to understand.

Animation should communicate state changes rather than create unnecessary visual noise.

---

## 2. Signal Workflow

The intended visual sequence is:

```text
MARKET SCANNING
      ↓
CONDITIONS CONFIRMED
      ↓
SIGNAL DETECTED
      ↓
SIGNAL HIGHLIGHT
      ↓
ENTRY DISPLAYED
      ↓
STOP LOSS DISPLAYED
      ↓
TARGETS DISPLAYED
      ↓
SETUP ACTIVE
```

---

## 3. Signal Highlight

When a new setup appears, the signal marker may use temporary visual emphasis.

Examples:

* Pulse effect
* Highlight
* Label emphasis
* Temporary transparency change

The effect should remain subtle.

---

## 4. Trade-Level Reveal

The trade plan can visually introduce the levels in sequence:

```text
SIGNAL
  ↓
ENTRY
  ↓
STOP LOSS
  ↓
TARGET 1
  ↓
TARGET 2
  ↓
TARGET 3
```

The actual numerical levels must remain fixed after setup creation.

---

## 5. Active Setup

An active setup may use a compact status indicator:

```text
● ACTIVE
```

The visual state should make it clear that the trade plan is still active.

---

## 6. Target Event

When a target is reached, the corresponding target may receive temporary visual emphasis.

Example:

```text
TARGET 1 ✓
TARGET 2
TARGET 3
```

---

## 7. Stop Event

When the Stop Loss condition occurs:

```text
SETUP INVALIDATED
```

The system should transition the setup to a completed state according to its logic.

---

## 8. Mobile Design

Animation must not reduce readability on small screens.

Avoid:

* Excessive flashing
* Large overlays
* Constantly moving levels
* Unnecessary chart objects
* Animation on every candle

Prefer:

* Short visual feedback
* Clear status changes
* Compact dashboards
* Strong hierarchy
* Stable trade levels

---

## 9. Pine Script Limitations

Pine Script does not provide the same animation capabilities as web technologies such as CSS or JavaScript.

Visual effects must therefore be implemented using available TradingView mechanisms such as:

* Labels
* Plots
* Shapes
* Tables
* Transparency
* Bar-state logic

More advanced animation can be implemented in a future Apex web/mobile interface.

---

## 10. Future Animation System

The long-term vision is:

```text
TradingView
    ↓
Signal Event
    ↓
Apex Web Dashboard
    ↓
Advanced UI Animation
    ↓
Mobile Interface
```

The animation system should always prioritize information clarity over visual effects.
