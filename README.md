# YICA-SL Website

Website for the **Youth Initiative for Climate Action – Sierra Leone (YICA-SL)** — a youth-led non-profit empowering young people to lead climate action and environmental protection.

Live domain: **www.yica-sl.org**

## What this is

A static website built with plain HTML and CSS (no build step, no framework). It works by simply opening the files in a browser, and deploys to any static host.

## Project structure

```
yica-website/
├── index.html                    # Home page (slider, about, problem, programmes, impact, partners)
├── team.html                     # Our Team
├── programme-mentorship.html     # Young Women Climate Mentorship
├── programme-restoration.html    # Community-Based Restoration & CEEComs
├── programme-policy.html         # National Policy Engagement
├── programme-gardens.html        # School Gardens & Capacity Building
├── styles.css                    # All shared styling + animations
├── 404.html                      # Not-found page
├── assets/
│   └── yica-logo.jpg             # Logo (used in header and footer)
└── README.md
```

All pages share `styles.css` and link to each other with relative paths, so the
folder is fully portable — open `index.html` in any browser to preview locally.

## Local preview

Just open `index.html` in a browser. Or run a simple local server:

```bash
# Python 3
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy

This is a static site, so it works on any static host. Common options:

- **Cloudflare Pages** — connect the repo, set build command to *none*, output directory to `/` (root).
- **Netlify** — drag-and-drop the folder, or connect the repo. No build command.
- **GitHub Pages** — push to a repo, enable Pages on the root.
- **Existing host (yica-sl.org)** — upload the files via FTP/cPanel to the web root.

There is no build step. The files served are exactly the files in this folder.

## Editing notes

- **Colours & fonts** live as CSS variables at the top of `styles.css` (`:root`).
  The brand greens are `--teal`, `--lime`, and `--lime-bright`.
- **Photos**: several sections currently use labelled placeholders
  (e.g. "Replace with photo — mentorship cohort"). Search the HTML for
  `Replace with` to find every spot that needs a real image. The homepage
  slider expects landscape images around 1600×900px.
- **Stats**: the homepage impact figures (15k+ trees, etc.) and the team list
  are hard-coded in `index.html` and `team.html` — edit the text directly.
- **Animations** are defined in the "VIBRANT MOTION LAYER" section at the bottom
  of `styles.css`. All motion respects `prefers-reduced-motion`.

## To do (suggested next steps)

- [ ] Replace placeholder images with real photos
- [ ] Add real social media links (currently `#` in the top bar and footer)
- [ ] Build an About page and a Contact page
- [ ] Add Open Graph / social share image
- [ ] Confirm impact figures are accurate before going live
