# AI 시대, 문서는 여전히 필요한가 — 리서치 정리

> 조사일: 2026-04-05
> 목적: 도입부 신규 챕터(`p0-why-document.qmd`) 집필을 위한 근거 자료

---

## 1. 핵심 발견 요약

### 1.1 문서는 죽지 않았다 — 오히려 AI가 문서를 더 필요로 한다

- AI 시스템(LLM, RAG, Copilot)은 **구조화된 문서를 입력으로** 사용한다. 문서 품질이 AI 출력 품질을 결정한다.
- llms.txt(2024.09 제안, 2025년 말 84만+ 사이트 도입), CLAUDE.md, AGENTS.md 등 **AI가 읽는 새로운 문서 유형**이 폭발적으로 증가.
- "AI value scales only as far as information quality allows" — 문서가 불명확하면 AI 출력도 부정확.
- 조직의 16%만이 워크플로우를 충분히 문서화 → AI 도입의 최대 장벽이 "문서 부족".

### 1.2 AI가 대체할 수 없는 문서의 4대 기능

| 기능 | 왜 AI가 대체 불가능한가 | 근거 |
|------|------------------------|------|
| **법적 증빙** | 감사 추적은 시스템 생성·변조 불가능해야 함. AI 생성물은 법적 증거력 없음 | EU AI Act, NIST RMF, ISO/IEC 42001 |
| **조직 기억** | LLM은 세션 종료 시 모든 맥락 소실. 조직 기억은 영속적 문서에만 존재 | 기업 기억 상실(corporate amnesia) 연구 |
| **재현성** | AI 생성 논문의 2.6%가 환각 인용 포함(2025). 과학적 재현은 검증 가능한 문서가 전제 | Nature 2025, Science 재현성 위기 보고 |
| **책임 소재** | "정책이 있다"는 증거가 아님. 감사 로그+타임스탬프+승인자가 기록된 문서만 증거 | AI 거버넌스 감사 문서화 가이드 |

### 1.3 AI가 바꾸는 것 vs 바꾸지 못하는 것

**AI가 바꾸는 것 (도구 장벽 ↓)**:
- 초안 생성 속도: 50% ↓
- 문서 구조화·포맷팅: 80% ↓
- 다국어 번역: 90% ↓
- 문서 검색·요약: 지식 노동자 시간의 20%를 점유하던 정보 탐색을 대폭 단축

**AI가 바꾸지 못하는 것 (지배 차원)**:
- 복잡도 판단: "이 문서가 필요한가?"는 맥락·목적·독자 이해 필요
- 법적 책임: 규제 준수 문서는 3~7년 보존 의무, 인간 승인 필수
- 사실 검증: AI 환각 검증은 문서당 추가 시간 필요
- 조직 기억: LLM 메모리는 구조적 한계 — "세션 종료 시 당신은 존재하지 않았다"

### 1.4 문서의 진화 — 소멸이 아니라 분화

문서는 사라지는 것이 아니라 **두 갈래로 분화**하고 있다:

1. **사람이 읽는 문서** (Human-readable): 보고서, 논문, 매뉴얼 → Quarto, LaTeX
2. **기계가 읽는 문서** (Machine-readable): CLAUDE.md, llms.txt, AGENTS.md, OpenAPI spec → AI 컨텍스트

두 갈래의 공통점: 둘 다 **구조화된 텍스트**이며, 둘 다 **버전 관리**가 필요하고, 둘 다 **정확성**이 생명이다.

### 1.5 검증 위기(Verification Crisis)

- AI 생성 콘텐츠의 폭증 → "정보 출처를 어떻게 검증하는가"가 핵심 과제
- 전문가들은 불투명한 탐지 시스템보다 **재현 가능한 출처 추적(reproducible provenance)** 선호
- 2025년 학술 논문의 2.6%에 환각 인용 포함 (2024년 0.3% 대비 급증)
- "허구적 정보가 진실에서 분리(epistemic fragmentation)" → 문서의 신뢰성이 민주주의·과학의 기반

---

## 2. 챕터 구성 제안

### 제목: "AI 시대, 문서는 여전히 필요한가"

| 섹션 | 내용 | SVG 다이어그램 |
|------|------|---------------|
| 도입 — "문서가 사라진다"는 예언 | ChatGPT 이후 "문서 종말론" 등장, 하지만 현실은 반대 | `doc-why-prophecy.svg` — 예언 vs 현실 |
| 문서의 4대 본질 기능 | 지식 보존, 법적 증빙, 재현성, 조직 기억 | `doc-why-four-pillars.svg` — 4대 기둥 |
| AI가 대체하는 것과 대체하지 못하는 것 | 도구 장벽 ↓ vs 지배 차원 불변 | `doc-why-ai-boundary.svg` — 경계선 |
| 문서의 분화 — 사람용과 기계용 | Human-readable + Machine-readable 두 갈래 | `doc-why-bifurcation.svg` — 분기 |
| 검증 위기와 문서의 새로운 역할 | 환각 인용, epistemic fragmentation | `doc-why-verification.svg` — 검증 |
| 조직 기억과 기업 기억 상실 | corporate amnesia, 지식 손실 비용 | (본문 표로 대체) |

