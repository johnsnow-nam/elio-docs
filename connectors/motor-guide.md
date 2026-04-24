---
title: 모터 커넥터 가이드
lang: ko
permalink: /connectors/motor-guide/
---

# 🦾 세상의 모든 모터를 ELIO에 연결하기

> "레고 모터, 집에 있는 이어폰·랜선·전화선, 산업용 모터까지 — 대부분의 모터가 ELIO에 연결됩니다." *— Yonghee*

## 🧱 지원 커넥터 종류

| 종류 | 젠더 필요? | 용도 |
|------|-----------|------|
| 🧱 **레고 PF (Power Functions)** | ✅ 레고 PF 젠더 | 레고 구형 모터 (9V) |
| 🔄 **레고 PU (Powered Up)** | ✅ 레고 PU 젠더 | 레고 신형 모터 |
| 📞 **전화선 (RJ11)** | ✅ RJ11 젠더 | DIY 케이블 변형 |
| 🌐 **랜선 (RJ45)** | ✅ RJ45 젠더 | 4모터까지 하나로 연결 |
| 🎧 **이어폰 (3.5mm)** | ✅ 3.5mm 젠더 | 소형 진동 모터·스피커 |
| 🔩 **일반 DC 모터** (2선) | 직결 | 6~12V 취미용 |
| ⚙️ **RC 서보** (3선) | 직결 | 표준 서보 |
| 🎛️ **Faulhaber / Maxon 소형 DC** | ✅ 2선 젠더 | 산업용 소형 정밀 모터 |

---

## 🧱 LEGO 모터 연결

### 필요한 젠더
- **PF (Power Functions)**: ELIO LEGO PF Adapter *(Tindie에서 판매 예정)*
- **PU (Powered Up)**: ELIO LEGO PU Adapter *(Tindie에서 판매 예정)*

### 연결 방법

```
[레고 모터] ──(레고 커넥터)── [ELIO LEGO PF/PU 젠더] ──(ELIO 4핀)── [ELIO 보드 DC1]
```

### 지원하는 레고 모터

| 모델 | 방식 | 특징 |
|------|------|------|
| LEGO Power Functions M 모터 | PF | 9V 기본 모터 |
| LEGO Power Functions L 모터 | PF | 고토크 |
| LEGO Power Functions XL 모터 | PF | 최고 토크, 크기 큼 |
| LEGO Power Functions 서보 | PF | 각도 제어 |
| LEGO Technic Hub 모터 | PU | 엔코더 내장 |
| LEGO SPIKE Prime 모터 | PU | 엔코더 + 각도 |

> **참고**: PU(Powered Up) 모터의 엔코더·위치 피드백은 현재 초기 지원 단계입니다. 자세한 기능은 펌웨어 프로파일별로 다릅니다.

---

## 🔩 일반 DC 모터 (브레드보드 · 점퍼 선)

2선 DC 모터는 **젠더 없이 직결** 가능:

```
DC 모터 선 (빨강) ──→ DC1 포트 단자 ①
DC 모터 선 (검정) ──→ DC1 포트 단자 ②
```

극성을 바꾸면 회전 방향만 반대가 됩니다.

### 전압·전류 한계

| 항목 | 값 |
|------|-----|
| 공급 전압 | 6 ~ 12 V |
| 최대 전류 (per channel) | 1.5 A (연속), 2.0 A (피크) |
| PWM 주파수 | 10 kHz (기본) |

---

## ⚙️ RC 서보 모터 (3선)

표준 3선 RC 서보는 **SV1 / SV2 포트에 직결**:

```
서보 (검정 / 빨강 / 노랑) ──→ SV1 (GND / +V / Signal)
```

핀 순서는 포트 라벨 확인.

---

## 🎛️ 산업용 소형 모터 (Faulhaber, Maxon)

2선 DC 직결과 동일하지만 **전압·전류 매칭**이 중요합니다.

| 권장 방법 |
|----------|
| Faulhaber 6V 이하 소형: DC1/DC2 직결 |
| Faulhaber 12V 이하: DC1/DC2 직결 + 별도 전원 |
| 12V 초과 산업용: **외부 H-브리지 드라이버** 사용 + ELIO IO를 신호선으로만 연결 |

---

## 🌐 흔한 케이블을 활용한 DIY 젠더

어린이·교사도 쉽게 만들 수 있도록:

### RJ11 (전화선)으로
- 전화선의 4선 (보통 빨·초·노·검) → DC 2채널 + 전원
- 끝을 잘라 ELIO 포트에 삽입
- *Instructables 튜토리얼 Wave 1에서 제공 예정*

### RJ45 (랜선)으로
- 8선 → DC×2 + 서보×2 또는 IO 확장까지
- 한 케이블로 많은 채널 동시 연결 가능

### 3.5mm 이어폰 잭으로
- 소형 진동 모터·스피커·LED 등 저전력 부속
- DIY 젠더를 만들어 여러 작품에 공용으로

---

## 🔌 ELIO 포트 핀맵 (공통)

DC1·DC2·SV1·SV2 포트의 핀 순서(예):

```
DC 포트 (4핀):
  ┌─────┬─────┬─────┬─────┐
  │ GND │  +V │  M+ │  M- │
  └─────┴─────┴─────┴─────┘

서보 포트 (3핀):
  ┌─────┬─────┬─────┐
  │ GND │  +V │ Sig │
  └─────┴─────┴─────┘
```

정확한 배치는 보드의 실크스크린 또는 [하드웨어 레퍼런스](/elio-docs/firmware/) 참조.

---

## 🛠 안전 주의사항

- ⚠️ **극성 반대 연결**: 손상되지는 않으나 회전 방향만 반대
- ⚠️ **과전류**: 연속 1.5A 초과 시 모터 드라이버가 자동 보호 (LED 빠른 깜빡임)
- ⚠️ **레고 서보의 기계적 엔드스톱**: 범위 밖 각도 지정 금지 (모터 타버림)
- ⚠️ **산업용 모터**: 12V 초과는 외부 드라이버 필수. ELIO는 신호 제어만

---

## 📸 Instructables 튜토리얼

- 🛠️ [**"Connect Any Motor with Cables You Already Own"**](https://instructables.com/) *(Wave 1 — 1편)*
- 🧱 [**"LEGO Motors + ELIO: Build Any Robot"**](https://instructables.com/) *(Wave 1 — 2편)*

---

## 🛒 젠더 구매

- 🌍 [Tindie 스토어](https://www.tindie.com/) *(준비 중)*
- 🇰🇷 [국내 문의 이메일](mailto:caram88@mobilian.biz)

---

🌐 [**English**](/elio-docs/en/connectors/motor-guide/)
