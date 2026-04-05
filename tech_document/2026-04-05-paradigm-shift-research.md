# 코드 재생성 패러다임 전환 리서치 정리

> 조사일: 2026-04-05
> 목적: `p1-paradigm.qmd` (143줄, 내용 중복) 전면 재작성

---

## 핵심 발견

### 재생성 가능한 코드의 5대 조건 (Urayev)
1. CLI 테스트를 통한 자가 검증
2. 이식 가능한 환경 (컨테이너)
3. 안정적 계약 (입출력 인터페이스 불변)
4. 선언적 구성 (pyproject.toml)
5. 프롬프트 스캐폴딩 (재사용 가능한 작업 명세)

### 비유: 레고 vs 점토
- 재사용 = 레고 블록 조립 (모듈 조합)
- 재생성 = 점토로 빚기 (유연한 생성)

### 실증 데이터
- AI 생성 코드: Type-4 의미적 클론 1.87배 (arxiv 2601.21276)
- 보안 취약성 2.74배 (CodeRabbit 2025.12)
- YC 2025 Winter: 25% 스타트업이 95%+ AI 코드
- 80/20 법칙: AI가 80% 생성, 나머지 20%에 80% 시간

### Software 1.0/2.0/3.0 → 에이전틱 엔지니어링
- 1.0: 인간 직접 작성
- 2.0: 신경망 가중치 (데이터+학습)
- 3.0: LLM + 자연어 프롬프트
- 2026: 에이전틱 엔지니어링 (체계적 오케스트레이션)

### 현재 챕터 문제
- 28-87줄과 51-105줄 내용 거의 동일 (중복)
- 구조 혼란, Software 3.0 프레임워크 부재

## 출처
- [arxiv 2601.21276 - AI PR 중복 코드](https://arxiv.org/html/2601.21276)
- [arxiv 2508.19834 - AI 시대 소프트웨어 재사용](https://arxiv.org/html/2508.19834v1)
- [Urayev - 재생성 가능한 코드](https://medium.com/@denisuraev/a-new-era-in-software-architecture-from-reusable-to-regeneratable-code-3a48c40609e6)
- [Thoughtworks - AI 네이티브 5대 빌딩블록](https://www.thoughtworks.com/insights/blog/generative-ai/beyond-vibe-coding-the-five-building-blocks-of-aI-native-engineering)
- [Vibe Coding Is Passe (The New Stack)](https://thenewstack.io/vibe-coding-is-passe/)
