# CLAUDE.md - AI Agent Coding 프로젝트

## 프로젝트 개요

"AI Agent Coding" Quarto 출판 프로젝트. AI 시대 프로그래밍(1부)과 통합 개발 환경(2부)을 다룬다.

- **GitHub**: https://github.com/bit2r/gpt-coding/
- **웹사이트**: https://r2bit.com/gpt-coding/
- **저자**: 이광춘 (공익법인 한국 R 사용자회)

## 기술 스택

- **포맷**: Quarto Markdown (`.qmd`), R + Python
- **출판**: HTML 우선 (`docs/` → GitHub Pages), PDF 준비 중
- **렌더링**: Quarto 1.4+ (`quarto preview` 포트 7771)
- **의존성**: R(`renv.lock`), Python(`.venv/`)
- **Extensions**: fontawesome, include-code-files, fancy-text

## 책 구조

모든 챕터는 `chapters/` 폴더에 위치한다. 이미지 참조 시 `../images/` 경로를 사용한다.

### 도입: AI 시대 글쓰기 환경

- `p0-writing.qmd` — 도구가 사고를 바꾸는 글쓰기
- `p0-environment.qmd` — 소프트웨어 3.0 시대

### 1부: AI 코딩

- `p1-paradigm.qmd` — 재사용에서 재생성으로
- `p1-meta.qmd` — 메타프로그래밍
- `p1-context.qmd` — 프롬프트에서 컨텍스트로
- `p1-workflow.qmd` — AI 코딩 실전 워크플로우
- `p1-review.qmd` — 코드 리뷰와 품질 관리
- `p1-tools.qmd` — AI 도구 생태계
- `p1-future.qmd` — 개발자의 미래

### 2부: 통합 개발 환경

- `p2-intro.qmd` — IDE 역사부터 미래
- `p2-positron.qmd` — Positron
- `p2-extension.qmd` — IDE 확장 프로그램
- `p2-setup.qmd` — 개발 환경 구축
- `p2-zed.qmd` — Zed 에디터
- `p2-docker.qmd` — Docker
- `p2-compendium.qmd` — Research Compendium

### 부록

- `glossary.qmd` — 용어집
- `references.qmd` — 참고문헌

## 디렉토리 구조

```
gpt-agent/
├── _quarto.yml          # Quarto 설정
├── _extensions/          # Quarto 확장
├── gpt-agent.Rproj      # R 프로젝트
├── index.qmd            # 서문 (루트 필수)
├── chapters/            # 본문 챕터 (.qmd)
├── images/              # SVG 다이어그램 (Tufte style)
├── assets/              # 스타일, 참고문헌
├── code/                # R/Python 공통 스크립트
├── docs/                # HTML 출력 (GitHub Pages)
├── tech_document/       # 기술 문서
├── PLAN.md              # 프로젝트 계획
├── PROGRESS.md          # 진행 현황
└── .claude/commands/    # Claude 스킬
```

## 핵심 규칙

### 다이어그램: Tufte Style Grayscale SVG

모든 다이어그램은 흑백(#333, #666, #999) Palatino 서체 SVG로 제작한다. HTML/PDF 양쪽 호환, 인쇄 품질 보장이 목적이다. 상세 규격과 템플릿은 `/diagram` 스킬 참조.

### 문체: 평서문 + AI 티 제거

- 서문(`index.qmd`) 외 모든 챕터는 평서문("~한다", "~이다")
- **"이 + 명사" 패턴 금지** (최우선): "이 메서드는" → "`startswith()`는"
- 기계적 연결어 금지: "다음으로,", "또한,", "마지막으로,"
- 상세 검사 규칙은 `/style-check` 스킬 참조

### 한글화 용어

- 첫 등장: 한글(영어) 병기 + `\index{한글}` — 재등장 시 한글만
- 브랜드/약어/패키지명은 원어 유지 (Git, IDE, API, pandas 등)
- 상세 규칙과 용어 분류는 `/translate` 스킬 참조

## 스킬 안내

| 스킬 | 용도 |
|------|------|
| `/status` | 집필 진행 현황 대시보드 |
| `/outline` | 챕터 아웃라인 설계 |
| `/new-chapter` | 신규 챕터 생성 |
| `/write-chapter` | 챕터 집필/보강 |
| `/review` | 원고 리뷰 |
| `/evaluate` | 품질 정량 평가 |
| `/compare` | 챕터 간 비교 |
| `/style-check` | 문체 검수 |
| `/translate` | 용어 일관성 |
| `/fact-check` | 기술 사실 검증 |
| `/execute` | 코드 실행 검증 |
| `/diagram` | Tufte SVG 생성 |
| `/research` | 최신 자료 조사 |
| `/render` | Quarto 렌더링 |
| `/publish` | 빌드+커밋+배포 |
| `/update-progress` | 진행 기록 갱신 |
