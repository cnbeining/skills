# Codex skills

This repo contains reusable Codex skills (each under `skills/<skill-name>/`).

## Included skills

- `skills/reviewer-feedback-integrator/`: Turn reviewer comments into an action matrix, concrete manuscript/experiment edits, and a response-to-reviewers draft.
- `skills/revealjs-mathjax-cloudflare/`: Create/debug a Reveal.js deck that renders LaTeX via MathJax and deploys as static files to Cloudflare Pages (including print/PDF export).

## Install into Codex (local)

By default, Codex uses `$CODEX_HOME/skills` (commonly `~/.codex/skills`).

To install from this repo:

```bash
mkdir -p ~/.codex/skills
cp -R skills/reviewer-feedback-integrator ~/.codex/skills/
cp -R skills/revealjs-mathjax-cloudflare ~/.codex/skills/
```

Restart Codex to pick up new skills.

## Package / share a skill (optional)

The `skill-creator` system skill includes a packager script:

```bash
mkdir -p dist
python ~/.codex/skills/.system/skill-creator/scripts/package_skill.py skills/reviewer-feedback-integrator dist
python ~/.codex/skills/.system/skill-creator/scripts/package_skill.py skills/revealjs-mathjax-cloudflare dist
```

Notes:
- If packaging fails with `ModuleNotFoundError: No module named 'yaml'`, install PyYAML for the Python you’re using: `python -m pip install pyyaml`.
- A `.skill` file is just a zip; install it by extracting into `~/.codex/skills/` (e.g., `python -m zipfile -e dist/<skill>.skill ~/.codex/skills`).

## Develop / add a new skill

Initialize a new skill folder using `skill-creator`:

```bash
python ~/.codex/skills/.system/skill-creator/scripts/init_skill.py my-skill --path skills --resources references,assets
```

Guidelines:
- Put all trigger wording in `SKILL.md` frontmatter `description:` (single line).
- Keep `SKILL.md` frontmatter to only `name` and `description`.
- Use `references/` for detailed docs and `assets/` for templates/boilerplate.
