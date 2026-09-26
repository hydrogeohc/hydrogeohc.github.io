# Ying-Jung Chen — personal website

A dependency-free static site: one `index.html`, one stylesheet, one script. No build step,
no npm install, no framework. Open `index.html` and it works.

## Structure

```
index.html      All content (hero, research, projects, publications, experience, skills, service, contact)
styles.css      Design tokens + layout. Light/dark themes live in the :root / [data-theme="dark"] blocks
script.js       Theme toggle, mobile nav, scroll-spy, reveal-on-scroll, footer year
_headers        Security headers (Cloudflare Pages)
robots.txt      Crawler rules
sitemap.xml     Single-page sitemap
.nojekyll       Tells GitHub Pages to serve files as-is
```

## Local preview

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploying

### GitHub Pages

```bash
git init && git add -A && git commit -m "New personal site"
git branch -M main
git remote add origin git@github.com:hydrogeohc/hydrogeohc.github.io.git
git push -u origin main
```

Then in repo **Settings → Pages**, set Source to `main` / root.
Live at `https://hydrogeohc.github.io/`.

### Cloudflare Pages

Connect the repo, leave the build command empty, and set the output directory to `/`.
`_headers` is picked up automatically.

## Editing

**Add a project** — copy an `<article class="project">` block in `index.html`. Badge classes:
`badge-safety`, `badge-agents`, `badge-geo`, `badge-teaching`.

**Add a publication** — copy an `<li class="pub">` block. Wrap your own name in
`<span class="me">` so it stands out.

**Change colors** — edit the `--accent` / `--amber` variables at the top of `styles.css`.
Both themes are defined in one place.

**Link a CV** — the site intentionally ships without resume PDFs. To add one, drop the file
in a new `assets/` folder and add a `<li>` to the `.link-row` list in the hero.
