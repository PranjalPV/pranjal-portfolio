# Deploying the portfolio

Two different things can be deployed. Don't mix them up.

| | What it is | When |
|---|---|---|
| **A. The preview** | The single `portfolio-preview.html` mockup + `photo-cutout.png` | Today, if you want a link to show people |
| **B. The real site** | The Astro site Claude Code builds from `portfolio-plan.md` | The actual portfolio |

**Before either one goes public:** replace every sample number (the dotted ones) and the red `placeholder` bits, or delete them. Invented metrics next to your real name are the one thing that can actually cost you an interview.

---

## Step 0 — get the files out of the temporary folder

The preview currently lives in a session folder that gets deleted. Move it somewhere real, for example `C:\Users\Asus\Documents\portfolio`, keeping these together:

```
portfolio/
├─ index.html          (renamed from portfolio-preview.html)
├─ photo-cutout.png
├─ portfolio-plan.md
└─ deploy-guide.md
```

The file must be named **index.html** for hosting to serve it automatically.

---

## A. Deploy the preview (fastest, no terminal)

**Option 1 — Netlify Drop (about 60 seconds, no account needed to try)**
1. Go to https://app.netlify.com/drop
2. Drag the whole `portfolio` folder onto the page.
3. You get a live URL straight away. Sign in to keep it and rename it.

**Option 2 — Vercel (recommended, same account you'll use later)**
1. Sign up at https://vercel.com with your GitHub account.
2. Install the CLI and deploy from inside the folder:

```bash
npm i -g vercel
```

```bash
vercel
```

Answer the prompts (accept the defaults). `vercel --prod` publishes it to the main URL.

---

## B. Deploy the real site (the normal route)

### 1. Put it on GitHub
```bash
git init && git add -A && git commit -m "portfolio: first version"
```
Create the repo and push (needs the GitHub CLI, `gh auth login` once):
```bash
gh repo create pranjal-portfolio --public --source=. --push
```
Or create an empty repo on github.com and follow the two lines it shows you.

### 2. Connect Vercel
1. https://vercel.com → **Add New… → Project** → import `pranjal-portfolio`.
2. Vercel detects Astro by itself: build `npm run build`, output `dist`.
3. **Deploy.** You get `pranjal-portfolio.vercel.app` in about a minute.

From then on, **every `git push` redeploys automatically**. Pull requests get their own preview URL.

### 3. Custom domain (optional, about ₹800–1200/year)
1. Buy the domain (Namecheap, GoDaddy, Cloudflare).
2. Vercel → Project → **Settings → Domains → Add**.
3. Copy the DNS records Vercel shows into your registrar's DNS panel.
4. HTTPS is set up automatically within a few minutes.

Good names: `pranjalverma.dev`, `pranjal.build`, `pranjalverma.in`. A custom domain on a CV reads better than `something.vercel.app`.

---

## After it's live — the checklist that matters

- [ ] Open it on a **real phone**, not just a narrow browser window
- [ ] Every link works: GitHub, LinkedIn, resume PDF, each project
- [ ] The resume PDF actually downloads
- [ ] Share the link in a WhatsApp/LinkedIn message to yourself and check the **preview card** (that's the OG image)
- [ ] Run https://pagespeed.web.dev on the URL — aim for 90+ on mobile
- [ ] Ask two friends to open it cold and tell you what they think you do
- [ ] Put the link in: LinkedIn (featured + contact info), GitHub bio, resume header, email signature
- [ ] **No sample numbers left anywhere**

## Keeping it updated
Adding a project later = add one `.md` file, commit, push. Vercel rebuilds within a minute. No hosting cost: Vercel's free tier covers a portfolio comfortably.
