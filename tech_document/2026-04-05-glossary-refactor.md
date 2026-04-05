# Quarto Glossary 재구성

- **날짜**: 2026-04-05
- **작업자**: Claude Code
- **상태**: 완료

## 배경

기존 `glossary.yml`은 두 가지 문제가 있었다:

1. **형식 불일치**: `name`/`def` 하위 구조를 사용했으나, `debruine/quarto-glossary` 확장은 단순 `key: definition` 형식만 인식
2. **용어 불일치**: 삭제된 1-7부(기초 CS)의 용어만 129줄 있었고, 현재 8-9부(AI Agent Coding)와 무관

## 조사 결과

### Quarto Glossary 확장 프로그램

- **패키지**: `debruine/quarto-glossary` (이미 설치됨)
- **방식**: Lua shortcode 기반
- **YAML 형식**: 단순 `key: definition` (중첩 구조 미지원)
- **Quarto 내장 glossary**: 미구현 (quarto-dev/quarto-cli#1697, Future 마일스톤)

### glossary.yml 올바른 형식

```yaml
# 올바름 (확장이 인식)
변수: 데이터를 저장하는 이름이 붙은 메모리 공간.

# 틀림 (확장이 인식 못함)
변수:
  name: 변수(variable)
  def: 데이터를 저장하는 이름이 붙은 메모리 공간.
```

### Shortcode 문법

```markdown
{{< glossary LLM >}}                        # 기본 참조
{{< glossary "AI 에이전트" >}}                # 여러 단어
{{< glossary LLM display="대규모 언어 모델" >}} # 표시 텍스트 변경
{{< glossary table=true >}}                   # 용어 테이블 출력
```

### _quarto.yml 설정

```yaml
glossary:
  path: glossary.yml    # 경로
  popup: click          # hover | click | none
  show: true            # 활성화 여부
```

### Book 프로젝트 주의사항

Quarto Book에서 각 챕터는 별도로 렌더링된다. `{{< glossary table=true >}}`는 같은 렌더링 단위에서 참조된 용어만 수집하므로, `glossary.qmd`에서 모든 용어를 명시적으로 `{{< glossary term >}}`으로 참조한 뒤 테이블을 생성해야 한다.

## 변경 내용

### 1. glossary.yml 전면 교체

- **삭제**: 기초 CS 용어 40여 개 (129줄)
- **추가**: AI Agent Coding 용어 40개 (8개 카테고리)

카테고리:
- AI 핵심 개념 (LLM, 토큰, 컨텍스트 윈도우, 할루시네이션 등)
- 프롬프트와 컨텍스트 (프롬프트 엔지니어링, 컨텍스트 엔지니어링 등)
- AI 코딩 패러다임 (바이브 코딩, 에이전트 코딩, 페어 프로그래밍 등)
- AI 도구와 서비스 (API, RAG, Function Calling, MCP, Ollama 등)
- IDE와 개발 환경 (IDE, LSP, Positron, Zed, Quarto 등)
- Docker와 컨테이너 (Docker, 이미지, Dockerfile, 볼륨 등)
- Research Compendium (재현성 등)
- 기타 (Git, 파이프라인, 오픈소스, 마크다운)

### 2. chapters/glossary.qmd 전환

- **삭제**: 150줄 수동 마크다운 테이블
- **추가**: `{{< glossary term >}}` shortcode로 모든 용어 참조 + `{{< glossary table=true >}}`로 자동 테이블 생성
- 카테고리별 소제목으로 구조화

### 3. _quarto.yml

변경 없음. 기존 설정이 올바름:
```yaml
glossary:
  path: glossary.yml
  popup: click
  show: true
```

## 다음 단계

- 각 챕터 본문에서 핵심 용어에 `{{< glossary term >}}` shortcode 삽입
  (예: "LLM"이 처음 등장하는 곳에 `{{< glossary LLM >}}` 적용)
- 챕터별 집필/보강 시 새 용어가 나오면 glossary.yml에 추가

## 참고 자료

- [debruine/quarto-glossary 문서](https://debruine.github.io/quarto-glossary/)
- [GitHub 저장소](https://github.com/debruine/quarto-glossary)
- [Quarto CLI Glossary Feature Request #1697](https://github.com/quarto-dev/quarto-cli/issues/1697)
