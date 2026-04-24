---
title: elio-servo 펌웨어
lang: ko
permalink: /firmware/elio-servo/
---

# 🦿 elio-servo — 서보 특화 프로파일

> 다관절 로봇, 짐벌, 기계 움직임이 많은 프로젝트를 위해 **서보 제어를 최적화**한 프로파일. 서보 캘리브레이션 기능 제공.

## 지원 기능

elio-base의 모든 기능 + 다음 특화:

| 기능 | 설명 |
|------|------|
| **서보 센터점 캘리브레이션** | 각 서보의 중립 위치 미세 조정 (스마트폰 UI) |
| **부드러운 모션** | 서보 각도 변경 시 선형 보간 |
| **동시 다축 동기화** | SV1 · SV2 동시 움직임 타이밍 맞춤 |
| **UART 직결 호환** | ELIO-Bridge Standard — Arduino/Pixhawk 연동 쉬움 |

## 추천 프로젝트

- 🤖 2축 짐벌 카메라 홀더
- 🦾 3D 프린트 로봇 팔
- 🎭 인형극·아트 오토마타
- 🚁 Pixhawk 드론의 페이로드 서보

## 캘리브레이션 UI (앱)

```
앱 → [elio-servo 탑재 후] → 설정 → 서보 캘리브레이션
  ↓
[SV1 센터점: 현재 90°]  [+] [-]  [저장]
[SV2 센터점: 현재 87°]  [+] [-]  [저장]
```

조립 오차로 서보의 기구학적 중립이 90°가 아닐 때 이 UI로 맞춥니다.

## 다음 단계

- 🔌 [**Arduino로 다관절 팔 만들기**](/elio-docs/ecosystem/arduino/)
- 🚁 [**Pixhawk 드론에 짐벌 달기**](/elio-docs/ecosystem/pixhawk/)

---

⬅ [펌웨어 개요](/elio-docs/firmware/)
