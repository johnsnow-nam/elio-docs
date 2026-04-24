---
title: micro:bit + ELIO
lang: ko
permalink: /ecosystem/microbit/
---

# 🔬 micro:bit + ELIO — 교실에서 만나는 두 플랫폼

> micro:bit의 **MakeCode 블록 코딩** + ELIO의 **모터·센서 제어**. 초·중학교 교육 현장에서 최고의 조합입니다.

> ⚠ **[추정]** micro:bit ↔ ELIO UART 연동은 현재 개발 단계입니다. 배선·프로토콜 정보는 검증 후 업데이트됩니다.

---

## 왜 micro:bit + ELIO?

- **micro:bit의 강점**: 교육용 MakeCode 환경, LED 매트릭스, 버튼, 가속도계
- **ELIO의 강점**: DC 모터, 서보, 스마트폰 BLE 연결
- **함께 쓰면**: micro:bit가 두뇌, ELIO가 구동계

---

## 준비물

| 항목 | 설명 |
|------|------|
| micro:bit v2 | (v1도 가능하나 v2 권장) |
| ELIO 보드 | 세대3 (ELIO-52810) |
| 점퍼 와이어 | 3선 (TX·RX·GND) |
| 레벨 시프터 | micro:bit 3.3V ↔ ELIO 3.3V (직결 가능) |

> micro:bit는 3.3V 로직이므로 레벨 시프터 없이 직결 가능합니다.

---

## 배선

```
micro:bit (3.3V 로직)      ELIO 보드 (3.3V 로직)
─────────────             ─────────────
P0 (TX)   ──────────────→ RX (P0.31)
P1 (RX)   ←────────────── TX (P0.29)
GND       ──────────────── GND
```

> micro:bit의 엣지 커넥터 P0·P1·GND 핀 사용. 악어클립 케이블로 쉽게 연결 가능.

---

## MakeCode 직렬 통신 블록

MakeCode에서 **직렬(Serial)** 카테고리 블록으로 UART 통신:

```
시작할 때
  → 직렬 보드 연결 설정 (TX: P0, RX: P1, 속도: 115200)

무한 반복
  → 직렬 쓰기 (숫자) [ELIO 명령 바이트 전송]
```

> **⚠ [추정]**: ELIO 전용 MakeCode 확장 블록은 개발 예정입니다. 현재는 직렬 원시 바이트로 제어합니다.

---

## 프로토콜 개요 (개발자용)

ELIO UART 프레임 구조:

```
[STX] [CMD: 'M'] [LEN: 10] [dc1] [dc2] [sv1] [sv2] [io1..io4] [CRC] [ETX]
```

- Baud: **115,200** (8-N-1)
- 프레이밍: STX(`0x02`) / ETX(`0x03`) / ESC(`0x1B`) + XOR CRC

---

## 🎮 프로젝트 아이디어

### 프로젝트 A: micro:bit 기울기로 ELIO 조종
- micro:bit 가속도계(X/Y축) 값 읽기
- 기울임에 따라 DC 모터 속도 계산
- UART로 ELIO에 전달 → 무선 RC 카

### 프로젝트 B: 버튼으로 서보 제어
- micro:bit A 버튼 → 서보1 0도
- micro:bit B 버튼 → 서보1 90도
- A+B 동시 → 서보1 180도

### 프로젝트 C: LED 매트릭스로 배터리 표시
- ELIO 배터리 상태 수신
- micro:bit 5×5 LED로 배터리 레벨 시각화

---

## 교육 활용 팁

- micro:bit 하나로 블록 코딩 교육 → ELIO로 물리 제어까지 확장
- "MakeCode로 코딩 → ELIO가 움직인다"는 과정이 학생 동기 부여에 효과적
- 빨대 프레임 구조물 + micro:bit + ELIO 조합으로 로봇 제작 수업 가능

---

## 🆘 문제 해결

| 증상 | 해결 |
|------|------|
| ELIO가 반응 없음 | TX/RX 교차 확인 (P0→ELIO RX, P1←ELIO TX) |
| 데이터 깨짐 | Baud rate 115200 확인 |
| 전원 불안정 | ELIO에 별도 전원 공급 권장 |

---

🌐 [**English**](/en/ecosystem/microbit/)

---

**다음 단계**
- [Arduino + ELIO](/ecosystem/arduino/) — C++ 환경
- [ESP32 + ELIO](/ecosystem/esp32/) — WiFi + AI 비전
- [교육 가이드](/education/) — 수업 활용 자료
