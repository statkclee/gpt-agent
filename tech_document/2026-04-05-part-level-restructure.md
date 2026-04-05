# Part 수준 재구성 제안서

> 작성일: 2026-04-05
> 목적: 도입부에 "AI 시대 글쓰기 환경" 추가, 전체 Part 재구성

---

## 현재 구조의 문제

```
도입: 글쓰기의 대전환
  └─ p0-writing.qmd        — 도구가 사고를 바꾸는 글쓰기 (역사, 개념)

1부: AI 시대 프로그래밍
  ├─ p1-intro.qmd           — 소프트웨어 3.0 시대 ★ 여기가 문제
  ├─ p1-paradigm.qmd        — 재사용에서 재생성으로
  ├─ p1-meta.qmd            — 메타프로그래밍
  ├─ p1-context.qmd         — 프롬프트에서 컨텍스트로
  ├─ p1-workflow.qmd        — AI 코딩 실전 워크플로우
  ├─ p1-review.qmd          — 코드 리뷰와 품질 관리
  ├─ p1-tools.qmd           — AI 도구 생태계
  └─ p1-future.qmd          — 개발자의 미래

2부: 통합 개발 환경
  ├─ p2-intro.qmd           — IDE 선택과 발전
  ├─ ... (6개 챕터)
```

**핵심 문제:**
1. `p1-intro.qmd`(소프트웨어 3.0, AI 주기율표, LLM 본질)는 1부의 한 챕터가 아니라
   **전체 책의 배경 지식**이다. 도입부에 있어야 한다.
2. 도입이 "글쓰기 역사"(p0-writing)만 다루고 **기술 환경**(SW 3.0, LLM)을 빠뜨렸다.
   독자가 1부에 진입할 때 AI 기술 지형도를 모르는 상태가 된다.
3. 메타프로그래밍(p1-meta)이 context, workflow 뒤에 배치되어 논리적 선후 관계가
   어긋난다. 메타프로그래밍은 AI 코딩의 이론적 토대이므로 앞에 와야 한다.

---

## 제안 구조

```
도입: AI 시대 글쓰기 환경
  ├─ p0-writing.qmd         — 도구가 사고를 바꾸는 글쓰기
  │    (역사, 문서 엔지니어링, 패러다임 전환, 인간 중심 글쓰기)
  └─ p0-environment.qmd     — 소프트웨어 3.0 시대 ★ p1-intro에서 이동+개명
       (SW 1.0→2.0→3.0, AI 주기율표, LLM 본질, 로드맵)

1부: AI 코딩
  ├─ p1-paradigm.qmd        — 재사용에서 재생성으로
  ├─ p1-meta.qmd            — 메타프로그래밍 ★ 앞으로 이동
  ├─ p1-context.qmd         — 프롬프트에서 컨텍스트로
  ├─ p1-workflow.qmd        — AI 코딩 실전 워크플로우
  ├─ p1-review.qmd          — 코드 리뷰와 품질 관리
  ├─ p1-tools.qmd           — AI 도구 생태계
  └─ p1-future.qmd          — 개발자의 미래

2부: 통합 개발 환경
  ├─ p2-intro.qmd           — IDE 선택과 발전
  ├─ p2-positron.qmd        — Positron
  ├─ p2-zed.qmd             — Zed
  ├─ p2-extension.qmd       — IDE 확장 프로그램
  ├─ p2-setup.qmd           — 개발 환경 구축
  ├─ p2-docker.qmd          — Docker
  └─ p2-compendium.qmd      — Research Compendium

부록
  └─ glossary.qmd            — 용어집
```

---

## 변경 사항 요약

| 변경 | 파일 | 내용 |
|------|------|------|
| **이동** | `p1-intro.qmd` → `p0-environment.qmd` | 도입부로 이동, 파일명 변경 |
| **순서** | `p1-meta.qmd` | 1부 내에서 2번째로 이동 (paradigm 바로 뒤) |
| **삭제** | 1부에서 p1-intro 제거 | 도입부로 옮겼으므로 |
| **이름** | 도입 Part 이름 | "글쓰기의 대전환" → "AI 시대 글쓰기 환경" |

---

## 논리적 흐름 (독자 여정)

### 도입: AI 시대 글쓰기 환경 — "왜, 무엇을"

**ch1. 도구가 사고를 바꾸는 글쓰기** (p0-writing)
> 동굴벽화 → 인쇄 → 디지털 → AI. 36,000년 기록 역사.
> 문서 엔지니어링, WYSIWYG→WYAIWYM, 인간 중심 공동저작.
> **독자가 얻는 것:** "글쓰기 도구가 왜 중요한가"에 대한 역사적 확신

**ch2. 소프트웨어 3.0 시대** (p0-environment, 기존 p1-intro)
> SW 1.0(코드) → 2.0(모델) → 3.0(프롬프트). AI 기술 주기율표.
> LLM의 본질, 한계(환각), 로드맵.
> **독자가 얻는 것:** AI 기술 지형도, "지금 어디에 서 있는가"

→ 도입 완료: 독자는 역사적 맥락과 기술적 환경을 모두 갖추고 1부에 진입

