# Project context for Claude Code

## What this project is
A static website for **YICA-SL (Youth Initiative for Climate Action – Sierra Leone)**,
a youth-led climate non-profit based in Freetown. Domain: www.yica-sl.org.

Plain HTML + CSS. **No framework, no build step, no package.json.** The deployed
output is exactly the source files.

## Architecture
- Multi-page static site. Each page is a standalone `.html` file that repeats
  its own `<header>`/`<footer>` inline — there is no templating, so a nav or
  footer change must be applied to every page individually.
- All pages share `styles.css` (linked, not inlined), loaded via
  `styles.css?v=YYYYMMDD` on every page. **Bump that version string on every
  CSS-only change** — browsers/CDNs cache `.css` more aggressively than
  `.html`, so a CSS edit can redeploy successfully and still not show up for
  visitors until the query string changes.
- Logos live at `assets/YICA-Logo-png-final.png` (header/favicon) and
  `assets/YICA Logo white.png` (footer/splash, white variant).
- Pages link to each other with relative paths (e.g. `href="team.html"`).
- Small inline `<script>` at the bottom of each page handles: mobile menu,
  scroll-reveal (IntersectionObserver), and (on index.html) the hero slider,
  count-up stats, splash screen, and partner marquee.
- No backend: `contact.html` and `volunteer.html` forms don't submit
  anywhere — on submit they build a `mailto:` link from the field values and
  hand off to the visitor's mail client. Nothing is stored or validated
  server-side.

## Pages
- `index.html` — home: hero slider, about, problem, solution, programmes,
  concrete-actions stories, impact panel, partners marquee.
- `about.html` — mission, vision, approach, values.
- `team.html` — six team members.
- `contact.html`, `volunteer.html` — forms (see "No backend" above).
- `programme-*.html` (4) — programme detail pages, chained to each other via
  a "next programme" CTA at the bottom.
- `news.html` + `news-*.html` (5 articles) — news index and story pages.
- `resources.html` + `resources-*.html` (5 categories) — resource hub.
  `resources-press-releases.html` and `resources-opportunities.html` are
  currently empty placeholders ("will be posted here soon").
- `404.html` — not-found page. Uses the same full nav as every other page
  (it drifted out of sync once before — keep it in sync when the nav changes).

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
  `.navlinks` — including `404.html`, which is easy to forget since it's not
  part of the visible nav flow.
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
