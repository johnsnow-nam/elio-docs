---
title: 박스 QR 포스터 — 인쇄용 콘텐츠
lang: ko
permalink: /assets/downloads/box-poster-content/
---

# 📦 박스 QR 포스터 콘텐츠 명세

> 이 문서는 ELIO 박스 동봉 QR 포스터의 **텍스트·구성 명세**입니다.  
> 실제 디자인·인쇄 레이아웃은 디자인 팀에서 별도 진행합니다.  
> 인쇄 규격: **B5 (182 × 257 mm)** 양면

---

## 앞면 (Front)

### 상단 — 브랜드 영역

```
[ELIO 로고] (상단 중앙)
"Play first, Code later."
```

### 중앙 — 핵심 메시지

```
📱 Scan to start in 30 minutes
```

(큰 타이포그래피, 한 줄)

### QR 코드 영역 — 3개

| QR | 목적지 | 라벨 텍스트 |
|----|--------|-------------|
| QR ① | `https://elioseokhee.github.io/elio-docs/quickstart/` | **빠른 시작 가이드** / Quick Start |
| QR ② | Android 앱 (Google Play) | **Android 앱** |
| QR ③ | iOS 앱 (App Store) | **iOS 앱** |

레이아웃: 3개 QR 코드를 가로로 배치. 각 QR 아래에 라벨.

### 하단 — 브랜드 태그라인

```
ELIO — The bridge board that talks to everything.
elioseokhee.github.io/elio-docs
```

---

## 뒷면 (Back)

### 상단 헤드라인

```
🎭 One board, four personalities.
```

### 4종 펌웨어 카드 (2×2 그리드)

각 카드 구성: 이름 + 아이콘 + 1줄 설명 + 추천 프로젝트

#### 카드 1 — elio-base

```
⚙️ elio-base
기본 구성 — RC 카, 자유 제어
추천: RC 카, 기본 로봇
```

#### 카드 2 — elio-farm

```
🌱 elio-farm
환경 센서 — 온도·습도·수분
추천: 스마트 화분, 농업 IoT
```

#### 카드 3 — elio-servo

```
🦾 elio-servo
서보 특화 — 다관절·정밀 각도
추천: 로봇 팔, 2축 짐벌
```

#### 카드 4 — elio-sensor

```
📡 elio-sensor
풀 센서 스택 — 초음파·라인·조도
추천: 라인 팔로잉, 자율 주행
```

---

### 중간 — 앱 내 펌웨어 전환 안내

```
✨ 펌웨어 전환 방법
bletoy 앱 → ⚙ 설정 → 펌웨어 업데이트 → 원하는 프로파일 선택
(인터넷 연결 필요 / 약 1분 소요)
```

### 하단 — 지원·커뮤니티

```
📚 전체 가이드: elioseokhee.github.io/elio-docs
🛒 구매·부품: Tindie — search "ELIO"
📢 Instructables: instructables.com — search "ELIO robot"
```

---

## 디자인 지침 (디자이너용)

| 항목 | 스펙 |
|------|------|
| 규격 | B5 (182 × 257 mm), 양면 |
| 도련 | 3mm 사방 |
| 해상도 | 300 DPI 이상 |
| 색상 모드 | CMYK |
| 주색상 | `#1E5FA8` (ELIO 블루) |
| 보조색 | `#FFFFFF`, `#F5F5F5`, `#333333` |
| 폰트 | 한국어: Noto Sans KR / 영어: Inter 또는 동일 계열 |
| QR 크기 | 최소 25 × 25 mm (스캔 가능 최소 크기) |

### QR 코드 생성 시 주의

- URL에 UTM 파라미터 추가 권장: `?utm_source=box&utm_medium=qr&utm_campaign=w1`
- QR 코드 색상: 검정 배경에 흰색 QR은 스캔 안 됨 → 반전 금지
- 여백(quiet zone) 최소 4셀 확보

---

*이 명세를 기반으로 실제 Figma·InDesign 레이아웃은 디자인 파트에서 진행합니다.*
