# /publish - 빌드 + 커밋 + 배포

모드: $ARGUMENTS

("preview"로 빌드만, "deploy"로 전체 배포, 인자 없으면 현황 확인 후 선택)

## 목적

렌더링 → 검증 → 커밋 → 푸시를 한 번의 명령으로 실행한다. 반복적인 배포 작업을 자동화하되, 각 단계에서 문제가 발견되면 즉시 중단하고 보고한다.

## 작업 절차

### 0단계: 사전 현황 확인

배포 전 현재 상태를 파악한다.

```bash
git status          # 변경된 파일 목록
git log -3 --oneline # 최근 커밋
```

**중단 조건:**
- 커밋하지 않은 변경사항이 있는데 사용자가 인지하지 못한 경우 → 확인 요청
- main 브랜치가 아닌 경우 → 확인 요청

### 1단계: 렌더링

```bash
quarto render
```

**검증 항목:**
- 렌더링 성공/실패 여부
- 경고(warning) 발생 여부
- `docs/` 디렉토리에 출력 파일 생성 확인

**중단 조건:**
- 렌더링 실패 시 → 오류 보고 후 중단
- 심각한 경고 시 → 사용자 확인 요청

### 2단계: 변경사항 확인

렌더링 결과 변경된 파일을 확인한다.

```bash
git diff --stat
```

**보고 내용:**
- 변경된 `.qmd` 파일 목록
- 변경된 `docs/` 파일 목록
- 새로 추가된 파일
- 삭제된 파일

### 3단계: 커밋 (deploy 모드)

변경사항을 커밋한다.

**커밋 메시지 규칙:**
- 콘텐츠 변경: `docs: [챕터명] [작업 내용]`
- 이미지 추가: `assets: [다이어그램 설명] 추가`
- 설정 변경: `config: [변경 내용]`
- 복합 변경: `publish: [주요 변경 요약]`

**커밋 전 확인:**
- `.env`, 인증 정보 등 민감한 파일이 포함되지 않았는지 확인
- 불필요하게 큰 파일(10MB 이상)이 포함되지 않았는지 확인
- `.DS_Store` 등 시스템 파일 제외

### 4단계: 푸시 (deploy 모드)

```bash
git push origin main
```

**중단 조건:**
- 원격 브랜치와 충돌 시 → 보고 후 중단
- 인증 실패 시 → 사용자에게 안내

### 5단계: 배포 확인 (deploy 모드)

GitHub Pages 배포 상태를 확인한다.

```bash
gh run list --limit 3
```

## 출력 형식

### preview 모드

```
🔨 빌드 결과

■ 렌더링: ✅ 성공
  변경 파일: 5개 (.qmd 2, docs/ 3)

■ 변경 내역
  M  73-context-engineering.qmd
  M  images/context-flow.svg
  M  docs/73-context-engineering.html
  M  docs/search.json
  M  docs/sitemap.xml

배포하려면: /publish deploy
```

### deploy 모드

```
🚀 배포 완료

■ 렌더링: ✅ 성공
■ 커밋: ✅ docs: 컨텍스트 엔지니어링 챕터 보강
■ 푸시: ✅ origin/main
■ 배포: ✅ GitHub Pages 업데이트 중

🌐 https://r2bit.com/gpt-coding/
```

## 주의사항
- 푸시 전 반드시 사용자 확인을 받는다.
- force push는 절대 사용하지 않는다.
- `docs/` 디렉토리의 변경은 렌더링 결과이므로 수동 편집하지 않는다.
- 렌더링 실패 시 `/render`로 상세 진단을 권장한다.
- 배포 후 웹사이트에서 결과를 직접 확인할 것을 안내한다.
