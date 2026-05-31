---
title: Obsidian LLM Wiki 셋업 공유 가이드
created: 2026-05-31
type: 가이드
domain: Learning
tags: [obsidian, llm-wiki, setup-guide, plugins, claude-code, 공유용]
related: [[L007_AI_3Layer_Workflow_초보자_가이드]]
status: 씨앗
source: self
aliases: [옵시디언 셋업 가이드, Obsidian Setup Share]
---

# Obsidian LLM Wiki 셋업 공유 가이드

🌏 **한국어** · [English](./GUIDE.en.md)

> 이 문서 하나로 내 Obsidian 셋업(플러그인 + 설정 + 폴더 구조 + AI 워크플로우)을 **누구나 동일하게 복제**할 수 있다. 복사해서 공유 가능.

## 정의 (한 줄)

PARA 폴더 구조 + Karpathy의 **LLM Wiki 패턴**(Obsidian=IDE · LLM=프로그래머 · wiki=코드베이스) + Claude Code 연동을 합친, **사람과 AI가 같이 읽고 쓰는 지식 시스템** 셋업.

## 맥락 — 왜 이 셋업인가

일반 메모 앱은 지식이 쌓일수록 검색이 안 되는 쓰레기장이 된다. 이 셋업은 ① **원자 노트 + wikilink 그래프**로 검색성을 유지하고, ② **AI가 정리·교차참조·갱신을 전담**(LLM Wiki)하며, ③ **Claude Code/CLI로 수집→정리→질의→시각화**를 자동화한다. 핵심은 플러그인 개수가 아니라 *수집(Web Clipper) → 정리(ingest) → 질의(query) → 점검(lint) → 시각화(graphify)* 흐름이다.

---

## A. 폴더 구조 (PARA 변형 + LLM Wiki)

```
vault/
├── 00_Meta/          # 템플릿·인박스·첨부 (Files/, Inbox/, Templates/)
├── 000-Inbox/        # 빠른 캡처
├── 01_Daily/         # 데일리 노트 (daily/)
├── 02_Work/          # 프로젝트 작업
├── 03_Learning/      # 학습·가이드 (이 문서 위치)
├── 04_Creation/      # 창작 산출물
├── 05_Resources/     # 참고 자료
├── 06_Archive/       # 보관 (검색 제외)
├── 07_InvestWiki/    # LLM Wiki 인스턴스 ① 투자 도메인
├── 08_Hub/           # LLM Wiki 인스턴스 ② AI/개발 메타
└── 09_Reference/     # 규칙·정리원칙 (_정리원칙.md)
```

각 LLM Wiki(`07_*`, `08_*`)는 `raw/`(원본 불변) → `wiki/`(LLM 생성) → `Output/`(공유용) 3계층 + `CLAUDE.md`(스키마) 구조. 자세한 건 [[L007_AI_3Layer_Workflow_초보자_가이드]] 및 각 폴더의 CLAUDE.md.

## B. 커뮤니티 플러그인 (32개 — 카테고리별)

> 설치: 설정 → 커뮤니티 플러그인 → 찾아보기에서 아래 ID 검색. (BRAT은 비공식 플러그인용)

**지식 그래프·검색 (핵심)**
- `dataview` — 노트를 DB처럼 쿼리 (MOC·인덱스 자동화)
- `smart-connections` — 임베딩 기반 관련 노트 추천
- `omnisearch` — 전문(full-text) 퍼지 검색
- `obsidian-local-rest-api` — 외부(AI·CLI)에서 vault 접근하는 REST API

**AI 연동**
- `mcp-tools` — Obsidian을 MCP 서버로 노출 (Claude 등 에이전트가 vault 조작)
- `cc-obsidian` — Claude Code ↔ Obsidian 브리지
- `copilot` — vault 내 AI 채팅/작성
- `gemini-assistant` — Gemini 연동
- `hermes-console` — Hermes 에이전트 콘솔 (앱 내 노트 컨텍스트)

**수집·정리**
- `obsidian-clipper` — 웹 클리퍼 (raw/로 목적 있는 수집; LLM Wiki의 입구)
- `obsidian-importer` — 타 앱(노션 등) 가져오기
- `obsidian-auto-note-mover` — 규칙 기반 노트 자동 분류
- `obsidian-linter` — 저장 시 frontmatter·형식 자동 정리
- `obsidian-sort-and-permute-lines` — 줄 정렬

**시각화·다이어그램**
- `obsidian-excalidraw-plugin` — 손그림·다이어그램
- `canvas-mindmap` / `advanced-canvas` — 캔버스 마인드맵 강화
- `obsidian-mind-map` — 노트→마인드맵
- `obsidian-chartsview-plugin` — 차트
- `marp` / `marp-slides` — 마크다운 → 슬라이드

**할 일·일정**
- `obsidian-tasks-plugin` — 체크박스 작업 관리(쿼리)
- `obsidian-kanban` — 칸반 보드
- `obsidian-calendar-plugin` / `google-calendar` — 캘린더·구글 연동

**파일 형식·도구**
- `qmd-as-md-obsidian` — qmd(로컬 마크다운 검색엔진) 연동
- `table-editor-obsidian` — 표 편집
- `templater-obsidian` — 강력한 템플릿 (템플릿 폴더: `08_Hub/templates`)

