---
type: knowledge
tags:
  - methodology
  - reference
  - obsidian
updated: 2026-09-19
related: "[[00 Foundation of project structure]]"
---

# Obsidian setup

A snapshot of the working vault's configuration as of 2026-09-19. The
goal is to take a fresh, empty Obsidian vault, follow the steps below,
and end up with an environment that behaves the same way: the same
plugins, the same hotkeys, the same look. This isn't an `.obsidian/`
archive (that may contain personal paths and caches) — it's a
reproducible set of instructions.

## 1. Community plugins — install and enable

Through **Settings → Community plugins → Browse**, one at a time, in
this order of meaning (infrastructure first, then working plugins):

| Plugin | Why |
|---|---|
| **Dataview** | live queries over frontmatter and tasks — [[Focus]] and [[Task summary]] are built on it |
| **Tasks** (`obsidian-tasks-plugin`) | checkboxes with priority (🔺⏫🔼), `due`/`scheduled` dates, `tasks` code blocks |
| **Kanban** (`obsidian-kanban`) | the top-level board — [[Kanban board]] |
| **Calendar** | navigation across daily notes |
| **Iconic** | folder/file icons, used in MOC files' frontmatter (`icon:`) |
| **Colored Tags** | visually distinguishing tags like `moc/inbox`, `example`, etc. |
| **Mermaid Tools** | helpers for Mermaid diagrams (maps, schematics in `map.md`) |
| **Document Exporter** | exporting notes |
| **Obsidian LiveSync** | syncing the vault through CouchDB (see section 5 — needs its own configuration, no keys live here) |
| **BRAT** (`obsidian42-brat`) | installing plugins outside the official catalog — used for `karpathywiki` |
| **Karpathywiki** | a third-party plugin (installed via BRAT) |
| **AI Audio Transcription & Summary** | transcribing voice notes to text |
| **Copilot** (`obsidian-copilot`) | a chat/AI assistant inside Obsidian — models and keys are configured separately, see section 6 |
| **Markdown Formatting Assistant** | auxiliary Markdown formatting |

Installed but **not enabled** in the current vault (safe to skip on
first setup, enable if needed): `better-export-pdf`, `captains-log`,
`perplexity-converter`, `smart-connections`,
`smart-connections-visualizer`.

## 2. Core plugins — check what's enabled

**Settings → Core plugins.** Disabled by default in this vault
(deliberately, not forgotten): `footnotes`, `slash-command`,
`markdown-importer`, `zk-prefixer`, `random-note`, `slides`,
`audio-recorder`, `publish`, `webviewer`. Everything else in core is
enabled, including `daily-notes`, `templates`, `bases`, `sync`,
`bookmarks`, `canvas`.

## 3. General settings (Settings → Files & Links / Editor)

| Setting | Value | Where to change it |
|---|---|---|
| New file location | `current` (in the current folder, not at the root) | Files & Links |
| Automatically update links on move | enabled | Files & Links |
| Default attachment folder | `(R) Utility/Assets` | Files & Links |
| Line numbers in the editor | off | Editor |
| Spell check | off | Editor |

## 4. Daily Notes and Templates

| Plugin | Setting | Value |
|---|---|---|
| Daily notes | folder | `(A) Journal` |
| Daily notes | template | `(R) Utility/Templates/Day template.md` |
| Templates | templates folder | `(R) Utility/Templates` |

Place the templates themselves (`Day template.md` and others) in
`(R) Utility/Templates` — they aren't included in this starter kit as
files, only as a path reference; this kit's entity templates live in
[[_templates]] next to this file.

## 5. Dataview — non-default settings

Most Dataview settings are left at their defaults, except:

- `dataviewJsKeyword: dataviewjs` (default) — what matters is that
  `enableDataviewJs` and `enableInlineDataviewJs` are **enabled** —
  without this, the ` ```dataviewjs ` blocks in [[Focus]] and
  [[Task summary]] won't work.
- `refreshInterval: 2500` — dashboards re-read every 2.5 seconds.

## 6. Appearance

| Setting | Value |
|---|---|
| Theme | AnuPpuccin (Settings → Appearance → CSS themes; installed via Community themes) |
| Accent color | `#13d110` |
| Interface font | PT Sans Caption |
| Text font | PT Sans |
| Monospace font | PT Mono |
| Base font size | 16 |
| Window translucency | off |

Also installed (not necessarily active) are the **ITS Theme** and
**Obsidian Nord** themes — any theme can be used, it doesn't affect the
vault structure.

## 7. Iconic — icons

Key toggles: `minimalFolderIcons: true` (minimalist-style folder icons),
`showTitleIcons`/`showMarkdownTabIcons: true` (the icon shows both in
the file title and on the tab). The icons themselves attach via the
`icon:` field in MOC files' frontmatter (see `icon: target` in [[Focus]],
`icon: list-checks` in [[Task summary]]) — they need to be set by hand
through Iconic's context menu or frontmatter; the plugin doesn't
generate them automatically.

## 8. Copilot — AI inside Obsidian

The plugin is installed, but **no API key is stored in the
configuration** — in this vault snapshot every `*ApiKey` field is empty.
To get a working chat:

1. In the Copilot plugin's settings → provide the key for whichever
   provider (Anthropic/OpenAI/Google/OpenRouter, etc.) you want yourself
   — keys aren't part of this kit and should never end up in it (see the
   section on secrets in [[00 Foundation of project structure]]).
2. The plugin's data folder is `(R) Utility/copilot` (conversation
   history, custom prompts in the `copilot-custom-prompts` subfolder).
3. Contexts: `qaExclusions: copilot` — the plugin itself doesn't index
   its own history folder when building context.

## 9. Obsidian LiveSync — synchronization

The plugin is installed, but **not configured** in this vault snapshot
(CouchDB address, login, and password are empty strings, `liveSync:
false`). If you need sync across devices — it's configured separately,
outside the scope of the vault structure: see the plugin's own
documentation. Sync secrets (database URL/login/password) must never end
up in any file in this vault — only in the plugin's own settings (the
plugin's `data.json` isn't synced as a note).

## 10. Deliberately not part of this kit

- The theme/plugin files themselves — install them fresh through
  Community plugins/themes, they aren't copied as binaries.
- Any API key, token, or CouchDB password values — none are stored
  anywhere in this vault in any form.
- Personal paths and `userId` — specific to an install, not carried over.
