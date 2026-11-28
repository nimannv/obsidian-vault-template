# Obsidian Vault Template

An opinionated Obsidian vault template pre-configured with community plugins, **Obsidian Bases** dashboards, a clean flat-note structure, **Templater** workflows, and a built-in note lifecycle & credit system.

## Getting Started

1. Clone or download this repository.
2. Open Obsidian and select **Open folder as vault**, then choose this directory.
3. When prompted, click **Turn on community plugins** to enable the pre-installed plugins and settings in `.obsidian/`.
4. Open `my-notes/My Note Taking System.md` to read through the included starter notes explaining the system.

> All plugins, CSS snippets, graph settings, hotkeys, and vault paths listed below are already pre-configured in `.obsidian/`. You only need to adjust them manually if you want to customize the defaults or recreate the setup from scratch.

---

## Folder Structure

```text
.
├── Starting Points.base    # Card view of #starting_point entry notes
├── Note Credits.base       # Table view ranking notes by freshness/maturity credit
├── TODO.base               # Kanban board of notes grouped by status
├── my-notes/               # Default location for all notes (flat structure)
├── resources/
│   ├── AI/                 # AI-generated resources and references
│   └── attachments/        # Default location for images and attachments
└── templates/              # Templater templates
    ├── Init.md
    ├── Meeting.md
    ├── Person.md
    └── TODO Section.md
```

---

## Bases & Dashboards

The vault uses Obsidian's **Bases** core plugin to surface and manage notes in `my-notes/`:

| Base | View Type | Purpose |
| --- | --- | --- |
| `Starting Points.base` | Cards | Displays notes tagged with `#starting_point` as entry points into your vault, showing `status`, `maturity`, and `tags`. |
| `Note Credits.base` | Table | Computes a **Credit** score (`0–100`) for every note based on its `maturity` and how recently it was `updated` and `viewed` (using a half-life decay formula), sorted ascending so stale notes surface first. |
| `TODO.base` | Kanban | Groups notes by `status` (`to activate` → `active` → `suspend` → `inactive`) with each card displaying its `credit`, `description`, and `maturity`. |

---

## Templates & Workflows

Press `Cmd+Shift+T` (macOS) or `Ctrl+Shift+T` (Windows/Linux) to insert a template using **Templater**.

| Template | Purpose | Key Behavior |
| --- | --- | --- |
| `Init.md` | Standard note initialization | Prompts for a `description` and adds frontmatter (`tags`, `maturity: baby`, `status: active`, `created`, `updated_count: 0`, `updated`, `viewed`, `description`). Automatically inherits `tags` if the note is linked from a single parent note. |
| `Person.md` | People & contacts | Adds `tags` frontmatter and a `Contact` table section. |
| `Meeting.md` | Meeting notes | Prompts for a meeting title and inserts structured `Attendance` and `Meeting Notes` sections. |
| `TODO Section.md` | Action items | Appends a divider and a `# To Do:` checklist section to the note. |

### Usage Conventions

- **Flat notes vs. resources:** All notes (ideas, people, topics, MOCs) live together in `my-notes/`. External references and attachments that you don't author directly go in `resources/`.
- **Maturity (`maturity`):** Tracks how developed an idea is (`baby` → `young` → `adult` → `elderly`), updated via **Metadata Menu**. Higher maturity gives a note a higher maximum credit (`25` / `50` / `75` / `100`) and a longer decay half-life (`7` / `30` / `90` / `365` days) in `Note Credits.base`.
- **Status (`status`):** Drives the `TODO.base` Kanban board:
  - `to activate`: There is something to do in the note.
  - `active`: Actively working or thinking on it.
  - `suspend`: Has work remaining, but waiting on something else.
  - `inactive`: No active plan to work on it.
- **Starting points (`#starting_point`):** Tag top-level or entry-point notes with `#starting_point` to display them in `Starting Points.base` and highlight them in Graph View.

---

## Included Plugins & Configuration

### Core Plugins & Settings
- **Files & Links:** New notes default to `my-notes`; new attachments default to `resources/attachments`; automatic link updates enabled (`alwaysUpdateLinks: true`).
- **Backlinks:** Enabled at the bottom of notes (`backlinkInDocument: true`).
- **Bases:** Enabled for the root `.base` dashboards.
- **Graph View:** Filtered to `path:my-notes`, displays link arrows, and highlights `#starting_point` notes in a dedicated color group.

### CSS Snippets
- **`hidden_properties.css`** (`.obsidian/snippets/hidden_properties.css`): Hides automatically managed timestamp/counter properties (`created`, `updated_count`, `updated`, `viewed`) from the Properties panel to keep frontmatter clean.

### Community Plugins
- **Templater** (`templater-obsidian`)
  - Template folder: `templates`
  - Hotkey for *Insert template*: `Mod+Shift+T`
- **Dataview** (`dataview`)
  - Enabled for querying notes and frontmatter properties.
- **Metadata Menu** (`metadata-menu`)
  - Pre-configured select fields:
    - `maturity`: `baby`, `young`, `adult`, `elderly`
    - `status`: `active`, `to activate`, `suspend`, `inactive`
- **Frontmatter Date Manager** (`frontmatter-date-manager`)
  - Automatically maintains `created`, `updated`, `viewed`, and `updated_count` frontmatter fields (excluding `templates/` and `resources/`) using body content hashing.
- **Iconize** (`obsidian-icon-folder`)
  - Pre-configured Lucide icons for vault folders (`my-notes`, `resources`, `resources/AI`, `resources/attachments`, `templates`) and `.base` files.
- **Editing Toolbar** (`editing-toolbar`) *(optional)*