### 1부: AI 코딩 — "어떻게"

**ch3. 재사용에서 재생성으로** (p1-paradigm)
> Copy-Paste → Library → Framework → LLM 재생성.
> "코드는 소모품" 패러다임.
> **위치 근거:** 가장 큰 패러다임 변화를 먼저 이해해야 이후 내용이 납득됨

**ch4. 메타프로그래밍** (p1-meta) ★ 앞으로 이동
> 코드가 코드를 생성하는 원리. 결정론적 vs 확률적 메타프로그래밍.
> AI 코드 생성의 이론적 토대.
> **위치 근거:** context engineering, workflow의 이론적 기반.
> "AI가 코드를 생성한다"가 메타프로그래밍의 한 형태임을 이해한 후
> 구체적 방법론(context, workflow)으로 진입하는 것이 자연스럽다.

**ch5. 프롬프트에서 컨텍스트로** (p1-context)
> Prompt Engineering → Context Engineering 진화.
> CLAUDE.md, .cursorrules 등 컨텍스트 파일 설계.
> **위치 근거:** 메타프로그래밍 원리를 이해한 후, 실전 기법으로 진입

**ch6. AI 코딩 실전 워크플로우** (p1-workflow)
> TDD with AI, 단계별 실전 패턴.
> **위치 근거:** 이론(패러다임+메타) → 기법(컨텍스트) → 실전(워크플로우) 순서

**ch7. 코드 리뷰와 품질 관리** (p1-review)
> AI 생성 코드의 특성, 리뷰 체크리스트, 품질 도구.
> **위치 근거:** 코드를 생성한 후 검증하는 순서

**ch8. AI 도구 생태계** (p1-tools)
> Claude Code, Cursor, Copilot 등 도구 비교.
> **위치 근거:** 원리와 실전을 이해한 후 도구를 선택하는 것이 올바른 순서

**ch9. 개발자의 미래** (p1-future)
> Coder → Orchestrator 역할 전환, 역량 로드맵.
> **위치 근거:** 1부의 자연스러운 마무리, 전망 제시

### 2부: 통합 개발 환경 — "어디서"

> IDE 역사부터 미래, Positron, Zed, 확장 프로그램,
> 개발 환경 구축, Docker, Research Compendium.
> **위치 근거:** 1부에서 "무엇을 어떻게" 이해한 후,
> "어디서" 실행할지를 다루는 것이 학습 곡선에 맞다.

---

## 근거: 최신 AI 코딩 책 구성 참고

### O'Reilly "AI-Assisted Programming" (Taulli, 2024)
- Part 구분 없이 선형 흐름: 개념(Gen AI) → 기능(코드 제안) → IDE 통합 →
  문서화 → 한계 → 개발자 미래
- **시사점:** "환경/개념 먼저, 실전 나중, 미래 마지막" 패턴 일치

### Agent Factory (Panaversity, 2026)
- Part 1: General Agents — Foundations (개념 → 소통 → 도구 → 원칙)
- Part 2: Practical Implementation
- Part 3: Enterprise Patterns
- **시사점:** 기초(Foundations)를 독립 Part로 분리하는 것이 모범 사례

### Anthropic "2026 Agentic Coding Trends Report"
- Agentic SDLC: 요구사항 → 코딩 → 테스팅 → 배포 → 유지보수
- **시사점:** 요구사항(의도 명세)이 코딩보다 앞에 와야 하는 것처럼,
  환경 이해가 코딩 실전보다 앞에 와야 함

---

## 구현 계획

### 파일 작업
1. `chapters/p1-intro.qmd` → `chapters/p0-environment.qmd` (이동+개명)
2. `_quarto.yml` 수정: 도입 Part에 p0-environment 추가, 1부에서 제거
3. `_quarto.yml` 수정: 1부 내 p1-meta 순서 변경 (paradigm 바로 뒤)
4. `CLAUDE.md` 업데이트

### 이미지 경로
- p1-intro.qmd의 이미지 참조는 `../images/` 경로이므로 이동 후에도 동일 (변경 불필요)

### 기존 문서 내 참조
- `p1-intro.qmd` 내부의 `{#sec-gpt-coding}` 등 cross-reference ID는 유지
- 다른 챕터에서 p1-intro를 참조하는 곳이 있다면 확인 필요

---

## 출처

- [O'Reilly AI-Assisted Programming](https://www.oreilly.com/library/view/ai-assisted-programming/9781098164553/)
- [Agent Factory - Part 1: Foundations](https://agentfactory.panaversity.org/docs/General-Agents-Foundations)
- [2026 Agentic Coding Trends Report (Anthropic)](https://resources.anthropic.com/hubfs/2026%20Agentic%20Coding%20Trends%20Report.pdf)
- [AI Coding Best Practices 2025](https://dev.to/ranndy360/ai-coding-best-practices-in-2025-4eel)
- [Technical Writing Trends 2026](https://medium.com/softserve-technical-communication/technical-writing-trends-2026-lessons-from-a-year-of-ai-73e107390052)
- [AI in Technical Writing 2026](https://instrktiv.com/en/ai-in-technical-writing/)
