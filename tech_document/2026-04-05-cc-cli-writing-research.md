# Claude Code CLI 글쓰기 도구 — 리서치 정리

> 조사일: 2026-04-05
> 목적: 1부 신규 챕터(`p1-cc-writing.qmd`) 집필을 위한 근거 자료

---

## 1. 핵심 발견

### 1.1 Claude Code CLI는 코딩 도구가 아니라 저작 도구다

Claude Code는 터미널에 상주하며 코드베이스를 이해하고, 파일을 읽고 쓰고, 명령을 실행하고, 자연어로 소통하는 에이전트 도구다. "코딩 도구"라는 이름이 붙어 있지만, 본질적 기능 -- 파일 읽기/쓰기, 구조 이해, 명령 실행, 자연어 대화 -- 은 글쓰기에도 그대로 적용된다.

실제로 "Writing Books with Claude Code"라는 책이 Claude Code로 집필되었고, Mintlify는 Claude Code를 기술 문서 작성 보조 도구로 활용하는 사례를 공개했다. 한 저자는 Claude Code의 에이전트 팀 기능으로 소설을 24시간 안에 완성했다.

### 1.2 Claude Code의 저작 관련 핵심 기능

| 기능 | 설명 | 저작 활용 |
|------|------|-----------|
| **CLAUDE.md** | 프로젝트 루트 설정 파일, 매 세션 시작시 로드 | 문체 규칙, 용어집, 스타일 가이드 정의 |
| **Skills** | 맥락 매칭으로 자동 활성화되는 확장 | /write-chapter, /diagram, /style-check 등 저작 스킬 |
| **Slash Commands** | 사용자가 직접 호출하는 단축 명령 | /status, /render, /publish 등 출판 워크플로우 |
| **Subagents** | 병렬로 동작하는 하위 에이전트 | Explore(탐색), Plan(설계), 범용(실행) 3종 내장 |
| **Agent Teams** | 여러 Claude Code 인스턴스 협업 | 챕터별 병렬 집필, 리뷰-편집 분리 |
| **Hooks** | 이벤트 기반 자동 실행 셸 명령 | 저장 시 자동 렌더링, 커밋 시 문체 검사 |
| **MCP Servers** | 외부 도구 통합 프로토콜 | 브라우저 자동화, DB 접근, API 연동 |
| **Auto Memory** | 세션 간 지식 자동 축적 | 프로젝트 컨벤션, 디버깅 패턴, 스타일 선호 학습 |
| **Plugins** | 슬래시 명령+에이전트+훅+MCP 번들 | 팀 전체 공유 가능한 저작 워크플로우 패키지 |

### 1.3 CLAUDE.md 컨텍스트 엔지니어링

CLAUDE.md는 .gitignore만큼 필수적인 프로젝트 인프라로 자리잡았다.

**핵심 원칙:**
- 루트 CLAUDE.md는 50-100줄 이내 (HumanLayer 사례: 60줄 미만)
- 모든 줄에 대해 "이 줄을 제거하면 Claude가 실수하는가?" 질문
- 상세 내용은 별도 파일로 분리하고 @path로 임포트
- 모노레포에서는 하위 디렉토리별 CLAUDE.md 계층 구조 활용

**저작 프로젝트에서의 CLAUDE.md:**
- 문체 규칙 (평서문, AI 티 제거, "이 + 명사" 금지)
- 용어 한글화 규칙 (첫 등장 병기, 재등장 한글만)
- 다이어그램 스펙 (Tufte grayscale SVG)
- 챕터 구조와 파일 명명 규칙
- 렌더링 명령과 출판 워크플로우

### 1.4 저작을 위한 슬래시 커맨드 생태계

이 프로젝트에서 실제 운용 중인 17개 슬래시 커맨드가 저작 워크플로우를 증명한다:

**집필 단계:** /outline(아웃라인), /new-chapter(생성), /write-chapter(집필)
**품질 관리:** /review(리뷰), /evaluate(평가), /style-check(문체), /fact-check(사실검증), /translate(용어)
**출판 단계:** /diagram(SVG), /render(렌더링), /publish(배포)
**관리:** /status(현황), /compare(비교), /research(조사), /execute(코드검증), /update-progress(기록)

### 1.5 멀티 에이전트 저작 프레임워크

Claude Book 프로젝트는 소설 집필을 위한 멀티 에이전트 오케스트레이션을 구현했다:

- **Planner**: 스토리 구조, 챕터 아웃라인 설계
- **Writer**: 실제 본문 집필 (3명 병렬)
- **Reviewer**: 일관성 검사, 문체 검사 (4명 병렬, 관점별)
- **Perplexity Gate**: AI스러운 문장 탐지 및 재작성

에이전트 팀 기능으로 한 저자가 10년간 방치한 소설을 12시간 만에 완성한 사례도 보고되었다.

### 1.6 패러다임 전환 -- 개발자에서 오케스트레이터로

