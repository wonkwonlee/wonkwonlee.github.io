---
name: alfolio-preflight
description: Pre-deploy verification checklist for this al-folio site (wonkwonlee.github.io). Use after editing site content and before committing/pushing, to confirm the build is clean, links resolve, pages render, and no stale content leaked. Complements the build skill with an evidence-based sign-off.
---

# Pre-deploy checklist for the al-folio site

Run after content edits, before committing/pushing. Assumes the toolchain from
[[alfolio-build-preview]] is set up. Prefix build/serve commands with:
```bash
export PATH="$PWD/.venv/bin:$HOME/.rbenv/versions/3.2.2/bin:$PATH"
```

## 1. Clean build
```bash
bundle exec jekyll build 2>&1 | grep -v "Imagemagick:" | grep -iE "error|done in" ; echo "EXIT=${pipestatus[1]}"
```
Pass = `EXIT=0` and **no `Conversion error`** line. A `jupyter` conversion error
means the venv isn't on PATH — fix the environment, don't treat it as a content bug.

## 2. Links & assets resolve (serve first, then poll)
```bash
bundle exec jekyll serve --skip-initial-build --no-watch --port 4000 &
until curl -s -o /dev/null http://localhost:4000/; do sleep 2; done
for u in / /projects/ /cv/ /publications/ /repositories/ \
         /assets/pdf/Raymond_Lee_AI_Infrastructure_Applied_AI_Resume.pdf; do
  printf "%-64s" "$u"; curl -s -o /dev/null -w "%{http_code}\n" "http://localhost:4000$u"
done
```
All should be `200`. Add any new internal link or PDF you referenced this round.

## 3. Rendered spot-check (Playwright MCP)
Screenshot `/`, `/projects/`, `/cv/` and eyeball:
- Header/footer/title show the intended display name (from `_config.yml` name fields).
- `/projects/` — engineering section on top (2-col), research below (3-col).
- `/cv/` — driven by `assets/json/resume.json`; confirm new work/projects/skills appear.
- Navigation order matches intent.

Verify CV text without trusting a small screenshot:
```bash
python3 - <<'PY'
import re,html
t=html.unescape(re.sub(r'<[^>]+>',' ',open('_site/cv/index.html').read()))
for k in ["Network Engineer","ChangeSafe","AI Infrastructure"]:
    print(("OK  " if k in t else "MISS"), k)
PY
```

## 4. No stale content leaked
This site was repositioned away from a PhD-applicant framing. Confirm old artifacts
aren't referenced in the built output:
```bash
grep -rl "WLee-SOP\|WLee-PS\|Trustworthy AI\|System Engineer" _site/ 2>/dev/null || echo "clean"
```
(The SOP/PS PDFs still exist on disk by choice; just make sure nothing links to them.)

## 5. Clean up before commit
```bash
rm -rf _site .playwright-mcp
git status --short   # expect only intended source changes; .omc/ and .venv are ignored
```
