# scaralbi.github.io

Personal website + blog, Jekyll on GitHub Pages.

**Live:** https://scaralbi.github.io

## Structure

```
_config.yml         ← Jekyll config (collections, permalinks, plugins)
_layouts/           ← page templates (default, post, recipe, page, tag)
_posts/             ← blog posts
_recipes/           ← recipe pages (mirrored from private/cooking/recipes/)
assets/             ← CSS, images, fonts
*.md                ← top-level pages (about, blog, research, recipes, resources)
```

## Pages / Collections

| Path | Source | Notes |
|---|---|---|
| `/` | `index.md` | Homepage |
| `/about` | `about.md` | Bio |
| `/blog` | `blog.md` + `_posts/` | Filterable blog list |
| `/research` | `research.md` | Publications + PhD |
| `/recipes` | `recipes.md` + `_recipes/` | Filterable recipe library (since Apr 2026) |
| `/resources` | `resources.md` | Code + essays |
| `/tags/:name/` | `_layouts/tag.html` | Tag archive (jekyll-archives) |

## Recipes site (`/recipes`)

- Source of truth: `private/cooking/recipes/` in the parent personal-os repo (NOT here)
- Sync via `python3 scripts/sync-recipes.py` from the parent repo root
- Each recipe is a markdown file with YAML frontmatter (title, tags, time, macros)
- Layout: `_layouts/recipe.html` renders frontmatter → macros table + tag chips + stats
- Index: `recipes.md` has client-side JS for tag/macro/diet filtering

## Local development

```bash
bundle install
bundle exec jekyll serve   # http://127.0.0.1:4000
```

## Critical config notes

- The Jekyll config file MUST be `_config.yml` (with underscore). A plain `config.yml` is silently ignored, the site will fall back to defaults and any custom collections/permalinks won't work.
- Don't commit `Gemfile.lock` (it's gitignored). The github-pages gem updates frequently and stale lockfiles cause build failures.
- Don't put two YAML fields on the same line in any frontmatter, Jekyll's parser fails silently.

## Deploy

Push to `master` → GitHub Pages auto-builds and deploys (~30–60s).
