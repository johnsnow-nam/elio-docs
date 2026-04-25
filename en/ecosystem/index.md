---
title: Ecosystem — The bridge board that talks to everything
lang: en
permalink: /en/ecosystem/
---

# 🌐 Ecosystem

> **"The bridge board that talks to everything."**  
> ELIO talks UART to Arduino, ESP32, micro:bit, Pixhawk — all of them.

---

## 🔗 Compatible Partners

| Partner | Connection | Specialty |
|---------|-----------|-----------|
| [**Arduino**](/elio-docs/ecosystem/arduino/) | UART (TX/RX/GND) | Vast shield & library ecosystem |
| [**ESP32**](/elio-docs/ecosystem/esp32/) | UART (TX/RX/GND) | WiFi + AI vision |
| [**micro:bit**](/elio-docs/ecosystem/microbit/) | UART (TX/RX/GND) | Education, MakeCode blocks |
| [**Pixhawk**](/elio-docs/ecosystem/pixhawk/) | UART (TELEM2) | Drone & autonomous vehicle control |

---

## Why UART?

```
The universal interface every MCU has: TX · RX · GND
```

- Just 3 wires — no complex configuration
- Language & platform agnostic — same protocol, 10+ language implementations
- Speed: **115,200 bps** — more than enough for real-time motor & sensor control

---

## 📡 Ecosystem Connection Map

```
                    ┌──────────────┐
          BLE       │  iOS App     │
  ELIO ◄──────────►│  Android App │
   │                └──────────────┘
   │
   │  UART (TX/RX/GND)
   ├──────────────────────────► Arduino (shields, sensor hubs)
   ├──────────────────────────► ESP32 (WiFi, AI camera)
   ├──────────────────────────► micro:bit (education, block coding)
   └──────────────────────────► Pixhawk (drone, autonomous flight)
```

---

## 🤝 Philosophy: Hub Position

ELIO is a **companion, not a competitor** to Arduino, micro:bit, and Lego.

- When Arduino handles complex shields & logic → ELIO handles motors & BLE
- When micro:bit provides the educational block environment → ELIO handles the drive system
- When Pixhawk manages flight control → ELIO handles payload control

---

🇰🇷 [**한국어**](/elio-docs/ecosystem/)

---

**Related Docs**
- [Coding Platforms (Entry · Scratch · Python)](/elio-docs/en/platforms/)
- [Connector Guide](/elio-docs/en/connectors/motor-guide/)
- [Firmware Profiles](/elio-docs/en/firmware/)
