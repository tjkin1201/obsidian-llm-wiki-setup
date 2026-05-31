# Obsidian LLM Wiki 셋업 — 공유용 설정 번들

🌏 **한국어** · [English](./README.en.md)

![LLM Wiki 지식 그래프 — 08_Hub](./assets/graph-08hub.svg)

> 위 그림은 이 셋업으로 만든 08_Hub LLM Wiki를 **graphify**로 그린 지식 그래프 (96개 노드 · 7개 커뮤니티). 색은 커뮤니티(주제 군집), 선은 노트 간 연결. 이 셋업이 만들어내는 결과물의 예시다.

Karpathy **LLM Wiki 패턴** + PARA 폴더 + Claude Code 연동 Obsidian 셋업을 그대로 복제하는 번들입니다.
**플러그인 목록 + 코어/테마 설정 + 18개 플러그인의 세부 설정 + 템플릿 + LLM Wiki 스키마**까지 포함해 **약 95% 동일** 재현이 됩니다. **API 키·인증서·개인 데이터만 제외**(받는 사람이 자기 키 입력).

## 📦 번들 내용

```
obsidian-llm-wiki-bundle/
├── README.md / README.en.md       # 소개 (한/영)
├── GUIDE.md / GUIDE.en.md         # 전체 셋업 가이드 (한/영)
├── plugins.txt                    # 커뮤니티 플러그인 ID 31개
├── LLM-Wiki-CLAUDE.example.md     # LLM Wiki 스키마 예시 (07/08의 CLAUDE.md)
├── templates/                     # Templater 템플릿 3종 (daily/research/trend)
├── assets/graph-08hub.svg         # 지식 그래프 미리보기
└── .obsidian/
    ├── community-plugins.json     # 활성 커뮤니티 플러그인 목록
    ├── core-plugins.json          # 코어 플러그인 on/off
    ├── appearance.json            # 테마(Blue Topaz) + CSS 스니펫
    ├── app.json · daily-notes.json · types.json   # 핵심 설정
    ├── snippets/                  # CSS 스니펫 2종
    └── plugins/<18개>/data.json   # 플러그인별 세부 설정 (비밀 없는 것만)
```

플러그인 세부 설정 포함분(18): dataview · tasks · linter · templater · auto-note-mover · icon-folder · calendar · admonition · minimal-settings · canvas-mindmap · omnisearch · excalidraw · terminal · open-in-terminal · homepage · table-editor · smart-connections · brat

## 🚫 의도적으로 뺀 것 (비밀·개인정보) — 5종만

| 제외 | 이유 | 받는 사람 조치 |
|---|---|---|
| `gemini-assistant`·`obsidian-local-rest-api`·`copilot` data.json | **실제 API 키·인증서** 포함 | 각자 자기 키 입력 |
| `obsidian42-brat`은 포함하되 PAT는 빈값 | GitHub 토큰 비움 | 필요 시 자기 PAT |
| `hermes-console`·`cc-obsidian` data.json | 개인 세션·대화 데이터 | (선택 플러그인) |
| `workspace*.json` · `graph.json` · `bookmarks.json` · `hermes/` | 개인 레이아웃·좌표·북마크 | 자동 생성됨 |

→ 즉 **설정의 대부분은 이미 들어있고**, 받는 사람은 위 3개 AI 플러그인에 자기 키만 넣으면 됩니다.

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

**macOS / Linux**
```bash
pip install graphifyy          # (또는 pip3) 지식 그래프 시각화
npm install -g @tobilu/qmd     # 로컬 마크다운 검색엔진
```
**Windows (PowerShell)**
```powershell
py -m pip install graphifyy    # 또는 python -m pip install graphifyy
npm install -g "@tobilu/qmd"
```
> NotebookLM 연동은 `nlm` (선택, 모든 OS 동일).

## 📖 자세한 설명
- **플러그인 31개 개별 설명**(무엇·왜·어떻게) → [PLUGINS.md](./PLUGINS.md)
- 전체 셋업·워크플로우 → `GUIDE.md` 참조 (플러그인 32개 카테고리별 용도, 수집→정리→질의→점검→시각화 워크플로우, Gold In Gold Out 규율).

## 🖥 OS별 참고 (macOS · Windows · Linux)

Obsidian·플러그인·테마·`.obsidian/*.json`은 **3개 OS 모두 동일**합니다. 차이는 아래뿐:

| 항목 | macOS | Windows | Linux |
|------|-------|---------|-------|
| `.obsidian/` 폴더 보기 | Finder에서 `⌘⇧.` | 탐색기 → 보기 → "숨긴 항목" 체크 | 파일관리자 `Ctrl+H` |
| Python 실행 | `pip` / `pip3` | `py -m pip` | `pip3` |
| 설정 복사 | Finder 드래그 또는 `cp` | 탐색기 드래그 또는 `copy` | 파일관리자 드래그 또는 `cp` |
| 터미널 | Terminal/iTerm (zsh) | PowerShell | bash/zsh |

- **`.obsidian/` 위치**: OS 무관하게 **vault 폴더 안**에 있습니다(`<내vault>/.obsidian/`). 숨김 폴더라 위 방법으로 표시 후 이 번들의 파일을 덮어쓰면 됩니다.
- **권장(가장 쉬움)**: CLI 없이 → Obsidian 안에서 플러그인을 직접 설치(2단계) + 설정만 파일관리자로 복사(3단계). CLI 도구(graphify·qmd)는 **선택**이며 AI 자동화를 원할 때만.
- Windows에서 `obsidian-git` 사용 시 Git for Windows(https://git-scm.com) 설치 필요. macOS는 Xcode CLT, Linux는 `apt/dnf install git`.

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
