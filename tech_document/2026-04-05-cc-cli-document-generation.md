# Claude Code CLI 문서 생성 -- 콘텐츠 + 서식 = 문서

> 조사일: 2026-04-05
> 목적: `p1-cc-writing.qmd` 챕터 보강 -- 콘텐츠 생성만 다루던 것을 문서 생성(서식+출력)까지 확장

---

## 1. 핵심 통찰: 콘텐츠 != 문서

Claude Code CLI가 .qmd 파일에 텍스트를 쓰는 것은 **콘텐츠 생성**이다.
그 텍스트가 HTML, PDF, 슬라이드, 대시보드, 증명서로 변환되어야 **문서 생성**이다.

```
콘텐츠(텍스트 + 코드 + 데이터) + 서식(템플릿 + 스타일) = 문서
```

Claude Code는 이 등식의 양쪽을 모두 제어할 수 있다:
- **좌변(콘텐츠)**: .qmd 원고 작성, SVG 다이어그램, 코드 실행
- **우변(서식)**: _quarto.yml 설정, SCSS 테마, Typst 템플릿, YAML 프론트매터
- **등호(변환)**: `quarto render` 명령 실행

---

## 2. Claude Code로 생성 가능한 8대 문서 유형

### 2.1 단일 소스 다중 출력(OSMU) 구조

Quarto의 핵심 설계 원리는 하나의 .qmd 파일에서 여러 포맷을 동시 생성하는 것이다:

```yaml
format:
  html: default
  pdf: default
  docx: default
  revealjs: default
```

`quarto render --to all`로 모든 포맷을 한번에 생성한다.

### 2.2 8대 문서 유형별 생성 방법

| 유형 | Quarto 포맷 | 서식 엔진 | Claude Code 역할 |
|------|-------------|-----------|-----------------|
| **웹 문서** | `format: html` | SCSS 테마 | .qmd 작성 + SCSS 커스텀 + 렌더링 |
| **PDF 보고서** | `format: pdf` 또는 `typst` | LaTeX/Typst | .qmd 작성 + 템플릿 설정 + 렌더링 |
| **슬라이드** | `format: revealjs` | Revealjs | .qmd 작성 + 테마/전환 설정 + 렌더링 |
| **대시보드** | `format: dashboard` | Observable JS | .qmd 작성 + 레이아웃 + 차트 코드 |
| **책** | `project: book` | HTML/PDF/ePub | 챕터 구조 + _quarto.yml + 렌더링 |
| **웹사이트** | `project: website` | HTML + 네비게이션 | 페이지 구조 + 사이드바 + 렌더링 |
| **증명서** | `format: typst` + 커스텀 | Typst 템플릿 | 템플릿 디자인 + 데이터 바인딩 + 렌더링 |
| **MS Office** | `format: docx`/`pptx` | 참조 문서 | .qmd 작성 + 참조 docx 설정 + 렌더링 |

### 2.3 각 유형별 상세

#### 웹 문서 (HTML)
- 기본 출력, 가장 많이 사용
- Lightbox, 인터랙티브 차트, 코드 접기, 검색 기능 내장
- Claude Code가 SCSS 테마 파일도 편집 가능

#### PDF 보고서 (Typst/LaTeX)
- Typst: 2023년 등장한 차세대 조판 엔진, LaTeX보다 빠르고 간결
- Quarto + Typst = .qmd → .typ → PDF 파이프라인
- Claude Code가 Typst 템플릿(.typ)을 직접 작성/수정 가능
- 한글 폰트 설정: `mainfont: "Noto Sans KR"` 등 YAML에서 지정
- typst-claude-skill: Claude Code용 Typst 전문 스킬 (9개 템플릿 내장)

#### 슬라이드 (Revealjs)
- 웹 기반 프레젠테이션, 하나의 .qmd에서 HTML 슬라이드 생성
- `---`로 슬라이드 구분, `## 제목`으로 새 슬라이드
- 전환 효과, 스피커 노트, 자동 애니메이션 지원
- Claude Code가 슬라이드 내용 + 발표자 노트를 동시 작성

#### 대시보드 (Dashboard)
- Quarto 1.4+에서 기본 지원
- 행/열 레이아웃, 탭셋, 값 상자(value box)
- Observable JS 또는 Shiny로 인터랙티브 구현
- Claude Code가 데이터 분석 코드 + 레이아웃 YAML을 동시 생성

#### 책 (Book)
- 이 프로젝트가 사용 중인 포맷
- _quarto.yml에 챕터 구조 정의, 교차 참조, 색인, 참고문헌 자동화
- HTML + PDF + ePub 동시 출력 가능
- Claude Code가 챕터 단위로 집필 + 빌드 + 배포

