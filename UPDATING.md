# Updating your website

Everything on the site comes from plain text files in this repository. You can edit them directly on GitHub: open a file, click the pencil icon, make your change, and click **Commit changes**. The site rebuilds and goes live automatically about two minutes later (watch progress under the **Actions** tab).

Text between `---` lines at the top of a file is the page's settings ("front matter"). Keep the quotation marks and indentation as you find them.

---

## Add a paper

1. Go to `content/publication/` and click **Add file → Create new file**.
2. Name it `lastname-year-short-title/index.md` (for example `smith-2027-cavity-bec/index.md`). **This folder name becomes the paper's permanent web address, so never rename it later.**
3. Paste this and fill it in:

```yaml
---
title: "Paper title"
date: 2027-03-15
authors: ["Benjamin D. Smith", "Co-Author Name"]
publication_types: ["journal_article"]   # or "preprint" for submitted work, "thesis"
publication: "Journal Name 12, 345678"
journal: "Journal Name"
doi: "10.xxxx/xxxxx"
abstract: "Paste the abstract here."
links:
  - name: Publisher's Version
    url: "https://doi.org/10.xxxx/xxxxx"
  - name: arXiv
    url: "https://arxiv.org/abs/xxxx.xxxxx"
tags: ["quantum sensing", "atom interferometry"]
---
```

- **tags** are optional keywords; each one gets a page listing the items that share it.
- The Works page is a curated selection. Add items that are meaningful and have something to link to (a paper, PDF, poster, or recording); the full C.V. PDF covers everything else.
- To host a PDF yourself, upload it to `static/files/` and link it as `url: "files/your-file.pdf"` (no leading slash).
- When a submitted paper is published, change `publication_types` to `["journal_article"]`, remove `status:`, and update the venue and links. Keep the same folder.

## Add a talk or poster

Create `content/talk/YYYY-MM-short-name/index.md`:

```yaml
---
title: "Talk title"
date: 2027-06-01
authors: ["Benjamin D. Smith"]
publication_types: ["presentation"]
talk_type: "contributed"     # invited, contributed, seminar, or poster
event: "58th Annual Meeting of the APS DAMOP"
location: "City, ST"
tags: ["atom interferometry"]
links:
  - name: "Poster (PDF)"
    url: "files/posters/2027-damop.pdf"
  - name: "Video"
    url: "https://..."
---
```

Large videos don't fit in the repository (GitHub's file limit is 100 MB), so link to YouTube or Google Drive for those.

## Add software

Create `content/software/project-name/index.md` with `title`, `date`, `summary`, `links` (Live App / Source Code), and `tags`. Add `featured: true` to show it as the wide card at the top of the Software page.

## Update your bio or C.V.

- **Bio text:** `content/bio/index.md` (everything below the second `---`).
- **Home page:** `content/_index.md` holds the intro (keep it different from the bio), the Research paragraph, the Teaching highlights and quote, and the tiles that link to other pages.
- **C.V. highlights** (education and research positions): `data/cv.yaml`.
- **Full C.V. PDF:** comes straight from Google Drive, so the site shows whatever is in that Drive file. To update it, open the file in Drive and use **⋮ → File information → Manage versions → Upload new version**. Uploading a *new* file instead gives it a new ID; then paste the new ID into `cv_drive_id` in `content/bio/index.md` (the ID is the long string between `/d/` and `/view` in the share link). Sharing must stay on "Anyone with the link".
- **Faith statement PDF:** also comes from Google Drive (`drive_id` in `content/faith/index.md`). Update it the same way, with **Manage versions → Upload new version** in Drive.
- **Photo:** replace `assets/images/portrait.jpg`. It's cropped to a circle automatically, so a head-and-shoulders photo works best.
- **Title, institution, email, profile links:** `params.owner` in `hugo.yaml`.

## Update the Research page

`content/research/index.md` is ordinary Markdown: `## ` starts a section, `- ` starts a bullet, and links to your own pages look like `[Title]({{< relref "/publication/folder-name" >}})`. The starter text was drafted from your C.V.; rewrite it freely. The People section at the bottom links to the co-author list.

## Update teaching

Courses, the certification, and the student feedback quotes are in `data/teaching.yaml`. The PHYS 111 description and links are in `content/teaching/_index.md`. The teaching philosophy statement is `content/teaching/philosophy/index.md`.

## People page: please review it

The People page (`/authors/`, linked from the bottom of the Research page rather than the menu) is **built automatically from the co-authors on your papers, talks, and software**. Each name links to that person's website, university page, or LinkedIn, in that order of preference.

**These links were found by web search and may point to the wrong person or a stale page. Please check every entry.** They live in `data/coauthors.json`:

```json
"Bahar Babaei": { "url": "https://...", "type": "website" }
```

A name with an empty `url` appears without a link. When you add a paper with a new co-author, they appear on the People page automatically; add their link to `data/coauthors.json` if you want one.

## Rename a button or label

All button text (for example "Publisher's Version", "Download citations") is in `i18n/en.yaml`.

## Footer credit and invisible marker

`params.mysite` in `hugo.yaml`: `credit: false` hides the "Created using GaryKing.org/mysite" footer line (currently hidden), and `discovery: false` removes the invisible metadata in the page source (currently on).

## Preview changes on your own computer (optional)

Install [Hugo](https://gohugo.io/installation/) (`winget install Hugo.Hugo.Extended` on Windows), then run `hugo server` in this folder and open the address it prints. Site search uses Pagefind, which is only built on GitHub; locally it falls back to a simpler built-in search.
