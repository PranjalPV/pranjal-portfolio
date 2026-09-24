# Pranjal Verma — portfolio (preview build)

**What this is:** a working prototype of the portfolio — the "Scramble → Solve" cube concept, the 3D loading screen, the three.js cube, the project template system and the layout. It runs as a single HTML file with no build step and no backend.

**What this is not:** the finished site. The final version gets built as an Astro project (see `docs/portfolio-plan.md`), where each project is its own Markdown file and every page is generated.

---

## ⚠️ Before you publish this anywhere

Open `index.html` and fix these, or the site will show made-up information under your real name:

1. **Sample numbers.** Any number with a dotted underline is invented, so the layout could be judged. They live in the `PROJECTS` list near the top of the file, marked `sample: true`. Replace each with a real number, then set `sample: false` — or delete the metric.
2. **Red placeholders.** Text shown in red (`placeholder`, `XX students`, `dates`) still needs your real details: leadership numbers, dates, hackathon info.
3. **Links.** `links.study` and `links.live` are still `#` for most projects.

---

## Running it locally

Just open `index.html` in a browser. The three.js cube and the fonts load from the internet, so stay online the first time. Without a connection, a simpler CSS cube takes over automatically.

## Editing your projects

Everything you edit is in one block near the top of `index.html`, marked:

```
▓ EDIT EVERYTHING ABOUT YOU HERE ▓
```

```
TO ADD a project    → copy a { … } block, paste it, edit the fields
TO HIDE a project   → draft: false  →  draft: true
TO REORDER          → change the `order` number
TO FEATURE the big one at the top → featured: true
```

Your hackathon card is already written but hidden (`draft: true`). Flip it to `false` once you have the details.

Other settings worth knowing:

| Setting | Where | What it does |
|---|---|---|
| `ME` | top of the script | name, email, GitHub, LinkedIn, cube PB |
| `LOAD_MIN` | loader section | how long the loading screen runs |
| `AUTO_ENTER` | loader section | wait at 100% before it enters by itself |
| `NO_LOADER_ON_PHONE` | loader section | phones skip the loader (currently `true`) |

## Putting it on GitHub + Netlify

```bash
git init && git add -A && git commit -m "portfolio preview"
```

Create an empty repo on github.com, then run the two lines GitHub shows you (`git remote add origin …` and `git push -u origin main`).

Then on https://app.netlify.com → **Add new site → Import an existing project** → pick the repo. There's no build step: leave the build command empty and set the publish directory to `/`. Netlify serves `index.html` automatically.

Even faster, without GitHub: drag this folder onto https://app.netlify.com/drop.

Full details, including custom domains, are in `docs/deploy-guide.md`.

## What's in here

```
index.html              the whole preview (structure, styles, cube, loader)
photo-cutout.png        your photo, background removed, used by the page
assets/                 the same photo on orange / dark, spare versions
docs/portfolio-plan.md  the full build plan for the real Astro site
docs/deploy-guide.md    deployment steps in detail
```

## Credits

Concept, design and build directed by Pranjal Verma, made with Claude Code.
The theme comes from speedcubing: scrambled problems, broken into moves.
