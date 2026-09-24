# Pranjal Verma — Portfolio Plan (v1)

> Build plan for Claude Code to carry out later. Anything marked **[ASK]** needs an answer from Pranjal before building. Anything marked **[WRITE]** is text Pranjal should rewrite in their own words. Drafts are given only as a starting point.

---

## Decisions locked (2026-09-20)

- **Concept: A — "Scramble → Solve"** (the cube). B and C are dropped.
- **GitHub:** https://github.com/PranjalPV
- **LinkedIn:** https://www.linkedin.com/in/pranjal-verma-351546246/
- **Email:** pranjal1772004verma@gmail.com
- **Photo:** the phone screenshot has been cropped and the background removed. Files: `photo-cutout.png` (transparent), plus versions on paper, orange and dark backgrounds. It goes in the About section, and a small version goes in the footer or on the contact card.
- **Hackathon:** the card exists but stays hidden (`draft: true`) until Pranjal fills in the details.
- **Cube: three.js** (confirmed). Real lights, soft shadow, plastic stickers, and you can **drag a single layer to turn it**. About 150 KB, loaded after the page is usable. If it fails to load, a hand-built CSS 3D cube takes over, so the hero never looks broken.
- **No sound anywhere** on the site.
- **No loader on phones** (screens under 768px or touch devices go straight in).
- **Loader: full-screen 3D block field** (see §3.0). The earlier flat-grid and cube-assembly versions were rejected.
- **Cubing PB: 29s** (chasing sub-25). Used in the About tile and the Space-bar timer.
- **Sample numbers:** project metrics are filled with made-up sample values so the layout can be judged. Each one is marked `sample: true`, which draws a dotted underline and a hover tip. **The build is not finished until every `sample: true` is replaced with a real number or deleted** — a recruiter who checks an invented metric is the one thing that would damage trust.
- **Projects must be easy to swap.** This is the top priority: one Markdown file per project (§7). Adding a file adds a card and a case-study page; `draft: true` hides it. No code changes needed, ever.

---

## 0. What we learned from the reference site (abhinavshukla.vercel.app)

Why it works. These are the ideas to borrow, not the look:

1. **One idea runs through the whole site.** The site owner works on extracting roads from satellite images, so the whole site is a map: a road-trace canvas in the background, "Legend → Primary roads" for skills, "The route so far" for experience, and coordinates in the footer. Each section feels planned by a person.
2. **Real, specific numbers.** "IoU 0.656", "0.985 vs human 0.979", "200+ attendees". Specific numbers are the strongest sign that a person wrote the page and not AI.
3. **Small interactive demos inside the page.** A before/after slider for road masks and an F1 track trace. The visitor *plays* with the work instead of reading about it.
4. **Personal voice in the small lines.** "Messi. No debate entertained." / "More en route" / "Hand-coded. Plain HTML, CSS & Canvas." These human touches are the "cool comments" you liked.
5. **Honest findings.** "The ranking inverts… recall collapses." Admitting what didn't work sounds like an engineer.

**What we must NOT do: copy its look.** You two are from the same city, similar colleges and the same FOSS United Lucknow community. Recruiters and seniors may see both sites. So we don't reuse the dark teal grid, amber accent, mono section labels in the "01 · SECTION" style, or map metaphor. We take the *principles* and give you your own theme.

---

## 1. Core concept: "Scramble → Solve"

**Your hook comes from your own resume: speedcubing.**

A speedcuber looks at a scrambled cube, spots patterns and solves it step by step with known algorithms. That is also what your projects do:

| Project | Scramble (messy input) | Solve (structured output) |
|---|---|---|
| Hospital Triage | Vague patient symptoms | Predicted condition → severity → appointment token |
| Job Recommender | A resume + thousands of job posts | Ranked matches → skill gaps → roadmap |
| Research Assistant | A loose research question | Agents retrieve → embed → analyse → cited summary |

So the site's idea is: **"I take scrambled problems and break them into moves."** The idea is tied to your hobby *and* your work (agentic AI means breaking tasks into steps). Nobody else will have it.

