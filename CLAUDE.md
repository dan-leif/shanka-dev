# 閃卡 (Shanka) — Claude Context

## What this project is
閃卡 is a Chinese language learning flashcard PWA. Vanilla HTML/CSS/JS, no build system, no npm. The entire app is `index.html` (~1,250 lines) plus `vocab-1.js` (~6,000 lines of vocabulary data). Deployed to GitHub Pages via GitHub Actions on every push to `main`.

## Two-repo dev workflow

There are **two local folders and two GitHub repos**:

| Folder | Repo | GitHub Pages URL | Purpose |
|--------|------|-----------------|---------|
| `c:\DEV\shanka-dev\` | `dan-leif/shanka-dev` | `dan-leif.github.io/shanka-dev` | Development / staging |
| `c:\DEV\shanka\` | `dan-leif/shanka` | `dan-leif.github.io/shanka` | Production |

**All development happens in `shanka-dev\`.** Changes are promoted to `shanka\` manually when ready for production.

### Push to dev
```bash
# in c:\DEV\shanka-dev\
git push origin main
```

### Promote to production
```bash
# copy changed files
cp c:/DEV/shanka-dev/index.html c:/DEV/shanka/
cp c:/DEV/shanka-dev/vocab-1.js c:/DEV/shanka/
# (add any other changed files)

cd c:/DEV/shanka
git add -p        # review diff before committing
git commit -m "promote: <description>"
git push origin main
```

**Never develop directly in `c:\DEV\shanka\`.** It receives only deliberate promotions.

## Service worker cache isolation
`sw.js` auto-detects environment: `shanka-dev` uses cache `shanka-dev-v1`, `shanka` uses `shanka-v1`. No changes needed when promoting.

## Claude's working directory
Claude is typically opened with `c:\DEV\shanka-dev\` as the root. To work on the production folder, use absolute paths (`c:\DEV\shanka\...`) or ask the user to open a new Claude session rooted at `c:\DEV\shanka\`.

## Key files
- `index.html` — entire app (HTML + CSS + JS)
- `vocab-1.js` — vocabulary data as `window.VOCAB`
- `sw.js` — service worker (cache-first, offline support)
- `manifest.webmanifest` — PWA config (name: 閃卡, theme: orange)
- `.github/workflows/deploy.yml` — GitHub Pages auto-deploy (identical in both repos)

## Vocabulary schema
```js
window.VOCAB = {
  "Lesson 1-1": [
    { en: "you", trad: "你", simp: "你", py: "nǐ" },
    ...
  ],
  ...
}
```
22 lessons total, 474 entries, spanning Lesson 1-1 through Lesson 2-5.

## Current version
v4.1 — shown on load screen. Update `<div id="loadingVersion">` in `index.html` when bumping.
