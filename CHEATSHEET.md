# Website cheat sheet

One page: where everything lives, and what to do when something goes wrong.
For step-by-step instructions, see [UPDATING.md](UPDATING.md). Blank files to copy are in [templates/](templates/).

## Where everything lives

| On the website | File to edit |
|---|---|
| Home page: intro, Research paragraph, Teaching highlights, quote, bottom tiles | `content/_index.md` |
| Your name, title, institution, email, profile links (header, footer, Contact) | `hugo.yaml` → `params: owner:` |
| Menu (order and names) | `hugo.yaml` → `menu: main:` |
| Bio text | `content/bio/index.md` |
| Education and research positions (Bio & C.V. page) | `data/cv.yaml` |
| Full C.V. (PDF) | **Google Drive**: upload a new version of the same file |
| Research page blocks | `content/research/index.md` (top section) |
| People page (links, positions, groups) | `data/coauthors.yaml` |
| Teaching: courses, certification, student quotes (also feeds Teaching Experience on the Bio page) | `data/teaching.yaml` |
| Teaching: PHYS 111 and Qiskit workshop | `content/teaching/_index.md` |
| Teaching philosophy | `content/teaching/philosophy/index.md` |
| Faith page intro | `content/faith/index.md` |
| Faith essay (PDF) | **Google Drive**: upload a new version of the same file |
| Papers and theses | `content/publication/<folder>/index.md` |
| Talks and posters | `content/talk/<folder>/index.md` |
| Software projects | `content/software/<folder>/index.md` |
| Works page tabs | `data/writings_tabs.yaml` |
| Button and label wording | `i18n/en.yaml` |
| PDFs you host yourself (posters, course outline) | `static/files/` |
| Your photo | `assets/images/portrait.jpg` |
| Colors, fonts, spacing | `assets/css/custom.css` (design: best with help) |
| Page layouts | `layouts/` (code: best with help) |

## Common tasks

| I want to… | Do this |
|---|---|
| Add a paper | New folder in `content/publication/`, then copy [templates/new-paper.md](templates/new-paper.md) into it as `index.md` |
| Add a talk or poster | New folder in `content/talk/`, then copy [templates/new-talk.md](templates/new-talk.md) |
| Add software | New folder in `content/software/`, then copy [templates/new-software.md](templates/new-software.md) |
| Give a co-author a link or position | Paste [templates/new-coauthor.yaml](templates/new-coauthor.yaml) into `data/coauthors.yaml` |
| Start a new job | Update `hugo.yaml` (title, institution), `data/cv.yaml`, the bio, and add a block from [templates/new-research-block.yaml](templates/new-research-block.yaml) |
| Mark a preprint as published | In its `index.md`: `publication_types: ["journal_article"]`, update `publication`, `journal`, `doi`, links; delete `status:` |
| Update the C.V. or faith essay | In Google Drive: right-click the file → **File information → Manage versions → Upload new version** |
| Remove something | Delete its folder (or the lines in the data file) |

## Editing on GitHub

1. Go to the repository on github.com and open the file.
2. Click the **pencil** icon, make the change, and click **Commit changes**.
3. Watch the **Actions** tab: a green check (about 2 minutes) means the site is updated.

To create a new folder on GitHub: **Add file → Create new file**, and type the folder name, a slash, then `index.md` (for example `content/talk/2027-06-my-talk/index.md`).

## If the update fails (red ✗ in the Actions tab)

The live site **is not broken**. It keeps showing the last version that worked. GitHub also emails you.

1. Click the failed run in the **Actions** tab, then the **build** step, and look for a line starting with `ERROR`. It names the file and usually the line number.
2. Fix the most common causes:
   - **Indentation:** lines in `.yaml` files and between the `---` lines must line up with their neighbours. Use spaces, never Tab.
   - **Quotes:** text containing a colon (`:`) or starting with a special character needs quotation marks. A double quote *inside* quoted text must be written `\"`.
   - **Missing `---`:** the settings at the top of a page must start and end with a line containing only `---`.
   - **Date format:** `date: 2027-06-01` (year-month-day, no quotes).
3. Still stuck? Undo the change: open the file → **History** → pick the last good version → copy it back, or ask someone to "revert the last commit".

## If a new page doesn't appear (but there is no error)

- **Is its `date:` in the future?** Pages dated after today stay hidden until that day. Change the date to today or earlier.
- **Is the file named exactly `index.md`**, inside its own folder in the right section (`content/publication/`, `content/talk/`, `content/software/`)?
- **Did the settings block start and end with `---`?**

## Rules worth remembering

- **Never rename a folder** in `content/` once the site is live. The folder name is the page's web address, and others may have linked to it.
- **Local links have no leading slash:** `files/poster.pdf`, not `/files/poster.pdf`.
- **Names must match exactly** between a paper's `authors:` and `data/coauthors.yaml`. "Logan W. Cooke" and "Logan Cooke" count as two different people.
- **Videos go on Google Drive or YouTube**, not in the repository (GitHub's limit is 100 MB per file).
- **Photos of other people:** use only with their permission.
