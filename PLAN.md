# PLAN.md - 집필 계획

> 최종 업데이트: 2026-02-19

## 집필 목표

"AI Agent 코딩" 책을 **실용적이고 깊이 있는 AI 시대 프로그래밍 안내서**로 완성한다.
독자가 AI Agent와 함께 코딩하는 워크플로우를 이해하고, 적절한 개발 환경을 구축할 수 있도록 한다.

---

## Phase 1: 핵심 콘텐츠 보강 (최우선)

약한 챕터를 보강하여 1부의 전체적인 완성도를 끌어올린다.

### 1-1. 컨텍스트 엔지니어링 심화 (`73-context-engineering.qmd`)

**현재**: 115줄, Vibe Coding 소개 수준
**목표**: 400줄 이상, 컨텍스트 엔지니어링의 핵심 가이드

- [ ] Prompt Engineering → Context Engineering 진화 과정 상세화
- [ ] CLAUDE.md, .cursorrules, Copilot Instructions 등 컨텍스트 파일 비교
- [ ] 효과적인 컨텍스트 설계 패턴 (시스템 프롬프트, 규칙 파일, 메모리)
- [ ] Vibe Coding vs. Context Engineering 실전 비교
- [ ] 관련 Tufte SVG 다이어그램 추가

### 1-2. 패러다임 전환 확장 (`72-paradigm-shift.qmd`)

**현재**: 143줄, 기본 프레임워크
**목표**: 350줄 이상, 구체적 사례 포함

- [ ] 재사용(Copy-Paste → Library → Framework) 역사 구체화
- [ ] 재생성(LLM 기반 코드 생성) 패러다임 실전 사례
- [ ] 전통 소프트웨어 vs. AI 생성 소프트웨어 비교
- [ ] "코드는 소모품" 개념 심화

### 1-3. 코드 리뷰와 품질 관리 (`75-code-review.qmd`)

**현재**: 139줄, 보안 감사 기본
**목표**: 400줄 이상, AI 코드 품질 관리 체계

- [ ] AI 생성 코드의 특성과 위험 요소
- [ ] 코드 리뷰 체크리스트 (보안, 성능, 가독성)
- [ ] AI 코드 리뷰 도구 (CodeRabbit, PR-Agent 등)
- [ ] 실전 코드 리뷰 사례 (Before/After)
- [ ] 테스트 전략: AI 코드에 대한 신뢰 구축

### 1-4. 개발자의 미래 (`77-developer-future.qmd`)

**현재**: 165줄, 역할 변화 기본 틀
**목표**: 350줄 이상, 미래 개발자 역량 로드맵

- [ ] Coder → Orchestrator + Verifier 역할 전환 구체화
- [ ] AI 시대 필수 역량 (컨텍스트 설계, 검증, 시스템 사고)
- [ ] 직업 전망과 새로운 역할 (AI Whisperer, Prompt Engineer 등)
- [ ] 학습 로드맵과 준비 전략

---

## Phase 2: 2부 확장 및 신규 챕터

### 2-1. Cursor IDE 챕터 정식 등록

**현재**: `ide_cursor.qmd` 파일 존재하나 `_quarto.yml` 목차 미등록

- [ ] `_quarto.yml`에 `ide_cursor.qmd` 추가
- [ ] 콘텐츠 검토 및 보강
- [ ] Cursor의 AI 기능 심화 (Composer, Chat, Tab 자동완성)

### 2-2. Claude Code 챕터 신규 작성

**목표**: AI Agent 코딩의 핵심 도구인 Claude Code 전용 챕터

- [ ] `ide_claude_code.qmd` 신규 생성
- [ ] Claude Code CLI 기본 사용법
- [ ] CLAUDE.md 작성 가이드
- [ ] Agent 모드 워크플로우 (계획 → 실행 → 검증)
- [ ] MCP(Model Context Protocol) 서버 활용
- [ ] 실전 프로젝트 사례
- [ ] Tufte SVG 다이어그램 제작
- [ ] `_quarto.yml`에 등록

### 2-3. IDE 개요 및 Positron 보강

- [ ] `ide.qmd` 보강: IDE 선택 기준 매트릭스, AI IDE 비교표
- [ ] `ide_positron.qmd` 보강: 실전 사용법, R/Python 전환 워크플로우

### 2-4. Docker 챕터 보강 (`docker_concept.qmd`)

- [ ] Dockerfile 작성 실전 예제 추가
- [ ] Docker Compose 기본 활용
- [ ] AI 개발 환경용 Docker 이미지 구성

---

## Phase 3: 품질 향상 및 마무리

### 3-1. 참고문헌 정리

- [ ] `assets/references.bib`에 인용 문헌 체계적 등록
- [ ] 각 챕터별 핵심 참고문헌 확인
- [ ] CSL 스타일(IEEE) 적용 확인

### 3-2. 용어집 확장

- [ ] AI Agent 관련 신규 용어 추가 (MCP, Context Window, Token 등)
- [ ] 2부 개발 환경 관련 용어 보강

### 3-3. 교차 참조 및 일관성 검토

- [ ] 챕터 간 상호 참조(cross-reference) 확인
- [ ] 용어 사용 일관성 점검
- [ ] 문체 점검 (평서문, AI 티 제거)

### 3-4. 렌더링 및 배포

- [ ] 전체 `quarto render` 오류 없이 성공
- [ ] 이미지 누락/깨짐 점검
- [ ] 검색 인덱스(`search.json`) 정상 생성 확인
- [ ] GitHub Pages 배포 확인

---

## Phase 4: PDF 출판 준비 (장기)

- [ ] LaTeX 환경 설정 (`_quarto.yml`에 pdf format 추가)
- [ ] SVG → PDF 변환 테스트
- [ ] 한글 폰트 설정 (NanumSquare, Noto Sans KR 등)
- [ ] 페이지 레이아웃 및 여백 조정
- [ ] 표지 디자인 PDF 버전 제작
- [ ] 인쇄 테스트 (grayscale 출력 품질 확인)

---

## 우선순위 매트릭스

| 우선순위 | 작업 | 예상 영향 |
|----------|------|-----------|
| 🔴 높음 | Phase 1: 1부 약한 챕터 보강 (72, 73, 75, 77) | 책 전체 완성도 급상승 |
| 🔴 높음 | Phase 2-2: Claude Code 챕터 신규 작성 | 핵심 도구 누락 해소 |
| 🟡 중간 | Phase 2-1: Cursor 챕터 정식 등록 | 목차 완결성 |
| 🟡 중간 | Phase 2-3: IDE 개요/Positron 보강 | 2부 균형 |
| 🟢 낮음 | Phase 3: 참고문헌, 용어집, 일관성 | 품질 마감 |
| 🟢 낮음 | Phase 4: PDF 출판 | 장기 목표 |

---

## 작업 규칙

1. **PROGRESS.md 업데이트**: 작업 완료 시마다 진행률과 작업 로그 갱신
2. **한 번에 한 챕터**: 여러 챕터를 동시에 건드리지 말고, 하나씩 완성
3. **렌더링 확인**: 챕터 수정 후 반드시 `quarto render` 테스트
4. **이미지 규칙**: 새 다이어그램은 반드시 Tufte style grayscale SVG
5. **문체 준수**: 평서문, "이 + 명사" 패턴 금지, AI 티 제거
6. **Git 커밋**: 의미 있는 단위로 커밋, 명확한 메시지
