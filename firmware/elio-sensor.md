---
title: elio-sensor 펌웨어
lang: ko
permalink: /firmware/elio-sensor/
---

# 👁️ elio-sensor — 풀 센서 프로파일

> 초음파 · 라인 센서 ×2 · 조도까지 풀 스택으로 지원. **라인 팔로잉 로봇, 자율 주행, 센서 기반 AI 프로젝트**를 위한 프로파일.

## 지원 기능

elio-base의 모든 기능 + 다음 센서:

| 센서 | 포트 | 출력 |
|------|------|------|
| 초음파 (HC-SR04 계열) | 5V + IO1 + IO2 | 거리 0 ~ 400 cm |
| 라인 트래커 #1 | 3V + IO3 | 0 (감지) / 1 (미감지) |
| 라인 트래커 #2 | 3V + IO4 | 0 / 1 |
| 조도 센서 | 내장 | Lux 상대값 |

## 센서 마스크 (선택 활성화)

앱 또는 API에서 필요한 센서만 선택:

```
sensor_sonic  = 0x01
sensor_line1  = 0x02
sensor_line2  = 0x04
sensor_light  = 0x08

예: 초음파 + 라인 ×2 → mask = 0x07
```

## 추천 프로젝트

- 🤖 라인 팔로잉 로봇 (경진대회용)
- 🚗 장애물 회피 자율주행
- 🧠 센서 → 조건 → 동작의 기초 AI 개념
- 💡 어두워지면 LED 자동 점등

## 예: 라인 팔로잉 (Scratch 블록 예)

```
▶ 깃발 클릭
  ▶ elio-sensor 펌웨어 변신
  ▶ 초음파·라인1·라인2 센서 켜기
  ▶ 무한 반복
    ▶ 만약 라인1 = 0 이면 (왼쪽 라인 감지)
      ▶ DC1 = 50, DC2 = 30 (오른쪽으로 선회)
    ▶ 아니고 만약 라인2 = 0 이면
      ▶ DC1 = 30, DC2 = 50
    ▶ 아니면
      ▶ DC1 = 50, DC2 = 50 (직진)
```

## 다음 단계

- 🏎️ [**Instructables: Line-Following Robot**](https://instructables.com/) *(Wave 1)*
- 📷 [**ESP32 AI 카메라와 결합**](/elio-docs/ecosystem/esp32/)

---

⬅ [펌웨어 개요](/elio-docs/firmware/)
