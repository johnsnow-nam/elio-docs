---
title: Python UART SDK + ELIO
lang: ko
permalink: /platforms/python/
---

# 🐍 Python으로 ELIO 제어하기

> USB 동글 없이 **TX/RX/GND 3선 직결**로 ELIO를 Python에서 제어합니다. AI 프로젝트, 자동화, 고급 제어에 적합합니다.

> **대응 펌웨어**: 세대3 (ELIO-52810) 전용. 세대1/2 보드는 UART 직결 채널이 없습니다.

---

## 준비물

| 항목 | 설명 |
|------|------|
| ELIO 보드 | 세대3 (ELIO-52810) |
| USB-UART 어댑터 | CP2102, CH340, FT232 등 (3.3V 레벨) |
| PC | Python 3.8 이상 |
| `elio-uart` 패키지 | PyPI 설치 |

> **중요**: USB-UART 어댑터는 반드시 **3.3V 로직 레벨** 제품을 사용하세요. 5V 어댑터는 레벨 시프터가 필요합니다.

---

## 1단계 — 배선

```
USB-UART 어댑터          ELIO 보드
─────────────           ─────────────
TX (송신)  ──────────→  RX (P0.31)
RX (수신)  ←──────────  TX (P0.29)
GND       ──────────── GND
(전원은 별도 공급 또는 VCC 연결)
```

> **크로스 연결**: 어댑터의 TX → ELIO RX, 어댑터의 RX ← ELIO TX.

---

## 2단계 — SDK 설치

```bash
pip install elio-uart
```

의존성: `pyserial` (자동 설치됨)

---

## 3단계 — 첫 번째 코드

```python
from elio_uart.comm.eliochannel import eliochannel
import time

with eliochannel('/dev/ttyUSB0') as ch:  # Windows: 'COM3'
    # DC 모터 제어
    ch.sendPower(dc1=80, dc2=80)   # 앞으로
    time.sleep(1)
    ch.sendPower(dc1=0, dc2=0)     # 정지
    time.sleep(0.5)
    ch.sendPower(dc1=-80, dc2=-80) # 뒤로
    time.sleep(1)
    ch.sendPower(dc1=0, dc2=0)     # 정지
```

### 포트 이름 찾기

```bash
# macOS / Linux
ls /dev/tty*

# Windows (장치 관리자 또는)
python -m serial.tools.list_ports
```

---

## 📚 주요 API

| 함수 | 설명 |
|------|------|
| `ch.sendPower(dc1, dc2)` | DC 모터 제어 (-100 ~ 100) |
| `ch.sendServo(sv1, sv2)` | 서보 각도 (0 ~ 180) |
| `ch.sendIO(io1, io2, io3, io4)` | IO 포트 출력 |
| `ch.sensorConfig(sonic, line1, line2)` | 센서 활성화 (`True`/`False`) |
| `ch.readStatus()` | 센서 상태 수신 (거리·라인 값) |

---

## 🤖 센서 읽기 예제

```python
from elio_uart.comm.eliochannel import eliochannel
import time

with eliochannel('/dev/ttyUSB0') as ch:
    # 초음파 + 라인 센서 활성화
    ch.sensorConfig(sonic=True, line1=True, line2=True)
    time.sleep(0.1)  # 센서 워밍업

    for _ in range(10):
        status = ch.readStatus()
        print(f"거리: {status.sonic_cm}cm | 라인1: {status.line1} | 라인2: {status.line2}")
        time.sleep(0.2)
```

---

## 🚀 AI 프로젝트 예

### 카메라 + OpenCV 장애물 회피

```python
import cv2
from elio_uart.comm.eliochannel import eliochannel

cap = cv2.VideoCapture(0)
with eliochannel('/dev/ttyUSB0') as ch:
    while True:
        ret, frame = cap.read()
        # 이미지 분석 로직
        obstacle_detected = analyze_frame(frame)

        if obstacle_detected:
            ch.sendPower(dc1=0, dc2=0)    # 정지
        else:
            ch.sendPower(dc1=60, dc2=60)  # 전진
```

### Raspberry Pi 자율 주행

- Raspberry Pi의 Python 환경에서 동일한 SDK 사용
- `elio-uart` + OpenCV + TFLite 조합으로 시각 처리 자동화

---

## Baud Rate 및 프로토콜 정보

| 항목 | 값 |
|------|----|
| Baud rate | 115,200 |
| 데이터 비트 | 8 |
| 패리티 | None |
| 스톱 비트 | 1 |
| 프레이밍 | STX / ETX / ESC + XOR CRC |

---

## 🆘 문제 해결

| 증상 | 해결 |
|------|------|
| `serial.SerialException: port not found` | 포트 이름 재확인, 어댑터 재삽입 |
| 연결됐지만 ELIO 무반응 | TX/RX 교차 확인 (TX↔RX 뒤바뀐 경우 흔함) |
| 깨진 데이터 수신 | Baud rate 115200 확인 |
| Linux에서 권한 오류 | `sudo usermod -a -G dialout $USER` 후 재로그인 |
| macOS 포트 없음 | CP2102/CH340 드라이버 설치 확인 |

---

🌐 [**English**](/elio-docs/en/platforms/python/)

---

**다음 단계**
- [Arduino + ELIO](/elio-docs/ecosystem/arduino/) — 같은 UART 프로토콜, C++ 환경
- [ESP32 + ELIO](/elio-docs/ecosystem/esp32/) — WiFi + AI 비전 확장
- [에코시스템 전체 보기](/elio-docs/ecosystem/)
