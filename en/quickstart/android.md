---
title: Android Setup
lang: en
permalink: /en/quickstart/android/
---

# 📱 Connect via Android

> Install the ELIO app from Play Store and connect your phone to the ELIO board over Bluetooth LE.

## Estimated time

**5 minutes**

---

## 🛠 Requirements

- Android 7.0 (Nougat) or higher
- ELIO board (powered — LED slow blinking)
- Wi-Fi (for app download)

---

## 1️⃣ Install the ELIO App

### Option A — QR

Scan the **Android QR** on the QR card from the box.

### Option B — Search

1. Open Play Store
2. Search **"ELIO"**
3. Install the app with the *[ELIO logo]*

> *(Direct Play Store link will be added here once the app is officially released.)*

---

## 2️⃣ Grant Permissions

On first launch:

| Permission | Why |
|-----------|-----|
| **Location** | Required for BLE scanning on Android ≤ 11 |
| **Bluetooth** | Required for BLE connections on Android 12+ |
| **Storage** *(optional)* | For saving/sharing toy models |

Tap **Allow all**.

> **Why location?** Android classifies BLE scanning as location-sensitive. ELIO never reads your actual GPS.

---

## 3️⃣ Power ELIO

Plug USB-C → verify LED is **blinking slowly** (1-second interval).

---

## 4️⃣ Scan & Connect

1. Home screen → **Connect**
2. Device list appears
3. Tap your ELIO entry (default name: `ELIO`)
4. **Connected** badge shows at top

> If multiple ELIO devices appear, pick the one with strongest RSSI.

---

## 5️⃣ First Block — Spin a Motor

1. Bottom tab → **Control**
2. Default template shows a joystick/slider
3. Drag the slider → DC1 motor spins
4. No motion? Make sure a motor is connected to the DC1 port.

### Connecting a DC Motor

Wire the two leads of a DC motor to the two terminals of the **DC1** port. Swapping them just reverses rotation direction.

No motor? The app will still show the virtual output (-100 to +100).

---

## 6️⃣ Try a Sensor — Ultrasonic

1. Tab → **Sensors**
2. Toggle **Ultrasonic ON**
3. Connect ultrasonic module (5V + IO1 + IO2), wave your hand
4. Watch **Distance (cm)** change

---

## ✅ Checkpoints

- [x] App installed
- [x] BLE connected
- [x] Motor responding
- [x] Sensor reading

**You completed your first ELIO session** 🎉

---

## 🆘 Troubleshooting

- 🔌 [**Can't connect**](/en/troubleshooting/#connection)
- 📡 [**BLE not found**](/en/troubleshooting/#ble)
- 🔋 [**LED blinks but app can't find it**](/en/troubleshooting/#ble)

---

## Next

- [**Swap firmware profiles**](/en/firmware/)
- [**Connect LEGO motors**](/en/connectors/motor-guide/)
- [**Use with Scratch · Entry**](/en/platforms/)

---

⬅ [Back to Quick Start](/en/quickstart/)
