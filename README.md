# owe-slides

Josh Miller's spotlight presentation on how the Open Web would benefit from more MCP-related work.

This deck was prepared for DrupalCon Chicago 2026. Thanks to [Pantheon.io](https://pantheon.io/) for inviting Josh to speak on this important topic.

The presentation argues that websites should not stop at human-facing interfaces. They should also expose structured, agent-friendly capabilities so AI systems can interact with the web as a service layer instead of approximating human browsing behavior.

## Why this matters

- The open web remains essential, but AI agents need better interfaces than pagination, click paths, and brittle page traversal.
- MCP creates a practical path for exposing structured capabilities from real websites.
- Drupal is well-positioned to participate in that shift.

## Drupal and MCP

You can host MCP endpoints on any Drupal website with the Drupal MCP module. That makes it possible to expose site capabilities such as event discovery, speaker data, registration flows, and other structured actions without forcing agents to scrape pages.

## Support the people doing the work

Please consider sponsoring Mateu and working with Omedia. They are trying very hard to make this low-level technology work for everyone.

- Sponsor Mateu: <https://github.com/sponsors/e0ipso>
- Work with Omedia: <https://omedia.dev/services>

## Local development

```bash
npm install
npm run dev
```

Then open <http://localhost:3030>.

Useful routes:

- Slides: <http://localhost:3030>
- Presenter mode: <http://localhost:3030/presenter>
- Export UI: <http://localhost:3030/export>

## Build

```bash
npm run build
```

The production build is written to `dist/`.

## Deployment

This repo includes a GitHub Actions workflow that builds the Slidev deck and deploys it to GitHub Pages on pushes to `main`.

Live deck: <https://joshmiller83.github.io/owe-slides/>
