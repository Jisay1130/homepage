# al-folio Bootstrap

Use this skill when a user asks an agent to create, configure, or personalize a new al-folio v1.x website.

## Workflow

1. Read `AGENTS.md` and `docs/BOUNDARIES.md` before editing.
2. Keep the starter small: customize `_config.yml`, `_data`, content collections, and site assets first.
3. Leave runtime behavior in plugin repos. Do not copy plugin-owned layouts, includes, Sass, JavaScript, or assets into the starter unless the user intentionally wants a local override.
4. For local visual/content customization, prefer:
   - `_config.yml` feature flags and site metadata
   - `_data/*.yml`
   - `_pages`, `_posts`, `_projects`, `_news`, `_teachings`, `_bibliography`
   - local `_includes`, `_layouts`, and `_sass` overrides only when config/content cannot express the change
5. Run validation before handing work back:

```bash
npm ci
npm run lint:prettier
bundle exec al-folio upgrade audit --no-fail
bundle exec jekyll build --baseurl /al-folio
```

## Jisung Kim homepage notes

This repository is a project-page site for Jisung Kim, not the upstream al-folio demo. Keep personal overrides in `_config_personal.yml` and load it after `_config.yml`.

- Local Docker preview: `docker compose up`, then open `http://localhost:8081/homepage/`.
- Local Ruby preview: `bundle exec jekyll serve --config _config.yml,_config_personal.yml`.
- Production workflow already builds with `bundle exec jekyll build --config _config.yml,_config_personal.yml`.
- Public page URL is `https://jisay1130.github.io/homepage/`; keep the GitHub account/repository URL unless the repository is renamed.
- Personal pages to edit first: `_pages/about.md`, `_pages/research.md`, `_pages/cv.md`.
- `_config_personal.yml` excludes upstream demo posts, projects, books, teaching pages, and assets from the public site.

## Routing

- Starter wiring/docs/examples/tests: edit `al-folio`.
- Shared layouts/includes/assets: use `al_folio_core`.
- CV rendering: use `al_folio_cv`.
- Distill runtime: use `al_folio_distill`.
- Search/icons/math/comments/analytics/citations/external posts/newsletter/charts/images: use the owning `al-*` plugin repo.

## Handoff

Summarize changed files, validation results, and any local overrides created.
