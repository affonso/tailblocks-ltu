# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Tailblocks is a React app (Create React App) that showcases 60+ ready-to-use Tailwind CSS blocks. Users browse blocks in a sidebar, preview them in an iframe with responsive device views, toggle dark mode, switch color themes, and copy the generated HTML. Deployed to https://tailblocks.cc.

## Commands

- `yarn start` — dev server
- `yarn build` — production build
- `yarn test` — run tests (Jest via react-scripts)
- `yarn deploy` — build + deploy to GitHub Pages via gh-pages

## Architecture

**Single-component app** — `src/App.js` is a class component that owns all state (selected block, theme, dark mode, view mode, code view) and renders the entire UI: sidebar, toolbar, iframe preview, and code viewer.

**Block system** — Two parallel directory trees under `src/`:

- `src/blocks/<category>/light/<letter>.js` and `src/blocks/<category>/dark/<letter>.js` — React components that return Tailwind CSS HTML. Each accepts a `theme` prop (color name like "indigo") used in class names like `` `text-${theme}-500` ``. Light and dark variants are separate files with different Tailwind classes.
- `src/icons/<category>/<letter>.js` — SVG thumbnail components for the sidebar. Use CSS custom properties (`var(--solid)`, `var(--main-500)`, etc.) for theming.

**Block registry** — `src/blocks/index.js` exports `getBlock({theme, darkMode})` which returns a nested object `{ Category: { NameX: <Component /> } }`. `src/icons/index.js` exports `getIcons()` with the same structure. Both must be updated when adding/removing blocks.

**Categories:** Blog, Contact, Content, CTA, Ecommerce, Feature, Footer, Gallery, Header, Hero, Pricing, Statistic, Step, Team, Testimonial. Variants are named with letters (A, B, C, ...).

**Theming** — Color themes (indigo, yellow, red, purple, pink, blue, green) are applied via CSS custom properties in `src/index.css`. The `.dark-mode` class swaps the variable set. Blocks use the `theme` prop for Tailwind utility classes; the shell UI uses CSS variables.

**Preview** — Blocks render inside `react-frame-component` (iframe) with Tailwind CSS loaded from CDN (`cdnjs.cloudflare.com/ajax/libs/tailwindcss/2.0.2`). The "View Code" feature extracts innerHTML from a hidden `.markup` div and displays it via `react-syntax-highlighter`.

## Adding a New Block

1. Create `src/blocks/<category>/light/<letter>.js` and `src/blocks/<category>/dark/<letter>.js` — export a function component accepting `{theme}`.
2. Create `src/icons/<category>/<letter>.js` — export an SVG thumbnail component.
3. Register imports and entries in both `src/blocks/index.js` and `src/icons/index.js`.
