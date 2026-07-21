---
name: alfolio-content-map
description: Map of where content lives in this al-folio site (wonkwonlee.github.io) — which file to edit for the CV, about page, news, projects, name/branding, and navigation. Use before editing site content so you change the right source. Records non-obvious wiring (e.g. the CV page is driven by resume.json, not _data/cv.yml).
---

# Content map for the al-folio site

Where to edit what. The non-obvious parts are called out.

## Home / about
- `_pages/about.md` — front-matter `subtitle` is the tagline under the name;
  `profile.more_info` is the sidebar block; `profile.image` is `assets/img/prof_pic.jpeg`.
  Body is Markdown. `news: true` renders the announcements list here.

## Name & branding — **not a single field**
- Site header, footer copyright, and `<title>` are built from `_config.yml`
  `first_name` + `middle_name` + `last_name` (first name is bolded).
  Current: `first_name: Raymond`, `middle_name:` blank, `last_name: Lee` → "**Raymond** Lee".
- `_config.yml` `scholar.first_name`/`scholar.last_name` is **separate** — it only
  controls author bolding in the bibliography (publications are under "Wonkwon Lee").
  Do NOT change it to match the display name.
- `email`, `description`, `keywords`, `contact_note` also live in `_config.yml`.

## CV page — **driven by JSON, not YAML**
- `_pages/cv.md` just sets `cv_pdf:` (the download button) and `toc`.
- The actual CV content is **`assets/json/resume.json`** (loaded via `jekyll-get-json`;
  see `jekyll_get_json` / `jsonresume` in `_config.yml`). Sections: `basics`, `work`,
  `education`, `projects`, `publications`, `skills`, `languages`, `awards`.
- `_data/cv.yml` is **fully commented out and unused** — ignore it.
- Rendering templates: `_includes/resume/*.liquid`. Note `basics.liquid` intentionally
  skips `location`, `image`, `profiles`, so a `location` in resume.json won't show.

## News / announcements
- `_news/announcement_*.md`, `inline: true`, ordered by `date:`. Shown on the home
  page and `/news/`. `announcements.limit` in `_config.yml` caps the home list.

## Projects
- `_projects/*.md`. Front-matter: `title`, `description`, `img` (optional),
  `importance` (sort order, ascending), `category`.
- `_pages/projects.md` `display_categories: [engineering, research]` sets section
  order. Layout is per-category: `engineering` renders 2-col horizontal cards
  (`projects_horizontal.liquid`), others render the 3-col grid (`projects.liquid`) —
  controlled by `{% if page.horizontal or category == "engineering" %}`.
- Cards render fine without `img` (both templates guard `{% if project.img %}`).

## Publications & repositories
- Publications: `_bibliography/papers.bib` (jekyll-scholar). Page: `_pages/publications.md`.
- Repositories: `_data/repositories.yml` (`github_users`, `github_repos`). Page: `_pages/repositories.md`.

## Navigation order
- Each `_pages/*.md` sets `nav_order`. Current: about → projects (2) →
  repositories (3) → publications (4) → cv (5).

## Related
Build/preview with [[alfolio-build-preview]]; verify with [[alfolio-preflight]].