**Rules for the theme (so it doesn't feel gimmicky):**
- At most **one** cube reference per section. The copy stays professional.
- Cube notation (`R U R' U'`) is used as small decoration only, never as the main text.
- The site must still make sense to someone who has never touched a cube.

### Alternatives (if you don't like the cube)
- **B: "Agent Trace":** the site looks like a live multi-agent run log (planner → worker → output). It fits GenAI closely, but "AI node networks" are a cliché and it feels less personal.
- **C: "Beat / Waveform":** beatboxing as the idea: sections as beats, an audio-reactive waveform background, and an optional sound toggle. Very unique, but it's harder to link to your projects.

**Recommendation: A (Scramble → Solve), with a small B-style agent trace used *inside* the Research Assistant demo.** **[ASK] Confirm A, B or C.**

---

## 2. Visual design system

Chosen to look clearly different from the friend's site and from typical "AI template" portfolios. We avoid purple gradients, glassmorphism, Inter everywhere and emoji bullets.

### Colour: light "paper" by default, with a dark mode
| Token | Light | Dark | Use |
|---|---|---|---|
| `--bg` | `#F3EFE6` warm paper | `#131210` graphite | page |
| `--surface` | `#FBF9F4` | `#1C1A17` | cards |
| `--ink` | `#17150F` | `#EDE7DA` | text |
| `--muted` | `#6B665B` | `#9A9384` | secondary text |
| `--line` | `#D9D3C5` | `#2C2924` | borders/grid |
| `--accent` | `#E4472B` signal red-orange | `#FF6A4A` | links, CTAs, highlights |
| cube stickers | `#E4472B #F2A516 #F4F1E8 #2F9E5B #2D6CDF #E8D22C` | same, slightly darker | **only** inside the cube/facelet visuals |

Dark mode follows the system setting, with a manual toggle styled as a tiny cube face.

### Type
- **Display:** Bricolage Grotesque (bold with character; not overused)
- **Body:** Source Serif 4 (an editorial feel that makes it look like a real person writes here)
- **Mono / notation / labels:** JetBrains Mono
- Big type contrast: very large hero, calm body text (18px, line-height 1.65, max width about 68ch).

### Layout
- A 12-column grid with generous white space. Asymmetric sections (text on 7 columns, visual on 5, swapping sides).
- Section markers are small mono labels using real cube-solving stage names: `SCRAMBLE`, `CROSS`, `F2L`, `OLL`, `PLL`, `SOLVED`.
- Works properly at 360px phone width. No horizontal scroll.

### Motion rules
- Motion always *means* something (a solve, an agent step or a score filling in). Nothing moves just for decoration.
- Durations 200–600ms with an ease-out curve. No bouncing.
- `prefers-reduced-motion` turns off all ambient animation and shows static finished states instead.

---

## 3. Interactive background and signature moments

### 3.1 Facelet field (site-wide background)
- A faint grid of 3×3 "sticker" tiles in `--line` colour on a Canvas 2D layer, fixed behind the content.
- **Cursor:** tiles within about 120px slowly *flip* and briefly show a sticker colour, like peeking under a cube face, then fade back. It stays subtle, with 8–12% opacity max.
- **Scroll:** as you go down the page, the colour in the field becomes more ordered. Random colours at the top become matching colours by the footer, so the page "solves itself" as you read.
- **Touch:** a tap ripples the tiles. The effect is disabled on low-power / reduced-motion devices.
- Budget: 60fps, redraws only near the cursor ("dirty" tiles), pauses when the tab is hidden.

### 3.0 Loading screen (same family as devashish.design)
- The whole screen is a **grid of blocks**. As the page loads they **push out of the page in 3D**, each one showing a coloured side in a cube-sticker tint, extruding away from the centre of the screen so the perspective reads correctly. Some blocks stay flat, which keeps the field calm rather than busy.
- The **counter sits in a raised block at the centre** — a solid accent-coloured tile with a hard shadow slab behind it, counting 0% → 100%. Under it, the status runs through real solve stages: `scrambling → inspecting → cross · f2l → last layer → solved`.
- At 100% the centre block lifts and turns into **ENTER / click to enter**. It also enters by itself shortly after, so nobody gets stuck, and any key skips it. On entering, the blocks drop back down in a wave and the page appears.
- Rules: about **2 seconds maximum**, shown **once per visit** (a repeat visit within the same session goes straight in), skipped entirely for reduced-motion users, and the page underneath is fully built before it lifts. A loader that makes recruiters wait is worse than no loader.

### 3.2 Hero cube
- A real 3D 3×3 cube built from **26 separate cubies**, so a turn swings the whole layer round like a real cube instead of just recolouring squares. Proven in the preview with CSS 3D and matrix maths; the final build can use the same approach or three.js for nicer lighting and shadows.
- It starts **scrambled**. Visitors can **drag to rotate** it. A "Solve" button replays the inverse of every move made, so it genuinely unwinds back to solved.
- **Keyboard easter egg:** typing moves (`R`, `U`, `F`, `L`, `D`, `B`, with Shift for prime) turns the cube. A tiny hint below says `try: R U R' U'`.

### 3.3 Cubing timer easter egg
- Press **Space** (when no input is focused) and a small stack-timer overlay appears: `00:00.00`. Press again to stop and it shows: *"Nice. My PB is [ASK] s."*
- It's hidden and only mentioned in the footer: `psst — press space`.

### 3.4 Console note for developers
```
  ┌───┬───┬───┐
  │   Pranjal │   You opened devtools. Respect.
  └───┴───┴───┘   Source → github.com/[ASK]
                  Hiring? pranjal1772004verma@gmail.com
```

### 3.5 Footer signature
`Built by hand with Astro & Canvas · Lucknow 26.85°N 80.95°E · last solved <build date>`
(Say "built by hand" only if it's true. You can say "designed & directed by me, built with help from Claude Code". **[ASK]** which you're comfortable with. Being honest is safer, because interviewers do ask.)

---

## 4. Handling "no internship yet"

A missing internship is not a hole if the page never *shows* a hole. Strategy:

1. **No empty "Experience" section.** Replace it with **"Proof of Work"** (projects as case studies) and **"Team Solves"** (leadership).
2. **Depth beats a job title.** Each flagship project gets a full case study: the problem, architecture, decisions, what broke, results and what's next. A recruiter reading *how you think* learns more than from "Intern at X".
3. **Playable demos.** Recruiters spend 30–90 seconds. A demo they can click beats any bullet point (see §6).
4. **Leadership shown as real responsibility.** Placement Coordinator, Peer Mentor, Class Representative, FOSS United volunteer, Tech Club and the hackathon win go on a dated timeline with *impact numbers* (how many students, events, juniors). **[ASK]** for the numbers.
5. **Hackathon win becomes its own project card** with a 🏆-style badge (drawn in SVG, not an emoji).
6. **"Notes" (optional, strong signal):** 1–2 short technical write-ups, for example *"What broke when my CrewAI agents talked to Semantic Scholar"*. That makes you look like an engineer rather than a student. Add them only if you'll actually write them.
7. **Clear availability line in the hero:** *"Open to GenAI / Software Engineering internships and roles — graduating 2027."* **[ASK]** exact roles.
8. **Never write:** "fresher", "aspiring", "passionate", "no experience", or "eager to learn".

---

## 5. Sitemap and section-by-section content

### Home (`/`), a single long scroll
| # | Marker | Section | Content |
|---|---|---|---|
| 00 | `SCRAMBLE` | **Hero** | Name, one-line thesis, availability, CTAs (See my work / Resume / GitHub / Email), interactive cube |
| — | — | **Proof strip** | Scrolling ticker of *real* facts: `CGPA 8.63` · `50% merit scholarship` · `Hackathon winner` · `3 AI systems shipped` · `LLaMA 3.3 70B multi-agent pipeline` · numbers **[ASK]** |
| 01 | `CROSS` | **Flagship solve** | The strongest project as a big feature with a live demo (§6). Suggested: *Agentic Research Assistant* |
| 02 | `F2L` | **More solves** | The other projects as cards generated from content files (§7) |
| 03 | `OLL` | **How I solve** | 3–4 short principles on how you build (e.g. "Prototype the ugly version first", "Every agent gets one job") **[WRITE]** |
| 04 | `PLL` | **Team Solves** | Timeline: Placement Coordinator, Peer Mentor, CR, FOSS United, Tech Club, Hackathon, then education |
| 05 | `ALGS` | **Skills: "Algorithm sheet"** | Skills grouped like a cuber's algorithm sheet: *Main moves* (Python, FastAPI, LangGraph, CrewAI, RAG), *Also fluent* (Java, C++, SQL, React, Supabase, ChromaDB), *Foundations* (DSA, ML, REST, Git) |
| 06 | `OFF THE CLOCK` | **About** | Photo, a short personal story, plus three hobby tiles with a line of personality each (drafts below) |
| 07 | `SOLVED` | **Contact: "Your move."** | Email (copy button), LinkedIn, GitHub, Resume PDF, response-time line |

### Project page (`/work/[slug]`), one per project
Generated automatically from the project file (§7): hero with status and links → metrics row → Problem → Architecture diagram (animated step-by-step) → Key decisions & trade-offs → What broke & how I fixed it → Results → What I'd do next → Stack → Next/previous project.

### Other routes
- `/resume.pdf`, served directly
- `/notes` (optional)
- `404` page: *"This page is still scrambled."* with a mini cube you can rotate and a link home

### Draft microcopy (**[WRITE]**: rewrite so it sounds like you)
- Hero: **"I break scrambled problems into moves."** Sub-line: *"I'm Pranjal, a CS undergrad in Lucknow building AI systems that do actual work: agents that research, models that triage, and matchers that find the right job."*
- Hobby tiles:
  - **SPEEDCUBING:** "PB [ASK]s. Still chasing sub-[ASK]."
  - **BEATBOXING:** "Rhythm first. Then everything else."
  - **UKULELE:** "Four strings, questionable singing."
- Contact: **"Your move."** "Fastest route is email. I reply within a day."
- Empty project slot: **"Next scramble loading…"**

---

## 6. Interactive project demos (no API keys, zero running cost)

All demos run on **pre-recorded real outputs** stored as JSON in the repo, so they are fast, free, and never break when an API quota runs out. Each demo shows the label *"Replay of a real run"* for honesty, with a link to the live app if one is deployed.

1. **Agentic Research Assistant: "Watch the agents work"**
   A query is typed out → the Planner agent card lights up → the Retriever shows 5 paper cards arriving from Semantic Scholar → a ChromaDB "embedding" bar fills → the Analyst writes the summary with citations. A side panel shows the agent trace log with timestamps. There are 2–3 preset queries to pick from.
2. **AI Job Recommender: "Match me"**
   Pick one of 3 sample profiles (or skill chips) → ranked job cards animate in with match % → a skill-gap bar chart → a 3-step roadmap reveals.
3. **Hospital Triage: "Triage desk"**
   Click symptom chips → a severity gauge moves → a printed "appointment token" slides out (`TOKEN A-014 · PRIORITY HIGH · Dr. General Medicine`). Small disclaimer: *"Demo only — not medical advice."*

**[ASK]** For each project: GitHub link, a live deployed link (if any), and a real sample input/output we can record.

---

## 7. Easy-to-change project template (content-driven)

You weren't sure which projects to include, so **projects are just files**. Add, remove or hide a project without touching code.

```
src/content/projects/
  _template.md              ← copy this to add a project
  research-assistant.md
  job-recommender.md
  hospital-triage.md
```

### `_template.md`
```md
---
title: "Project Name"
slug: "project-name"
tagline: "One line: what it does and for whom."
status: "shipped"          # shipped | in-progress | hackathon | archived
featured: false            # true = eligible for flagship slot on home
order: 10                  # lower = earlier on the page
draft: true                # true = hidden everywhere
date: "2026-01"
role: "Solo"               # or "Team of 4 — backend & agents"
stack: ["Python", "FastAPI"]
links:
  github: ""
  live: ""
  video: ""
metrics:                   # 2–4 REAL numbers; leave empty if none
  - { label: "Papers analysed per query", value: "20" }
cover: "./covers/project-name.png"
demo: "none"               # none | research-trace | job-match | triage-desk | <new>
architecture:              # rendered as animated step diagram
  - "User query"
  - "Planner agent"
  - "Retriever"
  - "Answer"
---

## Problem
## Approach
## Key decisions
## What broke
## Results
## What I'd do next
```

- A schema (Zod) validates every file, so a typo in a field fails the build with a clear message instead of silently breaking the site.
- The home page shows the project with `featured: true` and the lowest `order` as the flagship, and all others as cards.
- If there are more than 6 projects, a **"Show more solves"** button appears automatically.

---

## 8. Tech stack and architecture

| Choice | Why |
|---|---|
| **Astro 5 + TypeScript** | Content collections suit the project files, it ships almost no JS by default, and it's fast |
| **Vanilla CSS with design tokens** | Full control over a custom look, with no Tailwind-template look |
| **Canvas 2D** for the facelet background | Light and smooth |
| **three.js** (lazy-loaded) for the hero cube only | The 3D cube with face turns is much easier with it |
| Small **React islands** only where state is heavy (demos) | You already know basic React, so you can maintain them |
| **Vercel** hosting | Free, and a custom domain is easy **[ASK]** do you want to buy `pranjalverma.dev` or similar? |
| **Vercel Analytics** (optional) | See whether recruiters visit |

### Folder structure
```
/
├─ public/            resume.pdf, og-image.png, favicon.svg
├─ src/
│  ├─ content/projects/   *.md + _template.md + covers/
│  ├─ data/               site.ts (name, links, hobbies, timeline), demos/*.json
│  ├─ components/
│  │   ├─ background/FaceletField.ts
│  │   ├─ hero/Cube.ts, CubeFallback.astro
│  │   ├─ demos/ResearchTrace.tsx, JobMatch.tsx, TriageDesk.tsx
│  │   ├─ ProjectCard.astro, ProjectFlagship.astro, ArchitectureSteps.astro
│  │   ├─ Timeline.astro, SkillSheet.astro, ProofStrip.astro
│  │   └─ easter-eggs/CubeTimer.ts, consoleNote.ts
│  ├─ layouts/Base.astro
│  ├─ pages/index.astro, work/[slug].astro, 404.astro
│  └─ styles/tokens.css, global.css
└─ README.md          how to add a project / change links
```
**All personal info lives in one file, `src/data/site.ts`**, so changing an email or link is a single edit.

### Quality bar (checked before launch)
- Lighthouse: Performance ≥ 95, Accessibility 100, Best Practices 100, SEO 100
- Initial JS ≤ 60 KB gzipped (the cube and demos load later)
- Full keyboard navigation, visible focus, alt text, colour contrast AA in both themes
- Open Graph image and meta tags, so the LinkedIn preview looks polished
- Tested on Chrome, Firefox, Safari, Android Chrome, and at 360 / 768 / 1440px

---

## 9. "Doesn't look AI-made" checklist
- [ ] Every sentence was reread and rewritten by Pranjal in their own voice
- [ ] Real numbers only; no invented metrics
- [ ] At least one "what broke" story per flagship project
- [ ] A real photo (not AI-generated, not a LinkedIn crop with a blurred background)
- [ ] No banned words: *passionate, leverage, cutting-edge, seamless, robust, innovative, delve, journey, aspiring*
- [ ] No typing-effect "Hi, I'm Pranjal 👋", no purple gradients, no glass cards, no generic tech-icon grid
- [ ] Personal details only you have (cube PB, beatbox, specific hackathon story)
- [ ] GitHub repos linked from the site have proper READMEs with screenshots (recruiters click through)
- [ ] Honest footer credit

---

## 10. Build phases (for Claude Code)

1. **Setup:** Astro project, tokens, fonts, base layout, light/dark theme, `site.ts`, deploy an empty site to Vercel.
2. **Content system:** project collection, schema, `_template.md`, card + flagship + project page.
3. **Static sections:** hero (with the fallback cube), proof strip, how I solve, timeline, skill sheet, about, contact, 404.
4. **Signature interactions:** facelet background → 3D cube → keyboard moves → timer easter egg → console note.
5. **Demos:** record real JSON runs → Research Trace → Job Match → Triage Desk.
6. **Polish:** motion pass, reduced motion, mobile pass, OG image, SEO, analytics.
7. **QA and launch:** Lighthouse, accessibility, cross-browser, real content check, custom domain.

Each phase ends with a deployed preview for Pranjal to review before the next phase starts.

---

## 11. Information needed from Pranjal **[ASK]**

**Must have**
1. GitHub and LinkedIn URLs (the resume says "Github / Linkedin" but the links couldn't be read).
2. For each project: repo link, a live link if any, screenshots, *real* numbers (accuracy, response time, number of papers/jobs, dataset size, users), team or solo, and one thing that broke and how you fixed it.
3. Hackathon: name, organiser, date, team size, what you built, and your role.
4. Leadership numbers: how many students you coordinated for placement, how many juniors mentored, FOSS United events you helped with, and the tech club name.
5. Target roles: GenAI engineer? SDE? ML? Internship, full-time, or both? Graduation month in 2027?
6. A photo you like (a candid photo looks more human than a formal one).
7. Concept choice: **A** Scramble → Solve / **B** Agent Trace / **C** Beat / Waveform.

**Nice to have**
8. Cubing PB and main event (3×3? OH?), and a beatbox clip link (optional, for the About tile).
9. The certificate issuers. Supervised ML and Advanced Learning Algorithms are probably DeepLearning.AI/Stanford (Andrew Ng). Confirm, and add links.
10. Domain name preference.
11. Honesty line for the footer (§3.5).
12. 2–3 more portfolio links you like, especially any *light-themed* ones.

---

## 12. Resume fixes noticed (worth doing before the site links to it)
- **The skills table is misaligned:** the "Languages" row lists frameworks, the "Frameworks" row lists soft skills, and so on. The labels and rows are shifted by one.
- **FastAPI appears twice** in the same row.
- The summary says **"Computer Science graduate"**, but your B.Tech runs 2023–2027. Use "Computer Science undergraduate" (or "final-year" if applicable).
- The bullet symbols render as `�` in some PDF readers. Re-export with a standard font.
- The project bullets have no numbers. Once you give numbers for §11.2, add them to the resume too, so the site and resume match.
