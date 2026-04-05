# 컨텍스트 엔지니어링 리서치 정리

> 조사일: 2026-04-05
> 목적: `p1-context.qmd` (115줄 -> 350줄+) 전면 보강

---

## 1. 핵심 발견

### 1.1 전환의 공식 계기

2025년 6월 Andrej Karpathy가 X에서 "context engineering"을 공식 명명.
정의: "다음 단계를 위해 컨텍스트 윈도우를 적절한 정보로 채우는 정교한 기술과 과학"
Shopify CEO Tobi Lutke도 동시기에 "AI를 위한 완전한 각본을 쓰는 것"으로 표현.

### 1.2 진화 타임라인

| 시기 | 단계 | 핵심 기술 |
|------|------|-----------|
| 2022 | 프롬프트 엔지니어링 등장 | 역할 지정, 지시 최적화 |
| 2023 | 고급 프롬프트 기법 | Chain-of-thought, Few-shot |
| 2024 | 메모리/히스토리 도입 | RAG, 대화 이력 관리 |
| 2025 중반 | 컨텍스트 엔지니어링 명명 | MCP, CLAUDE.md, AGENTS.md |
| 2026 | 하네스 엔지니어링 | 에이전트 루프, 도구 체인, 가드레일 |

### 1.3 Karpathy의 컨텍스트 7대 구성 요소

1. 작업 설명(Task descriptions)
2. 퓨샷 예시(Few-shot examples)
3. RAG 검색 결과(Retrieved knowledge)
4. 관련 데이터(Related data, multimodal)
5. 도구(Tools)
6. 상태와 히스토리(State and history)
7. 압축/컴팩팅(Compacting)

### 1.4 LangChain 4대 전략: Write-Select-Compress-Isolate

| 전략 | 설명 | 실전 적용 |
|------|------|-----------|
| Write | 컨텍스트 외부에 정보 저장 | Auto Memory, 스크래치패드 |
| Select | 필요한 정보만 컨텍스트로 | RAG, grep, 시맨틱 검색 |
| Compress | 요약, 트리밍 | auto-compact, 요약 미들웨어 |
| Isolate | 멀티에이전트로 분리 | 서브에이전트, Agent Teams |

### 1.5 Full Context Stack (8개 계층)

1. 시스템 프롬프트
2. 코드베이스 컨텍스트
3. Git 히스토리
4. 의존성/라이브러리
5. 도구 정의
6. 팀 표준/패턴
7. 대화 히스토리
8. 검색된 문서

### 1.6 메모리 3분류 (LangChain)

- 에피소딕(Episodic): 구체적 예시 (Few-shot)
- 절차적(Procedural): 행동 지시 (CLAUDE.md)
- 의미(Semantic): 사실적 지식 (RAG 문서)

### 1.7 프로젝트 메모리 파일 비교

| 파일 | 에이전트 | 용도 |
|------|----------|------|
| CLAUDE.md | Claude Code | 코딩 표준, 아키텍처, 리뷰 체크리스트 |
| AGENTS.md | 범용 (Linux Foundation 표준) | 모든 에이전트 공통 지시 |
| .cursorrules | Cursor | Cursor IDE 전용 프로젝트 규칙 |

---

## 2. 챕터 보강 구성 (p1-context.qmd)

### 현재 문제
- 115줄, Vibe Coding 내용이 p1-paradigm과 중복
- 컨텍스트 엔지니어링 본론이 30줄 미만
- SVG 1개(vibe-coding), 교차참조 0개

### 보강 구성안

| 섹션 | 내용 | SVG |
|------|------|-----|
| 프롬프트에서 컨텍스트로: 전환의 역사 | 2022-2026 타임라인, Karpathy 정의 | context-evolution.svg |
| 컨텍스트의 해부학 | 7대 구성 요소, Full Context Stack | context-anatomy.svg |
| Write-Select-Compress-Isolate | LangChain 4대 전략, 실전 워크플로우 | context-wsci.svg |
| 프로젝트 메모리 파일 실전 | CLAUDE.md vs AGENTS.md vs .cursorrules | (본문 표) |
| MCP와 도구 컨텍스트 | Model Context Protocol, 외부 연결 | (본문 설명) |
| 컨텍스트 윈도우 = RAM | OS 비유, auto-compact, 요약 | context-ram.svg |

---

## 3. 출처

- [Karpathy X 포스트 (2025.06)](https://x.com/karpathy/status/1937902205765607626)
- [Faros AI - Context Engineering Complete Guide](https://www.faros.ai/blog/context-engineering-for-developers)
- [LangChain - Context Engineering for Agents](https://blog.langchain.com/context-engineering-for-agents/)
- [Addy Osmani - Context Engineering](https://addyo.substack.com/p/context-engineering-bringing-engineering)
- [Martin Fowler - Context Engineering for Coding Agents](https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html)
- [Prompt Engineering vs Context vs Harness (Medium)](https://medium.com/@server_62309/prompt-engineering-vs-context-engineering-vs-harness-engineering-whats-the-difference-in-2026-2883670f78f1)