#### 웹사이트 (Website)
- 블로그, 포트폴리오, 문서 사이트
- 네비게이션, 사이드바, 검색, 다국어 지원
- GitHub Pages, Netlify, Quarto Pub 배포
- Claude Code가 페이지 생성 + 네비게이션 설정 + 배포

#### 증명서/인증서 (Certificate)
- Typst 커스텀 템플릿으로 디자인
- 매개변수화(parameterized) 렌더링으로 대량 생산
- 수료자 이름, 날짜, 과정명을 파라미터로 주입
- Claude Code가 반복 렌더링 스크립트 작성 + 실행

#### MS Office (DOCX/PPTX)
- 참조 문서(reference-doc)로 브랜드 스타일 유지
- 조직 내 Word/PPT 양식에 맞춘 자동 변환
- Claude Code가 .qmd 작성 + 참조 문서 설정 + 렌더링

---

## 3. Claude Code의 문서 생성 워크플로우

### 3.1 콘텐츠 + 서식의 분리 원칙

```
저자 지시
   ↓
Claude Code (콘텐츠 생성)
   │  .qmd 파일 작성
   │  SVG/차트/코드 생성
   │  데이터 바인딩
   ↓
Claude Code (서식 설정)
   │  _quarto.yml 포맷 설정
   │  SCSS/Typst 템플릿 편집
   │  YAML 프론트매터 조정
   ↓
Claude Code (변환 실행)
   │  quarto render (HTML/PDF/slides/...)
   │  오류 진단 + 수정
   │  결과물 검증
   ↓
문서 (HTML, PDF, 슬라이드, 대시보드, ...)
```

### 3.2 매개변수화 렌더링(Parameterized Rendering)

하나의 .qmd 템플릿에서 데이터만 바꿔가며 N개 문서를 자동 생성:

- 월간 보고서: 월별 데이터 파라미터 → 12개 PDF 자동 생성
- 수료증: 수료자 명단 CSV → 100장 인증서 자동 생성
- 지역별 분석: 지역 코드 → 17개 시도별 보고서 자동 생성

Claude Code는 이 반복 렌더링 루프를 Bash/R/Python 스크립트로 작성하고 실행할 수 있다.

### 3.3 Claude Code 문서 생성 스킬 생태계

| 스킬/플러그인 | 역할 |
|--------------|------|
| typst-claude-skill | Typst 전문 문서 생성 (9개 템플릿) |
| claude-office-skills | Word, PPT, Excel, PDF 조작 |
| PDF Generator Skill | PDF 문서 자동화 |
| Quarto Authoring Migration | Beamer → Quarto 변환 |

---

## 4. 챕터 보강 제안

### 기존 p1-cc-writing.qmd에 추가할 섹션

**"콘텐츠에서 문서로 -- 서식과 변환"** 섹션 신규 추가:

1. 콘텐츠 + 서식 = 문서 등식
2. 단일 소스 다중 출력(OSMU) -- 하나의 .qmd에서 8가지 문서
3. 매개변수화 렌더링 -- 100장 증명서를 10분에
4. Claude Code 문서 생성 파이프라인 (콘텐츠→서식→변환→문서)

### SVG 다이어그램 제안

- `cc-writing-doc-equation.svg`: 콘텐츠 + 서식 = 문서 등식
- `cc-writing-osmu.svg`: 단일 소스 다중 출력 구조

---

## 5. 출처

- [Quarto: All Formats](https://quarto.org/docs/output-formats/all-formats.html)
- [Quarto: Including Other Formats](https://quarto.org/docs/output-formats/html-multi-format.html)
- [Quarto: Typst Basics](https://quarto.org/docs/output-formats/typst.html)
- [Quarto: Custom Typst Formats](https://quarto.org/docs/output-formats/typst-custom.html)
- [Quarto: Parameterized Reports](https://quarto.org/docs/blog/posts/2025-07-24-parameterized-reports-python/)
- [Quarto: Revealjs Presentations](https://quarto.org/docs/presentations/revealjs/)
- [R4DS: Quarto Formats](https://r4ds.hadley.nz/quarto-formats.html)
- [How to Make High-Quality PDFs with Quarto and Typst](https://rfortherestofus.com/2025/11/quarto-typst-pdf)
- [typst-claude-skill (GitHub)](https://github.com/ChanMeng666/typst-claude-skill)
- [claude-office-skills (GitHub)](https://github.com/tfriedel/claude-office-skills)
- [PDF Generator Skill (MCP Market)](https://mcpmarket.com/tools/skills/pdf-generator)
- [Awesome Claude Code Skills for Document Processing](https://apidog.com/blog/claude-skills-for-document-processing/)
