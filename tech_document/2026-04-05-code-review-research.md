# AI 코드 리뷰와 품질 관리 리서치 정리

> 조사일: 2026-04-05
> 목적: `p1-review.qmd` (139줄, 이미지 0개) 전면 보강

---

## 핵심 발견

### AI 생성 코드 품질 문제
- 40-45% 보안 결함 포함, 모델 세대 바뀌어도 미개선
- 취약점 2.74배, 권한 상승 경로 322% 증가
- 구문 오류(-76%)와 로직 버그(-60%)는 감소했지만 보안은 악화

### 슬롭스쿼팅(Slopsquatting) -- 신규 공급망 공격
- LLM이 존재하지 않는 패키지 추천: 20%
- 환각 패키지의 43%가 반복 쿼리에서 일관 재등장
- huggingface-cli 사례: 환각 패키지를 누가 등록하자 3개월 30,000건 다운로드

### 3단계 리뷰 파이프라인
1. AI 자동 리뷰 (수 초)
2. 정적 분석/SAST (분)
3. 인간 리뷰 (비즈니스 로직)

### 생산성 역설
- 개발자 체감: 20% 빠름
- 실측: 19% 느림 (METR 2025.7)
- PR 98% 더 많이 열지만, 리뷰 91% 길어짐
- 복잡성이 "생성"에서 "리뷰"로 이전

### AI 코드 라벨링 효과
- PR에 AI 생성 코드 명시 표시 → AI 관련 프로덕션 버그 30-40% 감소

### 현재 챕터 문제
- 이미지 0개, 인용 0개
- pylint/mypy/bandit/black 나열 수준
- AI 코드 리뷰 도구(Copilot Code Review, CodeRabbit 등) 미언급
- 슬롭스쿼팅, 생산성 역설 등 최신 이슈 부재

## 출처
- [GitHub - 60M Copilot Code Reviews](https://github.blog/ai-and-ml/github-copilot/60-million-copilot-code-reviews-and-counting/)
- [Endor Labs - AI 코드 취약점](https://www.endorlabs.com/learn/the-most-common-security-vulnerabilities-in-ai-generated-code)
- [BleepingComputer - 슬롭스쿼팅](https://www.bleepingcomputer.com/news/security/ai-hallucinated-code-dependencies-become-new-supply-chain-risk/)
- [Qodo - Best Automated Code Review 2026](https://www.qodo.ai/blog/best-automated-code-review-tools-2026/)
- [Exceeds.ai - AI Code Benchmarks](https://blog.exceeds.ai/industry-benchmarks-ai-code-productivity/)
