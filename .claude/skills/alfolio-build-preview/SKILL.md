---
name: alfolio-build-preview
description: Build and locally preview this al-folio Jekyll site (wonkwonlee.github.io). Use whenever you need to run `jekyll build`/`serve`, reproduce the CI build locally, or see edits rendered before committing. Captures the exact Ruby/bundler/jupyter toolchain this repo requires, which is not obvious from the repo alone.
---

# Build & preview the al-folio site locally

This repo (al-folio theme) will NOT build with the system Ruby. Reproduce the CI
toolchain exactly (`.github/workflows/deploy.yml` pins Ruby 3.2.2, bundler cache,
and `pip3 install --upgrade jupyter`).

## One-time environment setup

1. **Ruby 3.2.2 via rbenv** (system Ruby 2.6 fails; `Gemfile.lock` needs bundler 2.5.7):
   ```bash
   brew install rbenv ruby-build
   rbenv install 3.2.2
   ```
   A repo-local `.ruby-version` (gitignored) already pins `3.2.2`.

2. **bundler + gems** (imagemagick is already installed via brew; the theme's
   `jekyll-imagemagick` needs it):
   ```bash
   export PATH="$HOME/.rbenv/versions/3.2.2/bin:$PATH"
   gem install bundler:2.5.7 --no-document
   bundle install                     # ~89 gems, builds mini_racer native ext
   ```

3. **jupyter in a venv** — the theme ships `assets/jupyter/blog.ipynb`, and
   `jekyll-jupyter-notebook` shells out to a `jupyter` CLI during build. macOS
   system Python is locked by PEP 668, so install into a venv (path is gitignored):
   ```bash
   python3 -m venv .venv
   .venv/bin/pip install --upgrade pip jupyter nbconvert
   ```
   Skipping this gives: `Conversion error: ... No such file or directory - jupyter`.
   That error is an environment gap, NOT a content bug.

## Build / serve (every time)

Put the venv AND rbenv ruby on PATH in the same command:
```bash
export PATH="$PWD/.venv/bin:$HOME/.rbenv/versions/3.2.2/bin:$PATH"
bundle exec jekyll build                                   # expect EXIT 0, no "Conversion error"
bundle exec jekyll serve --skip-initial-build --no-watch --port 4000
```
Wait for readiness with a poll, not a fixed sleep:
```bash
until curl -s -o /dev/null http://localhost:4000/; do sleep 2; done
```

## Local-only noise to ignore

- Broken GitHub readme-stats / trophy images on `/repositories/` — they call an
  external service; fine in production.
- A thumbnail that shows its `project thumbnail` alt on first paint — lazy-load
  timing, not a missing image. Re-screenshot to confirm.
- `Pagination: ... couldn't find any pagination page` warning — benign.

## Related

Verify the result with [[alfolio-preflight]]. For where content lives, see [[alfolio-content-map]].