**UI·꾸미기**
- `obsidian-minimal-settings` / `obsidian-style-settings` — 테마 세부 설정
- `obsidian-icon-folder` — 폴더 아이콘
- `obsidian-scroll-to-top-plugin` — 맨 위로
- `homepage` — 시작 페이지 지정
- `open-in-terminal` / `terminal` — vault에서 터미널 (CLI 워크플로우)

**버전관리·확장**
- `obsidian-git` — vault 자동 커밋/백업 (공유·이력)
- `obsidian42-brat` — 비공식/베타 플러그인 설치기

## C. 코어 플러그인 (활성)

file-explorer · global-search · switcher · **graph** · backlink · **canvas** · outgoing-link · tag-pane · **properties** · page-preview · **daily-notes** · **templates** · note-composer · command-palette · **slash-command** · bookmarks · outline · word-count · **slides** · file-recovery · **bases** · webviewer · sync · publish
(footnotes·zk-prefixer·random-note·audio-recorder·workspaces·markdown-importer는 끔)

## D. 테마·외관

- 테마: **Blue Topaz** (`cssTheme`)
- CSS 스니펫 2개: `multi-column-callout`(다단 콜아웃), `cute-vibes`(감성 스타일) — `.obsidian/snippets/`에 넣고 설정→외관에서 활성

## E. 핵심 설정 (설정 → 파일 및 링크)

```
첨부 파일 폴더:      00_Meta/Files
새 노트 위치:        00_Meta/Inbox (지정 폴더)
링크 자동 업데이트:   ON (파일 이동 시 링크 유지)
휴지통:              로컬 (.trash)
줄 번호 표시:        ON
검색 제외(userIgnore): 06_Archive/ · __pycache__/ · node_modules/ · venv/ · .trio_backup_
```
- 데일리 노트: 폴더 `daily`, 형식 `YYYY-MM-DD`, 템플릿 `00_Meta/Templates/Template_Daily_Note`
- Templater 템플릿 폴더: `08_Hub/templates`

## F. AI·CLI 워크플로우 (이 셋업의 심장)

Obsidian 밖 CLI 도구 + 플러그인이 함께 돈다:

| 단계 | 도구 | 하는 일 |
|------|------|--------|
| 수집 | `obsidian-clipper` 템플릿 5종 | 웹/유튜브/논문/책/팟캐스트를 `raw/`로 (목적 메모 필수 = Gold In) |
| 정리 | Claude Code `/wiki-ingest`·`/ingest` | raw → wiki 페이지 생성 + 교차참조 + index·log 갱신 |
| 질의 | `/wiki-query`·`/query` + `smart-connections` | wiki 기반 답변 합성, 좋은 답은 wiki에 file back |
| 점검 | `/wiki-lint` | 깨진 링크·고아·중복·stale 점검 |
| 검색엔진 | `qmd` (CLI) + `qmd-as-md-obsidian` | 로컬 마크다운 검색 인덱스 |
| 시각화 | `graphify` (CLI) | vault → 지식 그래프(HTML·JSON·리포트) |
| 외부접근 | `obsidian-local-rest-api` + `mcp-tools` | AI 에이전트가 vault를 직접 읽고 씀 |

> 핵심 규율 **Gold In, Gold Out**: 아무거나 긁어넣지 말고 "왜 수집했나"를 적은 것만 인제스트. 의도 없는 데이터는 노이즈.

## 복제 체크리스트 (따라하기)

1. **Obsidian 설치** → 새 vault 생성
2. **폴더 구조** 위 A처럼 생성 (00_Meta ~ 09_Reference)
3. **커뮤니티 플러그인 ON** → B의 32개 설치 (최소 핵심: dataview·templater·obsidian-git·obsidian-clipper·smart-connections·omnisearch)
4. **테마** Blue Topaz 설치 + CSS 스니펫 2개 적용
5. **핵심 설정** E대로 (첨부 폴더·새 노트 위치·검색 제외)
6. **LLM Wiki 스키마**: `07_/08_`에 `CLAUDE.md`(raw/wiki/Output 3계층 규칙) 작성 — [[L007_AI_3Layer_Workflow_초보자_가이드]] 참조
7. **CLI 도구**: `pip install graphifyy`, `npm i -g @tobilu/qmd`, NotebookLM은 `nlm` (선택)
8. **Claude Code 스킬**: `/wiki-ingest`·`/wiki-query`·`/wiki-lint`·`/graphify` (스킬 폴더 공유 또는 graphify install)
9. **첫 사이클**: 웹 클리퍼로 1건 수집 → `/wiki-ingest` → `/wiki-query`로 질문 → `/graphify`로 그래프 확인

## 예시 — 하루 흐름

아침에 기사 1개를 웹 클리퍼로 `raw/`에 저장(목적: "반도체 사이클 판단용") → Claude Code에 "방금 클립한 거 인제스트해줘" → wiki에 source 페이지 + 관련 종목 페이지 갱신 → "지금 반도체 사이클 어디야?" 질의 → 답변이 wiki에 축적 → 주 1회 `/wiki-lint` + `/graphify`로 점검·시각화.

## 관련 노트

- [[L007_AI_3Layer_Workflow_초보자_가이드]] — 3-Layer 워크플로우 입문
- 각 LLM Wiki의 `CLAUDE.md` — 도메인별 스키마
- [[_정리원칙]] — vault 노트 작성 5원칙

## 출처

- self (2026-05-31 현재 vault `.obsidian` 설정 기준 정리)
- Karpathy LLM Wiki 패턴, graphify/qmd/nlm 공식 도구
