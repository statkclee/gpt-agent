# /diagram - Tufte Style Grayscale SVG 다이어그램 생성

인자: $ARGUMENTS

첫 번째 인자는 파일명(확장자 제외), 나머지는 다이어그램 설명이다.
예: `/diagram context-flow 프롬프트에서 컨텍스트 엔지니어링 진화 과정`
→ 파일명: `images/context-flow.svg`, 설명: "프롬프트에서 컨텍스트 엔지니어링 진화 과정"

## 디자인 규칙 (엄격 준수)

### 색상 - Grayscale Only
- 텍스트: `#333333`
- 보조 텍스트: `#666666`
- 경계선/구분선: `#999999`
- 배경 강조: `#f5f5f5`
- 연한 경계: `#cccccc`
- 전체 배경: `#ffffff`
- **컬러 사용 절대 금지** (빨강, 파랑, 초록 등 일체 불가)

### 타이포그래피
- 주 서체: `font-family: Palatino, 'Book Antiqua', Georgia, serif;`
- 제목: 16-18px, bold, `#333`
- 본문: 12-14px, regular, `#333`
- 주석/캡션: 10-11px, italic, `#666`

### 레이아웃
- viewBox 설정 필수 (반응형)
- 적절한 여백 (최소 20px)
- 명확한 시각적 계층 구조
- 불필요한 장식 최소화 (High Data-Ink Ratio)
- 화살표는 단순한 선 + 삼각형
- 박스 모서리: rx="3" 정도의 미세한 라운드

### SVG 기본 템플릿

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 500">
  <defs>
    <style>
      text { font-family: Palatino, 'Book Antiqua', Georgia, serif; }
      .title { font-size: 18px; font-weight: bold; fill: #333; }
      .label { font-size: 13px; fill: #333; }
      .caption { font-size: 11px; fill: #666; font-style: italic; }
      .box { fill: #f5f5f5; stroke: #999; stroke-width: 1; }
      .line { stroke: #999; stroke-width: 1; }
      .arrow { fill: #666; stroke: none; }
    </style>
    <marker id="arrowhead" markerWidth="10" markerHeight="7"
            refX="10" refY="3.5" orient="auto">
      <polygon points="0 0, 10 3.5, 0 7" class="arrow"/>
    </marker>
  </defs>
  <rect width="800" height="500" fill="#ffffff"/>
  <!-- 다이어그램 내용 -->
</svg>
```

## 작업 절차

1. 설명을 분석하여 다이어그램 유형 결정 (흐름도, 비교표, 아키텍처, 타임라인 등)
2. 위 디자인 규칙을 적용하여 SVG 코드 작성
3. `images/` 폴더에 저장
4. 해당 챕터의 `.qmd` 파일에 삽입할 마크다운 코드 제시

## 주의사항
- 한글 텍스트는 SVG 내에서 정상 렌더링되도록 한다.
- viewBox 크기는 내용에 맞게 조정한다 (기본 800x500, 필요시 변경).
- 기존 `images/` 폴더의 다이어그램과 시각적 일관성을 유지한다.
- 복잡한 다이어그램은 여러 개로 분리하는 것을 권장한다.
