---
title: elio-farm 펌웨어
lang: ko
permalink: /firmware/elio-farm/
---

# 🌱 elio-farm — 환경 센서 프로파일

> elio-base 기능에 **온도 · 습도 · 수분** 환경 센서를 추가한 프로파일. 스마트 화분, 실내 농장, 환경 IoT에 최적.

## 지원 기능

elio-base의 모든 기능 + 다음 센서:

| 센서 | 포트 | 단위 |
|------|------|------|
| 온도 | I²C (내장) | °C |
| 습도 | I²C | % RH |
| 수분 (토양) | IO3 (ADC) | 0–1023 raw |

## 추천 프로젝트

- 🪴 자동 물주기 화분
- 🌡️ 실내 공기 상태 대시보드
- 🌾 학교 실습 농장 모니터링

## 사용 예 (Entry 블록)

```
[farm 펌웨어 탑재 후]

▶ 초록색 깃발 클릭 시
  ▶ 매 10초마다 반복
    ▶ ELIO 온도 표시
    ▶ ELIO 수분 < 400 이면
      ▶ DC1 모터 5초간 50 %로 회전 (펌프)
```

## 다음 단계

- 🏫 [**중학교 기술 교과 연계 — 스마트 화분 만들기**](/education/middle-school/)
- 🔌 [**Arduino로 농장 센서 확장하기**](/ecosystem/arduino/)

---

⬅ [펌웨어 개요](/firmware/)
