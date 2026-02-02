# Troubleshooting

## 404 errors for Reveal assets

Symptoms:
- Blank page
- Console shows missing `reveal.js`, `markdown.js`, or `dist/print/*.css`

Fix:
- Prefer vendoring (`vendor/revealjs/...`) so `index.html` references local files.
- Ensure the on-disk folder names match the URLs exactly (case-sensitive).

## Math not rendering

Symptoms:
- `\( ... \)` shows literally
- No errors but equations never typeset

Fix:
- Confirm `vendor/revealjs/plugin/math/math.js` loads.
- Confirm `RevealMath.MathJax3` is in `plugins: [...]`.
- Confirm MathJax URL is reachable and not blocked.

## Markdown not loading

Symptoms:
- Slides show a single blank slide
- Network shows `slides.md` 404

Fix:
- Ensure `slides.md` is in the same folder as `index.html` (or update `data-markdown`).
- Confirm `vendor/revealjs/plugin/markdown/markdown.js` loads.

## Print/PDF is unstyled

Symptoms:
- Printed PDF lacks layout/formatting

Fix:
- Open with `?print-pdf` and ensure `dist/print/pdf.css` loads.
- If `paper.css` / `pdf.css` is missing, your Reveal.js distribution is incomplete.

