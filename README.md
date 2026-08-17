# Pratik Akole — Portfolio v2

A static, GitHub-Pages-friendly portfolio. The public site is **read-only** for
everyone. You add/edit everything (experience, skills, projects, files,
images) through a **hidden, private admin panel** that commits straight to
this repo — no separate backend, no database, no monthly cost.

## File map

```
index.html          → the public site
admin.html           → your private editor (NOT linked from index.html)
data/content.json    → every bit of text/data on the site lives here
css/style.css        → public site styles
css/admin.css         → admin panel styles
js/main.js            → renders index.html from content.json
js/admin.js            → the admin panel logic (talks to GitHub's API)
assets/uploads/        → where images/files you upload through admin land
```

## 1. Deploy it

1. Push this whole folder to a GitHub repo (or replace the contents of your
   existing `pratik-akole.portfolio.io` repo with these files).
2. In the repo: **Settings → Pages → Deploy from a branch → `main` / root**.
3. Your public site is `https://<username>.github.io/<repo>/`.
4. Your private admin panel is `https://<username>.github.io/<repo>/admin.html`
   — bookmark it, don't link to it from anywhere public.

## 2. Set up your admin access (one-time)

1. On GitHub: **Settings → Developer settings → Personal access tokens →
   Fine-grained tokens → Generate new token**.
2. **Repository access:** "Only select repositories" → pick this repo only.
3. **Permissions → Repository permissions → Contents:** set to **Read and
   write**.
4. Generate, copy the token.
5. Open `admin.html`, enter your GitHub username, this repo's name, branch
   (`main`), and paste the token in. Click **Connect**.

The token is only ever stored in your own browser (`sessionStorage`, cleared
when you close the tab — nothing is written into the code or repo). You'll
paste it in again each time you visit `admin.html`, unless you use a password
manager to save it.

## 3. Turn on the contact form

The contact form posts to [Formspree](https://formspree.io) (free tier is
enough for a portfolio):

1. Create a free Formspree account, create a form, copy your form's endpoint
   URL (looks like `https://formspree.io/f/xxxxxxx`).
2. Paste it into `admin.html → Contact → Formspree endpoint`, then **Save to
   GitHub**. That's it — no code changes needed.

Until you do this, the form will politely tell visitors to email you directly
instead of failing silently.

## 4. Add/update anything, anytime

Open `admin.html`, log in, and use the left-hand tabs:

- **Hero** — name, tagline, bio, resume PDF, stat numbers, social links
- **About** — summary paragraph, quick facts
- **Experience** — add/remove roles, edit responsibilities
- **Skills** — add/remove categories and individual skills
- **Certifications** — certifications and achievements
- **Projects** — the big one: business problem, dataset, approach, tools,
  KPIs, insights, business impact, dashboard preview image, dashboard link,
  and any attached files (datasets, extra screenshots, PDFs)
- **AI & Automation** — your GenAI/automation roadmap and tools you're
  exploring
- **Contact** — email, phone, socials, WhatsApp, Formspree endpoint

Every uploaded file/image goes into `assets/uploads/` in this repo. Click
**Save to GitHub** and the live site updates within a few seconds — no
rebuild step, no redeploy.

## Notes

- Everything in `data/content.json` is plain data — you could also hand-edit
  that file directly and push, if you ever prefer that to the UI.
- The admin panel is a static page too — its security comes entirely from
  the GitHub token, not from being "hidden." Don't share the token, and
  revoke it from GitHub any time you want to cut off access.
