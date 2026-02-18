# 🇳🇱 Werkwoorden Quiz

A mobile-friendly multiple-choice quiz app for Dutch learners, focusing on **samengestelde werkwoorden** (compound/separable verbs) at B1+ level.

**[→ Try the live quiz](https://chardrizard.github.io/samengestelde-werkwoorden-quiz/)**

![Screenshot](og-image.png)

---

## What is this?

Dutch compound verbs are notoriously tricky — *opnemen*, *aannemen*, *afnemen*, and *innemen* all use "nemen" but mean completely different things. This quiz helps you practice distinguishing between them through contextual sentences.

**160+ questions** across multiple verb themes including:

| Theme | Verbs covered |
|-------|--------------|
| 🚪 **-komen** | aankomen · opkomen · bijkomen · uitkomen · voorkomen · meekomen · achterkomen · langskomen |
| 📌 **-zetten** | aanzetten · opzetten · afzetten · doorzetten · neerzetten · inzetten · voortzetten · uitzetten |
| 🤲 **-nemen** | opnemen · aannemen · afnemen · innemen · meenemen · toenemen |
| 🎯 **-halen** | ophalen · afhalen · inhalen · achterhalen · binnenhalen · uithalen |

New themes are added by dropping a JSON file into `data/` — see [Adding themes](#adding-a-new-theme) below.

## Features

- **Mobile-first dark UI** — designed for phone-in-hand study sessions
- **Choose your session length** — 10, 20, or all questions per theme
- **Mix mode** — random questions from all themes combined
- **Instant feedback** — correct/wrong explanations for every answer, including why the wrong options are wrong
- **Hints** — optional hints if you're stuck
- **Shuffled questions** — different order every attempt
- **Review wrong answers** — see all mistakes at the end with explanations
- **Full keyboard navigation** — A/B/C/D to answer, H for hint, Enter/Escape to navigate
- **Separated data & UI** — themes and questions live in `data/`, independently editable
- **Zero dependencies** — single HTML file + JSON, no build step, no backend
- **Works offline** — once loaded, no internet needed

## Target level

**B1+ / B2** — suitable for learners who already know basic Dutch grammar and are working on expanding vocabulary and understanding idiomatic usage of separable verbs.

## Project structure

```
werkwoorden-quiz/
├── index.html                  ← UI (HTML + CSS + JS, fetches from data/)
├── site.webmanifest            ← PWA manifest
├── og-image.png                ← Social sharing preview image
├── data/
│   ├── themes.json             ← Theme registry (id, label, emoji, color)
│   ├── komen.json              ← Questions for -komen theme
│   ├── zetten.json             ← Questions for -zetten theme
│   ├── nemen.json              ← Questions for -nemen theme
│   └── halen.json              ← Questions for -halen theme
├── assets/
│   └── icons/                  ← Favicons and PWA icons
│       ├── favicon-16x16.png
│       ├── favicon-32x32.png
│       ├── apple-touch-icon.png
│       ├── android-chrome-192x192.png
│       ├── android-chrome-512x512.png
│       └── site.webmanifest    ← (unused, kept for reference)
├── README.md
├── LICENSE
└── .gitignore
```

**Architecture:** `index.html` loads `data/themes.json` on startup to build the home screen, then lazily fetches `data/{themeId}.json` when the user starts a quiz. This means you can add new themes without touching the UI code, and the browser caches each file independently.

## Adding or editing questions

Open the relevant file in `data/` (e.g. `data/nemen.json`). Each question looks like this:

```json
{
  "sentence": "De patiënt is gisteren in het ziekenhuis ______.",
  "options": ["opgenomen", "aangenomen", "ingenomen", "afgenomen"],
  "correct": 0,
  "explanation": "'Opnemen' = in het ziekenhuis laten blijven.",
  "wrongExplanations": {
    "1": "'Aangenomen' = geaccepteerd (baan).",
    "2": "'Ingenomen' = medicijn slikken.",
    "3": "'Afgenomen' = verminderen."
  },
  "hint": "Denk aan wat er in een ziekenhuis gebeurt."
}
```

- `correct` is the 0-based index of the right answer in the `options` array
- `wrongExplanations` keys are the string indices of wrong options
- Save, commit, push — GitHub Pages updates automatically

## Adding a new theme

1. Create a new question file in `data/`, e.g. `data/geven.json` with an array of questions
2. Add the theme to `data/themes.json`:

```json
{
  "id": "geven",
  "label": "-geven",
  "description": "meegeven · opgeven · aangeven · uitgeven · doorgeven · afgeven",
  "emoji": "🎁",
  "color": "#8B5CF6"
}
```

3. That's it — the home screen picks it up automatically

## Tech stack

Intentionally minimal:

- Single HTML file with inline CSS and vanilla JS
- External JSON files in `data/` for all quiz content
- No framework, no build tools, no npm
- Google Fonts (DM Sans + DM Mono)
- Hosted on GitHub Pages (free)

## Run locally

```bash
git clone https://github.com/chardrizard/samengestelde-werkwoorden-quiz.git
cd samengestelde-werkwoorden-quiz
# Need a local server because of fetch() — opening file:// won't work
python3 -m http.server 8000
# Then visit http://localhost:8000
```

## Roadmap

- [ ] Add more verb themes (-geven, -staan, -slaan, -vallen)
- [ ] localStorage progress tracking
- [ ] Spaced repetition for wrong answers
- [ ] PWA support for install-to-homescreen
- [ ] Custom domain

## Contributing

Found a question with a wrong explanation or an unnatural sentence? Edit the relevant JSON file in `data/` and open a PR. Native speaker corrections are especially welcome.

## License

MIT — use it, fork it, adapt it for other languages.

---

Built as a study tool for the Dutch diaspora community 🧡
