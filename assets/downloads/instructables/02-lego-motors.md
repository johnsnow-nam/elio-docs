---
title: "Instructables 2편: Lego Motors Meet ELIO"
lang: en
permalink: /assets/downloads/instructables/02/
---

# Lego Motors Meet ELIO — Bring Your Bricks to Life

**Platform**: Instructables  
**Status**: ✅ Ready to publish  
**Target audience**: Lego fans, parents, educators  
**Est. read time**: 12 minutes  
**Est. build time**: 45 minutes

---

## Introduction

ELIO has a secret: it speaks Lego.

Every ELIO kit includes a **Lego Power Functions adapter** — the same flat 4-wire connector used in Lego Technic battery boxes. That means every PF motor you own (M-Motor, L-Motor, XL-Motor) plugs directly into ELIO with no modification, no soldering, and no adapters to buy.

**What we'll build**: A Lego Technic chassis with ELIO as the brain — controlled from your smartphone over Bluetooth.

**Why this matters**: Lego motors are precision-geared, quiet, and reliable. ELIO gives them a Bluetooth-controlled brain without replacing the Lego ecosystem you've already invested in.

---

## Supplies

| Item | Notes |
|------|-------|
| ELIO board × 1 | Includes Lego PF adapter |
| Lego Power Functions motor × 2 | M-Motor (88003) or L-Motor (88004) recommended |
| Lego PF extension cable × 2 | Gives you routing flexibility on the chassis |
| Lego Technic chassis | Any Technic set with axles, or build your own |
| Smartphone | iOS 14+ or Android 9+ |
| bletoy app | Free — App Store / Google Play |
| 9V battery (PP3) or 7.4V LiPo | Motors need external power |

> **Don't have Lego Technic?** A cardboard chassis works fine for testing. Tape the motors down and go.

---

## Step 1 — Know Your Connector

The Lego Power Functions connector has **4 pins**:

| Pin | Signal | ELIO uses |
|-----|--------|-----------|
| C1 | Motor wire 1 | ✅ |
| C2 | Motor wire 2 | ✅ |
| GND | Ground | ✅ |
| VCC | 9V supply | ❌ (ELIO provides its own power) |

ELIO controls direction and speed by driving C1 and C2 — exactly how a Lego battery box works.

> **Compatibility**: Works with all **Lego Power Functions** (PF) motors and lights. Does **not** work with Powered Up / Control+ (different connector, different protocol).

---

## Step 2 — Connect the Motors

1. Take the Lego PF adapter cable included with ELIO.
2. Plug one end into the **Lego motor**.
3. Plug the other end into **DC-1** on ELIO.
   - The connector clicks in one way only — no force needed.
4. For the second motor (right side of chassis): plug into **DC-2**.

No tools. No soldering. Done.

---

## Step 3 — Mount ELIO on the Chassis

ELIO has four **M3 mounting holes** on the corners.

**On a Lego chassis:**
- Use M3 × 6mm screws through ELIO's corners into a Technic beam or plate.
- Or use Lego-compatible mounting brackets (M3 to Lego pin adapters, available on Thingiverse).

**On cardboard:**
- Tape ELIO to the chassis with double-sided tape.
- Route the motor cables underneath.

Keep ELIO near the center of the chassis for balanced weight.

---

## Step 4 — Connect the Battery

ELIO runs from an **external battery** (motors need more current than a coin cell).

**Option A — 9V PP3 battery:**
- Most common. Plug into ELIO's 9V barrel jack.
- Good for ~1 hour of driving with two M-Motors.

**Option B — 7.4V LiPo (2S):**
- Lighter, rechargeable. Use a JST connector to ELIO's LiPo port.
- Better for performance builds.

---

## Step 5 — Power On and Connect

1. Press the **power button** once.
2. Blue LED blinks → ELIO is advertising via BLE.
3. Open **bletoy** on your phone.
4. Tap **Scan** → select **ELIO** from the list.
5. Blue LED goes solid → connected.

---

## Step 6 — Drive

In bletoy:

1. Select **RC Car** mode.
2. The left joystick controls both motors (DC-1 and DC-2 linked).
3. For **tank-style steering** (left motor / right motor independent):
   - Go to **Custom** mode.
   - Assign left joystick axis → DC-1, right joystick axis → DC-2.

**Calibration tip**: If the robot veers left or right on "straight", one motor is stronger. In Custom mode, reduce the stronger motor's max speed by 5–10%.

---

## Step 7 — Build and Experiment

Once you have the basic drive working, the real fun begins:

**Differential steering (most common):**
- Left motor = left wheel, right motor = right wheel.
- Push both joysticks forward = straight. Push one forward, one back = spin in place.

**Add a servo for Ackermann steering:**
- Connect a servo to ELIO's S-1 port.
- Use the steering wheel in the app to control the front axle.
- See [Tutorial 1](/elio-docs/assets/downloads/instructables/01/) for servo wiring.

**Add lights:**
- ELIO's IO ports can drive an LED (up to 20mA).
- Wire a 3mm LED + 220Ω resistor to IO-1.
- Assign it to a button in bletoy.

---

## Troubleshooting

| Symptom | Fix |
|---------|-----|
| Motor doesn't spin | Check PF cable is fully clicked in |
| Motor spins wrong direction | Flip the cable end-for-end in the port |
| Both motors spin but robot goes backward | Swap DC-1 and DC-2 assignments in app |
| Jerky movement at low speed | Normal for PF motors below ~25% — use 30%+ for smooth start |
| App can't find ELIO | Make sure blue LED is blinking, not solid or off |

---

## What's Next?

- **Add block coding** → [Tutorial 3: Block Code with Entry](/elio-docs/assets/downloads/instructables/03/)
- **Go wireless with Arduino** → [Tutorial 4: UART Bridge to Arduino](/elio-docs/assets/downloads/instructables/04/)
- **Full ELIO docs** → [Documentation](https://johnsnow-nam.github.io/elio-docs/)

---

*Part of the ELIO Instructables series.*
