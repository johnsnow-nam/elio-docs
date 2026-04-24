---
title: Scratch 3.0 + ELIO
lang: ko
permalink: /platforms/scratch/
---

# 🟠 Scratch 3.0 + ELIO

> MIT의 글로벌 블록 코딩 플랫폼 **Scratch 3.0**에서 ELIO를 제어해보세요. 브라우저만 있으면 됩니다.

> ⚠ **현재 상태**: Scratch Extension은 **개발 진행 중** (#wip)입니다. 핵심 블록(모터·서보·센서)은 동작하며, 다국어 및 공식 배포는 향후 업데이트 예정입니다.

---

## 준비물

| 항목 | 설명 |
|------|------|
| ELIO 보드 | 전원 ON 상태 |
| USB 동글 | nRF52840 기반 |
| **Chrome 89+** | Web Serial API 지원 필수 (Safari·Firefox 불가) |
| ELIO Scratch GUI | 별도 빌드 버전 (아래 참조) |

---

## Scratch와 Entry의 차이

| 항목 | Entry | Scratch 3.0 + ELIO |
|------|-------|---------------------|
| 언어 | 한국어 중심 | 다국어 |
| 앱 설치 | Entry HW 앱 필요 | 브라우저만 (Web Serial) |
| 배포 | 공식 등록 | ELIO 커스텀 빌드 |

---

## 1단계 — ELIO Scratch GUI 열기

> ELIO Scratch는 Scratch GUI를 포크(fork)해 ELIO 확장이 내장된 버전입니다.

1. ELIO Scratch 주소에 접속 (Wave 2 공식 배포 예정 — 현재 Beta)
2. **HTTPS** 또는 **localhost** 환경 필수 (Web Serial 보안 요건)

---

## 2단계 — USB 동글 연결

1. Chrome에서 ELIO Scratch 페이지 열기
2. 좌측 확장 라이브러리 탭 → **ELIO** 카드 클릭
3. `connect elio` 블록 실행 → 팝업에서 **동글 포트** 선택
4. "ELIO 연결됨" 메시지 확인

---

## 3단계 — 블록 사용

### 주요 블록

| 블록 | 기능 |
|------|------|
| `connect elio` | 동글 포트 선택·연결 |
| `set DC1 power to (n) %` | DC1 모터 속도 (-100 ~ 100) |
| `set DC2 power to (n) %` | DC2 모터 속도 |
| `set servo1 angle to (n)°` | 서보 1 각도 (0 ~ 180) |
| `sensor sonic (on/off)` | 초음파 센서 활성화 |
| `(sonic cm)` | 초음파 거리 리포터 |
| `(line1 detect)` | 라인 센서 1 리포터 |

---

## 🎮 첫 번째 프로젝트 — 스마트 RC 카

```scratch
[스페이스키 눌렸을 때]
  → connect elio
  → 반복하기 (계속)
    → 만약 <키 [↑] 눌림?> 이라면
      → set DC1 power to (80) %
      → set DC2 power to (80) %
    아니라면
      → set DC1 power to (0) %
      → set DC2 power to (0) %
```

---

## 브라우저 요건 (Web Serial API)

- ✅ **Chrome 89+** (Windows·macOS·Linux)
- ✅ **Edge 89+**
- ❌ Safari — Web Serial 미지원
- ❌ Firefox — Web Serial 미지원
- 동글 연결 시 **사용자 허용(팝업)** 클릭 필요

---

## 🆘 문제 해결

| 증상 | 해결 |
|------|------|
| 포트 선택 팝업이 안 뜸 | Chrome인지, HTTPS/localhost인지 확인 |
| 포트 목록에 동글 안 보임 | 동글 재삽입 후 새로고침 |
| 블록 실행해도 ELIO 무반응 | ELIO 전원·배터리 확인 |
| macOS에서 "액세스 거부" | Chrome 설정 → 개인정보 → 직렬 포트 허용 |

---

🌐 [**English**](/elio-docs/en/platforms/scratch/)

---

**다음 단계**
- [Entry (엔트리) + ELIO](/elio-docs/platforms/entry/) — 한국어 교육 플랫폼
- [Python UART SDK](/elio-docs/platforms/python/) — 동글 없이 직결
- [에코시스템](/elio-docs/ecosystem/) — Arduino·ESP32 확장
