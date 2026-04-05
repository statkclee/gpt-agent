# 프로젝트 구조 재편: chapters/ 폴더 도입

- **날짜**: 2026-04-05
- **작업자**: Claude Code
- **상태**: 계획 수립 → 실행 예정

## 배경

프로젝트 루트에 `.qmd` 파일 18개가 흩어져 있어 설정 파일, 문서, 데이터 파일과 뒤섞인다. 집필에 집중할 수 있도록 콘텐츠 파일을 `chapters/` 폴더로 분리한다.

## 현재 루트 구조 (정리 전)

```
gpt-agent/
├── p1-intro.qmd                  ← 콘텐츠 (이동 대상)
├── p1-paradigm.qmd       ← 콘텐츠
├── p1-context.qmd  ← 콘텐츠
├── p1-workflow.qmd             ← 콘텐츠
├── p1-review.qmd          ← 콘텐츠
├── p1-tools.qmd             ← 콘텐츠
├── p1-future.qmd     ← 콘텐츠
├── p2-intro.qmd                     ← 콘텐츠
├── p2-positron.qmd            ← 콘텐츠
├── p2-zed.qmd                 ← 콘텐츠
├── p2-extension.qmd           ← 콘텐츠
├── p2-setup.qmd               ← 콘텐츠
├── p2-docker.qmd          ← 콘텐츠
├── p2-compendium.qmd              ← 콘텐츠
├── glossary.qmd                ← 콘텐츠
├── references.qmd              ← 콘텐츠
├── index.qmd                   ← 콘텐츠
├── CLAUDE.md                   ← 프로젝트 설정 (루트 유지)
├── GEMINI.md                   ← 프로젝트 설정
├── PLAN.md                     ← 프로젝트 관리
├── PROGRESS.md                 ← 프로젝트 관리
├── README.md                   ← 프로젝트 문서
├── _quarto.yml                 ← Quarto 설정
├── _common.R                   ← Quarto 설정
├── _extensions/                ← Quarto 확장
├── glossary.yml                ← 데이터
├── gpt-coding.Rproj            ← R 프로젝트
├── requirements.txt            ← 의존성
├── # terminology.md 삭제됨 (2026-04-05, glossary.yml로 통합)
├── assets/                     ← 스타일/참고문헌
├── images/                     ← 이미지 자산
├── docs/                       ← 빌드 출력
└── tech_document/              ← 기술 문서
```

## 목표 루트 구조 (정리 후)

```
gpt-agent/
├── _quarto.yml                 ← Quarto 설정 (수정 필요)
├── _common.R                   ← Quarto 설정
├── _extensions/                ← Quarto 확장
├── gpt-coding.Rproj            ← R 프로젝트
├── requirements.txt            ← 의존성
├── glossary.yml                ← 데이터
├── # terminology.md 삭제됨 (2026-04-05, glossary.yml로 통합)
│
├── CLAUDE.md                   ← AI 지침
├── GEMINI.md                   ← AI 지침
├── PLAN.md                     ← 프로젝트 관리
├── PROGRESS.md                 ← 프로젝트 관리
├── README.md                   ← 프로젝트 문서
│
├── index.qmd                   ← 서문 (Quarto book 홈페이지, 루트 필수)
│
├── chapters/                   ← 📂 본문 챕터 (신규)
│   ├── p1-intro.qmd
│   ├── p1-paradigm.qmd
│   ├── p1-context.qmd
│   ├── p1-workflow.qmd
│   ├── p1-review.qmd
│   ├── p1-tools.qmd
│   ├── p1-future.qmd
│   ├── p2-intro.qmd
│   ├── p2-positron.qmd
│   ├── p2-zed.qmd
│   ├── p2-extension.qmd
│   ├── p2-setup.qmd
│   ├── p2-docker.qmd
│   ├── p2-compendium.qmd
│   ├── glossary.qmd
│   └── references.qmd
│
├── images/                     ← 이미지 자산 (위치 유지)
├── assets/                     ← 스타일/참고문헌 (위치 유지)
├── docs/                       ← 빌드 출력
├── tech_document/              ← 기술 문서
└── .claude/                    ← Claude 스킬
```

## 수정이 필요한 파일 목록

### 1. `_quarto.yml` — 챕터 경로 변경

모든 `.qmd` 참조에 `chapters/` 접두사 추가:

```yaml
# 변경 전
chapters:
  - index.qmd

# 변경 후
chapters:
  - chapters/index.qmd
```

`render:` 섹션도 변경:

```yaml
# 변경 전
render:
  - "*.qmd"

# 변경 후
render:
  - "chapters/*.qmd"
```

### 2. `.qmd` 파일 내 이미지 경로 — 상대 경로 변경

`.qmd` 파일이 `chapters/`로 이동하면 `images/` 폴더와의 상대 경로가 바뀐다.

```markdown
# 변경 전 (루트에서)
![캡션](images/파일.svg)

# 변경 후 (chapters/에서)
![캡션](../images/파일.svg)
```

**영향 범위**: 13개 파일, 51건의 이미지 참조

### 3. `CLAUDE.md` — 프로젝트 구조 설명 갱신

디렉토리 구조 섹션, 작업 가이드 경로 등을 새 구조에 맞게 업데이트.

### 4. `PLAN.md`, `PROGRESS.md` — 파일 경로 참조 갱신

챕터 파일 경로가 언급된 부분 업데이트.

## 실행 계획

### Step 1: chapters/ 폴더 생성 및 파일 이동

```bash
mkdir chapters/
mv index.qmd chapters/
mv p1-intro.qmd p1-paradigm.qmd ... chapters/
mv p2-intro.qmd p2-positron.qmd ... chapters/
mv glossary.qmd references.qmd chapters/
```

17개 `.qmd` 파일 이동.

### Step 2: _quarto.yml 수정

- `render:` 경로 변경
- `chapters:` 블록 내 모든 파일 경로에 `chapters/` 접두사 추가

### Step 3: 이미지 경로 일괄 변경

13개 `.qmd` 파일에서 `images/` → `../images/` 변경 (51건)

### Step 4: CLAUDE.md 업데이트

프로젝트 구조, 작업 가이드의 경로 설명 갱신.

### Step 5: 렌더링 검증

```bash
quarto render
```

오류 없이 빌드되는지 확인.

## 위험 요소 및 대응

| 위험 | 대응 |
|------|------|
| 이미지 경로 누락 | Grep으로 `images/` 패턴 전수 검사, `../images/` 변환 확인 |
| _quarto.yml 오타 | 렌더링 전 YAML 문법 검증 |
| 교차 참조(@sec-) 깨짐 | Quarto book 프로젝트에서 교차 참조는 파일 위치 무관 (ID 기반) → 영향 없음 |
| glossary.yml 경로 | _quarto.yml에서 상대 경로로 참조 중 → `glossary.yml`은 루트 유지이므로 영향 없음 |
| _common.R 참조 | qmd에서 source() 호출 없음 확인됨 → 영향 없음 |
| Git 이력 | git mv 사용으로 이력 보존 |

## 롤백 절차

문제 발생 시:

```bash
git mv chapters/*.qmd .
rmdir chapters
git checkout HEAD -- _quarto.yml
```
