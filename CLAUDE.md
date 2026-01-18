# CLAUDE.md - AI Agent Coding 프로젝트

## 프로젝트 개요

이 프로젝트는 **"챗GPT 코딩: 인공지능(LLM)과 동료(Git/GitHub)와 함께 하는 프로그래밍"** 중 **AI Agent Coding**에 집중한 특화 버전입니다. [Quarto](https://quarto.org/) 출판 시스템을 사용하여 제작됩니다.

### 프로젝트 재구성 (2026-01-18)

AI 시대 프로그래밍의 핵심인 **Agent Coding**에 집중하기 위해 프로젝트 구조를 대대적으로 정리했습니다.

**남긴 내용:**
- **8부: AI 시대 프로그래밍** - AI 코딩의 패러다임, 워크플로우, 도구 생태계
- **9부: 통합 개발 환경** - IDE, Docker, Compendium 등 개발 환경 구축

**제거한 내용:**
- 1-7부 전통 프로그래밍, 자료구조, Git, 도구, 패러다임, 아키텍처, ML 관련 내용
- 관련 이미지, 코드, 데이터 파일

### 출판 전략: HTML 우선, PDF 대비

**HTML 우선 출판**
- 웹 출판 (`docs/` 디렉토리)을 우선으로 개발
- 인터랙티브 기능 활용 가능
- GitHub Pages를 통한 즉각적인 배포

**PDF 출판 대비 전략**
- 모든 시각 자료를 **grayscale Tufte style SVG**로 제작
- 중복 작업 방지: HTML/PDF 양쪽에서 동일한 이미지 사용
- LaTeX 컴파일 호환성 확보
- 인쇄 시 토너 절약 및 최적 가독성

### 핵심 디자인 원칙: Tufte Style

Edward Tufte의 정보 디자인 원칙을 따라 모든 다이어그램 제작:

1. **Grayscale Only** - 흑백 계열만 사용 (#333, #666, #999)
2. **High Data-Ink Ratio** - 불필요한 장식 최소화, 정보 전달에 집중
3. **Serif Typography** - Palatino, Georgia 계열 가독성 높은 서체
4. **Clear Visual Hierarchy** - 명확한 계층 구조와 여백 활용
5. **Minimal Decoration** - 단순하고 깔끔한 선과 도형

**이점:**
- HTML 렌더링: 깔끔하고 전문적인 느낌
- PDF 변환: 별도 수정 없이 고품질 출력
- 인쇄: 흑백 인쇄 시 품질 저하 없음
- 일관성: 전체 책의 시각적 통일성 확보

## 기술 스택

### 콘텐츠 제작
- **포맷**: Quarto Markdown (`.qmd`)
- **언어**: R, Python (dual-language approach)
- **출판**: HTML (현재), PDF (준비 중)

### 개발 환경
- **버전 관리**: Git/GitHub
- **렌더링**: Quarto 1.4+
- **의존성**:
  - R 패키지: `renv.lock` (renv 관리)
  - Python 패키지: `requirements.txt`

### Quarto Extensions

```yaml
filters:
  - fontawesome        # 아이콘
  - include-code-files # 외부 코드 포함
  - fancy-text         # 커스텀 숏코드
```

## 책 구조

### 8부: AI 시대 프로그래밍

AI Agent Coding의 핵심 개념과 실전 워크플로우:

- `71-gpt.qmd` - AI 시대 프로그래밍의 도래
- `72-paradigm-shift.qmd` - 재사용에서 재생성으로
- `73-context-engineering.qmd` - 프롬프트에서 컨텍스트로
- `74-workflow.qmd` - AI 코딩 실전 워크플로우
- `75-code-review.qmd` - 코드 리뷰와 품질 관리
- `76-ai-tools.qmd` - AI 도구 생태계
- `77-developer-future.qmd` - 개발자의 미래

**주요 다이어그램 (Tufte style SVG):**
- `gpt-*.svg` - GPT 개념도, 소프트웨어 진화, UI 발전
- `ai-*.svg` - AI 네이티브 스택, TDD 워크플로우
- `llm-*.svg` - LLM API 비교, 배포 시나리오
- `workflow-*.svg` - 도구 비교, 타임라인
- `function-calling.svg` - Function Calling 개념
- `rag-architecture.svg` - RAG 아키텍처

### 9부: 통합 개발 환경

AI 시대 개발 환경 구축의 모든 것:

- `ide.qmd` - IDE 선택의 여정: 역사부터 미래까지
- `ide_positron.qmd` - Positron: R과 Python을 위한 차세대 IDE
- `ide_extension.qmd` - IDE 확장 프로그램: 필요성과 아키텍처
- `ide_setup.qmd` - 개발 환경 구축
- `docker_concept.qmd` - Docker 컨테이너 기반 개발
- `compendium.qmd` - Research Compendium

**주요 다이어그램 (Tufte style SVG):**
- `ide-*.svg` - IDE 아키텍처, 커널, Extension Host, LSP
- `positron-*.svg` - Positron UI, 확장, 워크플로우
- `docker-*.svg` - Docker 아키텍처, 이미지/컨테이너, 볼륨
- `compendium-*.svg` - Compendium 구조, 파일 조직

### 부록

- `glossary.qmd` - 용어집
- `references.qmd` - 참고문헌

## 이미지 자산

현재 `images/` 폴더에는 **54개의 SVG/JPG 파일**이 있으며, 모두 8부와 9부 관련:

**8부 관련 (AI 시대 프로그래밍):**
- gpt-*.svg/jpg (15개)
- ai-*.svg (2개)
- llm-*.svg (2개)
- workflow-*.svg (2개)
- function-calling.svg, rag-architecture.svg 등

**9부 관련 (통합 개발 환경):**
- ide-*.svg (11개)
- positron-*.svg (4개)
- docker-*.svg (9개)
- compendium-*.svg (4개)
- ollama-architecture.svg, reproducibility-concepts.svg 등

**공통:**
- book_cover.jpg

## 빌드 및 개발

### 로컬 미리보기

```bash
quarto preview
```

포트 7771에서 브라우저 미리보기 제공 (`_quarto.yml` 설정)

### 전체 렌더링

```bash
quarto render
```

출력: `docs/` 디렉토리 (GitHub Pages 배포용)

### 의존성 복원

**R 패키지:**
```R
renv::restore()
```

**Python 패키지:**
```bash
pip install -r requirements.txt
```

## 프로젝트 디렉토리 구조

```
gpt-agent/
├── _quarto.yml           # Quarto 설정 (8부, 9부만 활성화)
├── index.qmd             # 서문 및 시작 페이지
├── 71-gpt.qmd            # 8부 시작
├── 72-paradigm-shift.qmd
├── 73-context-engineering.qmd
├── 74-workflow.qmd
├── 75-code-review.qmd
├── 76-ai-tools.qmd
├── 77-developer-future.qmd # 8부 마지막
├── ide.qmd               # 9부 시작
├── ide_positron.qmd
├── ide_extension.qmd
├── ide_setup.qmd
├── docker_concept.qmd
├── compendium.qmd        # 9부 마지막
├── glossary.qmd          # 부록
├── references.qmd        # 참고문헌
├── images/               # SVG 다이어그램 (54개, Tufte style)
├── docs/                 # HTML 출력 (GitHub Pages)
└── _extensions/          # Quarto 확장 프로그램
```

## 작업 가이드

### 이미지 생성 규칙

**모든 다이어그램은 반드시 Tufte style grayscale SVG로 제작:**

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 WIDTH HEIGHT">
  <defs>
    <style>
      .tufte-text {
        font-family: Palatino, 'Book Antiqua', Georgia, serif;
        fill: #333;
      }
      /* Grayscale only: #333, #666, #999, #ccc, #f5f5f5 */
    </style>
  </defs>

  <!-- White background -->
  <rect x="0" y="0" width="WIDTH" height="HEIGHT" fill="#ffffff"/>

  <!-- Content here -->
</svg>
```

**이유:**
- HTML과 PDF 양쪽에서 일관된 품질
- 색상 이미지 재작업 불필요
- LaTeX SVG 처리 오류 방지
- 인쇄 비용 절감

### 챕터 추가/수정 시

1. `.qmd` 파일 작성/수정
2. 이미지 필요 시 `images/` 폴더에 Tufte style SVG 생성
3. `quarto preview`로 렌더링 확인
4. Git 커밋 전 빌드 오류 확인

### Git 워크플로우

```bash
# 변경사항 확인
git status

# 렌더링 테스트
quarto render

# 커밋
git add .
git commit -m "작업 내용"
git push
```

## 문체 가이드

### 평서문 원칙

**기본 원칙**: 서문(index.qmd) 제외한 모든 qmd 파일은 평서문으로 작성

**평서문 스타일**:
- "~합니다" → "~한다" / "~함"
- "~입니다" → "~이다" / "~임"
- "~할 수 있습니다" → "~할 수 있다"

**예외 (존칭 유지)**:
- `index.qmd`: 서문 - 독자에게 존칭 사용

### AI 티 제거 필수

**⚠️ 최우선 규칙: "이 + 명사" 패턴 금지**

AI 생성 문장의 가장 전형적인 특징은 "이 메서드는", "이 문제를", "이처럼", "이러한" 등 지시 대명사 "이"로 시작하는 표현이다. **반드시 구체적인 명사로 대체**해야 한다.

| ❌ AI 특유 표현 | ✅ 자연스러운 표현 |
|----------------|-------------------|
| 이 메서드는 빈 문자열에서도... | `startswith()`는 빈 문자열에서도... |
| 이 문제를 방지한다 | 인덱스 오류를 방지한다 |
| 이러한 특성 덕분에 | 시퀀스라는 특성 덕분에 |
| 이처럼 조합하면 | `find()`와 슬라이싱을 조합하면 |

**제거할 AI 특성 표현**:

1. **"이 + 명사" 지시 대명사** (최우선)
2. **과도한 지시 대명사**: "이러한 방식은" → "해당 방식은"
3. **불필요한 관형사형**: "~하는 것입니다" → "~한다"
4. **기계적 연결어**: "다음으로,", "또한,", "마지막으로,"
5. **과도한 격식**: "본 연구에서는..." → "~를 살펴본다"

## 최근 작업 이력 (2026-01-18)

### 프로젝트 구조 대대적 정리

**목표**: AI Agent Coding에 집중

**삭제한 내용:**
- 1-7부 전체 qmd 파일 (40개 이상)
- 관련 이미지 280개 이상
- code/ 폴더 전체 (예제 코드)
- data/ 폴더 전체 (샘플 데이터)
- archive/ 폴더

**남긴 내용:**
- 8부, 9부 qmd 파일 (14개)
- 관련 이미지 (54개)
- 서문, 참고문헌, 용어집

**결과:**
- qmd 파일: 60개 이상 → 16개
- 이미지: 340개 이상 → 54개
- 프로젝트 크기: 약 1/3로 축소
- 집중도: AI Agent Coding 100%

## 다음 단계

1. **8부 보강**: AI 코딩 워크플로우 실전 예제 추가
2. **9부 확장**: Claude Code, Cursor 등 최신 AI IDE 도구 추가
3. **실습 자료**: Agent Coding 실습 프로젝트 개발
4. **PDF 출판**: LaTeX 설정 최종 테스트

## 저장소 정보

- **GitHub**: https://github.com/bit2r/gpt-coding/
- **웹사이트**: https://r2bit.com/gpt-coding/
- **저자**: 이광춘
- **소속**: 공익법인 한국 R 사용자회

## AI 어시스턴트 작업 시 주의사항

Claude Code 또는 다른 AI 도구로 작업할 때:

1. **이미지 생성**: 반드시 Tufte style grayscale SVG로 제작
2. **렌더링 테스트 필수**: 커밋 전 `quarto render`로 오류 확인
3. **한글 처리**: 파일명, 경로에 한글 사용 시 주의 (인코딩 UTF-8)
4. **PDF 준비**: 이미지는 항상 grayscale SVG
5. **커밋 메시지**: 명확하고 구체적인 변경 내용 기록
6. **문체 준수**: 평서문, AI 티 제거 규칙 엄격히 준수
7. **집중**: AI Agent Coding (8부, 9부)에만 집중
