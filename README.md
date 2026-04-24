# elio-docs

ELIO 공식 문서 사이트 소스.

> **Phase 5 Wave 1 — GitHub Pages 기반 초기 구축 버전**

## 구조

```
elio-docs/
├── _config.yml              ← Jekyll 설정
├── index.md                 ← 홈 (한국어)
├── en/index.md              ← 홈 (영어)
│
├── quickstart/              ← 빠른 시작 (30분 안에)
│   ├── index.md
│   ├── unboxing.md
│   ├── android.md
│   └── ios.md
│
├── firmware/                ← 4종 펌웨어 프로파일
│   ├── index.md             ← "One board, four personalities"
│   ├── elio-base.md
│   ├── elio-farm.md
│   ├── elio-servo.md
│   └── elio-sensor.md
│
├── connectors/              ← 모터 커넥터 가이드
│   └── motor-guide.md
│
├── education/               ← 교육 (교사·학교)
│   ├── middle-school.md     ← 중학교 기술 교과 연계 (B5 PDF 대기)
│   └── elementary.md        ← 초등 빨대 프레임 (PPT 대기)
│
├── platforms/               ← 교육 플랫폼 연결
│   ├── entry.md
│   ├── scratch.md
│   └── python.md
│
├── ecosystem/               ← 다른 보드와 대화
│   ├── arduino.md
│   ├── microbit.md
│   ├── esp32.md
│   └── pixhawk.md
│
├── troubleshooting/         ← FAQ · 문제 해결
│   └── index.md
│
├── en/                      ← 영어 버전 (전 섹션 미러)
│   └── ...
│
└── assets/
    ├── css/
    ├── images/
    └── downloads/           ← PDF, 인쇄물
```

## 로컬 개발

```bash
# Ruby + Bundler 필요
gem install bundler jekyll
bundle install
bundle exec jekyll serve

# 브라우저에서 http://localhost:4000/elio-docs 열기
```

## GitHub Pages 배포

1. GitHub 저장소에 push
2. Settings → Pages → Source: `main` branch / `(root)`
3. 임시 주소: https://elioseokhee.github.io/elio-docs
4. 도메인 확정 후 `CNAME` 파일 추가 + DNS 설정

## Wave 1 진행 상황

- [x] 사이트 골격 (모든 폴더·스켈레톤 파일)
- [x] Quick Start 한/영 8페이지
- [x] QR 포스터 내용
- [x] Instructables 1편 (Connect Any Motor)
- [ ] Instructables 2~10편 — 프레임만 (Wave 1 후반)
- [ ] 교사 수업 가이드 구조 (B5 PDF 수령 후 본문 작성)
- [ ] 빨대 프레임 초등 가이드 (PPT 수령 후)
- [ ] 브랜드 디자인 적용 (Claude Code 디자인 투입 후)

자세한 기획은 `elio-worlds/seok/PHASE5_WAVE1_EXECUTION_BRIEF.md` 참고.

## 라이선스

문서: CC BY 4.0  
코드 예제: MIT
