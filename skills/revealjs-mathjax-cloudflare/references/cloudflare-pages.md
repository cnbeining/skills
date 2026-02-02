# Cloudflare Pages Deployment

## No-build static deployment

Reveal.js decks can be deployed as plain files with:
- **Build command:** (empty / none)
- **Output directory:** the folder containing `index.html` (e.g., `deck/`)

## Deploy options

### Option A: Cloudflare Pages UI (simplest)

1. Create a Pages project.
2. Point it at your repo.
3. Set output directory to your deck folder (or move the deck to the repo root).

### Option B: Wrangler CLI

Use Wrangler to deploy the folder that contains `index.html`:

- Provide an explicit **project name** to avoid “name undefined” warnings.
- Deploy the folder directly (no build step).

## Common gotcha: wrong base path

If your deck is deployed under a subpath, keep all asset URLs relative (as in the template) and avoid absolute `/...` paths.

