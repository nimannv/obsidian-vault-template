# Obsidian Vault Template

An opinionated Obsidian vault template pre-configured with community plugins, a clean folder structure, and **Templater** workflows for evergreen notes, people, and meetings.

## Getting Started

1. Clone or download this repository.
2. Open Obsidian and select **Open folder as vault**, then choose this directory.
3. When prompted, click **Turn on community plugins** to enable the pre-installed plugins and settings in `.obsidian/`.

> All plugins, theme settings, hotkeys, and vault paths listed below are already pre-configured in `.obsidian/`. You only need to adjust them manually if you want to customize the defaults or recreate the setup from scratch.

---

## Folder Structure

```text
.
├── my-notes/               # Default location for new notes
├── people/                 # Person notes (auto-moved here by Person.md)
├── resources/
│   ├── ai/                 # AI-generated resources and references
│   └── attachments/        # Default location for images and attachments
└── templates/              # Templater templates
    ├── Init.md
    ├── Meeting.md
    └── Person.md
```

---

## Templates & Workflows

Press `Cmd+Shift+T` (macOS) or `Ctrl+Shift+T` (Windows/Linux) to insert a template using **Templater**.

| Template | Purpose | Key Behavior |
| --- | --- | --- |
| `Init.md` | Standard note initialization | Adds frontmatter (`tags`, `maturity: baby`, `status: active`, `create at`, `last update`) and a summary callout. Automatically inherits `tags` if the note is linked from a single parent note. |
| `Person.md` | People & contacts | Creates `Contact` and `Notes` sections, strips the leading `@` from the H1 heading, and automatically moves `@`-prefixed notes into `people/`. |
| `Meeting.md` | Meeting notes | Prompts for a meeting title and inserts structured `Attendance` and `Meeting Notes` sections. |

### Usage Conventions

- **People links:** Prefix person links with `@`, for example `[[@nima nnv]]`. When you create that note and apply `Person.md`, it is automatically organized into `people/`.
- **Note lifecycle:** Notes initialized with `Init.md` start with `status: active` and `maturity: baby`. Update these properties via **Metadata Menu** as notes grow (`baby` → `young` → `adult` → `elderly`).

---

## Included Plugins & Configuration

### Core Plugins & Settings
- **Files & Links:** New notes default to `my-notes`; new attachments default to `resources/attachments`.
- **Backlinks:** Enabled at the bottom of notes (`backlinkInDocument: true`).

### Community Plugins
- **Templater** (`templater-obsidian`)
  - Template folder: `templates`
  - Hotkey for *Insert template*: `Mod+Shift+T`
- **Dataview** (`dataview`)
  - Enabled for querying notes and frontmatter properties.
- **Metadata Menu** (`metadata-menu`)
  - Pre-configured select fields:
    - `status`: `active`, `inactive`
    - `maturity`: `baby`, `young`, `adult`, `elderly`
- **Update modified date** (`frontmatter-modified-date`)
  - Only updates existing fields (`onlyUpdateExisting: true`)
  - Target property: `last update`
- **Editing Toolbar** (`editing-toolbar`) *(optional)*
- **Harper** (`harper`) *(optional)*
