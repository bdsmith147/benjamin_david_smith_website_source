# Updating your website

Everything on the site comes from plain text files in this repository. You can edit them directly on GitHub: open a file, click the pencil icon, make your change, and click **Commit changes**. The site rebuilds and goes live automatically about two minutes later (watch progress under the **Actions** tab).

Text between `---` lines at the top of a file is the page's settings ("front matter"). Keep the quotation marks and indentation as you find them.

---

## Add a paper

1. Go to `content/publication/` and click **Add file → Create new file**.
2. Name it `lastname-year-short-title/index.md` (for example `smith-2027-cavity-bec/index.md`). **This folder name becomes the paper's permanent web address (`/works/your-folder-name/`), so never rename it later.**
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

The Research page is built from blocks listed at the top of `content/research/index.md` (between the `---` lines). Each block has:

```yaml
  - eyebrow: "2024 – 2026 · Postdoctoral Research Associate"   # small label above the heading
    title: "Compact cold-atom interferometers: Sandia National Laboratories"
    people: "Supervisor: Dr. Jongmin Lee"
    text: |
      A paragraph (or several) describing the work.
    works:                                    # optional: related items, by folder
      - "/publication/smith-2026-gmot-atom-interferometer"
      - "/talk/2025-06-cold-atom-navigation-damop"
```

Add `current: true` to make a block full-width (used for your current position). Titles and links of the `works` are filled in automatically. The starter text was drafted from your C.V.; rewrite it freely. A People block at the bottom links to the full People page.

## Update teaching

Courses, the certification, and the student feedback quotes are in `data/teaching.yaml`. The PHYS 111 description and links are in `content/teaching/_index.md`. The teaching philosophy statement is `content/teaching/philosophy/index.md`.

## People page: please review it

The People page (`/authors/`, linked from the Research page rather than the menu) is a grid of portrait cards, grouped by where you worked together. **Everyone named in an `authors:` list appears automatically**; their details live in `data/coauthors.yaml`:

```yaml
  "Bahar Babaei":
    url: "https://www.linkedin.com/in/..."      # website, university page, or LinkedIn; "" for no link
    affiliation: "Application Scientist, Zero Point Cryogenics"
    group: "University of Alberta"              # one of the groups listed at the top of the file
    photo: "images/people/babaei.jpg"           # "" shows a silhouette
    photo_source: "https://..."                 # where the photo came from
```

To add a photo, upload a head-and-shoulders image to `assets/images/people/` and put its path in `photo:`; it's cropped to a circle automatically.

**The links and positions were found by web search (or supplied by you) and may be wrong or out of date. Please check every entry.** Photos are currently off: everyone shows a silhouette. Add a photo only with that person's permission (a photo being visible online doesn't grant the right to reuse it); ideally use one they send you.

## Rename a button or label

All button text (for example "Publisher's Version", "Download citations") is in `i18n/en.yaml`.

## Footer credit and invisible marker

`params.mysite` in `hugo.yaml`: `credit: false` hides the "Created using GaryKing.org/mysite" footer line (currently hidden), and `discovery: false` removes the invisible metadata in the page source (currently on).

## Preview changes on your own computer (optional)

Install [Hugo](https://gohugo.io/installation/) (`winget install Hugo.Hugo.Extended` on Windows), then run `hugo server` in this folder and open the address it prints. Site search uses Pagefind, which is only built on GitHub; locally it falls back to a simpler built-in search.
