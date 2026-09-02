# Kaharin Translator

A self-contained, client-side translator for **Kaharin** — the liturgical language of the Kaharim, featured in the game *Tibilidis re Io*.

**No server, no installs, no build step.** Everything (dictionary, grammar engine, styling) lives in a single HTML file that runs entirely in the browser — so it works on phones, tablets, desktops, and can be opened offline.

**▶ Live here: <https://delgadoirene-star.github.io/Kaharin-translator/>**

---

## Features

| Feature | Description |
|---------|-------------|
| **Translate** | Bidirectional English ↔ Kaharin with per-word glosses and grammar notes |
| **Listen** 🔊 | Audible pronunciation of the translated Kaharin using the Web Speech API (Spanish-compatible pure vowels), inspired by the Kaharin phonetics rules |
| **Dictionary** | Browse all ~267 headwords with part-of-speech filters and live search |
| **Conjugator** | Full verb tables: person × tense × mood × aspect |
| **Grammar** | Quick reference: word order, negation, articles, possession, plurals, verb morphology, adpositions, compounds, questions |

---

## Usage

1. Go to the live URL (or open `index.html` directly in any browser).
2. On the **Translate** tab, type English or Kaharin into either box and click the matching button.
3. Press **🔊 Listen** to hear the translation spoken aloud.
4. Use the **Dictionary** tab to explore the lexicon, and the **Conjugator** / **Grammar** tabs for reference.

> **Audio note:** The translator uses the browser's built-in speech synthesis, so it works offline with no external files. For the closest match to Kaharin's sound (Spanish pure monophthongs, tapped /r/, soft /h/), it selects a **Spanish (es)** voice when available. You can choose any installed voice later if you prefer a different accent.

---

## The language

Kaharin blends **Spanish pure vowels**, **Kurdish chest-resonant tone**, and **Byzantine liturgical cadence** (an "ison drone" base with penultimate stress). Core sacred roots keep hard /k/, soft /h/, and tapped /ɾ/; longer administrative words soften intervocalic /b/→/v/, /g/→/ɣ/, and the *eu* diphthong→[ev].

Example phrase in the "Imperial Temple Blend":

> **Eo irhi re Kaharin em eugo mese irhi'ri semeugo eo pliria ferag'es tibilidis'e irhi**
> — /eo̯ ˈiɾ.hi ɾe ka.ha.ˈɾin em ˈev.go ˈme.se ˈiɾ.hi.ɾi se.ˈmev.go eo̯ ˈpli.ɾja fe.ˈɾa.ɣes ti.vi.li.ˈdi.se ˈiɾ.hi/

---

## How the dictionary is maintained

The translator's dictionary (`const D = { ... }` inside `index.html`) is **auto-generated** from the authoritative language files in the parent game project:

- `game-data.js` — the working lexicon
- `kaharin-word-families.md`, `kaharin-cheatsheet.md`, `kaharin-practice.md` — the markdown lexicons that new words are added to

To regenerate and republish after adding words, run the wrapper (from the game project):

```bash
bash publish.sh
```

This runs `node sync-translator.js` (which melds new lexemes from the markdown into `game-data.js` and rebuilds `index.html`), copies the result here, commits, and pushes to GitHub Pages.

> Do **not** hand-edit the `const D = { ... }` block — it is regenerated from source.

---

## Tech

- Single static HTML file — no frameworks, no dependencies
- Web Speech API (`SpeechSynthesisUtterance`) for audio
- Finite dictionary + rule-based grammar engine (SVO/VSO, enclitic articles/possession/plurals, 6-slot verb morphology)
- Hosted on **GitHub Pages** from the `main` branch

---

*Kaharin — Liturgical language of the Kaharim — Io re!*
