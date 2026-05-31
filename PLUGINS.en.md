# Plugin Reference — What · Why · How

🌏 [한국어](./PLUGINS.md) · **English**

The 31 community plugins enabled in this setup, each as **what it does / why / how to use**. Install IDs in code.

---

## 🧠 Knowledge graph & search (the core)

- **`dataview`** — Query notes' frontmatter/tags/links **like a database** → tables/lists/calendars. *Why*: auto-generate MOC/index pages and dynamic lists. *How*: a ` ```dataview ` block, e.g. `TABLE file.mtime FROM "03_Learning" SORT file.mtime DESC`.
- **`smart-connections`** — Embedding-based **related-note suggestions** in a side panel. *Why*: surfaces semantically similar notes even without links. *How*: open a note → related notes appear (first run builds embeddings).
- **`omnisearch`** — **Full-text fuzzy search** (typos, partial, camelCase). *Why*: smarter than default search. *How*: hotkey → search box; can index PDFs/images in settings.
- **`obsidian-local-rest-api`** 🔑 — A **REST API server** to read/write the vault over HTTP. *Why*: lets AI agents/CLI operate your notes. *How*: generate an API key in settings (your own). *(excluded from bundle — secret)*
- **`mcp-tools`** — Exposes Obsidian as an **MCP server** for agents (e.g. Claude). *Why*: AI runs vault tasks directly. *How*: works with local-rest-api; register in your MCP client.

## 🤖 AI integration

- **`copilot`** 🔑 — **In-vault AI chat/writing** (OpenAI/Anthropic/Gemini keys). *Why*: ask/summarize/generate with notes as context. *How*: enter your API key, use the chat panel. *(key excluded)*
- **`gemini-assistant`** 🔑 — Call **Gemini** on selection/document. *How*: enter your Gemini API key, run the command. *(key excluded)*
- **`cc-obsidian`** — **Claude Code ↔ Obsidian bridge** (by this setup's author, reallygood83). *How*: install via BRAT (`reallygood83/cc-obsidian`).
- **`hermes-console`** — In-app **Hermes agent console** (terminal-style). Personal infra, optional. *(personal data excluded)*

## 📥 Capture & organize (LLM Wiki entry)

- **`obsidian-clipper`** — Clip web/youtube/papers as **markdown** into the vault. *Why*: the *capture (raw)* stage of the LLM Wiki — save with a purpose note = Gold In. *How*: browser extension + 5 templates → save to `raw/`.
- **`obsidian-importer`** — Import from **Notion/Evernote/HTML**, etc. *How*: Command palette → Import.
- **`obsidian-auto-note-mover`** — **Auto-file notes by tag/regex rules**. *Why*: tidy the inbox automatically (this setup: `#insight`→`01_Daily/Insights`). *How*: define folder↔tag rules in settings.
- **`obsidian-linter`** — **Auto-format frontmatter/markdown on save** (YAML order, spacing, headings). *Why*: the key to consistency across thousands of notes. *How*: toggle rules; apply on save or via command.
- **`obsidian-sort-and-permute-lines`** — Sort/shuffle/reverse selected **lines**. *How*: run from command palette.

## 📊 Visualization & diagrams

- **`obsidian-excalidraw-plugin`** — **Hand-drawn diagrams** (Excalidraw) inside the vault. *How*: create an Excalidraw file; embed in notes.
- **`canvas-mindmap` / `advanced-canvas`** — Enhance core Canvas with **mindmap shortcuts, auto-layout, node styles**. *How*: in a canvas, Tab/Enter to branch nodes.
- **`obsidian-mind-map`** — Render markdown headings as a **mindmap**. *How*: command → Mind Map view.
- **`obsidian-chartsview-plugin`** — Visualize data as **charts** (bar/line/pie). *How*: a ` ```chart ` block; combine with dataview.
- **`marp` / `marp-slides`** — Markdown → **presentation slides** (Marp). *How*: `---` separates slides; preview/export PDF/PPT.

## ✅ Tasks & schedule

- **`obsidian-tasks-plugin`** — Add **due/priority/recurrence** to checkboxes + query them. *How*: `- [ ] task 📅 2026-06-01` + a ` ```tasks ` block.
- **`obsidian-kanban`** — Notes as **Kanban boards** (To Do/Doing/Done). *How*: create a Kanban board, drag cards.
- **`obsidian-calendar-plugin`** — Sidebar **calendar** + quick daily-note nav. *How*: click a date.
- **`google-calendar`** — **Google Calendar integration** (view/create events). *How*: authenticate your Google account.

## 🗂 File formats & tools

- **`templater-obsidian`** — Powerful **template engine** (dates, variables, scripts). *Why*: consistent daily/research notes (templates folder `08_Hub/templates`; 3 examples in `templates/`). *How*: `<% tp.date.now() %>` syntax.
- **`qmd-as-md-obsidian`** — Work with **qmd** (local markdown search engine) files in Obsidian. *How*: install qmd (`npm i -g @tobilu/qmd`), then integrate.
- **`table-editor-obsidian`** — Edit markdown **tables like a spreadsheet**. *How*: shortcuts inside a table.
- **`obsidian-admonition`** — Extended **callout boxes** (note/warning/tip). *How*: ` ```ad-note ` or core `> [!note]`.

## 🎨 UI & styling

- **`obsidian-minimal-settings` / `obsidian-style-settings`** — UI to tweak theme **colors/fonts/spacing** (Minimal/Blue Topaz). *How*: Settings → Style Settings.
- **`obsidian-icon-folder`** — **Icons for folders/notes**. *How*: right-click folder → Change icon.
- **`obsidian-scroll-to-top-plugin`** — **Scroll to top/bottom** buttons. *How*: top-right button.
- **`homepage`** — Open a **designated home note** at startup. *How*: set the home note in settings.
- **`open-in-terminal` / `terminal`** — Launch a **terminal** at the vault (`terminal` = in-app; `open-in-terminal` = external/Claude·Codex·Gemini). *Why*: run CLI workflow (graphify·qmd·git·Claude Code) beside notes. *How*: Command palette → Open terminal.

## 🔧 Version control & extensions

- **`obsidian-git`** — **Auto commit/backup/sync** the vault with Git. *Why*: history, multi-device sync, recovery. *How*: install Git, set auto-commit interval (Windows needs Git for Windows).
- **`obsidian42-brat`** — Install **beta/unlisted plugins** from GitHub repos. *Why*: install/update unlisted plugins like `cc-obsidian`. *How*: BRAT → Add beta plugin → `reallygood83/cc-obsidian`.

---

> 🔑 = needs an API key/secret, so its config is excluded from the bundle. Add your own key to use it.
> Full workflow (capture→organize→query→lint→visualize): see [GUIDE.en.md](./GUIDE.en.md).
