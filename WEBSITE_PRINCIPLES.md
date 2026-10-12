# Website principles and architecture

A playbook for anyone (human or AI) maintaining this site. Read it before changing templates.

## Stack

| Layer | Choice |
|---|---|
| Generator | Hugo (built with 0.152.2 extended in CI; templates also build on the standard edition) |
| Theme | Project-owned templates in `layouts/` (no external theme) |
| CSS | One file, `assets/css/custom.css`, minified and fingerprinted by Hugo |
| Search | Pagefind, built in CI after Hugo; falls back to `index.json`, then a Google `site:` search |
| Hosting | GitHub Pages project site, deployed by `.github/workflows/deploy.yml` on every push to `main` |

**Why not Hugo Blox?** The build instructions called for Hugo Blox `blox-tailwind` v0.10.0. That version does not exist (the newest release is v0.9.0), and v0.9.0 compiles Tailwind CSS v4 at build time, which needs Node.js plus the Tailwind CLI and Go for Hugo modules. The site already overrode nearly every Blox partial (base layout, navbar, footer, search modal, every list and detail page), so it uses its own templates instead. That keeps the build to one binary with no external dependencies, which matters for the long-lived, hermetic builds this site wants. Conventions from the Blox approach are kept: `layouts/_partials/`, `publication_types`, `featured.*` image discovery, and the content layout.

## Content model

- Every item is a folder with `index.md`. **The folder name is the permanent URL** (`permalinks` use `:contentbasename`). Never rename a folder once live; change `title:` instead.
- `content/publication/`: articles (`journal_article`), submitted work (`preprint`), theses (`thesis`). Shown publicly as **Works**: the list is at `/works/` and each paper at `/works/<folder>/` (`permalinks` in `hugo.yaml`); the internal section name stays `publication`. Templates link to the list with `(site.GetPage "/publication").RelPermalink`, never a hard-coded path.
- `content/talk/`: presentations (`publication_types: [presentation]`, `talk_type`: invited / contributed / seminar / poster).
- `content/software/`: tools (`publication_types: [software]`).
- Structured, repeated data lives in `data/`: `cv.yaml`, `teaching.yaml`, `coauthors.json`, `writings_tabs.yaml`. Templates read these; nothing is typed twice.
- The homepage intro (`content/_index.md` `intro:`) and the bio (`content/bio/index.md`) must remain different text.

## Templates (`layouts/`)

| File | Role |
|---|---|
| `baseof.html` | Shell: skip link, navbar, `<main>`, footer, search modal |
| `landing/list.html` | Home: centered portrait hero, Research and Teaching blocks, tiles linking to the rest of the site (text in `content/_index.md`) |
| `publication/list.html` | Works page: server-rendered dense list + vanilla-JS tabs, filters, sort, hash sync, BibTeX export |
| `publication/single.html`, `talk/single.html`, `software/single.html` | All call `_partials/item_single.html` |
| `talk/list.html`, `software/list.html` | Talks by year; software cards |
| `_default/bio.html` · `teaching.html` · `people.html` · `contact.html` · `document.html` | Selected with `layout:` in front matter |
| `_partials/scholarly_meta.html` | Google Scholar `citation_*` tags + JSON-LD |
| `_partials/fn/*.html` | Small functions that return values: tokens, kind, tab, bibtex |
| `index.json` | Fallback search index (home JSON output) |
| `robots.txt` | Allows all crawlers, points to the sitemap and `llms.txt` |

Hugo already applies the base path to menu URLs, so templates use `.URL` from menus as-is. Everywhere else, local paths go through `relURL` **without** a leading slash (`"files/x.pdf" | relURL`). Front-matter `links:` use `files/...`, never `/files/...`.

## Editorial choices made with the owner

- **No automatic See Also lists** on item pages; the owner found them distracting. Link related items inline in the body text or with a `links:` button instead.
- **No research-area taxonomy.** The work is not organized into fixed topic categories; the home page has a short Research paragraph instead.
- **Works is curated**, not a copy of the C.V.: articles, preprints, theses, and only those presentations with a poster or recording. The full C.V. PDF on the Bio page lists everything.
- **Bio & C.V. page** shows Education and Research Positions, then embeds the full C.V. **from Google Drive** (`cv_drive_id` in `content/bio/index.md`) so it updates when the owner replaces the Drive file. The faith statement on the Faith page works the same way (`document.drive_id` in `content/faith/index.md`). These are deliberate exceptions to "all PDFs live in the repo".
- **Menu order:** Bio & C.V., Research, Teaching, Faith, Works, Software, Contact (`menu.main` in `hugo.yaml`). People is not in the menu; it is a section of the Research page, and its `parent_page: "/research"` front matter makes the breadcrumb and highlighted tab read Research.
- **Home page:** the Research and Teaching block headings link to those pages.

## Works page contract

- Every item is in the HTML at load time (works without JS and for crawlers).
- Each `<li class="pub-item">` carries `data-tab`, `data-year`, `data-sub`.
- Tabs come from `data/writings_tabs.yaml`; only tabs with content render. Every tab button has a click listener.
- State lives in the URL hash: `#tab&q=…&year=…&type=…&sort=…`. Tab changes push history (the back button works); typing replaces it.

## Design

- Carried over from the previous site (benjamindavidsmith.com): white page, centered round portrait, teal accent. The design quest was skipped because this was a migration; the record is in `params.mysite.design`.
- Tokens are in `:root` in `custom.css`. Teal `--color-accent` is used for buttons, active tabs, and the favicon. Air Force blue `--color-institution` appears only as the navbar's bottom rule and on button hover.
- Always light mode. Native system fonts. `prefers-reduced-motion` strips transitions.
- Favicon: "BDS" in white on the accent teal (`static/favicon*`).

## Accessibility and SEO checklist

Skip link; one H1 per page; visible `:focus-visible` outlines; labeled form controls; accordions are native `<details>`; search modal closes on Esc and supports arrow keys and Ctrl/Cmd-K; `baseURL` is the final `https://` address and is never overridden in CI; `llms.txt`, `robots.txt`, sitemap, and per-publication JSON-LD are present.

## Things to remember

- Don't put process notes in visible text; use `<!-- … -->` comments in Markdown.
- People-page links are guessed: see `UPDATING.md`.
- Videos are linked externally (Google Drive / YouTube); keep repository files under 100 MB.
- If the site moves to the custom domain (benjamindavidsmith.com), change `baseURL` in `hugo.yaml`, add `static/CNAME`, and update the URLs in `static/llms.txt`. The `aliases:` on the Bio, Teaching, Works, and Software pages already redirect the old site's paths (`/about/main/`, `/teaching/main/`, `/research/...`).
