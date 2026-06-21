# Project context for Claude Code

## What this project is
A static website for **YICA-SL (Youth Initiative for Climate Action – Sierra Leone)**,
a youth-led climate non-profit based in Freetown. Domain: www.yica-sl.org.

Plain HTML + CSS. **No framework, no build step, no package.json.** The deployed
output is exactly the source files.

## Architecture
- Multi-page static site. Each page is a standalone `.html` file.
- All pages share `styles.css` (linked, not inlined).
- Logo lives at `assets/yica-logo.jpg`, referenced as `assets/yica-logo.jpg`.
- Pages link to each other with relative paths (e.g. `href="team.html"`).
- Small inline `<script>` at the bottom of each page handles: mobile menu,
  scroll-reveal (IntersectionObserver), count-up stats, and (on index.html)
  the hero slider + partner marquee.

## Pages
- `index.html` — home: hero slider, about, problem, solution, programmes,
  concrete-actions stories, impact panel, partners marquee.
- `team.html` — six team members.
- `programme-*.html` — four programme detail pages.

## Conventions
- Brand colours are CSS variables in `:root` at the top of `styles.css`.
  Greens: `--teal #159b86`, `--lime #3aa843`, `--lime-bright #54b95a`,
  `--teal-deep`, `--teal-ink`, `--ink #0c1226` (dark navy), `--paper` (cream bg).
- Fonts: Space Grotesk (headings), Mulish (body), loaded from Google Fonts.
- Animations are grouped under the "VIBRANT MOTION LAYER" comment at the bottom
  of `styles.css`. Keep `prefers-reduced-motion` support intact.
- Image placeholders are marked with the text "Replace with" — preserve that
  convention when adding new placeholder slots.

## Common tasks
- **Add a page**: copy an existing subpage, keep the same `<header>`/`<footer>`
  and the bottom `<script>`, link `styles.css`, add a nav link in every page's
  `.navlinks`.
- **Change content/stats**: edit the HTML text directly (no data layer).
- **Deploy**: static host, no build. Cloudflare Pages / Netlify / GitHub Pages,
  output dir = project root, build command = none.

## Things to be careful about
- This is public-facing for a real organisation. Don't invent statistics —
  ask before changing impact figures, partner names, or team details.
- Keep relative paths (don't switch to absolute `/...` paths unless deploying
  to a domain root and confirmed).
- The single-file `YICA-SL-website.html` (if present in a parent folder) is a
  separate self-contained preview build; this folder is the deployable version.
