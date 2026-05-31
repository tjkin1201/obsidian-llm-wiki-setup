# Obsidian LLM Wiki Setup — Full Guide

🌏 [한국어](./GUIDE.md) · **English**

> Replicate this whole Obsidian setup (plugins + settings + folder structure + AI workflow) from a single document.

## Definition (one line)

PARA folders + Karpathy's **LLM Wiki pattern** (Obsidian = IDE · LLM = programmer · wiki = codebase) + Claude Code integration — a knowledge system that **humans and AI read and write together**.

## Why this setup

A plain notes app turns into a junkyard as knowledge piles up — search stops working. This setup keeps it searchable via ① **atomic notes + a wikilink graph**, ② **the AI handling organization, cross-referencing, and updates** (LLM Wiki), and ③ **Claude Code / CLI automating capture → organize → query → visualize**. The point is not the number of plugins but the flow: *capture (Web Clipper) → organize (ingest) → query → lint → visualize (graphify)*.

---

## A. Folder structure (PARA + LLM Wiki)

```
vault/
├── 00_Meta/          # templates, inbox, attachments (Files/, Inbox/, Templates/)
├── 000-Inbox/        # quick capture
├── 01_Daily/         # daily notes (daily/)
├── 02_Work/          # project work
├── 03_Learning/      # learning & guides (this doc lives here)
├── 04_Creation/      # creative output
├── 05_Resources/     # reference material
├── 06_Archive/       # archive (excluded from search)
├── 07_InvestWiki/    # LLM Wiki instance #1 — investing domain
├── 08_Hub/           # LLM Wiki instance #2 — AI/dev meta
└── 09_Reference/     # rules & principles (_정리원칙.md)
```

Each LLM Wiki (`07_*`, `08_*`) uses a 3-layer structure: `raw/` (immutable sources) → `wiki/` (LLM-generated) → `Output/` (shareable) + `CLAUDE.md` (the schema).

## B. Community plugins (32, by category)

> Install: Settings → Community plugins → Browse, search each ID below. (Use BRAT for unlisted/beta plugins.)

**Knowledge graph & search (core)**
- `dataview` — query notes like a database (auto MOCs/indexes)
- `smart-connections` — embedding-based related-note suggestions
- `omnisearch` — full-text fuzzy search
- `obsidian-local-rest-api` — REST API for external (AI/CLI) access to the vault

**AI integration**
- `mcp-tools` — expose Obsidian as an MCP server (agents operate the vault)
- `cc-obsidian` — Claude Code ↔ Obsidian bridge
- `copilot` — in-vault AI chat/writing
- `gemini-assistant` — Gemini integration
- `hermes-console` — Hermes agent console (in-app note context)

**Capture & organize**
- `obsidian-clipper` — web clipper (purposeful capture into raw/; the entry point of the LLM Wiki)
- `obsidian-importer` — import from other apps (Notion, etc.)
- `obsidian-auto-note-mover` — rule-based auto-filing
- `obsidian-linter` — auto-clean frontmatter/format on save
- `obsidian-sort-and-permute-lines` — line sorting

**Visualization & diagrams**
- `obsidian-excalidraw-plugin` — sketches/diagrams
- `canvas-mindmap` / `advanced-canvas` — canvas mindmap enhancements
- `obsidian-mind-map` — note → mindmap
- `obsidian-chartsview-plugin` — charts
- `marp` / `marp-slides` — markdown → slides

**Tasks & schedule**
- `obsidian-tasks-plugin` — checkbox task management (queries)
- `obsidian-kanban` — kanban boards
- `obsidian-calendar-plugin` / `google-calendar` — calendar & Google sync

**File formats & tools**
- `qmd-as-md-obsidian` — qmd (local markdown search engine) integration
- `table-editor-obsidian` — table editing
- `templater-obsidian` — powerful templates (templates folder: `08_Hub/templates`)

**UI & styling**
- `obsidian-minimal-settings` / `obsidian-style-settings` — theme detail settings
- `obsidian-icon-folder` — folder icons
- `obsidian-scroll-to-top-plugin` — scroll to top
- `homepage` — set a start page
- `open-in-terminal` / `terminal` — terminal from the vault (CLI workflow)

