# nchappa.github.io — redesigned

A sleek, dark-first redesign of Ravi Chappa's academic website. Pure static HTML/CSS/JS — no Jekyll, no build step.

## What's in this folder

```
site/
  index.html              ← the page
  styles.css              ← all styles (dark + light themes)
  assets/
    profile_pic.jpg
    publication_preview/  ← all paper figures
```

That's it. Drop these files into a static host and you're live.

## Deploying to GitHub Pages

You have **two options** for getting this on `nchappa.github.io`:

### Option A — Replace the Jekyll site (simplest)

If you're okay leaving al-folio behind:

1. In your local clone of `nchappa/nchappa.github.io`, **delete everything** on the `master` branch except the `.git` folder. (Back it up first with `git branch backup-jekyll` if you want to keep the old version recoverable.)
2. Copy the contents of this `site/` folder into the repo root (so `index.html`, `styles.css`, and `assets/` sit at the top level).
3. Add an empty file named `.nojekyll` at the repo root — this tells GitHub Pages **not** to run the Jekyll build:
   ```bash
   touch .nojekyll
   ```
4. Commit and push:
   ```bash
   git add .
   git commit -m "Redesign: dark-first static site"
   git push origin master
   ```
5. Pages will rebuild within ~1 minute. Visit `https://nchappa.github.io/`.

### Option B — Keep al-folio on a branch, deploy this on `main`

1. Rename your current branch:
   ```bash
   git branch -m master jekyll-archive
   git push origin jekyll-archive
   ```
2. Create a fresh `main` branch with these files:
   ```bash
   git checkout --orphan main
   git rm -rf .
   # copy in the site/ contents at repo root
   touch .nojekyll
   git add .
   git commit -m "New static redesign"
   git push origin main
   ```
3. In repo Settings → Pages, switch the source branch to `main`.

## Customizing

- **Email, social handles, paper links** — search `index.html` for `#` and `nchappa@chop.edu`; replace with your real URLs.
- **Profile photo** — drop a new `assets/profile_pic.jpg` (any aspect ratio; the hero crops to 4:5).
- **Publications** — each paper is a `<li class="pub">` block in `index.html`. Duplicate, edit, done. Thumbnails live in `assets/publication_preview/`.
- **Theme** — open `styles.css`; the top of the file is a `:root` block with all colors, fonts, and the type scale. Change a CSS variable, the whole site updates.
- **Adding a new section** — copy any existing `<section class="section">` block and edit. The `.section-id` numbering (§01, §02 …) is manual — bump them yourself when reordering.

## Browser support

Tested in current Chrome, Safari, Firefox. Uses `color-mix()` and `backdrop-filter` — both supported in 2023+ browsers. No build, no polyfills.

## What changed from the original al-folio site

- **Dark mode by default**, not light.
- **Full-bleed sections** instead of a single 800px column.
- **Instrument Serif** display + **Inter** body + **JetBrains Mono** labels — replaces Roboto.
- **One accent color** (signal cyan) instead of the al-folio purple/cyan duo.
- **Hero portrait card** replaces the floated headshot.
- **2-column publications** with hover preview thumbs that desaturate-on-hover.
- **2-column news grid** instead of a sparse table.
- **GitHub-style repo cards** instead of the al-folio Bootstrap project grid.
- **Numbered section IDs** (§01, §02 …) for that lab-paper feel.
- **Subtle scroll progress bar** and **reveal-on-scroll** animations — restrained, not flashy.

## Things you'll want to fix before going live

- Replace placeholder GitHub stars/forks (currently fake) with real numbers, or wire up the `github-readme-stats` SVG embeds you had before.
- Replace `nchappa@chop.edu` with your real email.
- Confirm the social URLs in the contact section (Scholar, GitHub, LinkedIn, X).
- Some publications use `et al.` for the author list — fill in real co-authors.
- Awards section uses placeholder honors — confirm or remove.

— Designed and packaged for upload. Have fun!
