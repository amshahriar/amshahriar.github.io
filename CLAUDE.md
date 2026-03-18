# CLAUDE.md

## Project Overview
Personal academic website for Shahriar Aghaei (Research Science Manager, AWS Center for Quantum Computing). Single-page site hosted on GitHub Pages at https://amshahriar.github.io/

## Architecture
- **Single file**: All HTML, CSS, and JS live in `index.html` (no build tools, no frameworks)
- **No dependencies**: Pure modern CSS (Grid, Flexbox, custom properties) and vanilla JS. No Bootstrap, jQuery, or other libraries.
- **Static assets**: Images in `img/`, CV PDF in `docs/`

## Style Guide

### Color Scheme (CSS Custom Properties on `:root`)
- **Dark mode (default)**: `--bg-primary: #0a0a1a`, `--bg-secondary: #0f1029`
- **Light mode** (`.light-mode` class on `<html>`): `--bg-primary: #f5f7fa`, `--bg-secondary: #ffffff`
- **Accents**: `--accent-teal: #00d4aa`, `--accent-blue: #4a9eff`, `--accent-purple: #7c5cbf`
- **Gradient**: `--gradient-accent: linear-gradient(135deg, teal, blue)` used for headings, brand, section lines
- Dark mode is the default. Light mode only activates if user explicitly toggles (stored in `localStorage` key `site-theme-v2`)

### Typography
- **Headings & body**: Inter (Google Fonts), weights 400/500/600/700
- **Monospace** (code tags, publication numbers, typed effect): JetBrains Mono
- Fluid sizing via `clamp()` throughout

### Layout
- Max container width: `--container-max: 1000px`
- Section padding: `clamp(3rem, 8vw, 6rem)`
- Cards use `--bg-card` with `border: 1px solid var(--border-subtle)` and `--radius-md: 12px`
- Frosted glass effect: `backdrop-filter: blur()` with `-webkit-` prefix

### Components
- **Hero card**: 900px wide, 25% opacity bg, backdrop blur, contains 3:1 aspect photo with bottom gradient fade
- **Section titles**: Gradient-colored `<span>` inside `<h2>`, with a 60px gradient line below
- **Pills/buttons**: `border-radius: 100px`, subtle border, hover lifts with `translateY(-2px)`
- **Publication cards**: Flex row with mono-font number + content, topic-filterable via `data-topic` attribute
- **Timeline**: Horizontal scroll on desktop, vertical on mobile (<768px)

### Animations
- Scroll reveals: `IntersectionObserver`, 0.45s fade+translate for sections, 0.35s for cards with 35ms stagger
- Hero background: CSS keyframe drift animation (`heroBgDrift`, 30s cycle)
- Typed tagline: Vanilla JS character-by-character with random delay
- All animations respect `prefers-reduced-motion: reduce`

### SEO
- Full meta tags: Open Graph, Twitter (summary_large_image), JSON-LD Person schema
- Canonical URL, robots.txt, sitemap.xml
- Descriptive alt text on all images
- Google Analytics: G-7B1WETETWP

### Icons
- All icons are inline SVGs (no icon font library). Social icons use filled SVGs, UI icons use stroked SVGs.

### Publications
- Each pub card has `data-topic` attribute: `quantum-dots`, `diamond`, or `superconducting`
- Links use DOI (`doi.org/`) for journal papers, `arxiv.org/abs/` for preprints
- Filter pills toggle visibility; view toggle switches card/list layout
