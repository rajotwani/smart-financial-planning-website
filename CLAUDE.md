# Smart Financial Planning LLC — website

Instructions for Claude when maintaining this site. Read this first; don't ask Raj to repeat it.

## The business
- **Owner:** Rajesh (Raj) Otwani — Texas General Lines Agent, License #3217321, NPN #21291416.
  Licensed for Life, Accident & Health, and Property & Casualty in Texas.
- **Business name:** Smart Financial Planning LLC (always "LLC", never "Inc.")
- **Location / market:** Houston, TX area; families and pre-retirees.
- **Products featured:** Term Life, IUL, Annuities (MYGA, FIA, SPIA, DIA, QLAC, income riders), Final Expense.
  Also licensed for home/auto/business (P&C) — not yet described on the site.
- **Phone:** (713) 231-6442 · **Hours:** Mon–Sat, 9am–10pm CST
- **Email:** raj.otwani@gmail.com (to be replaced by a business address on the domain — see "Open items")
- **Facebook:** https://www.facebook.com/profile.php?id=61590382359179
- **Instant quote tool (main lead source):** https://app.back9ins.com/apply/SmartFinancialPlan (BackNine)

## Voice and content rules
- Plain English, warm, no jargon, no pressure. Short sentences. Explain any insurance term the first time.
- Compliance — always:
  - Never promise returns, "guaranteed growth", or call insurance/annuities an "investment".
  - Annuity guarantees are "backed by the claims-paying ability of the issuing insurer"; not FDIC-insured.
  - Product availability, pricing and features "vary by state and carrier, subject to underwriting".
  - Keep the license line and the disclaimer paragraph in every page footer, unchanged unless Raj asks.
  - Don't claim licenses in states other than those listed above.
- Keep "20+/30+/40+ carriers" claims consistent with what the BackNine tool says (currently it says 30+ / 40+).

## How the site is built
- Plain static HTML + one shared stylesheet. No framework, no build step.
- **Hosting:** GitHub Pages from `main` of https://github.com/rajotwani/smart-financial-planning-website
  (`CNAME` = www.smarterfinancialplan.com). Cloudflare sits in front (proxy/DNS).
- **Live URL:** https://www.smarterfinancialplan.com — note: NOT smartfinancialplan.com or smarterfinancialplanning.com (those belong to others).
- **Deploying:** commit and push to `main`; GitHub Pages republishes in about a minute. Cloudflare may cache —
  hard-refresh or purge cache if a change doesn't show.
- **Local preview:** `python -m http.server 8080` in this folder (see `.claude/launch.json`).

### Files
| File | Purpose |
|---|---|
| index.html | Home |
| about.html | About Raj (uses headshot.jpg) |
| services.html | Term / IUL / Annuities / Final Expense, with anchors #term #iul #annuities #final-expense |
| annuities.html | Annuity education + FAQ |
| contact.html | Contact details + quote request form |
| life-quote.html, retirement-readiness.html | Ad/landing-page funnels (not in the main menu) |
| *-thankyou.html | Post-submit pages for the funnels (noindex) |
| 404.html | Not-found page — uses absolute links (`/about.html`) because it can be served at any path |
| styles.css | All styling. Colors are CSS variables in `:root` (navy #10243e, gold #c99a3f) |
| menu.js | Mobile menu toggle, included on every page |
| favicon.svg, robots.txt, sitemap.xml | SEO basics |
| SMART-~1.HTM | Old original draft — unused, safe to ignore |

### Conventions
- The header and footer are **copied into every page** (no includes). Any change to nav, phone, email,
  license line or footer must be made in **all** `.html` files, including 404 and the funnel pages.
- Header structure (keep it): `.logo`, `button.menu-toggle`, `nav#site-nav > ul` (last item `li.nav-cta-mobile`),
  `.header-right` (phone + "Get an Instant Quote"). Below 860px the menu becomes a ☰ dropdown;
  below 560px the header quote button moves into the dropdown.
- New page checklist: copy an existing page's header/footer, set `<title>` and meta description,
  add `<link rel="icon">` and `<script src="menu.js">`, add it to `sitemap.xml` (and the nav if it's a main page).
- Forms post via JavaScript to FormSubmit: `https://formsubmit.co/ajax/ea917fa2f663a855d8cccf80db20ca9c`
  (used in contact.html, life-quote.html, retirement-readiness.html). The key maps to Raj's inbox.
  **Never submit a live form to test without asking Raj** — it sends him a real email.

## Before calling a change done
1. Every internal link returns 200; anchors exist.
2. Check at phone width (375px) and desktop: no sideways scrolling, menu opens/closes, buttons readable.
3. No console errors.
4. Footer license line and disclaimer intact on every page.
5. Show Raj what changed, then ask before pushing to `main` (pushing = live).

## Open items (Nov 2026)
- Business email on smarterfinancialplan.com — once live, replace raj.otwani@gmail.com in every page and
  re-point the FormSubmit key to the new address.
- Decide: add a home/auto/business insurance section, or drop "property" from titles/footers.
- Add New York license to the footer if/when active.
- Unknown URLs used to fall back to the home page with status 200; 404.html should fix this — verify after deploy.
