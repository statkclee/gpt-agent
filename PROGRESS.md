# PROGRESS.md - 집필 진행 현황

> 최종 업데이트: 2026-02-19

## 프로젝트 개요

- **책 제목**: AI Agent 코딩
- **부제**: LLM과 IDE로 시작하는 차세대 프로그래밍
- **구성**: 1부(AI 시대 프로그래밍) + 2부(통합 개발 환경) + 부록
- **출판 형식**: HTML (GitHub Pages), PDF (준비 중)

---

## 전체 진행률 요약

| 구분 | 챕터 수 | 완성도 | 비고 |
|------|---------|--------|------|
| 1부 AI 시대 프로그래밍 | 7개 | ~60% | 74-workflow가 핵심, 나머지 보강 필요 |
| 2부 통합 개발 환경 | 7개 | ~65% | Zed, Setup, Compendium 충실 |
| 부록 | 2개 | ~70% | 용어집 충실, 참고문헌 미비 |

---

## 챕터별 상세 현황

### 1부: AI 시대 프로그래밍

| 챕터 | 파일 | 분량(줄) | 완성도 | 상태 |
|------|------|----------|--------|------|
| AI 시대 프로그래밍의 도래 | `71-gpt.qmd` | 338 | ★★★☆☆ | CLI→GUI→MUI→LUI 진화, Software 1.0/2.0/3.0 개념 정립 |
| 재사용에서 재생성으로 | `72-paradigm-shift.qmd` | 143 | ★★☆☆☆ | 기본 프레임워크만 존재, 사례/예제 보강 필요 |
| 프롬프트에서 컨텍스트로 | `73-context-engineering.qmd` | 115 | ★★☆☆☆ | Vibe Coding 소개 수준, 컨텍스트 엔지니어링 심화 필요 |
| AI 코딩 실전 워크플로우 | `74-workflow.qmd` | 1,181 | ★★★★★ | **가장 완성도 높음** - 6단계 워크플로우, LLM API, TDD, RAG |
| 코드 리뷰와 품질 관리 | `75-code-review.qmd` | 139 | ★★☆☆☆ | 보안 감사 기본 내용, 실전 리뷰 프로세스 보강 필요 |
| AI 도구 생태계 | `76-ai-tools.qmd` | 366 | ★★★☆☆ | Copilot, ChatGPT, Claude, Cursor 개요 |
| 개발자의 미래 | `77-developer-future.qmd` | 165 | ★★☆☆☆ | Coder→Orchestrator+Verifier 역할 변화 기본 틀 |

### 2부: 통합 개발 환경

| 챕터 | 파일 | 분량(줄) | 완성도 | 상태 |
|------|------|----------|--------|------|
| IDE 선택의 여정 | `ide.qmd` | 104 | ★★☆☆☆ | 60년 IDE 역사 개괄, 상세 내용 보강 필요 |
| Positron IDE | `ide_positron.qmd` | 147 | ★★☆☆☆ | R/Python 차세대 IDE 소개 수준 |
| Zed 에디터 | `ide_zed.qmd` | 773 | ★★★★☆ | GPU 가속, AI 통합, 설정 등 상세 |
| IDE 확장 프로그램 | `ide_extension.qmd` | 216 | ★★★☆☆ | Extension Host, LSP 아키텍처 |
| 개발 환경 구축 | `ide_setup.qmd` | 424 | ★★★★☆ | Git/R/Python 설치 가이드 충실 |
| Docker 컨테이너 | `docker_concept.qmd` | 280 | ★★★☆☆ | VM→Container 역사, 아키텍처 기본 |
| Research Compendium | `compendium.qmd` | 727 | ★★★★☆ | 재현성 4개념, 폴더 구조, 환경 명세 |

### 부록

| 챕터 | 파일 | 분량(줄) | 완성도 | 상태 |
|------|------|----------|--------|------|
| 용어집 | `glossary.qmd` | 159 | ★★★★☆ | AI 관련 용어 충실 |
| 참고문헌 | `references.qmd` | 4 | ★☆☆☆☆ | 컨테이너만 존재, bib 파일 연결 |

---

## 이미지 자산 현황

- **총 58개** (SVG 55개 + JPG 2개 + PNG 1개)
- 모든 SVG는 Tufte style grayscale 준수
- 1부 관련: ~20개, 2부 관련: ~35개, 공통: 3개

---

## 주요 마일스톤

### 완료

- [x] 프로젝트 구조 정리 (1-7부 제거, 8-9부만 유지) - 2026-01-18
- [x] _quarto.yml 1부/2부 체계로 재편 - 2026-01-18
- [x] GitHub Pages 배포 설정 - 2026-01-18
- [x] 74-workflow.qmd 완성 (6단계 워크플로우 + TDD + RAG) - 2026-01-18
- [x] Zed 에디터 챕터 추가 (`ide_zed.qmd`) - 2026-01-26
- [x] Cursor IDE 챕터 추가 (`ide_cursor.qmd`) - 2026-01-26
- [x] 전체 HTML 렌더링 성공 확인 - 2026-01-26

### 미완료

- [ ] `ide_cursor.qmd`를 `_quarto.yml`에 등록 (현재 렌더링되나 목차 미포함)
- [ ] 1부 약한 챕터 보강 (72, 73, 75, 77)
- [ ] 2부 약한 챕터 보강 (ide.qmd, ide_positron.qmd)
- [ ] 참고문헌(references.bib) 정리
- [ ] PDF 출판 테스트

---

## 최근 작업 로그

| 날짜 | 작업 내용 |
|------|-----------|
| 2026-01-26 | Zed 에디터 챕터 추가, Cursor IDE 챕터 추가, 이미지 최적화 |
| 2026-01-18 | 프로젝트 대대적 구조 정리, 1-7부 제거, AI Agent Coding 집중 |
| 2026-01-18 | GitHub Pages 및 저장소 URL 업데이트 |
| 2026-01-18 | 책 제목 및 page-footer 개선 |
| 2026-01-18 | Initial commit: AI Agent 코딩 프로젝트 |
