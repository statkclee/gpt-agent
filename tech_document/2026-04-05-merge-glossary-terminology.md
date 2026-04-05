# terminology.md와 glossary.yml 통합 기술문서

- **날짜**: 2026-04-05
- **목적**: 용어 관련 파일 중복 분석 및 단일 소스(Single Source of Truth) 통합

---

## 1. 현황 분석

### 대상 파일 3개

| 파일 | 형식 | 용어 수 | 용도 | 소비자 |
|------|------|---------|------|--------|
| `glossary.yml` | YAML | ~40개 | Quarto glossary 확장 프로그램 데이터 | `glossary.lua` (hover/click 팝업) |
| `terminology.md` | Markdown 테이블 | ~30개 + 규칙 | 한글 번역 규칙 가이드 | 저자/AI (참고용) |
| `chapters/glossary.qmd` | Markdown 테이블 | ~90개 | 부록 용어집 페이지 (독자용) | Quarto 렌더링 → HTML |

### 용어 유형 비교

```
glossary.yml / glossary.qmd        terminology.md
─────────────────────────          ─────────────────────────
프로그래밍 개념 정의                 고유명사 한글 번역 규칙
(변수, 디버깅, CPU, 함수 등)        (Docker→도커, ChatGPT→챗GPT 등)

"이 용어가 무엇인가?"               "이 용어를 한글로 어떻게 쓰는가?"
독자 대상                           저자/AI 대상
```

### 중복 분석 결과

| 비교 쌍 | 직접 중복 | 설명 |
|---------|-----------|------|
| terminology.md ↔ glossary.yml | **0건** | 완전히 다른 유형 (고유명사 vs 개념) |
| glossary.yml ↔ glossary.qmd | **~40건** | glossary.yml은 glossary.qmd의 부분집합 |
| terminology.md ↔ glossary.qmd | **0건** | 완전히 다른 유형 |

### 추가 발견 사항

1. **glossary 확장 미사용**: `{{< glossary >}}` shortcode가 어떤 챕터에서도 호출되지 않음
2. **glossary.yml은 사실상 유휴 상태**: `_quarto.yml`에 등록되어 있으나 실제 팝업 기능 미활용
3. **glossary.qmd 수동 관리**: glossary.yml과 별도로 마크다운 테이블을 직접 유지 중

---

## 2. 통합 전략

### 원칙

- **단일 소스**: 용어 데이터는 `glossary.yml` 한 곳에서 관리
- **역할 분리**: 용어 정의(독자용) ↔ 번역 규칙(저자용)은 다른 파일에 배치
- **terminology.md 폐기**: 고유명사 정의는 `glossary.yml`로, 번역 규칙은 `CLAUDE.md`로 이전

### 실행 계획

```
terminology.md (폐기)
├── 용어 정의 (도커, 파이썬, 챗GPT 등)  → glossary.yml에 추가
├── 번역 규칙 (원어 유지, 첫 등장 표기 등) → CLAUDE.md에 추가
└── 업데이트 이력                        → 본 기술문서에 기록
```

### glossary.yml 추가 항목 (terminology.md 출처)

총 30개 고유명사 정의를 추가:

**운영체제/플랫폼 (10개):**
도커, 파이썬, 윈도우, 맥OS, 리눅스, 우분투, 데비안, 러스트, 파워셸, 아나콘다

**문서 도구 (3개):**
쿼토, 판독, 타이니텍

**개발 환경 (3개):**
아톰, 일렉트론, 포지트론

**AI 도구 (7개):**
챗GPT, 클로드 코드, 클로드 소넷, 커서, 제미나이, 구글 앤티그래비티, 윈드서프

**글꼴 (2개):**
프리텐다드, D2코딩

**워크플로우 (1개):**
스네이크메이크

**조직/인명 (4개):**
볼란드, 젯브레인즈, 포짓, 앤더스 헤일스버그

### CLAUDE.md 추가 내용

terminology.md의 다음 규칙을 CLAUDE.md `문체 가이드` 섹션에 이전:
- 첫 등장 시 한글(영어) 병기 원칙
- 원어 유지 목록 (브랜드명, 약어, 기술 용어)
- 명령어/파일명/URL 원어 유지 규칙
- 혼합 표기 허용 규칙

---

## 3. 파일별 변경 내역

| 파일 | 작업 | 상세 |
|------|------|------|
| `glossary.yml` | 수정 | 30개 고유명사 정의 추가 |
| `CLAUDE.md` | 수정 | 한글화 번역 규칙 섹션 추가 |
| `terminology.md` | 삭제 | 내용이 glossary.yml + CLAUDE.md로 이전 완료 |
| `tech_document/` | 참조 업데이트 | terminology.md 언급 부분 수정 |

---

## 4. 향후 고려사항

- **glossary 확장 활성화**: `{{< glossary >}}` shortcode를 챕터에서 활용하면 glossary.yml 팝업 기능 활성화 가능
- **glossary.qmd 자동 생성**: glossary.yml에서 glossary.qmd 테이블을 자동 생성하는 스크립트 검토 (현재는 수동 관리)
