# 문서 생성 엔진 대안 평가 -- Quarto는 유일한 선택인가

> 조사일: 2026-04-05
> 목적: `p1-cc-writing.qmd` "콘텐츠에서 문서로" 섹션 보강 -- Quarto 외 대안 평가

---

## 1. 문서 생성 엔진 분류

"콘텐츠 + 서식 = 문서" 등식에서 변환(=)을 담당하는 엔진은 크게 4개 범주로 나뉜다.

### 1.1 범주별 분류

| 범주 | 도구 | 핵심 특성 |
|------|------|-----------|
| **다중 포맷 출판** | Quarto, R Markdown, Jupyter Book | 코드+텍스트 통합, 다중 출력 |
| **조판 엔진** | Typst, LaTeX, ConTeXt | PDF 품질 최적화, 학술/인쇄 |
| **범용 변환기** | Pandoc, WeasyPrint | 포맷 간 변환 특화 |
| **문서 사이트** | Docusaurus, MkDocs, Sphinx, Starlight | 웹 문서/API 문서 특화 |

### 1.2 도구별 상세 평가

#### Quarto (현재 선택)
- **강점**: 다중 언어(R, Python, Julia, Observable), 다중 출력(HTML/PDF/Revealjs/DOCX/ePub/Dashboard), Pandoc 기반, 교차 참조/색인/참고문헌 자동화, 매개변수화 렌더링, 활발한 생태계
- **약점**: 단순 문서에는 과잉, LaTeX 기반 PDF 조판 품질 한계(Typst로 보완 가능), 빌드 속도 대형 프로젝트에서 저하
- **AI 에이전트 적합성**: 최상 -- CLI 기반, 텍스트 파일(.qmd), YAML 설정, Bash 실행

#### Typst (차세대 조판)
- **강점**: LaTeX 대비 10-100배 빠른 컴파일, 깔끔한 문법, 완전 로컬 CLI, PDF 인쇄 품질
- **약점**: HTML 출력 미지원, 웹 문서 불가, 생태계 미성숙, 코드 실행 통합 없음
- **AI 에이전트 적합성**: 높음 -- CLI 기반, 텍스트 파일(.typ), 하지만 PDF 전용

#### LaTeX (전통 학술)
- **강점**: 40년 역사, 학술 출판 표준, 가장 넓은 템플릿 생태계, 인쇄 품질 최고
- **약점**: 문법 복잡, 컴파일 느림, HTML 변환 어려움, 학습 곡선 가파름
- **AI 에이전트 적합성**: 중간 -- AI가 LaTeX 코드 생성은 가능하나 디버깅이 어려움

#### Pandoc (범용 변환기)
- **강점**: 60+개 포맷 변환 지원, Lua 필터 확장, Quarto의 기반 엔진
- **약점**: 단독으로는 프로젝트 관리 기능 없음, 교차 참조/색인 약함
- **AI 에이전트 적합성**: 높음 -- CLI 기반, 하지만 프로젝트 수준 기능 부족
- **비고**: Pandoc 3.9에서 Typst 출력 기본 지원, WeasyPrint PDF 엔진도 지원

#### R Markdown (Quarto 전신)
- **강점**: 성숙한 생태계(bookdown, blogdown, distill), R 생태계 깊은 통합
- **약점**: R 중심 설계, Python/Julia 지원 제한적, Quarto에 기능적으로 흡수됨
- **AI 에이전트 적합성**: 높음 -- Quarto와 유사, 하지만 신규 프로젝트에 비추천

#### Jupyter Book (Python 중심)
- **강점**: Jupyter 노트북 기반, MyST Markdown, 인터랙티브 콘텐츠, Python 생태계
- **약점**: PDF 출력 품질 저하, 웹 우선 설계, 오프라인 접근성 제한
- **AI 에이전트 적합성**: 중간 -- 노트북 포맷(.ipynb)이 JSON이라 텍스트 편집 불편

#### Docusaurus / MkDocs / Sphinx / Starlight (문서 사이트)
- **강점**: API 문서, 기술 문서 사이트 특화, 버전 관리, 검색, 다국어
- **약점**: PDF/슬라이드 출력 미지원 또는 제한적, 코드 실행 통합 없음
- **AI 에이전트 적합성**: 높음(텍스트 기반) -- 하지만 다중 출력 불가

#### WeasyPrint (CSS-to-PDF)
- **강점**: HTML/CSS를 PDF로 변환, 웹 디자인 기술 활용, Python 라이브러리
- **약점**: 학술 조판 품질 미흡, 단독 문서 시스템이 아닌 변환기, 대형 문서 느림
- **AI 에이전트 적합성**: 중간 -- Pandoc의 PDF 엔진으로 사용 가능

---

## 2. 평가 매트릭스

