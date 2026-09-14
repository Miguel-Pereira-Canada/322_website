# CISC 322 Group Project Site

A static site for our CISC 322 (Software Architecture) group project, hosted on
GitHub Pages. Plain hand-written HTML and CSS: no build step, no frameworks, no
dependencies. The repository is servable exactly as it is.

**Live site:** https://miguel-pereira-canada.github.io/322_website/

## Repository layout

```
index.html        The whole site. Header, members, deliverables.
styles.css        All styling. No CDN links, no frameworks.
deliverables/     PDFs, slide decks, and reports go in here.
  .gitkeep        Keeps the empty folder in git. Do not delete.
.nojekyll         Tells GitHub Pages to serve files as-is, skipping Jekyll.
```

All links use relative paths, so the site works correctly under the GitHub Pages
project subpath (`/322_website/`) as well as from a local folder.

## Adding a deliverable

1. Put the file in `deliverables/`. Use a lowercase, hyphenated filename with no
   spaces, for example `assignment-1-conceptual-architecture.pdf`. Spaces and
   accented characters work badly in URLs.
2. Open `index.html` and find the `<ul class="deliverable-list">` block inside the
   deliverables section.
3. Copy the commented-out example `<li>` block, paste it at the top of the list,
   and remove the `<!--` and `-->` comment markers around it.
4. Edit four things in the block you just pasted:
   - `href` - the filename you added under `deliverables/`
   - the link text - the title shown on the page
   - `datetime` - the date as `YYYY-MM-DD` (not displayed, used by browsers and search engines)
   - the visible date text, and the type label in `<span class="deliverable-kind">`
5. The first time you add one, delete the
   `<li class="deliverable-empty">No deliverables posted yet.</li>` line.
6. Commit and push. GitHub Pages redeploys automatically, usually within a minute.

A finished entry looks like this:

```html
<li class="deliverable">
  <a class="deliverable-title" href="deliverables/assignment-1-conceptual-architecture.pdf">Assignment 1: Conceptual Architecture</a>
  <p class="deliverable-meta">
    <time datetime="2026-10-06">October 6, 2026</time>
    <span class="deliverable-kind">PDF</span>
  </p>
</li>
```

## Running the site locally

The quickest check is to open `index.html` directly in a browser. Because every
path is relative, the page and its stylesheet load fine from the filesystem.

To preview it the way GitHub Pages actually serves it, run a local web server
from the repository root:

```sh
python3 -m http.server 8000
```

Then visit http://localhost:8000 and press Ctrl+C in the terminal when finished.
Use a local server if you are testing anything path-related, since `file://` URLs
behave differently from real HTTP in some browsers.

## Editing conventions

- Keep it dependency-free. No npm, no frameworks, no CDN `<link>` or `<script>` tags.
- Never start a path with `/`. A leading slash breaks the site under the
  `/322_website/` subpath, even though it looks fine locally.
- Check narrow widths before pushing. The layout is responsive down to phone size;
  your browser's device toolbar is enough to confirm it.
