# 🇳🇱 Werkwoorden Quiz

A mobile-friendly multiple-choice quiz app for Dutch learners, focusing on **samengestelde werkwoorden** (compound/separable verbs) at B1+ level.

**[→ Try the live quiz](https://chardrizard.github.io/werkwoorden-quiz/)**

![Screenshot](og-image.png)

---

## What is this?

Dutch compound verbs are notoriously tricky — *opnemen*, *aannemen*, *afnemen*, and *innemen* all use "nemen" but mean completely different things. This quiz helps you practice distinguishing between them through contextual sentences.

**160 questions** across 4 verb themes:

| Theme | Verbs covered | Questions |
|-------|--------------|-----------|
| 🚪 **-komen** | aankomen · opkomen · bijkomen · uitkomen · voorkomen · meekomen · achterkomen · langskomen | 40 |
| 📌 **-zetten** | aanzetten · opzetten · afzetten · doorzetten · neerzetten · inzetten · voortzetten · uitzetten | 40 |
| 🤲 **-nemen** | opnemen · aannemen · afnemen · innemen · meenemen · toenemen | 40 |
| 🎯 **-halen** | ophalen · afhalen · inhalen · achterhalen · binnenhalen · uithalen | 40 |

## Features

- **Mobile-first dark UI** — designed for phone-in-hand study sessions
- **Instant feedback** — correct/wrong explanations for every answer, including why the wrong options are wrong
- **Hints** — optional hints if you're stuck
- **Shuffled questions** — different order every attempt
- **Review wrong answers** — see all mistakes at the end with explanations
- **Zero dependencies** — single HTML file, no build step, no backend
- **Works offline** — once loaded, no internet needed

## Target level

**B1+ / B2** — suitable for learners who already know basic Dutch grammar and are working on expanding vocabulary and understanding idiomatic usage of separable verbs.

## Tech stack

Intentionally minimal:

- Single HTML file with inline CSS and vanilla JS
- No framework, no build tools, no npm
- Google Fonts (DM Sans + DM Mono)
- Hosted on GitHub Pages (free)

## Run locally

```bash
git clone https://github.com/chardrizard/werkwoorden-quiz.git
cd werkwoorden-quiz
open index.html
# or use any local server:
python3 -m http.server 8000
```

## Roadmap

- [ ] Add more verb themes (-geven, -staan, -slaan, -vallen)
- [ ] localStorage progress tracking
- [ ] Spaced repetition for wrong answers
- [ ] "Quick 20" mode (random subset)
- [ ] PWA support for install-to-homescreen
- [ ] Custom domain

## Contributing

Found a question with a wrong explanation or an unnatural sentence? Open an issue or PR. Native speaker corrections are especially welcome.

## Data structure

Questions are stored as compact arrays for minimal file size:

```
[sentence, [option1, option2, option3, option4], correctIndex, explanation, {wrongIdx: wrongExplanation}, hint]
```

This keeps 160 questions + all explanations under 50KB total.

## License

MIT — use it, fork it, adapt it for other languages.

---

Built as a study tool for the Dutch diaspora community 🧡
