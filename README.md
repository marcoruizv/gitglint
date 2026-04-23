# *GitGlint*

> A self-contained, single-file Git-based markdown editor. Open it in a browser, connect your GitHub repo, and write.

No build step. No server. No install. Just one `.html` file.

---

## What it is

GitGlint is a lightweight content editor that talks directly to the GitHub API. It's designed for writers and developers who manage markdown content in a Git repository — blog posts, docs, notes, anything text-based — and want a clean editing interface without touching a code editor or the GitHub web UI.

It works on desktop and mobile, supports light and dark themes, and is very portable.

**Project Status: As-Is**
GitGlint is a completed, personal utility provided "as-is". To maintain its minimalist philosophy and keep the project low-maintenance, I am not accepting Issues or Pull Requests.
Please feel free to fork the repository if you wish to make your own modifications.

---

## Getting started

1. **Download** `GitGlint.html` and open it in any modern browser, or host it anywhere (GitHub Pages, Netlify, a local server — even `file://` works).
2. **Create a Fine-Grained Personal Access Token** with `repo` read/write scope at [github.com/settings/personal-access-tokens](https://github.com/settings/personal-access-tokens).
3. On first launch, enter your **PAT**, **owner** (GitHub username or org), and **repository name**, then click **Connect Repository**.
  - [Optional] Activate quasi-CMS mode by providing the path to where your content resides. This is useful if updating content for an Astro-based blog for example. Use syntax `label:path/to/markdown/files`. Toggle from settings.
5. Your repo's file tree loads in the sidebar. Click any file to open it.

---

## Features

### Editor

- Full markdown editor with live **split-pane preview** (Edit / Split / Preview modes)
- Markdown rendered with [marked](https://marked.js.org/) and sanitized with [DOMPurify](https://github.com/cure53/DOMPurify)
- **Formatting toolbar** — Bold, Italic, Strikethrough, H1–H3, Link, Code, Code block, Divider, Bullet list, Numbered list, Blockquote
- **Keyboard shortcuts** — `⌘B` Bold, `⌘I` Italic, `⌘S` / `Ctrl+S` open Commit, `Tab` inserts two spaces
- Unsaved changes tracked with a dot indicator and a Commit button; navigating away prompts for confirmation
- Auto-generated YAML frontmatter for new `.md` files (`title`, `date`, `draft`, `description`)
- Edits non-markdown text files too (JSON, YAML, TOML, HTML, CSS, JS/TS, Astro, Svelte, Vue, XML, and more)
- Image files display inline with a link to the raw source

### File management

- **Browse** any directory in your repo with a clickable breadcrumb trail
- **Create files** — opens in the editor immediately, committed to GitHub on save
- **Create folders** — a `.gitkeep` is added automatically (GitHub requires at least one file per folder)
- **Delete files** — confirmation modal shows the full path before committing the deletion
- **Upload images** — drag-and-drop or file picker; uploaded to a configurable path and inserted as markdown

### Branch management

- **Switch branches** via a searchable modal; unsaved changes prompt for confirmation before switching
- **Create branches** from any existing branch
- **Delete branches** from the switch modal (current branch is protected)

### CMS Mode

A focus mode for writers. Enable it in Settings to hide the full repo tree and show only your content directories.

- Configure one or more content paths — e.g. `content/posts` or `src/content/blog`
- **Label your paths** using `Label:path` syntax: `Posts:content/posts, Drafts:content/drafts`
- Multiple paths appear as **tab pills** in the sidebar for quick switching
- Navigation is **locked to your content root** — you can't accidentally browse outside it
- A **CMS badge** appears in the sidebar header when the mode is active
- New file and new folder buttons are available directly in the breadcrumb bar

### Mobile

- Responsive layout with a slide-in drawer for the sidebar
- Bottom navigation bar (Files / Write / Preview)
- **Commit button in the top header** when there are unsaved changes — stays visible above the keyboard

---

## Settings

Open the ⚙ settings panel at any time to adjust:

| Setting | Description |
|---|---|
| GitHub PAT | Your personal access token |
| Owner | GitHub username or organization |
| Repository | Repo name |
| Image path | Folder where uploaded images are stored (default: `public/images`) |
| CMS Mode | Toggle focus mode on/off |
| Content paths | Comma-separated paths for CMS mode, with optional labels |

All settings are saved to `localStorage` under the key `folio_v1`. Clicking **Disconnect** clears everything and returns to the setup screen.

---

## CMS path syntax

```
# Single path — no label needed
content/posts

# Multiple paths — labels become tab names
Posts:content/posts, Pages:content/pages, Drafts:content/drafts

# Mix labelled and unlabelled (unlabelled fall back to the folder name)
Posts:content/posts, content/drafts
```

---

## Supported file types

| Category | Extensions |
|---|---|
| Markdown | `.md` `.mdx` `.markdown` |
| Code / Config | `.txt` `.json` `.yaml` `.yml` `.toml` `.html` `.css` `.js` `.ts` `.jsx` `.tsx` `.astro` `.svelte` `.vue` `.xml` |
| Images (viewer) | `.png` `.jpg` `.jpeg` `.gif` `.webp` `.svg` `.avif` `.bmp` |

---

## Dependencies

All loaded from CDN — no local install required.

| Library | Version | Purpose |
|---|---|---|
| React | 18 | UI |
| Babel Standalone | latest | JSX transpilation in-browser |
| marked | 9 | Markdown → HTML |
| DOMPurify | 3.0.6 | Sanitize rendered HTML |
| Feather Icons | 4.29.0 | UI icons |

---

## Privacy & security

- Your GitHub PAT is stored only in your browser's `localStorage`. It is never sent anywhere except directly to `api.github.com`.
- All API calls go directly from your browser to GitHub — there is no backend, no proxy, no telemetry.
- Rendered markdown is sanitized with DOMPurify before being injected into the DOM.
- For shared or public devices, use an incognito/private window and click **Disconnect** before closing.

---

## Limitations

- GitHub's Contents API has a **1 MB file size limit** for reading/writing files. Large files will fail to load.
- The branch list fetches up to **100 branches**. Repos with more than 100 branches will show only the first 100.
- GitGlint requires an **internet connection** — it talks to the GitHub API in real time and has no offline mode.
- Binary files (PDFs, fonts, etc.) are not editable, though images are viewable.

---

## Meta 🤖

​GitGlint was built as an experiment in AI-collaborative development. The core logic and architecture were co-authored with AI to demonstrate a high-velocity, single-file deployment workflow. It is provided as-is, representing a "frozen" moment of that collaboration. 

This is a tool built using a LLM, all in a chat-interface, for personal use but making it public in case anyone wants to use it.

--- 

## License

MIT
