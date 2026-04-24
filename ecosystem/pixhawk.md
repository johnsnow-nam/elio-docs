---
title: Pixhawk + ELIO — 드론 페이로드 제어
lang: ko
permalink: /ecosystem/pixhawk/
---

# 🚁 Pixhawk + ELIO — 드론에 스마트 페이로드를

> Pixhawk가 비행 제어를 담당하고, ELIO가 **페이로드(카메라 짐벌·그리퍼·LED)를 스마트폰으로 제어**합니다. TELEM2 포트로 UART 연결.

> ⚠ **[추정]** Pixhawk ↔ ELIO UART 연동은 커뮤니티 실험 단계입니다. 비행 전 반드시 지상 테스트를 완료하세요.

---

## 시스템 구조

```
[스마트폰]
    │ BLE
    ▼
[ELIO 보드]                    [Pixhawk]
 ├─ DC 모터 (그리퍼·페이로드) │ 비행 제어
 ├─ 서보 (짐벌 팬/틸트)       │ GPS·IMU
 └─ UART TX/RX/GND ───────────┘ TELEM2 포트

```

**역할 분담**:
- **Pixhawk**: 비행(모터·ESC·PID), GPS 자율비행
- **ELIO**: 페이로드 제어 (짐벌·그리퍼·LED), 스마트폰 BLE 연결

---

## 준비물

| 항목 | 설명 |
|------|------|
| Pixhawk (또는 호환 FC) | Pixhawk 4, Cube Orange, ArduPilot 호환 |
| ELIO 보드 | 세대3 (ELIO-52810) |
| TELEM2 케이블 | JST-GH 6핀 → UART 변환 |
| 전원 | ELIO 별도 5V BEC 권장 |

---

## 배선 — TELEM2 포트

```
Pixhawk TELEM2 (3.3V)       ELIO 보드 (3.3V)
────────────────            ─────────────
TX (핀 2)  ──────────────→  RX (P0.31)
RX (핀 3)  ←────────────── TX (P0.29)
GND (핀 6) ──────────────── GND
(VCC 핀 1은 ELIO 전원으로 사용하지 말 것 — 별도 BEC 권장)
```

> **TELEM2 핀맵** (Pixhawk 4 기준):  
> 1=VCC, 2=TX, 3=RX, 4=CTS, 5=RTS, 6=GND

---

## ArduPilot 설정

TELEM2 포트를 순수 UART로 사용하려면 MAVLink 비활성화 필요:

```
Mission Planner → Config → Full Parameter List
SERIAL2_PROTOCOL = 0  (None — MAVLink 비활성화)
SERIAL2_BAUD = 115     (115200)
```

> 이렇게 설정하면 TELEM2는 MAVLink 통신 없이 원시 UART로 동작합니다.

---

## ELIO 페이로드 제어 시나리오

### 🎥 2축 카메라 짐벌

```
스마트폰 앱 조이스틱 → BLE → ELIO
ELIO → 서보1 (팬) · 서보2 (틸트)
```

- 앱 조이스틱으로 카메라 방향 실시간 제어
- 비행 중 Pixhawk와 독립적으로 동작

### 🤖 투하·그리퍼

```
스마트폰 앱 버튼 → BLE → ELIO
ELIO → DC 모터 또는 서보 (그리퍼 개폐)
```

- 드론 배송, 물체 투하 실험
- 앱 버튼 하나로 페이로드 릴리즈

### 💡 LED 조명 제어

```
스마트폰 앱 → BLE → ELIO → IO 포트 → LED
```

- 드론 야간 비행 표시등
- 촬영용 조명 원격 ON/OFF

---

## 안전 주의사항

> **비행 전 반드시 지상 테스트!**

- ELIO 동작이 Pixhawk 비행 제어와 충돌하지 않는지 확인
- 배선 단락(쇼트)이 Pixhawk를 손상시킬 수 있으므로 열수축 튜브 사용
- ELIO 전원은 Pixhawk TELEM VCC에서 직접 받지 말고 별도 BEC 사용
- BLE 제어 범위(~30m) 확인

---

## 프로토콜 정보 (개발자용)

Pixhawk에서 ELIO로 UART 직접 제어 시:

```c
// UART 제어 프레임
[STX=0x02][CMD='M'][LEN=10][dc1][dc2][sv1][sv2][io1..io4][CRC][ETX=0x03]
```

C/C++ 구현: ArduPilot의 AP_HAL UART 드라이버 사용.

---

## 🆘 문제 해결

| 증상 | 해결 |
|------|------|
| ELIO가 반응 없음 | TX/RX 교차 확인, Baud 115200 확인 |
| Pixhawk 부팅 후 TELEM2 통신 안 됨 | `SERIAL2_PROTOCOL=0` 재확인 |
| ELIO 전원 불안정 | 별도 BEC(5V 2A) 사용 |
| BLE 연결 안 됨 | 드론 배터리 전원 인가 후 ELIO 전원 순서 확인 |

---

🌐 [**English**](/elio-docs/en/ecosystem/pixhawk/)

---

**다음 단계**
- [ESP32 + ELIO](/elio-docs/ecosystem/esp32/) — WiFi 원격 제어
- [Arduino + ELIO](/elio-docs/ecosystem/arduino/) — 지상 로봇 제어
- [elio-servo 펌웨어](/elio-docs/firmware/elio-servo/) — 2축 짐벌 최적화 프로파일
