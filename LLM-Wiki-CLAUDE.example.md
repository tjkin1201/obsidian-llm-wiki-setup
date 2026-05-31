# LLM Wiki Schema

이 볼트는 Karpathy의 LLM Wiki 패턴을 따릅니다.
Obsidian은 IDE, LLM은 프로그래머, wiki는 코드베이스.

## 볼트 구조

```
raw/            원본 소스 (불변, LLM은 읽기만)
  articles/     웹 기사 (Obsidian Web Clipper)
  papers/       논문, 리포트
  notes/        개인 메모, 미팅 노트
  assets/       이미지, 첨부파일

wiki/           LLM이 생성하고 관리하는 위키
  index.md      전체 목차 (Ingest마다 업데이트)
  log.md        시간순 활동 기록 (append-only)
  entities/     인물, 회사, 제품, 도구 페이지
  concepts/     개념, 기술, 패턴, 방법론 페이지
  sources/      소스별 요약 페이지
  comparisons/  비교 분석 페이지
  synthesis/    종합 분석, 테제, 인사이트

MOC/            Map of Content (카테고리 허브, 기존 유지)
Glossary/       용어 사전 (기존 유지, wiki/entities와 연동)
Daily_Trends/   일일 트렌드 (기존 유지, raw 소스로 활용)
Today_Reading/  일일 읽기 (기존 유지, raw 소스로 활용)
Work/           프로젝트 작업 기록 (기존 유지)
```

## Ingest 워크플로우

새 소스가 들어왔을 때:

1. **읽기**: raw/에 저장된 소스를 읽고 핵심 내용 파악
2. **논의**: 사용자와 핵심 요점, 흥미로운 부분 논의
3. **요약 페이지**: `wiki/sources/` 에 소스 요약 페이지 생성
4. **엔티티 업데이트**: 언급된 인물/회사/도구 → `wiki/entities/` 페이지 생성 또는 업데이트
5. **개념 업데이트**: 핵심 개념/기술 → `wiki/concepts/` 페이지 생성 또는 업데이트
6. **교차참조**: 모든 관련 페이지에 ``[[wikilink]]`` 추가
7. **모순 체크**: 기존 내용과 충돌하면 `> [!warning]` 콜아웃으로 표시
8. **인덱스**: `wiki/index.md` 업데이트
9. **로그**: `wiki/log.md` 에 항목 추가

## Query 워크플로우

사용자가 질문했을 때:

1. `wiki/index.md` 읽어서 관련 페이지 찾기
2. 관련 페이지 읽고 종합 답변 생성
3. 가치 있는 답변은 `wiki/comparisons/` 또는 `wiki/synthesis/` 에 저장
4. 새 페이지 생성했으면 index.md 업데이트

## Lint 워크플로우

주기적 위키 건강검진:

1. 모순: 페이지 간 상충하는 정보 발견 및 표시
2. 갱신: 새 소스가 기존 내용을 대체하면 업데이트
3. 고아: inbound 링크 없는 페이지 발견
4. 누락: 언급되지만 자체 페이지가 없는 개념/엔티티
5. 교차참조: 빠진 `[[wikilink]]` 보충
6. 제안: 새로 조사할 질문이나 소스 추천

## 페이지 템플릿

### 엔티티 페이지 (wiki/entities/)
```yaml
---
type: entity
entity_type: person | company | product | tool
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: []
tags: []
---
```

### 개념 페이지 (wiki/concepts/)
```yaml
---
type: concept
domain: ai | dev | finance | general
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: []
tags: []
---
```

### 소스 요약 (wiki/sources/)
```yaml
---
type: source
source_type: article | paper | video | podcast | book
url: ""
author: ""
date: YYYY-MM-DD
created: YYYY-MM-DD
tags: []
---
```

### 비교/종합 (wiki/comparisons/, wiki/synthesis/)
```yaml
---
type: comparison | synthesis
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: []
tags: []
---
```

## 규칙

- raw/ 파일은 절대 수정하지 않는다
- wiki/ 파일은 LLM이 소유한다. 사람은 읽기 위주
- 모든 wiki 페이지에 frontmatter 필수
- 교차참조는 `[[wikilink]]` 형식 사용
- 날짜는 YYYY-MM-DD 형식
- 한국어로 작성 (기술 용어는 영어 유지)
- 기존 MOC/, Glossary/, Daily_Trends/ 구조와 자연스럽게 연동
- Dataview 쿼리 호환을 위해 frontmatter type 필드 일관되게 유지

## 기존 데이터 연동

- `Daily_Trends/` 노트 → Ingest 시 raw 소스로 취급 가능
- `Today_Reading/` 노트 → Ingest 시 raw 소스로 취급 가능
- `Glossary/` 항목 → `wiki/entities/` 또는 `wiki/concepts/`와 `[[wikilink]]`로 연결
- `MOC/` → 위키 카테고리 허브로 활용, wiki 페이지를 MOC에 링크
- `Work/` → 프로젝트별 synthesis나 comparison 페이지와 연결
