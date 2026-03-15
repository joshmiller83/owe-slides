---
theme: seriph
title: MCP Demo
info: |
  MCP demo deck for Drupal and Open Web Exchange.
class: text-slate-900
fonts:
  sans: DM Sans
  serif: Fraunces
  mono: JetBrains Mono
themeConfig:
  primary: '#0f766e'
drawings:
  persist: false
transition: fade
mdc: true
---

---
layout: image-right
image: ./generated_images/slide1-drupal-site.png
---

# Drupal Site

<div class="mt-8 max-w-xl space-y-6">
  <p class="text-lg leading-8 text-slate-700">
    A normal Drupal website is designed around pages, navigation, and actions that make sense for a human visitor.
  </p>

  <div class="grid grid-cols-3 gap-4 pt-4">
    <div class="rounded-2xl border border-teal-200 bg-white/80 px-4 py-5 text-center shadow-sm">
      <div class="text-xs font-mono uppercase tracking-[0.2em] text-teal-700">Tile</div>
      <div class="mt-2 text-lg font-semibold">Events</div>
    </div>
    <div class="rounded-2xl border border-teal-200 bg-white/80 px-4 py-5 text-center shadow-sm">
      <div class="text-xs font-mono uppercase tracking-[0.2em] text-teal-700">Tile</div>
      <div class="mt-2 text-lg font-semibold">Speakers</div>
    </div>
    <div class="rounded-2xl border border-teal-200 bg-white/80 px-4 py-5 text-center shadow-sm">
      <div class="text-xs font-mono uppercase tracking-[0.2em] text-teal-700">Tile</div>
      <div class="mt-2 text-lg font-semibold">Registration</div>
    </div>
  </div>

  <div class="rounded-2xl bg-teal-50 px-5 py-4 text-sm leading-6 text-teal-950">
    This interface works well for humans browsing and clicking.
  </div>
</div>

---
layout: image-right
image: ./generated_images/slide2-websites-are-broken.png
---

# AI Doesn't Use Websites Like Humans

<div class="mt-8 max-w-xl space-y-6">
  <p class="text-lg leading-8 text-slate-700">
    An AI agent has to follow page structure and click paths that were designed for people, not for machine-to-machine use.
  </p>

  <div class="grid gap-4">
    <div class="rounded-2xl border border-amber-200 bg-amber-50 px-5 py-4">
      <div class="text-xs font-mono uppercase tracking-[0.2em] text-amber-700">Constraint</div>
      <div class="mt-2 text-xl font-semibold">Pagination</div>
    </div>
    <div class="rounded-2xl border border-amber-200 bg-amber-50 px-5 py-4">
      <div class="text-xs font-mono uppercase tracking-[0.2em] text-amber-700">Constraint</div>
      <div class="mt-2 text-xl font-semibold">Linked bios</div>
    </div>
    <div class="rounded-2xl border border-amber-200 bg-amber-50 px-5 py-4">
      <div class="text-xs font-mono uppercase tracking-[0.2em] text-amber-700">Constraint</div>
      <div class="mt-2 text-xl font-semibold">Click paths</div>
    </div>
  </div>

  <div class="rounded-2xl bg-slate-900 px-5 py-4 text-sm leading-6 text-white">
    AI agents must navigate websites like humans, which leads to incomplete or inefficient results.
  </div>
</div>

---
layout: image-right
image: ./generated_images/slide3-intro-mcp.png
---

# MCP: Agent Interface

<div class="mt-6 max-w-xl space-y-6">
  <div class="rounded-2xl border border-teal-200 bg-white/85 px-5 py-4 shadow-sm">
    <div class="text-xs font-mono uppercase tracking-[0.2em] text-teal-700">Architecture</div>
    <div class="mt-3 text-2xl font-semibold">AI Agent → MCP → Drupal Website</div>
  </div>

  <div>
    <div class="text-sm font-mono uppercase tracking-[0.24em] text-slate-500">Services exposed</div>
    <ul class="mt-4 space-y-3 text-lg leading-7 text-slate-700">
      <li><span class="font-semibold text-slate-950">Events</span> as structured event data</li>
      <li><span class="font-semibold text-slate-950">Speakers</span> as linked profile records</li>
      <li><span class="font-semibold text-slate-950">Registration</span> as an explicit action</li>
    </ul>
  </div>

  <div class="rounded-2xl bg-teal-600 px-5 py-4 text-sm leading-6 text-white">
    MCP exposes structured services instead of forcing AI to browse pages.
  </div>
</div>

---
layout: image-right
image: ./generated_images/slide4-demo.png
---

# AI Uses the Website

<div class="mt-8 max-w-xl space-y-5">
  <ol class="space-y-4 text-lg leading-7">
    <li class="rounded-2xl border border-sky-200 bg-sky-50 px-5 py-4">
      <span class="font-mono text-sm uppercase tracking-[0.2em] text-sky-700">Step 1</span>
      <div class="mt-2 font-semibold">Ask AI for upcoming events</div>
    </li>
    <li class="rounded-2xl border border-sky-200 bg-sky-50 px-5 py-4">
      <span class="font-mono text-sm uppercase tracking-[0.2em] text-sky-700">Step 2</span>
      <div class="mt-2 font-semibold">Retrieve structured event and speaker information</div>
    </li>
    <li class="rounded-2xl border border-sky-200 bg-sky-50 px-5 py-4">
      <span class="font-mono text-sm uppercase tracking-[0.2em] text-sky-700">Step 3</span>
      <div class="mt-2 font-semibold">Register for an event</div>
    </li>
  </ol>

  <div class="rounded-2xl bg-sky-900 px-5 py-4 text-sm leading-6 text-white">
    The AI is using the website as a service, not scraping its pages.
  </div>
</div>

---
layout: image-right
image: ./generated_images/slide5-questions.png
class: text-white
---

# Questions?

<div class="mt-10 max-w-xl space-y-6">
  <p class="text-lg leading-8 text-white/85">
    Discussion topics for where Drupal, MCP, and the open web go next.
  </p>

  <div class="grid gap-4">
    <div class="rounded-2xl border border-white/20 bg-white/10 px-5 py-4 backdrop-blur-sm">
      <div class="text-xs font-mono uppercase tracking-[0.2em] text-white/70">Topic</div>
      <div class="mt-2 text-xl font-semibold">Drupal MCP</div>
    </div>
    <div class="rounded-2xl border border-white/20 bg-white/10 px-5 py-4 backdrop-blur-sm">
      <div class="text-xs font-mono uppercase tracking-[0.2em] text-white/70">Topic</div>
      <div class="mt-2 text-xl font-semibold">Open Web Exchange</div>
    </div>
    <div class="rounded-2xl border border-white/20 bg-white/10 px-5 py-4 backdrop-blur-sm">
      <div class="text-xs font-mono uppercase tracking-[0.2em] text-white/70">Topic</div>
      <div class="mt-2 text-xl font-semibold">Agentic web interfaces</div>
    </div>
  </div>

  <div class="rounded-2xl bg-white/15 px-5 py-4 text-sm leading-6 text-white">
    Websites remain essential by exposing services that AI can integrate with.
  </div>
</div>
