# YICA-SL Website

Website for the **Youth Initiative for Climate Action – Sierra Leone (YICA-SL)** — a youth-led non-profit empowering young people to lead climate action and environmental protection.

Live domain: **www.yica-sl.org**

## What this is

A static website built with plain HTML and CSS (no build step, no framework). It works by simply opening the files in a browser, and deploys to any static host.

## Project structure

```
yica-website/
├── index.html                          # Home (slider, about, problem, programmes, impact, partners)
├── about.html                          # Who We Are (mission, vision, approach, values)
├── team.html                           # Our Team
├── contact.html                        # Contact form (mailto:) + details
├── volunteer.html                      # Volunteer application form (mailto:)
├── programme-mentorship.html           # Young Women Climate Mentorship
├── programme-restoration.html          # Community-Based Restoration & CEEComs
├── programme-policy.html               # National Policy Engagement
├── programme-gardens.html              # NatureUp School Gardens & Capacity Building
├── news.html                           # News & Updates index
├── news-*.html                         # Individual news articles (5)
├── resources.html                      # Resources hub
├── resources-reports.html              # Annual/programme reports
├── resources-policy-positions.html     # YICA-SL's own policy position papers
├── resources-climate-policies.html     # National/international policy library (NDCs, NAP, BUR)
├── resources-press-releases.html       # Press releases (placeholder — none posted yet)
├── resources-opportunities.html        # Youth climate opportunities (placeholder — none posted yet)
├── styles.css                          # All shared styling + animations
├── 404.html                            # Not-found page
├── assets/
│   ├── YICA-Logo-png-final.png         # Logo (header/favicon)
│   ├── YICA Logo white.png             # Logo (footer/splash, white variant)
│   ├── Documents/                      # PDFs linked from the Resources pages
│   ├── news/                           # News article photos
│   ├── Team/                           # Team headshots
│   ├── Partner logos/                  # Partner/funder marquee logos
│   ├── Concrete Actions/               # Homepage "concrete actions" story photos
│   └── YCC Sierra Leone Launch Photos/ # Photos for the YCC launch article
└── README.md
```

All pages share `styles.css` and link to each other with relative paths, so the
folder is fully portable — open `index.html` in any browser to preview locally.
Every page repeats its own `<header>`/`<footer>` markup inline (there's no
templating), so any nav or footer change has to be applied to every page.

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

- [ ] Wire up real form submission for `contact.html` and `volunteer.html` — both
      currently just build a `mailto:` link and hand off to the visitor's mail
      client, so a submission can silently go nowhere if none is configured
      and nothing is stored anywhere.
- [ ] Populate `resources-press-releases.html` and `resources-opportunities.html`
      — both are placeholder pages ("will be posted here soon").
- [ ] Add real social media links where any `#` hrefs remain.
- [ ] Add Open Graph / social share image.
- [ ] Confirm impact figures are accurate before going live.
