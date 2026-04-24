---
title: Unboxing
lang: en
permalink: /en/quickstart/unboxing/
---

# 📦 Unboxing

> Know what's in the box, what each part does, and why.

## Estimated time

**3 minutes**

---

## 🧾 What's in the box

| # | Item | Purpose |
|---|------|---------|
| ① | **ELIO board** (×1) | The main hardware — motors, sensors, app all connect here |
| ② | **USB cable** (×1) | Power |
| ③ | **QR card** (×1) | QR codes to guides & apps |
| ④ | **Quick Start sheet** (×1, folded) | Printed version of this page |
| ⑤ | *(Optional)* **LEGO motor gender** | For connecting LEGO motors — sold separately |
| ⑥ | *(Optional)* **Extension sensor pack** | Ultrasonic · line sensors, etc. — sold separately |

> Missing something? Contact [📧 caram88@mobilian.biz](mailto:caram88@mobilian.biz)

---

## 🔍 ELIO Board at a Glance

```
       ┌───────────────────────────────────┐
       │   [LED1]   [LED2]                │
       │                                   │
       │  [DC1]───[DC2]    [SV1]─[SV2]   │  ← Motor & servo ports
       │                                   │
       │  [IO1][IO2][IO3][IO4]             │  ← Digital I/O
       │  [3V]           [5V]              │  ← Power output
       │                                   │
       │      [USB-C / USB]   [Power SW]  │
       │                                   │
       └───────────────────────────────────┘
```

### Key Ports

| Label | What | When to use |
|-------|------|-------------|
| **DC1 / DC2** | 2× DC motors | Wheels, propellers |
| **SV1 / SV2** | 2× Servo motors | Arms, heads (angle control) |
| **3V / 5V** | Power output | Powering external sensors |
| **IO1–IO4** | General I/O | Sensor signals, switches, LEDs |

---

## 💡 LED Status

| Pattern | Meaning |
|---------|---------|
| **Slow blink** (1 s) | Advertising (waiting for app) |
| **Fast blink** (0.1 s) | Motor fault (over-current, etc.) |
| **Off** | No power or connected |

---

## ⚡ Power Up

1. Plug USB-C cable into ELIO
2. Other end: power bank / laptop / wall adapter
3. LED starts **slow blinking** → success

> **No LED?** Swap the cable — cheap "charge-only" cables sometimes fail.

---

## Next

Once powered, install the app:

- 📱 [**Android**](/elio-docs/en/quickstart/android/)
- 🍎 [**iOS**](/elio-docs/en/quickstart/ios/)

---

⬅ [Back to Quick Start](/elio-docs/en/quickstart/)
