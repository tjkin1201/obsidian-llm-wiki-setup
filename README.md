# Obsidian LLM Wiki 셋업 — 공유용 설정 번들

🌏 **한국어** · [English](./README.en.md)

![LLM Wiki 지식 그래프 — 08_Hub](./assets/graph-08hub.svg)

> 위 그림은 이 셋업으로 만든 08_Hub LLM Wiki를 **graphify**로 그린 지식 그래프 (96개 노드 · 7개 커뮤니티). 색은 커뮤니티(주제 군집), 선은 노트 간 연결. 이 셋업이 만들어내는 결과물의 예시다.

Karpathy **LLM Wiki 패턴** + PARA 폴더 + Claude Code 연동 Obsidian 셋업을 그대로 복제하는 번들입니다.
**비밀(API 키·토큰·개인 워크스페이스)은 모두 제외**했습니다. 안전하게 공유 가능합니다.

## 📦 번들 내용

```
obsidian-llm-wiki-bundle/
├── README.md                  # 이 파일
├── GUIDE.md                   # 전체 셋업 가이드 (폴더구조·플러그인·워크플로우·복제 체크리스트)
├── plugins.txt                # 커뮤니티 플러그인 ID 31개 (한 줄당 1개)
└── .obsidian/
    ├── community-plugins.json # 활성 커뮤니티 플러그인 목록
    ├── core-plugins.json      # 코어 플러그인 on/off
    ├── appearance.json        # 테마(Blue Topaz) + CSS 스니펫
    ├── app.json               # 에디터/파일 핵심 설정
    ├── daily-notes.json       # 데일리 노트 설정
    ├── types.json             # 속성 타입
    └── snippets/              # CSS 스니펫 2종
```

## 🚫 의도적으로 뺀 것 (비밀·개인정보)

| 제외 파일 | 이유 |
|---|---|
| `plugins/*/data.json` | local-rest-api·mcp-tools·copilot·gemini·hermes 등에 **API 키/토큰** 포함 가능 |
| `workspace.json` / `workspace-mobile.json` | 개인 창 레이아웃·열어둔 파일 경로 |
| `hermes/`, `bookmarks.json`, `graph.json` | 개인 데이터·북마크·그래프 좌표 |

→ 받는 사람은 플러그인 설치 후 **각자 자기 키로** 설정합니다.

## 🛠 설치 방법

### 1) Obsidian 설치 + 새 vault 생성
https://obsidian.md

### 2) 커뮤니티 플러그인 켜기
설정 → 커뮤니티 플러그인 → "제한 모드 끄기" → 찾아보기에서 `plugins.txt`의 ID를 하나씩 설치.
(비공식/베타 플러그인은 `obsidian42-brat`로 설치)

**최소 핵심 6개만으로도 시작 가능**: `dataview` · `templater-obsidian` · `obsidian-git` · `obsidian-clipper` · `smart-connections` · `omnisearch`

### 3) 설정 적용
이 번들의 `.obsidian/` 안 json들을 새 vault의 `.obsidian/`에 복사(덮어쓰기)한 뒤 Obsidian 재시작.
⚠️ 새 vault에 이미 있는 `.obsidian/`을 덮어쓰므로, 빈 vault에서 하길 권장.

### 4) 테마
설정 → 외관 → 테마 → **Blue Topaz** 설치. `snippets/`의 css 2개를 새 vault `.obsidian/snippets/`에 넣고 외관에서 활성화.

### 5) 폴더 구조 + LLM Wiki
`GUIDE.md`의 "복제 체크리스트" 9단계를 따라가세요. (폴더 생성 → LLM Wiki CLAUDE.md → CLI 도구 → 첫 사이클)

### 6) CLI 도구 (선택, AI 워크플로우용)
```bash
pip install graphifyy          # 지식 그래프 시각화
npm install -g @tobilu/qmd     # 로컬 마크다운 검색엔진
# NotebookLM 연동은 nlm (선택)
```

## 📖 자세한 설명
→ `GUIDE.md` 참조 (플러그인 32개 카테고리별 용도, 수집→정리→질의→점검→시각화 워크플로우, Gold In Gold Out 규율).

## 🐙 GitHub에 올리기

```bash
cd ~/Desktop/obsidian-llm-wiki-bundle
gh repo create obsidian-llm-wiki-setup --public --source=. --push
```

`.gitignore`가 비밀 파일(plugins/*/data.json·workspace·hermes·local-rest-api 등)을 자동 제외하므로, 나중에 본인 vault의 전체 `.obsidian/`을 복사해 넣어도 키가 새지 않습니다.

## 📄 License

MIT — 자유롭게 사용·수정·재배포 가능. 자세한 건 [LICENSE](./LICENSE).

---
출처: 2026-05-31 기준 실제 vault `.obsidian` 설정에서 비밀 제거 후 추출.
