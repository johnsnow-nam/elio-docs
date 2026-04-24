---
title: iOS Setup
lang: en
permalink: /en/quickstart/ios/
---

# 🍎 Connect via iOS

> Install the ELIO app from App Store and connect your iPhone or iPad to the ELIO board over Bluetooth LE.

## Estimated time

**5 minutes**

---

## 🛠 Requirements

- iPhone or iPad running iOS 14.0+
- ELIO board (powered, LED blinking slowly)
- Apple ID (for App Store download)

---

## 1️⃣ Install the ELIO App

### Option A — QR

Scan the **iOS QR** on the QR card from the box.

### Option B — Search

1. Open App Store
2. Search **"ELIO"**
3. Install the app with *[ELIO logo]*

> *(Direct App Store link will be added here once the app is officially released.)*

---

## 2️⃣ Grant Permissions

On first launch:

| Permission | Why |
|-----------|-----|
| **Bluetooth** | Required for connecting to ELIO |
| **Camera** *(optional)* | For future vision features — can decline for now |

Make sure **Bluetooth** is enabled in iOS Settings.

---

## 3️⃣ Power ELIO

Plug USB-C → LED blinks slowly (1-second interval) indicates advertising mode.

---

## 4️⃣ Scan & Connect

1. Home → **Connect**
2. Device list shows `ELIO`
3. Tap to connect
4. Top badge shows 🔵 **Connected**

> iOS does **not** require location permission (unlike Android).

---

## 5️⃣ First Block — Motor

1. Bottom tab → **Control**
2. Drag the default slider → DC1 motor spins
3. Verify motor rotation or sound

---

## 6️⃣ Sensor — Ultrasonic

1. **Sensors** tab
2. Toggle **Ultrasonic ON**
3. Wave hand in front of sensor → distance updates

---

## ✅ Checkpoints

- [x] App installed
- [x] BLE connected
- [x] Motor responding
- [x] Sensor reading

**Done!** 🎉

---

## 💡 iOS-specific Tips

### Keep BLE in background
For continuous connection when the app is backgrounded: **Settings → General → Background App Refresh → ELIO: ON**.

### Firmware updates (DFU)
iOS supports safe OTA updates via Nordic DFU Library. One-tap in the app's **Firmware** menu.

### iPad big screen
Use the wider control surface to place multiple controllers simultaneously.

---

## 🆘 Troubleshooting

- 📡 [**BLE not found**](/elio-docs/en/troubleshooting/#ble)
- 🔄 **Reset iOS Bluetooth**: Settings → General → Transfer or Reset → Reset Network Settings
- ⚠️ **App not asking for Bluetooth permission**: Settings → ELIO → enable Bluetooth manually

---

## Next

- [**4 firmware profiles**](/elio-docs/en/firmware/)
- [**LEGO motor connection**](/elio-docs/en/connectors/motor-guide/)

---

⬅ [Back to Quick Start](/elio-docs/en/quickstart/)
