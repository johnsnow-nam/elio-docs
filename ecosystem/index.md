---
title: 에코시스템 — The bridge board that talks to everything
lang: ko
permalink: /ecosystem/
---

# 🌐 에코시스템

> **"The bridge board that talks to everything."**  
> ELIO는 Arduino·ESP32·micro:bit·Pixhawk 어느 것과도 UART로 대화합니다.

---

## 🔗 연결 가능한 생태계

| 파트너 | 연결 방식 | 특기 |
|--------|-----------|------|
| [**Arduino**](/elio-docs/ecosystem/arduino/) | UART (TX/RX/GND) | 방대한 쉴드·라이브러리 |
| [**ESP32**](/elio-docs/ecosystem/esp32/) | UART (TX/RX/GND) | WiFi + AI 비전 |
| [**micro:bit**](/elio-docs/ecosystem/microbit/) | UART (TX/RX/GND) | 교육, MakeCode 블록 |
| [**Pixhawk**](/elio-docs/ecosystem/pixhawk/) | UART (TELEM2) | 드론·자율주행 제어 |

---

## 왜 UART인가?

```
모든 MCU가 가진 공통 인터페이스: TX · RX · GND
```

- 배선이 단 3선 — 복잡한 설정 불필요
- 언어·플랫폼 무관 — 같은 프로토콜이 10+ 언어로 구현됨
- 속도: **115,200 bps** — 실시간 모터·센서 제어에 충분

---

## 📡 에코시스템 연결 지도

```
                    ┌──────────────┐
          BLE       │  iOS 앱      │
  ELIO ◄──────────►│  Android 앱  │
   │                └──────────────┘
   │
   │  UART (TX/RX/GND)
   ├──────────────────────────► Arduino (쉴드, 센서 허브)
   ├──────────────────────────► ESP32 (WiFi, AI 카메라)
   ├──────────────────────────► micro:bit (교육, 블록 코딩)
   └──────────────────────────► Pixhawk (드론, 자율비행)
```

---

## 🤝 철학: 허브 포지션

ELIO는 Arduino·micro:bit·Lego 같은 플랫폼의 **경쟁자가 아닌 동료**입니다.

- Arduino가 복잡한 쉴드·로직을 담당할 때 → ELIO가 모터·BLE 담당
- micro:bit가 교육 블록 환경을 제공할 때 → ELIO가 구동계 담당
- Pixhawk가 비행 제어를 담당할 때 → ELIO가 페이로드 제어 담당

---

🌐 [**English**](/elio-docs/en/ecosystem/)

---

**관련 문서**
- [코딩 플랫폼 (Entry·Scratch·Python)](/elio-docs/platforms/)
- [커넥터 가이드](/elio-docs/connectors/motor-guide/)
- [펌웨어 프로파일](/elio-docs/firmware/)
