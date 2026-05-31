# Obsidian LLM Wiki Setup — Shareable Config Bundle

🌏 [한국어](./README.md) · **English**

![LLM Wiki knowledge graph — 08_Hub](./assets/graph-08hub.svg)

> The image above is the 08_Hub LLM Wiki built with this setup, rendered by **graphify** (96 nodes · 7 communities). Colors = communities (topic clusters), lines = links between notes. An example of what this setup produces.

Replicate this Obsidian setup: Karpathy's **LLM Wiki pattern** + PARA folders + Claude Code integration.
**All secrets (API keys, tokens, personal workspace) are removed.** Safe to share.

## 📦 What's inside

```
obsidian-llm-wiki-setup/
├── README.md / README.en.md   # this guide (KO / EN)
├── GUIDE.md / GUIDE.en.md      # full setup guide (folders, plugins, workflow, checklist) — KO / EN
├── plugins.txt                 # 31 community plugin IDs (one per line)
└── .obsidian/
    ├── community-plugins.json  # enabled community plugins
    ├── core-plugins.json       # core plugin on/off
    ├── appearance.json         # theme (Blue Topaz) + CSS snippets
    ├── app.json                # editor/file core settings
    ├── daily-notes.json        # daily note config
    ├── types.json              # property types
    └── snippets/               # 2 CSS snippets
```

## 🚫 Intentionally excluded (secrets / personal)

| Excluded | Reason |
|---|---|
| `plugins/*/data.json` | may contain **API keys / tokens** (local-rest-api, mcp-tools, copilot, gemini, hermes) |
| `workspace.json` / `workspace-mobile.json` | personal window layout & open file paths |
| `hermes/`, `bookmarks.json`, `graph.json` | personal data, bookmarks, graph coordinates |

→ After installing plugins, each user configures **their own keys**.

## 🛠 Installation

### 1) Install Obsidian + create a new vault
https://obsidian.md

### 2) Enable community plugins
Settings → Community plugins → "Turn off restricted mode" → Browse and install each ID from `plugins.txt`.
(Use `obsidian42-brat` for beta/unlisted plugins.)

**Minimal core 6 to start**: `dataview` · `templater-obsidian` · `obsidian-git` · `obsidian-clipper` · `smart-connections` · `omnisearch`

### 3) Apply settings
Copy the `.obsidian/` json files from this bundle into your new vault's `.obsidian/`, then restart Obsidian.
⚠️ This overwrites the new vault's `.obsidian/` — best done on an empty vault.

### 4) Theme
Settings → Appearance → Themes → install **Blue Topaz**. Put the 2 css files from `snippets/` into your vault's `.obsidian/snippets/` and enable them.

### 5) Folders + LLM Wiki
Follow the "Replication checklist" in [`GUIDE.en.md`](./GUIDE.en.md) — 9 steps (folders → LLM Wiki CLAUDE.md → CLI tools → first cycle).

### 6) CLI tools (optional, for the AI workflow)
```bash
pip install graphifyy          # knowledge-graph visualization
npm install -g @tobilu/qmd     # local markdown search engine
# NotebookLM integration via `nlm` (optional)
```

## 🔄 The core workflow

| Stage | Tool | What it does |
|------|------|--------------|
| Capture | `obsidian-clipper` (5 templates) | clip web/youtube/paper/book/podcast into `raw/` (with a purpose note = Gold In) |
| Organize | Claude Code `/wiki-ingest` | raw → wiki pages + cross-refs + index/log update |
| Query | `/wiki-query` + `smart-connections` | synthesize answers from the wiki, file good answers back |
| Lint | `/wiki-lint` | check broken links, orphans, duplicates, stale notes |
| Search | `qmd` + `qmd-as-md-obsidian` | local markdown search index |
| Visualize | `graphify` | vault → knowledge graph (HTML/JSON/report) |
| External access | `obsidian-local-rest-api` + `mcp-tools` | let AI agents read/write the vault |

> Key discipline **Gold In, Gold Out**: only ingest what you noted a *purpose* for. No-intent data is noise.

## 🐙 Push to GitHub (already done here)

```bash
gh repo create obsidian-llm-wiki-setup --public --source=. --push
```
`.gitignore` auto-excludes secret files, so even if you later copy your full `.obsidian/`, keys won't leak.

## 📄 License

MIT — free to use, modify, redistribute. See [LICENSE](./LICENSE).

---
Source: extracted from a real vault `.obsidian` config (2026-05-31), secrets stripped.
