# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**briverr.com** is a static marketing website for a Saudi Arabian influencer marketing agency. No build system, no framework, no package manager — pure HTML, CSS, and vanilla JavaScript served directly via GitHub Pages.

## Pages

- `index.html` — Main landing page (hero, stats, how-it-works, brands section, influencers section, quote, footer)
- `register.html` — 3-step influencer registration form that submits via WhatsApp (`wa.me`)

## Development

Open files directly in a browser — there is no dev server, build step, or compilation.

To preview locally with a simple server (avoids some browser restrictions on `file://`):
```bash
python3 -m http.server 8080
```

There are no tests, linters, or CI configured.

## Design System

All CSS lives in `<style>` blocks inside each HTML file. CSS custom properties define the design tokens:

```css
--black: #0E0E0D
--maroon: #8D4343      /* primary brand color */
--maroon-l: #a85555    /* lighter maroon for hover states */
--white: #FAFAF8
--gray: #6b6b6b
--light: #F5F4F0
```

**Fonts** (loaded from Google Fonts):
- `Tajawal` — body text (Arabic)
- `Cairo` — Arabic headings
- `Montserrat` — English accents, numbers, stats
- `Cormorant Garamond` — italic taglines/quotes

## Key Conventions

**Language & direction**: All pages use `lang="ar" dir="rtl"`. Content is Arabic-primary with English used selectively (brand names, stats, taglines).

**Responsive breakpoint**: Single breakpoint at `max-width: 768px` handles all mobile layout changes (hamburger menu, stacked buttons, reduced padding).

**JavaScript patterns**: No libraries. State is managed by toggling `.active` and `.open` CSS classes. The registration form collects selections from `.chip-opt` elements into hidden inputs, then encodes everything into a WhatsApp `wa.me` URL on submit.

**Class naming**: Loosely BEM-inspired — section prefixes like `.sec-title`/`.sec-sub`, component prefixes like `.bcard`, `.chip`, `.chip-opt`, `.step-n`.

## Architecture Notes

### Register Form Flow
The multi-step form in `register.html` uses JS to show/hide `.step-1`, `.step-2`, `.step-3` divs and update progress dot indicators. On final submit, it builds a WhatsApp message string from all collected form values and opens `https://wa.me/<number>?text=<encoded>`.

### Navigation
The hamburger menu in both pages toggles `.open` on `.nav-links` to show/hide the mobile nav. The CTA button in the nav links to `register.html`.

## Deployment

Pushing to `main` deploys automatically via GitHub Pages. The `CNAME` file sets the custom domain to `briverr.com`.