### 2.1 5대 평가 기준

| 기준 | 설명 |
|------|------|
| **다중 출력** | 하나의 소스에서 HTML, PDF, 슬라이드, DOCX 등 다양한 포맷 생성 |
| **코드 통합** | R, Python 등 코드 실행 결과를 문서에 포함 |
| **AI 에이전트 적합성** | CLI 기반, 텍스트 파일, Bash 실행 가능 여부 |
| **생태계 성숙도** | 템플릿, 확장, 커뮤니티, 문서화 수준 |
| **학습 곡선** | 진입 장벽의 높이 |

### 2.2 도구별 점수 (5점 만점)

| 도구 | 다중 출력 | 코드 통합 | AI 적합성 | 생태계 | 학습 곡선 | 총점 |
|------|--------:|--------:|--------:|------:|--------:|-----:|
| **Quarto** | 5 | 5 | 5 | 4 | 3 | **22** |
| **Typst** | 1 | 1 | 4 | 2 | 4 | **12** |
| **LaTeX** | 2 | 2 | 3 | 5 | 1 | **13** |
| **Pandoc** | 4 | 1 | 4 | 3 | 3 | **15** |
| **R Markdown** | 4 | 4 | 5 | 4 | 3 | **20** |
| **Jupyter Book** | 2 | 5 | 3 | 3 | 3 | **16** |
| **Docusaurus** | 1 | 1 | 4 | 4 | 4 | **14** |
| **MkDocs** | 1 | 1 | 4 | 4 | 5 | **15** |

---

## 3. 결론 및 추천

### 3.1 Quarto가 최선인 이유

과학기술 저작에서 "콘텐츠 + 서식 = 문서" 등식을 가장 완전하게 만족하는 도구는 Quarto다.

1. **유일한 다중 출력**: HTML, PDF, 슬라이드, 대시보드, 책, 증명서, DOCX를 모두 지원하는 도구는 Quarto뿐
2. **다중 언어**: R, Python, Julia, Observable을 하나의 문서에서 혼용
3. **AI 에이전트 최적**: CLI 기반, .qmd(텍스트), YAML(설정), Bash(실행) -- Claude Code가 제어하기 가장 쉬운 구조
4. **Pandoc + Typst 통합**: Pandoc의 60+ 포맷 변환 + Typst의 빠른 PDF 컴파일을 모두 흡수

### 3.2 보완 조합

Quarto 단독으로 부족한 영역은 보완 도구와 조합한다:

| 필요 | 보완 도구 | 조합 방식 |
|------|-----------|-----------|
| 인쇄 품질 PDF | Typst | `format: typst` -- Quarto가 Typst를 PDF 엔진으로 사용 |
| API 문서 사이트 | MkDocs/Sphinx | 별도 프로젝트, CI/CD 연동 |
| 인터랙티브 노트북 | Jupyter | Quarto가 .ipynb 직접 렌더링 |
| 학술 저널 투고 | LaTeX | `format: pdf` + journal 템플릿 |

### 3.3 핵심 메시지

> Quarto는 "유일한 선택"이 아니라 "가장 넓은 선택"이다.
> 다른 도구들은 특정 영역에서 Quarto보다 뛰어나지만, "하나의 소스로 모든 문서를"이라는 OSMU 원칙을 충족하는 도구는 Quarto뿐이다.
> Claude Code + Quarto 조합이 AI 시대 과학기술 저작의 최적 해인 이유는 둘 다 CLI 기반 텍스트 도구이기 때문이다.

---

## 4. 출처

- [Quarto vs R Markdown](https://www.jumpingrivers.com/blog/quarto-rmarkdown-comparison/)
- [Are there any AlTEXnatives?](https://pierrebeaucoral.github.io/post/altexnatives/)
- [15 Best Documentation Tools (2025)](https://dev.to/therealmrmumba/i-tried-15-of-the-best-documentation-tools-heres-what-actually-works-in-2025-dam)
- [Static Site Generators for Documentation](https://justwriteclick.com/2025/02/06/a-flight-of-static-site-generators-sampling-the-best-for-documentation/)
- [Awesome Scientific Writing](https://github.com/writing-resources/awesome-scientific-writing)
- [Top 7 Reproducible Research Toolkits](https://www.giftwrapper.app/top-7-reproducible-research-toolkits-rstudio-quarto-adjacent-apps-that-grad-students-use-to-produce-publish-ready-reports-from-data-to-pdf-html/)
- [Building Content Pipelines: Markdown to PDF/ePub/HTML](https://dasroot.net/posts/2026/03/building-content-pipelines-markdown-pdf-epub-html/)
- [Pandoc User's Guide](https://pandoc.org/MANUAL.html)
- [Quarto: All Formats](https://quarto.org/docs/output-formats/all-formats.html)
