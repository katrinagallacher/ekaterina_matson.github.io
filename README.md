# Personal site

One static HTML page. No build step, no dependencies, no framework. Edit `index.html` and push.

---

## Before you push: five things to fill in

The page ships with visible amber placeholders where I didn't have the detail. Search `index.html` for `class="todo"` — each one marks a spot. **They render on the live page**, so clear them before you share the URL with anyone.

| Where | What to replace |
|---|---|
| Header links, `#medium` | Your Medium profile URL (appears twice — header and Elsewhere) |
| Header links, `#github` | Your GitHub profile URL (appears twice) |
| Header links, `#email` | `mailto:you@example.com` |
| Timeline | The TalTech microdegree year |
| Timeline | Confirm the date on the tokenization write-up entry |

When you replace a placeholder link, delete the whole `<span class="todo">…</span>` along with it. The X/Twitter link is already live.

---

## Publishing on GitHub Pages

1. Create a **public** repo named exactly `<your-username>.github.io`. The name has to match your username or Pages won't serve it at the root domain.
2. Put these files at the top level of the repo — `index.html` must be at the root, not in a subfolder.
3. Push to the `main` branch.
4. Repo → **Settings** → **Pages** → under *Build and deployment*, set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
5. Wait a minute or two. The site appears at `https://<your-username>.github.io`.

From then on, every push to `main` republishes within about a minute.

```bash
git init
git add .
git commit -m "Personal site"
git branch -M main
git remote add origin git@github.com:<your-username>/<your-username>.github.io.git
git push -u origin main
```

## Custom domain

1. Buy the domain. For `.ee`, use an Estonian registrar (Zone, Veebimajutus); for `.com`, Namecheap or Cloudflare Registrar.
2. At your DNS provider, add four `A` records for the apex domain pointing to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`, and a `CNAME` for `www` pointing to `<your-username>.github.io`.
3. In repo Settings → Pages, enter the domain under *Custom domain*. GitHub writes a `CNAME` file into the repo — leave it there.
4. Once DNS resolves, tick **Enforce HTTPS**. The certificate is issued automatically and free.

---

## Files

- `index.html` — the whole site
- `404.html` — served by Pages for unknown paths
- `.nojekyll` — tells Pages to serve files as-is instead of running them through Jekyll

## Notes on editing

- **Adding a research entry:** copy a `<div class="entry">` block. `status` takes an optional extra class — `paused` (amber dot) or `done` (grey dot); no extra class gives the green dot.
- **Adding a timeline row:** copy an `<li>` block. Adding `class="mark"` to the `<li>` gives it a filled dot — currently used to make the AI-safety training stand out from the rest.
- **Colours, fonts, spacing:** all defined as CSS custom properties in `:root` at the top of the file, with dark-mode overrides right below. Change them in one place.
- The two webfonts load from Google Fonts. If you'd rather not depend on that, download the files, drop them in a `fonts/` folder, and swap the `<link>` for an `@font-face` block.
