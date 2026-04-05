# /new-chapter - 신규 챕터 생성

인자: $ARGUMENTS

첫 번째 인자는 파일명(확장자 제외), 나머지는 챕터 제목이다.
예: `/new-chapter ide_claude_code Claude Code: AI Agent 코딩의 핵심 도구`
→ 파일: `ide_claude_code.qmd`, 제목: "Claude Code: AI Agent 코딩의 핵심 도구"

## 작업 절차

### 1단계: 위치 결정
- 사용자에게 어느 부(Part)에 배치할지 확인한다.
  - 1부: AI 시대 프로그래밍
  - 2부: 통합 개발 환경
- 해당 부 내 순서(어떤 챕터 다음에 배치)를 확인한다.

### 2단계: .qmd 파일 생성

아래 템플릿을 기반으로 `chapters/` 폴더에 `.qmd` 파일을 생성한다:

```markdown
---
title: "[챕터 제목]"
description: "[한 줄 설명]"
date: last-modified
format:
  html:
    code-overflow: wrap
execute:
  eval: false
  echo: true
---

# [챕터 제목] {#sec-[섹션ID]}

::: {.callout-note}
## 학습 목표

-
-
-
:::

## [첫 번째 섹션]

(내용)

## [두 번째 섹션]

(내용)

## 요약

(챕터 요약)
```

### 3단계: _quarto.yml 등록
- `_quarto.yml`의 `chapters:` 섹션에 `chapters/파일명.qmd` 경로로 올바른 위치에 추가한다.

### 4단계: PROGRESS.md 업데이트
- 해당 부의 챕터 목록에 새 항목 추가 (초기 상태: ★☆☆☆☆)
- 마일스톤에 기록

### 5단계: PLAN.md 업데이트
- 관련 TODO 항목이 있으면 체크 처리
- 새 챕터에 대한 콘텐츠 계획 TODO 추가

## 문체 규칙
- 평서문으로 작성 (index.qmd 제외)
- "이 + 명사" 패턴 금지
- AI 티 나는 표현 금지

## 주의사항
- 파일명은 영문 소문자 + 언더스코어 사용 (한글 불가)
- 같은 파일명이 이미 존재하면 경고 후 중단
- 생성 후 `quarto render`로 빌드 오류가 없는지 확인한다.
