# 閃卡 (Shanka) — Chinese Flashcard App

A flashcard app for studying Chinese vocabulary, with stroke practice, character lookup, and spaced repetition.

**[Open the app](https://dan-leif.github.io/shanka/)**

---

## Choosing what to study

The **lesson selector** (top-left dropdown) lets you pick your deck:

- **Individual lessons** (e.g. Lesson 1-1) — vocabulary from a single lesson
- **All** — every card across all lessons
- **Review (★)** — only cards you've starred
- **Due for Review** — cards whose [spaced repetition](https://en.wikipedia.org/wiki/Spaced_repetition) interval has elapsed

The number in parentheses shows how many cards are in each deck.

---

## Study modes

The **mode selector** controls what appears on the front of each card:

| Option | Tests you on |
|--------|-------------|
| 英 | English|
| 正 | Traditional Chinese|
| 简 | Simplified Chinese|
| 拼 | Pinyin|

---

## Flashcard basics

- **Tap the card** to flip it and reveal the answer
- **Swipe left** to go to the next card
- **Swipe right** to go to the previous card

The answer side of each card shows Traditional Chinese, Simplified Chinese (if different), Pinyin, and the English meaning.

---

## Drawing pad

The bottom half of the screen is a **drawing pad** for stroke practice. Draw with your finger or stylus — strokes are white on a dark background.

- The pad clears automatically when you move to a new card
- Tap **✕** (top-left of the pad) to clear it manually

---

## Rating cards

Four rating buttons appear at the bottom of every card. These drive the **spaced repetition** system — cards you find harder come back sooner:

| Button | Meaning | Next review |
|--------|---------|-------------|
| **Again** | Completely forgot it | Right now |
| **Hard** | Got it, but with effort | ~1 day |
| **Good** | Recalled it comfortably | ~3 days |
| **Easy** | Knew it instantly | ~7+ days |

Cards you've rated before appear in the **Due for Review** deck when their interval is up.

---

## Starring cards ★

Tap the **★ button** to star the current card. Starred cards are added to the **Review (★)** deck, so you can focus on a custom set. Tap again to unstar.

---

## Shadow mode ◐

Tap the **◐ button** to enable shadow mode. The character is displayed as a **tracing guide** on the drawing pad.

- Tap an individual character on the current card to select that character and display it on the drawing pad
- When a character is selected, the **⌕ lookup button** appears (see below)
- Shadow mode temporarily disables flipping and rating cards

---

## Character lookup ⌕

In shadow mode, after tapping a character to select it, tap the **⌕** button to open a lookup menu with three options:

- **Wiki** — Stroke order, radicals, and character evolution
- **Mnemonics** — Creative mnemonic devices
- **HanziHero** — Another creative mnenomic system

---

## Progress dots

The row of dots at the bottom shows your progress through the current deck. Each dot represents one card:

- **White** — current card
- **Red** — rated Again
- **Orange** — rated Hard
- **Green** — rated Good
- **Blue** — rated Easy
- **Dark** — not yet rated

---

## Fullscreen & install

Tap **⛶** (toolbar) to toggle fullscreen mode.

On mobile, you can install 閃卡 to your home screen as a Progression Web App (PWA) for a full-screen, offline-capable app experience. Use your browser's "Add to Home Screen" option.

---

## Open-Source License

The [source code](https://github.com/dan-leif/shanka) for this app is freely available under an MIT open-source license.