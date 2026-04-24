---
title: Arduino + ELIO
lang: ko
permalink: /ecosystem/arduino/
---

# 🔷 Arduino + ELIO — UART로 대화하기

> Arduino가 이미 있나요? 버리지 마세요. ELIO가 **Arduino의 동료**가 되어 드립니다.

## 왜 Arduino + ELIO?

- **Arduino의 강점**: 다양한 쉴드, 방대한 라이브러리
- **ELIO의 강점**: 스마트폰 연결, 멀티 펌웨어, 쉬운 모터/센서
- **함께 쓰면**: 최강 조합

**→** ELIO가 모터·센서 제어를 담당, Arduino가 복잡한 로직·쉴드 처리.

---

## 🔌 배선

```
Arduino UNO (5V 로직)        ELIO 보드 (3.3V 로직)
  ─────────────             ─────────────
  D1 (TX)  ──→ 레벨 시프터 ──→ RX (P0.31)
  D0 (RX)  ←── 레벨 시프터 ←── TX (P0.29)
  GND      ───────────────── GND
```

> **중요**: Arduino UNO는 5V 로직, ELIO는 3.3V. 직결하지 말고 레벨 시프터 사용. 또는 Arduino Nano 33 BLE (3.3V) 사용 가능.

---

## 📦 Arduino 라이브러리 설치

### Library Manager (권장 — Wave 2 공식 등록 예정)

```
Arduino IDE → 툴 → 라이브러리 관리자
→ "ELIO" 검색
→ 설치
```

### 수동 설치 (현재)

1. GitHub: [arduino-with-elio](https://github.com/johnsnow-nam/arduino-with-elio) ZIP 다운로드
2. Arduino IDE → 스케치 → 라이브러리 포함 → .ZIP 라이브러리 추가

---

## 💻 첫 스케치

```cpp
#include <Arduino.h>
#include <elio.h>

void setup() {
  Serial.begin(115200);
  delay(100);
}

void loop() {
  sendDC("DC1", 50);      // DC1 모터 50%
  delay(1000);
  sendDC("DC1", 0);       // 정지
  delay(1000);

  sendDC("DC2", -50);     // DC2 역방향
  delay(1000);
  sendDC("DC2", 0);
  delay(1000);
}
```

## 📚 핵심 API

| 함수 | 설명 |
|------|------|
| `sendDC(motor, power)` | DC 모터 제어 (`"DC1"` / `"DC2"`, -100 ~ +100) |
| `sendServo(servo, angle)` | 서보 각도 (`"SV1"` / `"SV2"`, 0 ~ 180) |
| `sendIO(port, value)` | IO 출력 (`"IO1"` ~ `"IO4"`, `"3V"`, `"5V"`) |
| `sensorConfig(sonic, line1, line2)` | 센서 활성화 (`"ON"` / `"OFF"`) |
| `getUartStatus()` | 상태 수신 (거리·라인 값) |

---

## 🛠 실제 프로젝트 예

### 프로젝트 A: 초음파 센서가 있는 Arduino 쉴드 + ELIO가 모터 담당

- Arduino가 HC-SR04로 거리 측정
- 거리 값에 따라 UART로 ELIO에 모터 명령
- "Arduino가 뇌, ELIO가 손발"

### 프로젝트 B: LCD 쉴드로 상태 표시

- Arduino에 1602 LCD 쉴드
- ELIO의 배터리·속도를 Arduino가 받아서 표시
- 사용자가 Arduino 버튼으로 ELIO 제어

### 프로젝트 C: RFID로 제어

- Arduino + RFID 리더
- 카드를 대면 Arduino가 ELIO에 "DC1 100%" 명령
- 출석 로봇, 출입 장치

---

## 📸 Instructables 튜토리얼

[**"ELIO + Arduino: Two Boards Talking via UART"**](https://instructables.com/) *(Wave 1 — 4편)*

---

## 🆘 문제 해결

- 🔌 **글자는 가는데 ELIO가 반응 없음**: 레벨 시프터 확인 (5V → 3.3V)
- 🔁 **깨진 데이터**: Baud rate 양쪽 115200 확인
- 🔋 **양쪽 다 USB 전원**: 접지(GND) 연결 필수

---

🌐 [**English**](/en/ecosystem/arduino/)
