---
name: revealjs-mathjax-cloudflare
description: Build and debug a Reveal.js slide deck that renders LaTeX via MathJax and deploys as a static site to Cloudflare Pages (no build step). Use for tasks involving reveal.js decks, Markdown slides, MathJax/LaTeX rendering, print/PDF export (?print-pdf), or wrangler/pages deployment issues.
---

# Revealjs Mathjax Cloudflare

## Goal

Create or fix a Reveal.js deck that works as plain static files, supports Markdown slides, renders LaTeX via MathJax v3, and prints clean PDFs.

## Recommended layout

Use a self-contained folder so it can be deployed directly:

```
deck/
  index.html
  slides.md
  assets/              (images, etc.)
  vendor/revealjs/     (Reveal.js dist + plugins; vendored for reliability)
```

Template: `assets/deck-template/` (copy and adapt).

## Workflow

### 1) Scaffold the deck

- Copy `assets/deck-template/` to a new folder (e.g., `proposal_deck/`).
- Ensure `index.html` and `slides.md` live side-by-side (relative paths stay simple).

### 2) Vendor Reveal.js (recommended)

Vendoring avoids CDN 404s (common for `dist/print/*.css` and plugin paths).

- Put the Reveal.js distribution under `vendor/revealjs/` so these exist:
  - `vendor/revealjs/dist/reveal.js`
  - `vendor/revealjs/dist/reveal.css`
  - `vendor/revealjs/dist/print/{paper.css,pdf.css}`
  - `vendor/revealjs/plugin/{markdown,highlight,notes,math}/`

Reference commands and options: `references/vendoring.md`.

### 3) Enable Markdown + MathJax

- Use the Reveal Markdown plugin (`data-markdown="slides.md"`).
- Enable MathJax via the Reveal Math plugin (`RevealMath.MathJax3`) in `Reveal.initialize(...)`.
- Write math in `slides.md` using `\( ... \)` (inline) and `\[ ... \]` (display).

Template `index.html` already wires this up; modify only if you change paths.

### 4) Print/PDF export

- Load the correct print stylesheet based on `?print-pdf`.
- To export: open `deck/index.html?print-pdf`, then print to PDF from the browser.

### 5) Deploy to Cloudflare Pages

- Deploy the `deck/` folder as a static site (no build command).
- If using `wrangler pages deploy`, set an explicit project name to avoid “name undefined” warnings.

Reference: `references/cloudflare-pages.md`.

## Troubleshooting (fast checks)

- CSS/JS 404s: confirm `vendor/revealjs/` paths match `index.html` and that `dist/print/*.css` exists.
- Math not rendering: confirm `RevealMath.MathJax3` is in the plugin list and MathJax URL is reachable.
- Markdown not loading: confirm the `<section data-markdown="slides.md">` path and that the Markdown plugin script loads.

Deeper notes: `references/troubleshooting.md`.