Anthropic 내부에서 코드의 대부분이 Claude Code로 작성되며, 엔지니어당 PR이 150% 증가했다. Stripe는 1,370명 엔지니어에게 배포하여 10,000줄 Scala-to-Java 마이그레이션을 4일 만에 완료했다 (기존 추정: 10인주).

글쓰기에 적용하면:
- 저자는 "쓰는 사람"에서 "지시하고 검증하는 사람"으로 전환
- 초안 생성 속도가 아닌 검증-편집 역량이 저작 품질을 결정
- CLAUDE.md가 "저작의 아키텍처"를 정의하는 핵심 문서가 됨

---

## 2. 챕터 구성 제안

### 제목: "Claude Code — 터미널에서 시작하는 글쓰기"

| 섹션 | 내용 | SVG |
|------|------|-----|
| 도입 -- 코딩 도구가 저작 도구가 되기까지 | CC 본질은 파일 읽기/쓰기+자연어 | `cc-writing-evolution.svg` |
| CLAUDE.md -- 저작의 아키텍처 | 컨텍스트 엔지니어링이 문체를 결정 | `cc-writing-claudemd.svg` |
| 슬래시 커맨드 -- 저작 워크플로우 자동화 | 17개 커맨드의 집필-품질-출판 파이프라인 | `cc-writing-pipeline.svg` |
| 에이전트 오케스트레이션 | 서브에이전트+팀으로 병렬 저작 | `cc-writing-agents.svg` |
| 메모리와 학습 | Auto Memory로 세션 간 지식 축적 | (본문 설명) |
| 실전: 이 책이 만들어지는 과정 | 본 프로젝트의 실제 워크플로우 재현 | `cc-writing-this-book.svg` |

---

## 3. 출처

### Claude Code 공식
- [Claude Code Overview](https://code.claude.com/docs/en/overview)
- [Claude Code Best Practices](https://code.claude.com/docs/en/best-practices)
- [How Claude Remembers Your Project](https://code.claude.com/docs/en/memory)
- [Create Custom Subagents](https://code.claude.com/docs/en/sub-agents)
- [Create Plugins](https://code.claude.com/docs/en/plugins)
- [GitHub - anthropics/claude-code](https://github.com/anthropics/claude-code)

### 저작 사례
- [Writing Books with Claude Code](https://cloudstreet-dev.github.io/Writing-Books-with-Claude-Code/)
- [How Mintlify Uses Claude Code as a Technical Writing Assistant](https://www.mintlify.com/blog/how-mintlify-uses-claude-code-as-a-technical-writing-assistant)
- [Using Claude Code to Help Me Write](https://andrewpwheeler.com/2026/03/20/using-claude-code-to-help-me-write/)
- [Day 1 with Claude Code: A Technical Writer's First Impressions](https://medium.com/@jennifer.oakleytx/day-1-with-claude-code-a-technical-writers-first-impressions-8ab46cf704e8)
- [Claude Book: Multi-Agent Novel Writing (HackerNoon)](https://hackernoon.com/claude-book-a-multi-agent-framework-for-writing-novels-with-claude-code)
- [AI Agent Teams Finished My Sci-Fi Novel in 12 Hours](https://barrgroup.com/software-expert-witness/blog/ai-agents-finished-decade-old-novel)

### CLAUDE.md & 컨텍스트 엔지니어링
- [Writing a Good CLAUDE.md (HumanLayer)](https://www.humanlayer.dev/blog/writing-a-good-claude-md)
- [CLAUDE.md Best Practices (UX Planet)](https://uxplanet.org/claude-md-best-practices-1ef4f861ce7c)
- [Context Engineering for Coding Agents (Martin Fowler)](https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html)
- [Claude Code Project Structure Best Practices](https://uxplanet.org/claude-code-project-structure-best-practices-5a9c3c97f121)

### 기능 & 아키텍처
- [Understanding Claude Code's Full Stack: MCP, Skills, Subagents, Hooks](https://alexop.dev/posts/understanding-claude-code-full-stack/)
- [Claude Code Complete Guide 2026](https://claude-world.com/articles/claude-code-complete-guide-2026/)
- [How I Use Every Claude Code Feature](https://blog.sshh.io/p/how-i-use-every-claude-code-feature)
- [Claude Code Is Changing How We Build Software In 2026](https://medium.com/techtrends-digest/claude-code-is-changing-how-we-build-software-in-2026-cba4a800297e)
- [awesome-claude-code (GitHub)](https://github.com/hesreallyhim/awesome-claude-code)

---

## 4. 후속 작업

1. **SVG 제작**: `cc-writing-evolution.svg`, `cc-writing-claudemd.svg`, `cc-writing-pipeline.svg`, `cc-writing-agents.svg`, `cc-writing-this-book.svg` (5개)
2. **챕터 집필**: `chapters/p1-cc-writing.qmd`
3. **_quarto.yml 등록**: 1부 첫 번째 챕터로 배치 (p1-paradigm.qmd 앞)
4. **깨진 문자 검사**: 작성 후 U+FFFD 스캔 필수
