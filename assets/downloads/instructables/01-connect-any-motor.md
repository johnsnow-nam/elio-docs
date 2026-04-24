---
title: "Instructables 1편: Connect Any Motor with Cables You Already Own"
lang: en
permalink: /assets/downloads/instructables/01/
---

# Connect Any Motor with Cables You Already Own

**Platform**: Instructables  
**Status**: ✅ Ready to publish (Wave 1)  
**Target audience**: All makers, beginners welcome  
**Est. read time**: 10 minutes  
**Est. build time**: 30 minutes

---

## Introduction

You've got a drawer full of cables — phone chargers, old headphones, network cables, Lego power leads. What if I told you that **any of them can control a motor**?

ELIO is a Nordic nRF52-based robot board that connects to your smartphone over BLE. But what makes it special is its **four motor connectors** — each accepts the most common cable types you already own:

- 🔴 **3.5mm audio jack** (stereo headphone cable)
- 🟡 **RJ11 (telephone cable)**
- 🔵 **RJ45 (Ethernet cable)**
- ⚫ **Lego Power Functions** (Lego motors directly!)

No soldering. No special adapters. Just plug in and play.

This tutorial covers the basics: connecting a motor, installing the app, and driving your first robot.

---

## Supplies

| Item | Notes |
|------|-------|
| ELIO board × 1 | Available on [Tindie](https://www.tindie.com/) — search "ELIO" |
| DC motor × 1 (or Lego motor) | Geared hobby motor, or pull from old toys |
| Cable (any of the 4 types) | See Introduction — whichever fits your motor |
| Smartphone | iOS 14+ or Android 9+ |
| bletoy app | Free — App Store / Google Play |
| USB-C cable + charger | For charging ELIO |
| AA batteries × 4 (or LiPo) | Power for motors |

**Optional (for a complete RC car):**
- Wheels × 4
- Chassis (cardboard works!)
- Hot glue gun

---

## Step 1 — Charge ELIO

1. Connect USB-C cable to ELIO's charging port.
2. Red LED = charging. Blue LED (or off) = fully charged.
3. A full charge takes about 90 minutes.

> **Tip**: While it's charging, install the app on your phone (next step).

---

## Step 2 — Install the bletoy App

**Android**: Search "bletoy" on Google Play → Install  
**iOS**: Search "bletoy" on App Store → Install

Grant these permissions when asked:
- Bluetooth (required)
- Location / Nearby devices (required for BLE scan on Android)

---

## Step 3 — Understand the Four Motor Ports

ELIO has two DC motor channels. Each channel offers **four connector options** — use whichever cable type you have:

```
DC1 port:
  ├── 3.5mm jack (⬤ stereo cable, pin: Tip=+, Ring=-)
  ├── RJ11 (telephone cable, pin 1/2 or 3/4)
  ├── RJ45 (Ethernet cable, pin 1/2)
  └── [internal pin header]

DC2 port:
  ├── 3.5mm jack
  ├── RJ11
  ├── RJ45
  └── [internal pin header]
```

For Lego motors: use the **Lego Power Functions gender adapter** (included in ELIO kits).

---

## Step 4 — Connect Your Motor

### Option A: 3.5mm Headphone Cable

1. Strip 2cm off a stereo audio cable — you'll see a red wire (+) and a bare/copper wire (-).
2. Alternatively, use a broken headphone — cut the cable, strip the ends.
3. Plug the 3.5mm jack into ELIO's DC1 port.
4. Connect the stripped wire ends to your motor terminals.

> The motor won't care about polarity for basic spinning — swap wires to reverse direction.

### Option B: Telephone Cable (RJ11)

1. Plug the RJ11 connector into ELIO's DC1 port.
2. The other end: strip the cable and connect to motor.
3. Pins 1 and 2 (outermost) carry the DC output.

### Option C: Ethernet Cable (RJ45)

1. Plug the RJ45 into ELIO's DC1 port.
2. Strip the other end — use the orange pair (pins 1+2) for DC output.
3. Connect to motor terminals.

### Option D: Lego Motor

1. Attach the Lego Power Functions gender adapter to ELIO's DC1 port.
2. Plug your Lego motor directly in.
3. No stripping needed — fully plug-and-play.

---

## Step 5 — Power On ELIO

1. Press and hold the power button for 1 second.
2. The blue LED starts blinking — ELIO is now broadcasting BLE.
3. Make sure your motor's power source (batteries/LiPo) is connected.

> ELIO's onboard battery only powers the board logic. Motors need external power via the motor power terminals.

---

## Step 6 — Connect via App

1. Open the bletoy app.
2. Tap **Scan** — your ELIO appears in the list ("ELIO_XXXX").
3. Tap to connect — blue LED changes from blinking to solid.
4. The control dashboard appears.

---

## Step 7 — Drive It!

1. On the app dashboard, find the **DC1 joystick** or **DC1 slider**.
2. Push forward — your motor spins!
3. Pull back — it reverses.
4. Release — it stops.

**If the motor spins the wrong direction**: swap the cable wires, or use the app's "reverse motor" setting.

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| ELIO not found in scan | Power on ELIO, check Bluetooth + Location permissions |
| Motor doesn't spin | Check external power source is connected and turned on |
| Motor spins only one way | Swap the two motor wires |
| App crashes | Force-close and reopen; ensure OS permissions are granted |
| Motor hums but doesn't move | Power may be too low — check battery charge or motor stall load |

---

## Next Steps

You've connected a motor with a cable you already had — that's ELIO's superpower. Here's where to go next:

- 🚗 **Build a full RC car** → Tutorial 2: [Lego Motors + ELIO](./02-lego-motors.md)
- 🌱 **Add sensors** → Tutorial 5: [Ultrasonic Sensor Obstacle Avoidance](./05-ultrasonic-avoidance.md)
- 🐍 **Code with Python** → [Python UART SDK Guide](/elio-docs/platforms/python/)
- 🛒 **Get another ELIO** → [Tindie store](https://www.tindie.com/) — search "ELIO"

---

*Tutorial by ELIO / elioseokhee.github.io/elio-docs*  
*Licensed CC BY-SA 4.0*
