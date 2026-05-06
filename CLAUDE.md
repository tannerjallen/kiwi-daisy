# Kiwi Daisy Art Studio — kiwidaisy.art

Static site for Jackie Matheney's art studio. Hosted on GitHub Pages at
https://github.com/tannerjallen/kiwi-daisy, serving the custom domain kiwidaisy.art.

Originally built by recreating a Carrd export (the raw export lives in
`Kiwi Daisy Art Studio - Crafty, Vibrant, and Fun Art.html` and its `_files/`
folder — keep them around as a reference but they are not served).

## File structure

```
index.html                  ← single-page site, all content lives here
CNAME                       ← tells GitHub Pages to use kiwidaisy.art
assets/
  css/style.css             ← all styles
  images/
    favicon.svg             ← daisy icon, teal background
    about.jpg               ← photo of Jackie (shown in About section)
    gallery/                ← 9 art images shown in the gallery grid
      691c093e.jpg
      c4027f94.jpg
      9525d511.jpg
      0c11547d.jpg
      30692a4d.jpg
      1757840d.jpg
      43fc8403.jpg
      583788b8.jpg
      4477fdad.jpg
```

## Design tokens

| Token | Value | Used for |
|-------|-------|----------|
| Teal | `#01818C` | Headings, divider, card accents |
| White | `#FFFFFF` | Body text, social icons, petals |
| Background | CSS gradient `#0d2b24 → #1a4a3a → #0a3440 → #015c68` | Full-page bg |
| Font | Sometype Mono (Google Fonts) | All text |
| Card shadow | `0 1.75rem 2rem rgba(0,0,0,0.14)` | Gallery and About cards |
| Card radius | `0.875rem` | Gallery and About cards |

## How to make common changes

**Update bio text** — edit the `<p>` inside `#about .about-text` in `index.html`.

**Add a gallery image** — drop the JPEG into `assets/images/gallery/`, then add an
`<a class="gallery-item" ...>` entry inside `.gallery-grid` in `index.html`.
The grid is 3-column on desktop; images are shown at a 3:4 aspect ratio, cropped
from center. No other changes needed — the lightbox picks up new items automatically.

**Replace the artist photo** — swap `assets/images/about.jpg` (keep the same filename).

**Change the background gradient** — edit the `background` property on `body` in
`assets/css/style.css`.

**Update social links** — find `<ul class="social-icons">` in `index.html` and edit
the `href` attributes. Facebook SVG id is `icon-facebook`, email is `icon-email`.

## Deploying changes

```bash
git add -A
git commit -m "describe what changed"
git push
```

GitHub Pages rebuilds automatically within ~30 seconds. No build step needed —
everything is plain HTML/CSS/JS.

## DNS (Namecheap)

Four A records on `@` pointing to GitHub's IPs, plus a CNAME for `www`:

```
A  @    185.199.108.153
A  @    185.199.109.153
A  @    185.199.110.153
A  @    185.199.111.153
CNAME  www  tannerjallen.github.io
```

HTTPS is enforced via GitHub Pages settings (Settings → Pages → Enforce HTTPS).
