# 閃卡 (Shanka) — Chinese Flashcard PWA

Minimal Chinese flashcards with draw pad and shadow mode.

**[Dev](https://dan-leif.github.io/shanka-dev/) · [Production](https://dan-leif.github.io/shanka/)**

---

## Features

- **474 vocabulary items** across 22 lessons (Lesson 1-1 through 2-5), each with Traditional Chinese, Simplified Chinese, Pinyin, and English
- **SM-2 spaced repetition** — four ratings (Again / Hard / Good / Easy) compute next review intervals; a "Due for Review" deck surfaces overdue cards
- **4 study prompt modes** — English (英), Traditional (正), Simplified (简), Pinyin (拼)
- **Shadow mode** (◐) — the answer character is shown at 14% opacity as a tracing guide; tap to select individual characters
- **Drawing pad** — HTML5 Canvas overlay for stroke practice, clears on card change
- **Character lookup** — tap ⌕ in shadow mode to open Dong Chinese Wiki, Mnemonics, or HanziHero
- **Star (★) cards** to build a focused review deck; count shown in the lesson selector
- **Progress dots** on each lesson, color-coded by SM-2 rating (Again/Hard/Good/Easy)
- **PWA** — installable to home screen, full offline support via service worker

---

## Project Structure

```
index.html            — entire app (~1,250 lines of HTML + CSS + JS, no build step)
vocab-1.js            — vocabulary data as window.VOCAB, 474 entries across 22 lessons
sw.js                 — service worker, cache-first strategy, dev/prod cache isolation
manifest.webmanifest  — PWA config (name: 閃卡, theme: orange, display: fullscreen)
tw-kai.ttf            — TW Kai Traditional Chinese font
icons/                — icon-192.png, icon-512.png
.github/workflows/    — GitHub Actions auto-deploy to GitHub Pages on push to main
```

---

## Getting Started

No build system or dependencies. Just open the file:

```bash
# Quickest — open directly in browser (no service worker)
open index.html

# Better — serve locally (enables service worker + PWA install)
npx serve .
# then visit http://localhost:3000
```

The service worker requires either `localhost` or HTTPS to activate.

---

## Deployment

Two repos, two environments:

| Repo | URL | Purpose |
|------|-----|---------|
| `dan-leif/shanka-dev` | `dan-leif.github.io/shanka-dev` | Development / staging |
| `dan-leif/shanka` | `dan-leif.github.io/shanka` | Production |

GitHub Actions deploys automatically on every push to `main` in each repo. The service worker auto-detects environment and uses separate caches (`shanka-dev-v1` vs `shanka-v1`) so the two instances never interfere.

---

## Vocabulary Schema

```js
window.VOCAB = {
  "Lesson 1-1": [
    { en: "you", trad: "你", simp: "你", py: "nǐ" },
    { en: "good; well", trad: "好", simp: "好", py: "hǎo" },
    ...
  ],
  ...
}
```

To add vocabulary, append entries to `vocab-1.js` following the schema above.

---

## SRS Notes

Spaced repetition is implemented via the SM-2 algorithm in `calculateNextReview()` in `index.html`. Ratings 0–3 (Again/Hard/Good/Easy) adjust an `ease_factor` and `interval` (in days). State is persisted in IndexedDB (`shan_srs` database):

- `scheduler` store — per-card SRS state (`interval`, `ease_factor`, `reps`, `next_due`)
- `reviews` store — full audit log of every review with timestamp and response time

Starred cards are stored in `localStorage` under `shan_review_v1`.

---

## License

MIT — see [LICENSE](LICENSE).
