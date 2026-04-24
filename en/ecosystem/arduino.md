---
title: Arduino + ELIO
lang: en
permalink: /en/ecosystem/arduino/
---

# 🔷 Arduino + ELIO — Talking via UART

> Already have an Arduino? Don't retire it. ELIO becomes **Arduino's teammate**.

## Why Arduino + ELIO?

- **Arduino's strength**: huge shield ecosystem, vast libraries
- **ELIO's strength**: smartphone BLE, multi-firmware, easy motor/sensor control
- **Together**: the best of both worlds

**→** ELIO handles motor & sensor control, Arduino handles complex logic and shields.

---

## 🔌 Wiring

```
Arduino UNO (5V logic)           ELIO board (3.3V logic)
  ─────────────                  ─────────────
  D1 (TX)  ──→ level shifter ──→ RX (P0.31)
  D0 (RX)  ←── level shifter ←── TX (P0.29)
  GND      ──────────────────── GND
```

> **Important**: Arduino UNO uses 5V logic; ELIO uses 3.3V. Do not connect directly — use a level shifter. Or use Arduino Nano 33 BLE (3.3V native).

---

## 📦 Install the ELIO Arduino Library

### Library Manager (recommended — official registration coming in Wave 2)

```
Arduino IDE → Tools → Library Manager
→ Search "ELIO"
→ Install
```

### Manual Install (current)

1. GitHub: [arduino-with-elio](https://github.com/johnsnow-nam/arduino-with-elio) — download ZIP
2. Arduino IDE → Sketch → Include Library → Add .ZIP Library

---

## 💻 First Sketch

```cpp
#include <Arduino.h>
#include <elio.h>

void setup() {
  Serial.begin(115200);
  delay(100);
}

void loop() {
  sendDC("DC1", 50);      // DC1 motor 50%
  delay(1000);
  sendDC("DC1", 0);       // Stop
  delay(1000);

  sendDC("DC2", -50);     // DC2 reverse
  delay(1000);
  sendDC("DC2", 0);
  delay(1000);
}
```

## 📚 Core API

| Function | Description |
|----------|-------------|
| `sendDC(motor, power)` | DC motor control (`"DC1"` / `"DC2"`, -100 to +100) |
| `sendServo(servo, angle)` | Servo angle (`"SV1"` / `"SV2"`, 0 to 180) |
| `sendIO(port, value)` | IO output (`"IO1"` to `"IO4"`, `"3V"`, `"5V"`) |
| `sensorConfig(sonic, line1, line2)` | Activate sensors (`"ON"` / `"OFF"`) |
| `getUartStatus()` | Receive status (distance, line values) |

---

## 🛠 Real Project Examples

### Project A: Arduino ultrasonic shield + ELIO handles motors

- Arduino reads HC-SR04 distance
- Sends UART motor commands to ELIO based on distance
- "Arduino is the brain, ELIO is the hands"

### Project B: LCD shield for status display

- Arduino with 1602 LCD shield
- Receives ELIO battery/speed → displays on LCD
- User controls ELIO via Arduino buttons

### Project C: RFID-controlled robot

- Arduino + RFID reader
- Card tap → Arduino sends "DC1 100%" to ELIO
- Attendance robot, access control device

---

## 📸 Instructables Tutorial

[**"ELIO + Arduino: Two Boards Talking via UART"**](/assets/downloads/instructables/04/) *(Wave 1 — Tutorial 4)*

---

## 🆘 Troubleshooting

- 🔌 **Data sends but ELIO doesn't respond**: check level shifter (5V → 3.3V)
- 🔁 **Garbled data**: verify baud rate is 115200 on both sides
- 🔋 **Both powered by USB**: make sure GND is connected between boards

---

🌐 [**한국어**](/ecosystem/arduino/)
