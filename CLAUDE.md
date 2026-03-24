# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A static recipe website that renders Markdown recipe files in the browser. No build step, no backend, no package manager — just HTML, CSS, and JavaScript served via GitHub Pages.

## Key Commands

**Regenerate `recipes.json`** (required after adding or removing recipe files):
```bash
./update-recipes.sh
```

**Preview locally** (any static file server works):
```bash
python3 -m http.server 8080
```

The CI pipeline runs `update-recipes.sh` automatically on push to master and then deploys to GitHub Pages via Jekyll.

## Architecture

- `recipes/*.md` — recipe files (one per recipe, kebab-case filenames)
- `recipes.json` — auto-generated flat JSON array of recipe filenames; consumed by `list-recipes.js` at runtime
- `index.html` + `list-recipes.js` — recipe index page with alphabetical nav
- `recipe.html` + `create-recipe.js` — single recipe view; fetches and renders the `.md` file client-side using Showdown.js
- `utils.js` — `linkify()` and `getDomain()` helpers used by `create-recipe.js`
- `images/*.jpg` — optional hero images; named identically to their recipe file (e.g. `brigadeiro-de-cacau.jpg` for `brigadeiro-de-cacau.md`)

Recipe rendering is entirely client-side: `recipe.html` reads the `#hash` from the URL, fetches the corresponding `.md` file, converts it to HTML with Showdown.js, and injects it into the DOM.

Site configuration (`helpUrls`, hero image toggle, `autoUrlSections`, `shortenUrls`) lives in the `<script>` block at the top of `recipe.html`.

## Recipe Format

Follow this structure (sections must use lowercase `##` headers exactly as shown):

```markdown
# Título da Receita
Subtítulo opcional

## info
* Cerca de XX minutos
* X porções

## ingredientes
* Item 1
* Item 2

## passos
1. Passo um
2. Passo dois

## notas
* Dica opcional

## fonte
* https://url-da-fonte.com
```

Sections `info`, `notas`, and `fonte` are optional. Ingredient subsections are supported but must **not** use Markdown headers — they are plain text subgroup labels. URLs in the `fonte` section are auto-linkified.
