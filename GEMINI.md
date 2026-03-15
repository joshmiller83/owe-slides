# Slidev Working Guide

This repo is a local Slidev deck scaffold with `slides.md` as the entrypoint, `generated_images/` containing source slide art, and support folders for custom `components/`, `pages/`, and `snippets/`.

## Current project shape

- CLI: `@slidev/cli` `^52.14.1`
- Themes installed: `@slidev/theme-default`, `@slidev/theme-seriph`
- Scripts:
  - `npm run dev`
  - `npm run build`
  - `npm run export`
- Existing hosting config:
  - Netlify via [`netlify.toml`](/Users/jomiller/Developer/github/joshmiller83/owe-slides/netlify.toml)
  - Vercel via [`vercel.json`](/Users/jomiller/Developer/github/joshmiller83/owe-slides/vercel.json)

## Core Slidev model

Slidev presentations are Markdown-first, but each slide can mix:

- Markdown
- HTML
- Vue components
- UnoCSS utility classes
- YAML frontmatter
- Scoped CSS
- Imported code snippets
- Speaker notes

Slides are separated with `---`. The first frontmatter block is the deck-level headmatter. Later frontmatter blocks configure individual slides.

Deck-level headmatter is where the important controls live: `theme`, `addons`, `fonts`, `themeConfig`, `defaults`, export options, `monaco`, `twoslash`, `browserExporter`, and drawing settings.

Minimal pattern:

```md
---
theme: seriph
title: Open Web Exchange
addons:
  - excalidraw
fonts:
  sans: DM Sans
  serif: Source Serif 4
  mono: IBM Plex Mono
---

# Opening

Intro copy

---
layout: two-cols
---

# Left

::right::

Right side
```

## Formats Slidev supports well

### Authoring formats

- `slides.md` as the main deck entry
- Additional imported markdown files via `src: ./path/to/file.md`
- Vue single-file components in `components/`
- Custom layouts in `layouts/`
- Code snippets in `snippets/`
- Static assets in `public/`

### Content formats inside slides

- Markdown headings, lists, tables, links, blockquotes
- HTML blocks when Markdown is too limiting
- Vue template syntax and event bindings
- Shiki-highlighted code fences
- `twoslash` TypeScript examples
- Mermaid diagrams
- PlantUML diagrams
- KaTeX/LaTeX math
- Images
- Local and remote video
- YouTube embeds
- Icons via Iconify collections

### Output formats

Slidev can export or ship as:

- PDF
- PNG
- PPTX
- Markdown
- hosted SPA

Important constraint: exports are less capable than the live browser deck. Complex interactivity, some video codecs, and timing-sensitive animation can degrade in PDF/PPTX/PNG outputs.

## Directory conventions that matter

Slidev recognizes these folders conventionally:

- `components/`
- `layouts/`
- `pages/`
- `public/`
- `setup/`
- `snippets/`
- `styles/`
- `slides.md`
- `vite.config.ts`
- `index.html`

Useful rules:

- Put reusable Vue pieces in `components/`
- Put code examples to be embedded with `<<<` into `snippets/`
- Put static assets you want referenced from `/...` in `public/`
- Keep generated slide art in `generated_images/` if we want to version the raw assets directly

## Styling model: use UnoCSS like Tailwind

Slidev uses UnoCSS by default. Most Tailwind-style utility classes work out of the box, so the right mental model is:

- prefer UnoCSS utilities first
- add light custom CSS second
- add custom layouts/components when the structure repeats
- avoid installing Tailwind unless there is a very specific reason

Practical guidance:

- Use utility-first composition in markdown and Vue components
- Centralize shared tokens in `styles/` and `themeConfig`
- Keep slide-specific overrides inside per-slide `<style>` blocks only when truly local
- Use layouts for repeated hero, quote, agenda, and demo patterns

Example utility-heavy slide:

```md
---
class: px-14 py-10
---

# MCP on Pantheon

<div class="mt-8 grid grid-cols-[1.2fr_0.8fr] gap-10 items-start">
  <div class="space-y-4 text-[1.15rem] leading-7">
    <p class="text-slate-700">Why websites feel broken and what the open web can recover.</p>
    <ul class="space-y-2">
      <li>Agents need structured interfaces</li>
      <li>Sites need machine-usable affordances</li>
      <li>MCP is one bridge, not the whole story</li>
    </ul>
  </div>
  <img src="./generated_images/slide1-drupal-site.png" class="rounded-2xl shadow-xl border border-slate-200" />
</div>
```

## Typography strategy

Slidev can auto-import web fonts through the `fonts` headmatter. The default provider is Google Fonts.

If we need to disable remote font loading for a fully offline or locked-down environment, configure fonts explicitly instead of assuming the default web import path.

Recommended starting stack for a polished deck:

```yaml
fonts:
  sans: DM Sans
  serif: Source Serif 4
  mono: IBM Plex Mono
```

Good alternates:

- `sans`: Inter Tight, Manrope, Plus Jakarta Sans, Space Grotesk
- `serif`: Source Serif 4, Fraunces, Crimson Pro, Cormorant Garamond
- `mono`: IBM Plex Mono, JetBrains Mono, Fira Code

Recommended approach for this repo:

- Keep body copy in a clean sans
- Use a strong serif only for section openers or quoted statements
- Use mono sparingly for protocol names, code, CLI, and structured labels
- Increase typographic contrast with weight and scale before adding visual clutter

