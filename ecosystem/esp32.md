---
title: ESP32 + ELIO — WiFi + AI 비전
lang: ko
permalink: /ecosystem/esp32/
---

# 📡 ESP32 + ELIO — WiFi 원격 제어 + AI 비전

> ESP32-CAM이 **ELIO의 두뇌**가 됩니다. Wi-Fi HTTP API + TFLite AI 추론으로 카메라가 보는 것에 반응하는 로봇을 만들어보세요.

---

## 시스템 구조

```
[스마트폰 / 브라우저]
        │ WiFi HTTP
        ▼
[ESP32-CAM]
   ├─ 카메라 → TFLite AI 추론
   ├─ HTTP API 서버 (/power, /sensor ...)
   └─ UART TX/RX/GND
        │
        ▼
[ELIO 보드 (세대3)]
   ├─ DC 모터 × 2
   ├─ 서보 × 2
   └─ 센서 (초음파·라인)
```

---

## 준비물

| 항목 | 설명 |
|------|------|
| ESP32-CAM | AI-Thinker 모듈 (또는 호환 보드) |
| ELIO 보드 | 세대3 (ELIO-52810) |
| 점퍼 와이어 | TX·RX·GND 3선 |
| Arduino IDE | ESP32 보드 패키지 설치 |

---

## 배선

```
ESP32-CAM (3.3V 로직)      ELIO 보드 (3.3V 로직)
──────────────            ─────────────
GPIO1 (U0TXD)  ─────────→ RX (P0.31)
GPIO3 (U0RXD)  ←───────── TX (P0.29)
GND            ──────────── GND
3V3 (또는 별도)  ──────────── VCC
```

> **주의**: ESP32-CAM 프로그래밍 시 GPIO0을 GND에 연결해야 합니다. 업로드 완료 후 분리하세요.

---

## 1단계 — 펌웨어 설치

```bash
# GitHub에서 클론
git clone https://github.com/johnsnow-nam/esp32-with-elio
```

Arduino IDE에서:
1. `esp32-with-elio/ELIOCameraWebServer/ELIOCameraWebServer.ino` 열기
2. WiFi SSID·패스워드 입력:
   ```cpp
   const char* ssid = "YOUR_WIFI";
   const char* password = "YOUR_PASS";
   ```
3. 보드: **AI Thinker ESP32-CAM** 선택
4. 업로드

---

## 2단계 — 연결 확인

1. 시리얼 모니터(115200) 열기
2. IP 주소 확인: `Camera Ready! Use 'http://192.168.x.x' to connect`
3. 브라우저로 접속

---

## HTTP API

| 엔드포인트 | 메서드 | 설명 |
|------------|--------|------|
| `/stream` | GET | 카메라 MJPEG 스트림 |
| `/status` | GET | ELIO 현재 상태 JSON |
| `/power` | POST | DC 모터 제어 |
| `/sensor` | POST | 센서 활성화 |
| `/ml` | POST | AI 추론 트리거 |

### 예: curl로 모터 제어

```bash
curl -X POST http://192.168.x.x/power \
  -d "dc1=80&dc2=80"   # 앞으로
```

---

## 🤖 AI 비전 파이프라인

```
카메라 → 320×240 JPEG 캡처
    → TFLite Micro 추론 (분류 / 검출)
    → 결과에 따라 ELIO 제어 명령 전송
```

**활용 예**:
- **물체 추적**: 카메라가 특정 색·물체 감지 → 방향 조정
- **얼굴 인식**: 얼굴 위치에 따라 서보 팬/틸트 제어
- **라인 팔로잉 (비전 기반)**: 바닥 라인 인식 → 모터 PID 제어

---

## Android 앱 연동

ELIO Android 앱은 **두 가지 연결 경로**를 동시 지원합니다:

1. **BLE 직접**: 앱 ↔ ELIO (일반 제어)
2. **WiFi 경유**: 앱 → ESP32 HTTP → ELIO (비전·원격 제어)

앱 설정에서 "WiFi 연결" 모드 선택 후 ESP32 IP 주소 입력.

---

## 🛠 프로젝트 아이디어

### 🏎 AI 자율 주행 RC 카
- 카메라 라인 인식 → PID로 모터 속도 조절
- 장애물 감지 → 자동 정지

### 🦾 원격 감시 로봇
- 스마트폰 앱으로 WiFi 조종
- 실시간 카메라 스트림 확인
- 센서 데이터(거리·라인) 실시간 모니터링

### 👋 제스처 인식 로봇
- ESP32 카메라로 손 제스처 인식
- 제스처에 따라 ELIO 동작 매핑

---

## 🆘 문제 해결

| 증상 | 해결 |
|------|------|
| ESP32가 WiFi 연결 안 됨 | SSID/PW 확인, 2.4GHz 망 확인 (5GHz 불가) |
| ELIO가 반응 없음 | TX/RX 교차 확인, ELIO 전원·세대 확인 |
| 카메라 스트림 안 보임 | 브라우저에서 http:// (https 아님) 접속 |
| 업로드 실패 | GPIO0-GND 연결 후 재시도, 업로드 후 분리 |

---

🌐 [**English**](/elio-docs/en/ecosystem/esp32/)

---

**다음 단계**
- [Arduino + ELIO](/elio-docs/ecosystem/arduino/) — C++ 환경, 더 단순한 구조
- [Python UART SDK](/elio-docs/platforms/python/) — PC Python 제어
- [에코시스템 전체](/elio-docs/ecosystem/)
