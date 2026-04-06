# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Snack de la Bruche — QR code menu for a snack restaurant. Currently a static site (Phase 1 complete), with plans to evolve into a full ordering app (see ROADMAP.md).

**Stack**: Pure HTML5 + Vanilla CSS + Vanilla JavaScript. No framework, no build system, no dependencies.

## Running the Project

Open any `.html` file directly in a browser, or serve with any static HTTP server. No build or install step required.

There are no tests, linters, or CI configured.

## Architecture

- **`index.html`** — Main entry point (latest version of the menu)
- **`v*.html`** — Previous iteration snapshots kept for reference
- **`images/`** — Product photos organized by category (Sandwiches, Burgers, Tacos, Assiettes, Extras, Desserts, Boissons & Bières)
- **`ROADMAP.md`** — Feature planning (Phases 1-3)

Everything is self-contained in single HTML files: CSS in `<style>` tags, JS in `<script>` tags, menu data hardcoded in HTML.

## Key Inline JavaScript Logic

- **`setMode(m)`** — Toggles display mode (`mode-small` / `mode-big` / `mode-all`) via body class, filtering products by CSS visibility
- **Category navigation** — `IntersectionObserver` tracks visible sections; clicking a category button smooth-scrolls to its section
- **Open/Closed status** — Calculates current time in `Europe/Paris` timezone, compares against per-day closing hours array, updates the header status pill

## Product Card Structure

```html
<div class="product-card [small-only|big-only]">
  <span class="price-tag">Price</span>
  <img class="product-image" src="images/name.png" loading="lazy">
  <h3 class="product-name">Name</h3>
  <p class="product-desc">Description</p>
</div>
```

- `small-only` class: visible only in "Petite faim" mode
- `big-only` class: visible only in "Grosse dalle" mode
- No class: visible in all modes

## Design System

Dark glassmorphism theme with CSS custom properties:
- Background: `#0f0f0f`, Cards: `#1a1a1a`, Accent: `#ff5c00` (orange)
- Backdrop-filter blur for glass effects
- Mobile-first responsive layout
- Font: Inter (Google Fonts)

## Deployment

GitHub Pages — auto-deploys on push to `main`. No build pipeline needed.

## Future Direction (Phase 3)

Planned migration to **Next.js 15 + TypeScript + Tailwind + Supabase + Better Auth + Stripe** for a full ordering system with cart, payments, kitchen dashboard, and real-time tracking.
