---
title: Motor Connector Guide
lang: en
permalink: /en/connectors/motor-guide/
---

# 🦾 Connect Any Motor to ELIO

> "Lego motors, old headphone cables, Ethernet cables, telephone cables, industrial motors — most motors connect to ELIO." *— Yonghee*

## 🧱 Supported Connector Types

| Type | Adapter Needed? | Use Case |
|------|----------------|----------|
| 🧱 **Lego PF (Power Functions)** | ✅ Lego PF adapter | Legacy Lego motors (9V) |
| 🔄 **Lego PU (Powered Up)** | ✅ Lego PU adapter | Modern Lego motors |
| 📞 **Phone cable (RJ11)** | ✅ RJ11 adapter | DIY cable builds |
| 🌐 **Ethernet (RJ45)** | ✅ RJ45 adapter | Connect up to 4 motors with one cable |
| 🎧 **3.5mm audio jack** | ✅ 3.5mm adapter | Small vibration motors, speakers |
| 🔩 **Standard DC motor** (2-wire) | Direct | 6–12V hobby motors |
| ⚙️ **RC servo** (3-wire) | Direct | Standard servos |
| 🎛️ **Faulhaber / Maxon** | ✅ 2-wire adapter | Industrial micro precision motors |

---

## 🧱 Lego Motor Connection

### Required Adapters
- **PF (Power Functions)**: ELIO Lego PF Adapter *(available on Tindie)*
- **PU (Powered Up)**: ELIO Lego PU Adapter *(available on Tindie)*

### Connection

```
[Lego motor] ──(Lego connector)── [ELIO Lego adapter] ──(ELIO 4-pin)── [ELIO DC1 port]
```

### Supported Lego Motors

| Model | Type | Notes |
|-------|------|-------|
| Lego Power Functions M Motor | PF | Standard 9V motor |
| Lego Power Functions L Motor | PF | High torque |
| Lego Power Functions XL Motor | PF | Max torque, larger size |
| Lego Power Functions Servo | PF | Angular control |
| Lego Technic Hub Motor | PU | Built-in encoder |
| Lego SPIKE Prime Motor | PU | Encoder + angle |

> **Note**: Encoder/position feedback for PU (Powered Up) motors is in early support. Capabilities vary by firmware profile.

---

## 🔩 Standard DC Motor (Direct Connection)

Two-wire DC motors connect **directly, no adapter needed**:

```
Motor wire (red)   ──→ DC1 port terminal ①
Motor wire (black) ──→ DC1 port terminal ②
```

Swap the wires to reverse direction.

### Voltage & Current Limits

| Parameter | Value |
|-----------|-------|
| Supply voltage | 6 – 12 V |
| Max current (per channel) | 1.5 A (continuous), 2.0 A (peak) |
| PWM frequency | 10 kHz (default) |

---

## ⚙️ RC Servo (3-wire)

Standard 3-wire RC servos connect **directly to SV1 / SV2 ports**:

```
Servo (black / red / yellow) ──→ SV1 (GND / +V / Signal)
```

Check the port label for pin order.

---

## 🎛️ Industrial Micro Motors (Faulhaber, Maxon)

Same as 2-wire DC direct connection, but **voltage/current matching is critical**.

| Recommendation |
|----------------|
| Faulhaber ≤6V small motors: direct to DC1/DC2 |
| Faulhaber ≤12V: direct + separate power supply |
| >12V industrial: **use external H-bridge driver** + ELIO IO as signal only |

---

## 🌐 DIY Adapters from Common Cables

Easy builds for kids and teachers:

### From RJ11 (Phone Cable)
- 4 wires (red/green/yellow/black) → DC 2 channels + power
- Cut end, insert into ELIO port
- *See Instructables Tutorial 1 for photos*

### From RJ45 (Ethernet Cable)
- 8 wires → DC×2 + servo×2 or IO extension
- One cable for many channels simultaneously

### From 3.5mm Audio Jack
- Small vibration motors, speakers, LEDs (low-power)
- Build once, reuse across projects

---

## 🔌 ELIO Port Pinout

DC1 · DC2 · SV1 · SV2 port pin layout (example):

```
DC port (4-pin):
  ┌─────┬─────┬─────┬─────┐
  │ GND │  +V │  M+ │  M- │
  └─────┴─────┴─────┴─────┘

Servo port (3-pin):
  ┌─────┬─────┬─────┐
  │ GND │  +V │ Sig │
  └─────┴─────┴─────┘
```

Verify exact layout from board silkscreen or [hardware reference](/en/firmware/).

---

## 🛠 Safety Notes

- ⚠️ **Reversed polarity**: motor spins backwards — no damage
- ⚠️ **Overcurrent**: driver auto-protects above 1.5A continuous (LED fast blink)
- ⚠️ **Lego servo mechanical endstop**: never command beyond rated range — motor will burn
- ⚠️ **Industrial motors >12V**: require external driver — ELIO handles signal only

---

## 📸 Instructables Tutorials

- 🛠️ [**"Connect Any Motor with Cables You Already Own"**](/assets/downloads/instructables/01/) *(Wave 1 — Tutorial 1)*
- 🧱 [**"Lego Motors + ELIO: Build Any Robot"**](/assets/downloads/instructables/02/) *(Wave 1 — Tutorial 2)*

---

## 🛒 Buy Adapters

- 🌍 [Tindie Store](https://www.tindie.com/) — search "ELIO"
- 📧 [Contact](mailto:caram88@mobilian.biz)

---

🌐 [**한국어**](/connectors/motor-guide/)
