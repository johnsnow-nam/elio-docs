---
title: Entry (엔트리) + ELIO
lang: ko
permalink: /platforms/entry/
---

# 🟢 Entry (엔트리) + ELIO

> 네이버 커넥트재단의 **한국어 블록 코딩 플랫폼** Entry에 ELIO를 연결해보세요. 초등·중학교 교육 현장에서 검증된 조합입니다.

---

## 준비물

| 항목 | 설명 |
|------|------|
| ELIO 보드 | 전원 ON 상태 |
| USB 동글 | nRF52840 기반 (ELIO 패키지 포함) |
| PC | Windows 10 / macOS 12 이상 |
| Entry HW 앱 | 아래에서 다운로드 |

---

## 1단계 — Entry HW 앱 설치

1. [playentry.org](https://playentry.org/) → 상단 메뉴 **하드웨어** 클릭
2. **Entry HW** 다운로드 → 설치 실행
3. PC 재시작 (드라이버 적용)

> **⚠ 드라이버 안내**: Entry HW 설치 화면에 "CH340 드라이버" 문구가 나올 수 있습니다. ELIO 동글은 Nordic CDC-ACM 방식이므로 CH340 드라이버는 **설치하지 않아도** 됩니다. OS가 자동 인식합니다.

---

## 2단계 — USB 동글 연결

1. USB 동글을 PC에 꽂는다
2. Entry HW 앱 실행
3. 하드웨어 목록에서 **"엘리오(ELIO)"** 선택
4. 연결 버튼 클릭 → 하단 상태바에 **"연결됨"** 표시

---

## 3단계 — ELIO 블록 사용

Entry 웹 에디터([playentry.org](https://playentry.org/))에서:

1. 좌측 블록 탭 → **하드웨어** 카테고리 선택
2. **엘리오(ELIO)** 블록 확인

### 주요 블록

| 블록 | 기능 |
|------|------|
| `엘리오 DC1 모터 [power]로 설정` | DC1 모터 속도·방향 (-100 ~ 100) |
| `엘리오 DC2 모터 [power]로 설정` | DC2 모터 속도·방향 |
| `엘리오 서보 1 [angle]도로 설정` | 서보 각도 (0 ~ 180) |
| `엘리오 초음파 [on/off]` | 초음파 센서 활성화 |
| `엘리오 거리 (cm)` | 초음파 거리 리포터 |
| `엘리오 라인 1 감지?` | 라인 센서 리포터 |

---

## 🎮 첫 번째 프로젝트 — RC 카

```
[키보드 위 화살표] 눌렀을 때
  → 엘리오 DC1 모터 100으로 설정
  → 엘리오 DC2 모터 100으로 설정

[키보드 위 화살표] 떼었을 때
  → 엘리오 DC1 모터 0으로 설정
  → 엘리오 DC2 모터 0으로 설정
```

---

## 🆘 문제 해결

| 증상 | 해결 |
|------|------|
| Entry HW에 ELIO가 안 보임 | 동글을 다시 꽂고 Entry HW 재시작 |
| 연결됐지만 ELIO가 안 움직임 | ELIO 전원·배터리 확인 |
| 블록 카테고리에 하드웨어 없음 | Entry HW 앱 실행 확인 (먼저 HW 연결해야 블록 뜸) |
| macOS에서 포트 안 잡힘 | 시스템 설정 → 개인 정보 보호 → USB 접근 허용 |

---

🌐 [**English**](/elio-docs/en/platforms/entry/)

---

**다음 단계**
- [Scratch 3.0 + ELIO](/elio-docs/platforms/scratch/) — 글로벌 플랫폼 도전
- [Python UART SDK](/elio-docs/platforms/python/) — 텍스트 코딩으로 확장
- [교육 가이드](/elio-docs/education/) — 수업 활용 자료
