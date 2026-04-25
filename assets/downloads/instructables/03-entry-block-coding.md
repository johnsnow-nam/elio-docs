---
title: "Instructables 3편: Block-Code Your Robot with Entry"
lang: en
permalink: /assets/downloads/instructables/03/
---

# Block-Code Your Robot with Entry (Korea's #1 Coding Platform)

**Platform**: Instructables  
**Status**: ✅ Ready to publish  
**Target audience**: Educators, students, parents in Korea; global makers curious about Entry  
**Est. read time**: 15 minutes  
**Est. build time**: 30 minutes (setup) + 1 hour (projects)

---

## Introduction

Entry is Korea's dominant block coding platform — used in over 90% of Korean elementary and middle schools. It's similar to Scratch but built specifically for Korean curriculum requirements, with official hardware support for classroom robots.

ELIO connects to Entry over a **USB dongle** (Nordic nRF52840 USB stick, included in every kit). From Entry's block editor, you drag-and-drop commands to spin motors, read sensors, and build fully autonomous behaviors.

**What we'll build**: An ELIO-powered RC car that you first control manually, then upgrade to avoid obstacles automatically — all in Entry blocks, no typing required.

---

## Supplies

| Item | Notes |
|------|-------|
| ELIO board × 1 | Kit includes USB dongle |
| USB dongle × 1 | nRF52840 USB, included in ELIO kit |
| PC | Windows 10+ or macOS 12+ |
| Entry HW app | Free download — [entrylabs.com](https://entrylabs.com) |
| DC motor × 2 | Or Lego motors via PF adapter |
| Chassis | Cardboard, Lego, or any base |
| 9V battery | External power for motors |

---

## Step 1 — Install Entry HW

Entry HW is the bridge between the Entry web editor and physical hardware.

1. Go to [https://entrylabs.com](https://entrylabs.com) → **Download** → **Entry HW**
2. Install the app (Windows .exe or macOS .dmg)
3. Launch **Entry HW**

> **macOS note**: You may need to allow the app in System Settings → Privacy & Security → Allow anyway.

---

## Step 2 — Connect the USB Dongle

1. Plug the **nRF52840 USB dongle** into your PC.
2. Windows will recognize it as a serial port (COMx). macOS shows it as `/dev/cu.usbmodem*`.
   - No extra driver needed — it uses Nordic's CDC-ACM USB class (built into the OS).
3. In Entry HW, click **Hardware connection** → select **ELIO** from the list.
4. Entry HW will auto-detect the dongle port and show **Connected**.

---

## Step 3 — Power On ELIO and Pair

1. Press ELIO's **power button** once.
2. Blue LED blinks = advertising.
3. Entry HW shows ELIO in the device list → click **Connect**.
4. Blue LED goes solid = paired.

> **Range**: BLE works up to ~10m in open space. Keep the dongle within 5m for classroom use.

---

## Step 4 — Open Entry Web Editor

1. Go to [https://playentry.org](https://playentry.org) in Chrome or Edge.
2. Create a free account (or log in).
3. Click **New project**.
4. In the left panel, click **Hardware** → **ELIO** should appear with a green dot (Entry HW is running).

You'll see ELIO-specific blocks added to the palette:

- **DC Motor 1 / DC Motor 2** — speed and direction
- **Servo 1** — angle control (0–180°)
- **IO-1 / IO-2** — digital output (LED, buzzer)
- **Sensor blocks** — if you've added sensors

---

## Step 5 — First Program: Manual Drive

Let's make the car move forward for 2 seconds, then stop.

**Drag these blocks:**

```
[When ▶ clicked]
  [DC Motor 1: forward ▶ 70%]
  [DC Motor 2: forward ▶ 70%]
  [wait 2 seconds]
  [DC Motor 1: stop]
  [DC Motor 2: stop]
```

Click the ▶ button. The car should roll forward and stop.

> **Motor goes backward?** Swap the cable end-for-end in the DC port (or use the "reverse" option in the motor block).

---

## Step 6 — Add Keyboard Control

Now let's drive it like an RC car using arrow keys.

```
[When ▶ clicked] → [repeat forever]
  [if] [↑ arrow key pressed?]
    [DC Motor 1: forward 80%]  [DC Motor 2: forward 80%]
  [else if] [↓ arrow key pressed?]
    [DC Motor 1: backward 80%] [DC Motor 2: backward 80%]
  [else if] [← arrow key pressed?]
    [DC Motor 1: backward 60%] [DC Motor 2: forward 60%]
  [else if] [→ arrow key pressed?]
    [DC Motor 1: forward 60%]  [DC Motor 2: backward 60%]
  [else]
    [DC Motor 1: stop] [DC Motor 2: stop]
```

Run it. You can now steer with keyboard arrows.

---

## Step 7 — Add an Ultrasonic Sensor (Obstacle Avoidance)

Connect an HC-SR04 ultrasonic sensor to ELIO's IO ports (IO-1 = Trig, IO-2 = Echo).

**Obstacle avoidance program:**

```
[When ▶ clicked] → [repeat forever]
  [set distance = ELIO ultrasonic distance (cm)]
  [if] [distance < 20]
    [DC Motor 1: backward 70%] [DC Motor 2: backward 70%]
    [wait 0.5 seconds]
    [DC Motor 1: forward 70%]  [DC Motor 2: backward 70%]  ← turn right
    [wait 0.8 seconds]
  [else]
    [DC Motor 1: forward 70%]  [DC Motor 2: forward 70%]  ← go straight
```

Now the robot drives forward and automatically backs up and turns when it gets within 20cm of an obstacle.

---

## Classroom Notes

**Group size**: 2 students per ELIO works well. One controls the laptop, one monitors the robot.

**Common questions:**

| Question | Answer |
|----------|--------|
| "The motor doesn't move" | Check ELIO is connected in Entry HW (green dot) |
| "Motor goes the wrong way" | Use the 'reverse' option in the motor block, or flip the cable |
| "Entry HW disconnects randomly" | USB dongle may be loose — use a USB extension if the port is on the back |
| "The robot drifts left/right" | One motor is stronger — reduce that motor's % by 5–10 |

**Extension activities (faster learners):**
- Add a score counter that increments every second the robot runs without hitting anything
- Use a button (IO-3) to switch between manual and autonomous mode
- Program a figure-8 route using timed turns

---

## What's Next?

- **More sensor projects** → [Tutorial 5: Ultrasonic Avoidance Deep Dive](/elio-docs/assets/downloads/instructables/05/)
- **Line following** → [Tutorial 6: Line Follower](/elio-docs/assets/downloads/instructables/06/)
- **Entry + ELIO full guide (Korean)** → [Entry 플랫폼 가이드](/elio-docs/platforms/entry/)

---

*Part of the ELIO Instructables series. Full documentation at [elio-docs](https://johnsnow-nam.github.io/elio-docs/).*