---

## 3. 출처

### 문서 트렌드 & AI 문서화
- [6 Must-Know Technical Documentation Trends Shaping 2026](https://www.fluidtopics.com/blog/industry-insights/technical-documentation-trends-2026/)
- [Major AI Documentation Trends for 2026](https://document360.com/blog/ai-documentation-trends/)
- [AI-Driven Documentation in 2026](https://overcast.blog/ai-driven-documentation-in-2026-f993f0c6d0d6)
- [AI Documentation Trends: What's Changing in 2025](https://www.mintlify.com/blog/ai-documentation-trends-whats-changing-in-2025)

### LLM 메모리 한계 & 조직 기억
- [From Human Memory to AI Memory: A Survey (arXiv)](https://arxiv.org/html/2504.15965v2)
- [Why LLM Memory Still Fails — A Field Guide](https://dev.to/isaachagoel/why-llm-memory-still-fails-a-field-guide-for-builders-3d78)
- [Institutional 'Forgetting' and The Failure of Corporate Memory](https://paulitaylor.com/2024/05/31/institutional-forgetting-and-the-failure-of-corporate-memory/)
- [The Cost and Consequence of Institutional Memory Drain (Inc.)](https://www.inc.com/bethmaser/the-cost-and-consequence-of-institutional-memory-drain/91178504)

### 법적·규제 문서
- [AI Legal Compliance in 2026 (Spellbook)](https://www.spellbook.legal/learn/ai-legal-compliance)
- [AI Governance Documentation: Essential Audit Evidence Guide](https://www.kiteworks.com/cybersecurity-risk-management/ai-governance-audit-documentation/)
- [Audit Trails for Accountability in LLMs (arXiv)](https://arxiv.org/html/2601.20727v1)
- [AI Agent Compliance & Governance in 2025 (Galileo)](https://galileo.ai/blog/ai-agent-compliance-governance-audit-trails-risk-management)

### 재현성 위기 & 검증
- [The Verification Crisis: Expert Perceptions of GenAI Disinformation (arXiv)](https://arxiv.org/html/2602.02100v1)
- [Is AI leading to a reproducibility crisis in science? (Nature)](https://www.nature.com/articles/d41586-023-03817-6)
- [Hallucinated citations are polluting the scientific literature (Nature 2026)](https://www.nature.com/articles/d41586-026-00969-z)
- [What is Reproducibility in AI/ML Research? (AI Magazine)](https://onlinelibrary.wiley.com/doi/full/10.1002/aaai.70004)

### AI 컨텍스트 문서 (새로운 문서 유형)
- [llms.txt, CLAUDE.md & AGENTS.md | AI File Formats Guide](https://p0stman.com/ai-file-formats)
- [The Complete Guide to AI Agent Memory Files](https://medium.com/data-science-collective/the-complete-guide-to-ai-agent-memory-files-claude-md-agents-md-and-beyond-49ea0df5c5a9)
- [What is llms.txt? (GitBook)](https://www.gitbook.com/blog/what-is-llms-txt)

### 지식 노동자 & AI
- [The Future of AI in Knowledge Work (Microsoft Research, CHI 2025)](https://www.microsoft.com/en-us/research/blog/the-future-of-ai-in-knowledge-work-tools-for-thought-at-chi-2025/)
- [AI at Work Report 2025 (Indeed Hiring Lab)](https://www.hiringlab.org/2025/09/23/ai-at-work-report-2025-how-genai-is-rewiring-the-dna-of-jobs/)
- [AI readiness report — What's holding back adoption (Lucid)](https://lucid.co/blog/ai-readiness-survey-2025)

---

## 4. 후속 작업

1. **SVG 제작**: `doc-why-prophecy.svg`, `doc-why-four-pillars.svg`, `doc-why-ai-boundary.svg`, `doc-why-bifurcation.svg`, `doc-why-verification.svg` (5개)
2. **챕터 집필**: `chapters/p0-why-document.qmd`
3. **_quarto.yml 등록**: 도입부 첫 번째 챕터로 배치 (p0-writing.qmd 앞)
4. **references.bib 추가**: 필요한 학술 인용 항목 추가