**Version control & extensions**
- `obsidian-git` — auto commit/backup the vault (sharing & history)
- `obsidian42-brat` — installer for unlisted/beta plugins

## C. Core plugins (enabled)

file-explorer · global-search · switcher · **graph** · backlink · **canvas** · outgoing-link · tag-pane · **properties** · page-preview · **daily-notes** · **templates** · note-composer · command-palette · **slash-command** · bookmarks · outline · word-count · **slides** · file-recovery · **bases** · webviewer · sync · publish
(off: footnotes, zk-prefixer, random-note, audio-recorder, workspaces, markdown-importer)

## D. Theme & appearance

- Theme: **Blue Topaz** (`cssTheme`)
- 2 CSS snippets: `multi-column-callout`, `cute-vibes` — drop into `.obsidian/snippets/` and enable under Settings → Appearance

## E. Core settings (Settings → Files and links)

```
Attachment folder:      00_Meta/Files
New note location:      00_Meta/Inbox (specified folder)
Auto-update links:      ON (keep links when files move)
Trash:                  local (.trash)
Show line numbers:      ON
Search exclude (userIgnore): 06_Archive/ · __pycache__/ · node_modules/ · venv/ · .trio_backup_
```
- Daily notes: folder `daily`, format `YYYY-MM-DD`, template `00_Meta/Templates/Template_Daily_Note`
- Templater templates folder: `08_Hub/templates`

## F. AI / CLI workflow (the heart)

CLI tools outside Obsidian run together with the plugins:

| Stage | Tool | What it does |
|------|------|--------------|
| Capture | `obsidian-clipper` (5 templates) | clip web/youtube/paper/book/podcast into `raw/` (purpose note required = Gold In) |
| Organize | Claude Code `/wiki-ingest`·`/ingest` | raw → wiki pages + cross-refs + index/log update |
| Query | `/wiki-query`·`/query` + `smart-connections` | synthesize answers from the wiki; file good answers back |
| Lint | `/wiki-lint` | check broken links, orphans, duplicates, stale notes |
| Search | `qmd` (CLI) + `qmd-as-md-obsidian` | local markdown search index |
| Visualize | `graphify` (CLI) | vault → knowledge graph (HTML/JSON/report) |
| External access | `obsidian-local-rest-api` + `mcp-tools` | AI agents read/write the vault directly |

> Key discipline **Gold In, Gold Out**: don't dump everything in — only ingest what you noted a *purpose* for. No-intent data is noise.

## Replication checklist

1. **Install Obsidian** → create a new vault
2. **Folder structure** as in A (00_Meta ~ 09_Reference)
3. **Enable community plugins** → install the 32 in B (minimal core: dataview · templater · obsidian-git · obsidian-clipper · smart-connections · omnisearch)
4. **Theme** install Blue Topaz + apply the 2 CSS snippets
5. **Core settings** per E (attachment folder, new note location, search excludes)
6. **LLM Wiki schema**: write a `CLAUDE.md` (raw/wiki/Output 3-layer rules) in `07_/08_`
7. **CLI tools**: `pip install graphifyy`, `npm i -g @tobilu/qmd`, NotebookLM via `nlm` (optional)
8. **Claude Code skills**: `/wiki-ingest`·`/wiki-query`·`/wiki-lint`·`/graphify` (share the skills folder or run `graphify install`)
9. **First cycle**: clip 1 item with the web clipper → `/wiki-ingest` → ask a question with `/wiki-query` → check the graph with `/graphify`

## Example — a daily flow

In the morning, clip one article into `raw/` (purpose: "for judging the semiconductor cycle") → tell Claude Code "ingest what I just clipped" → it creates a source page + updates related stock pages → ask "where are we in the semiconductor cycle?" → the answer accumulates into the wiki → weekly `/wiki-lint` + `/graphify` to review and visualize.

---
Source: extracted from a real vault `.obsidian` config (2026-05-31), secrets stripped.
