# Benjamin D. Smith — academic website

Source for Benjamin D. Smith's personal academic website, built with [Hugo](https://gohugo.io/) and published with GitHub Pages.

Everything on the site comes from plain text files in this repository. Edit a file, save (commit) it, and the site rebuilds and updates itself within a couple of minutes.

## Documentation

| File | What it's for |
|---|---|
| [CHEATSHEET.md](CHEATSHEET.md) | **Start here.** One page: where everything lives, common tasks, and what to do if an update fails |
| [templates/](templates/) | Ready-made blank files to copy: [new paper](templates/new-paper.md), [new talk/poster](templates/new-talk.md), [new software](templates/new-software.md), [new co-author](templates/new-coauthor.yaml), [new Research block](templates/new-research-block.yaml) |
| [UPDATING.md](UPDATING.md) | Step-by-step instructions for each kind of update |
| [WEBSITE_PRINCIPLES.md](WEBSITE_PRINCIPLES.md) | How the site is built, for anyone (or any AI) changing the design or code |

## Updating the site without installing anything

You can do every routine update in your web browser:

1. Open this repository on github.com.
2. Open the file you want to change (see [CHEATSHEET.md](CHEATSHEET.md)), click the **pencil** icon, edit, and click **Commit changes**.
3. Check the **Actions** tab. A green check means the live site is updated; a red ✗ means something needs fixing (the live site keeps the last working version; see the cheat sheet).

## Previewing changes on your own computer (optional)

A local preview lets you see changes instantly before publishing them.

### 1. Install Hugo (once)

- **Windows:** open a terminal (PowerShell) and run
  ```bash
  winget install Hugo.Hugo.Extended
  ```
- **macOS:** `brew install hugo`
- **Other:** see <https://gohugo.io/installation/>

Check that it worked (any version 0.146 or newer is fine; the published site uses 0.152.2):

```bash
hugo version
```

You also need a copy of this repository on your computer, for example with GitHub Desktop or `git clone`.

### 2. Start the preview server

In a terminal, go to the repository folder and start Hugo's built-in server:

```bash
cd "C:\Users\bensm\Documents\Benjamin\_Career\Website 2026\benjamin_david_smith_website_source"
hugo server
```

Or, from any folder, point Hugo at the repository:

```bash
hugo server --source "C:\Users\bensm\Documents\Benjamin\_Career\Website 2026\benjamin_david_smith_website_source"
```

When it says `Web Server is available at ...`, open the address it prints in your browser:

<http://localhost:1313/benjamin_david_smith_website_source/>

(The `/benjamin_david_smith_website_source/` part matches where the site will live on GitHub Pages. If the site moves to a custom domain, it disappears and the address becomes `http://localhost:1313/`.)

### 3. Using the preview server

- **Live reload:** leave the server running. Every time you save a file, the preview rebuilds in a fraction of a second and the open browser page refreshes itself.
- **Errors:** if you make a mistake, the browser shows a dark "Hugo Server: Error" page and the terminal shows a line starting with `ERROR` naming the file. Fix the file and save; the preview recovers on its own.
- **Stop the server:** click in the terminal and press **Ctrl+C**.
- **Restart the server** (Ctrl+C, then run `hugo server` again) when:
  - you **renamed, moved, or deleted** a folder and the preview still shows the old version or is missing a page;
  - an error message **won't go away** even though you've fixed the file;
  - you changed **`hugo.yaml`** and nothing seems to happen.
- **Future-dated pages:** pages with a `date:` after today are hidden, in the preview and on the live site. To preview one early, start the server with `hugo server --buildFuture`.
- **"Port 1313 is in use":** another preview is already running (perhaps in another terminal window). Use that one, close it, or start this one on a different port with `hugo server --port 1314`.
- **Not shown in the preview:** site search uses Pagefind, which is built only when the site is published; locally the search box falls back to a simpler built-in search. The C.V. and faith essay load from Google Drive, so they need an internet connection.

### 4. Building the site without a server (rarely needed)

```bash
hugo --gc --minify
```

This writes the finished website into the `public/` folder, which is the same thing GitHub does when it publishes. Use it to check for errors; `public/` isn't saved to the repository.

## How publishing works

Every commit to the `main` branch triggers the workflow in `.github/workflows/deploy.yml`, which builds the site with Hugo, builds the search index with Pagefind, and publishes the result to GitHub Pages. Nothing needs to be run by hand.

**One-time setup** (before the first publish): in the repository on GitHub, go to **Settings → Pages** and set **Source** to **GitHub Actions**.

The public address is set by `baseURL` in `hugo.yaml` (currently `https://bdsmith147.github.io/benjamin_david_smith_website_source/`).

## What's in this repository

```
content/        page text: bio, research, teaching, faith, contact, papers, talks, software
data/           structured lists: C.V. entries, teaching, co-authors, Works tabs
static/         files served as-is: PDFs, favicons
assets/         processed files: stylesheet, your photo
layouts/        page templates (HTML); design changes happen here
i18n/en.yaml    button and label wording
templates/      blank files to copy when adding content (not part of the website)
hugo.yaml       site settings: name, menu, addresses
```