If we need exact weights or italics beyond Slidev’s automatic import, add them through `index.html` and project CSS rather than relying entirely on the shorthand `fonts` config.

## Built-in features worth leaning on

- Layouts: `cover`, `center`, `quote`, `fact`, `section`, `statement`, `two-cols`, image layouts
- Click reveals: `v-click`, `v-after`, `v-clicks`
- Speaker notes in trailing comment blocks
- Presenter mode at `/presenter`
- Browser exporter at `/export`
- Drawing and annotations
- Draggable elements and arrows
- Magic Move for animated code transformations
- Monaco editor and writable code blocks for live demos

## Practical authoring patterns for this deck

### Use imported markdown for deck structure

As the deck grows, split `slides.md` into sections:

```md
---
theme: seriph
title: Open Web Exchange
---

## src: ./pages/intro.md
## src: ./pages/problem.md
## src: ./pages/mcp.md
## src: ./pages/demo.md
## src: ./pages/questions.md
```

### Keep reusable slide shells in layouts

Once patterns repeat, create custom layouts such as:

- `layouts/hero.vue`
- `layouts/image-callout.vue`
- `layouts/demo-frame.vue`
- `layouts/end-card.vue`

### Keep generated images versioned

The images in `generated_images/` are deck inputs, not build artifacts. Treat them like design assets and commit them.

### Prefer local assets for reliability

For a client-facing talk, local images are safer than hotlinking. Remote assets can work, but they add export risk and network dependency.

## Exports and operational constraints

For CLI export to PDF/PPTX/PNG, install Playwright Chromium:

```bash
npm i -D playwright-chromium
```

Then:

```bash
npm run export
```

Useful export notes:

- `slidev export` defaults to PDF
- `slidev export --format pptx`
- `slidev export --format png`
- `slidev export --with-toc`
- `slidev export --with-clicks`
- `slidev export --wait 1000`
- `slidev export --wait-until none`

Known caveats:

- browser export UI works best in Chromium-based browsers
- some video formats fail in export
- animation-heavy slides may need `--wait`
- the hosted SPA preserves interactivity better than static exports

## Recommended addons and adjacent tooling

Keep this restrained. Too many addons increases theme conflict risk.

### Strong recommendations

1. `@slidev/plugin-notes`
   - Useful if presenter-note workflows become central and we want the official notes plugin support explicitly in the deck config.

2. `excalidraw`
   - Official docs use it as an addon example.
   - Good fit if we want hand-drawn systems diagrams, architecture sketches, or more humane protocol visuals.

3. `playwright-chromium`
   - Not a Slidev addon, but effectively required for reliable CLI export.

### Maybe, depending on deck direction

1. A local custom theme
   - Best option if we want a strong typographic identity with repeatable layouts.
   - Better than stacking visual addons.

2. Vite plugins in `vite.config.ts`
   - Only when we have a concrete need, such as additional asset transforms or custom markdown handling.

3. Local addon package
   - Worth it only if the deck needs reusable custom components or layouts that should stay isolated from the main repo structure.

## Suggested visual direction

Because you prefer Tailwind-style workflows and Google Fonts, the strongest direction is:

- keep `seriph` only as a starting point, not the final identity
- use UnoCSS utilities for most composition
- define a small set of CSS variables for color and spacing
- pair a modern sans with an editorial serif
- use warm neutrals or muted technical tones instead of generic dark-mode gradients
- rely on large type, tight layout discipline, and the generated images as focal points

Two strong font pairings:

1. `DM Sans` + `Source Serif 4` + `IBM Plex Mono`
2. `Manrope` + `Fraunces` + `JetBrains Mono`

## Recommended near-term repo changes

1. Replace the starter `slides.md` with a deck outline that uses the five existing generated images.
2. Add `public/` for any logos or local static assets we do not want imported relatively.
3. Add `styles/` with a single `index.css` for deck tokens and typography.
4. Install `playwright-chromium` before serious export testing.
5. Decide whether to keep `seriph` or eject/build a local theme.

## Key source material

- Slidev docs: https://sli.dev/
- Syntax guide: https://sli.dev/guide/syntax
- Layouts: https://sli.dev/guide/layout
- Theme and addons: https://sli.dev/guide/theme-addon
- Exporting: https://sli.dev/guide/exporting
- Directory structure: https://sli.dev/custom/directory-structure
- Custom config reference: https://sli.dev/custom/
- Fonts: https://sli.dev/custom/config-fonts.html
- UnoCSS config: https://sli.dev/custom/config-unocss.html
- Work with AI: https://sli.dev/guide/work-with-ai
- Local package readme: [`node_modules/@slidev/cli/README.md`](/Users/jomiller/Developer/github/joshmiller83/owe-slides/node_modules/@slidev/cli/README.md)
- Local theme readme: [`node_modules/@slidev/theme-seriph/README.md`](/Users/jomiller/Developer/github/joshmiller83/owe-slides/node_modules/@slidev/theme-seriph/README.md)

## Working assumptions

- `generated_images/` should remain committed
- We are optimizing first for authoring speed and visual quality in-browser
- Export reliability matters, but live SPA delivery is still the highest-fidelity mode
- UnoCSS is the preferred styling layer over adding Tailwind proper
