# Vendoring Reveal.js (recommended)

## Why vendor

Vendoring avoids runtime failures from CDN path changes and missing files (especially `dist/print/*.css` and plugin assets). Cloudflare Pages serves static files reliably when everything is local.

## Target folder structure

Place the Reveal.js distribution so these paths exist:

- `vendor/revealjs/dist/reveal.js`
- `vendor/revealjs/dist/reveal.css`
- `vendor/revealjs/dist/print/paper.css`
- `vendor/revealjs/dist/print/pdf.css`
- `vendor/revealjs/plugin/markdown/markdown.js`
- `vendor/revealjs/plugin/highlight/highlight.js`
- `vendor/revealjs/plugin/notes/notes.js`
- `vendor/revealjs/plugin/math/math.js`

## How to vendor (choose one)

### Option A: Download a release zip (manual)

1. Download a Reveal.js release archive.
2. Extract it.
3. Rename/move the extracted folder to `vendor/revealjs/`.

### Option B: Use npm locally (requires a build toolchain, not ideal for “no build”)

If you already have Node tooling, install Reveal.js and copy `dist/` + `plugin/` into `vendor/revealjs/` for static hosting.

## Sanity check

Open `vendor/revealjs/dist/reveal.js` in your editor and confirm the file exists and is non-empty. If the browser console shows 404s, fix the on-disk paths first.

