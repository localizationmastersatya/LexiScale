# AGENTS.md

## Cursor Cloud specific instructions

This repository is a **fully static website** for LexiScale (a localization & AI data studio),
deployed via GitHub Pages (see `CNAME` → `lexiscale.com`). It has **no build system, no package
manager, and no dependencies**. The entire site is a single `index.html` (with inline CSS/JS)
plus `robots.txt`, `sitemap.xml`, and `CNAME`.

### Running locally (dev)
Serve the static files from the repo root with any static HTTP server, e.g.:

```
python3 -m http.server 8000
```

Then open http://localhost:8000/. Do **not** open `index.html` via the `file://` protocol —
some behavior (canonical links, relative asset paths) is best exercised over HTTP.

### Notable behavior / gotchas
- **Language switcher**: The header has a language dropdown (`[data-lang]` buttons: en/fr/es/pt/nl…).
  Selecting a language rewrites page copy client-side and updates the `?lang=` query param.
  Reloading with `?lang=fr` (etc.) loads the site in that language directly.
- **Contact form**: The contact form (`<form action="https://formspree.io/f/…">`) POSTs to a live
  Formspree endpoint. Do **not** actually submit it during testing — that sends real data to the
  production inbox. Verify it renders instead.

### Lint / test / build
There are no lint, test, or build steps — it is hand-authored static HTML. "Building" is just
committing the files; GitHub Pages serves them directly.
