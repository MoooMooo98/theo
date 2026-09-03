---
tags: [meta, changelog]
updated: 2026-08-18
---

# Changelog

Chronological log of notable changes to **this project**. Newest first.
Human-curated — not a mirror of `git log`.

Log a change here when it would surprise someone returning in six months: a new
dependency, a new route or section, a convention bent, a bug whose cause is worth
remembering. Routine commits do not need an entry.

For *why* the conventions are what they are, see [[decisions-log]].

---

## Baseline — built from `next16-claude-starter` v0.1.0

What the starter ships, so the first project entry has something to diff against:

| Area | What is there |
|------|---------------|
| Framework | Next.js 16 App Router · React 19 · TypeScript · Yarn · Node ≥ 20.19 |
| Styling | Tailwind v4, CSS-only config, three-tier design tokens ([[design-system]]) |
| Motion | Vendored spring engine + `spring-text-engine`, shared rAF ticker, reduced-motion ([[animation-system]]) |
| Layout | Adaptive scaling grid — root font-size tracks the viewport ([[design-system]]) |
| Scroll | Lenis smooth scroll + Zustand scroll store ([[smooth-scroll]]) |
| Server | `app/api` route handlers, zod-validated env, `{ data }`/`{ error }` envelope ([[api-architecture]]) |
| SEO | Metadata generator, `robots.ts`, `sitemap.ts`, JSON-LD ([[seo-metadata]]) |
| Agent harness | 8 commands, 7 path-scoped rules, 11 skills, 4 subagents, `verify.sh` ([[agent-harness]]) |
| Not included | CMS, database, auth, payments, i18n, tests — added per project ([[backend/README]]) |

The home view (`src/views/home.tsx`, route `/`) ships empty on purpose — start
there ([[new-page]]).

<!-- Log this project's changes below, newest first, under a `## YYYY-MM-DD` heading. -->

## 2026-09-03

- Added `public/storm-scene/index.html`: a standalone (non-React, no build
  step) Three.js r0.143.0 particle-orb scene, self-contained via an
  importmap. **Deliberately exempt** from the springs-only motion rule — it
  never enters the app's component tree. Must be served over HTTP; opening
  it via `file://` blank-pages on the ES-module import (browser CORS, not a
  bug — see the file's own README).
- Added "Theo", a clickable virtual-assistant demo inside that same file:
  click the orb (or Enter/Space) to cycle 6 scripted German messages in an
  iMessage-style bubble, positioned every frame via `camera.project()` so it
  tracks the orb through scroll/parallax. Purely simulated — no AI API, no
  network call. Reviewed against this starter's motion/UX judgement
  checklist (adapted for the non-React exemption); see the commit for the
  fixes that came out of that review (aria-hidden reset on auto-hide,
  length-scaled read time, hover/focus pause, non-overshooting exit easing).
- Neither is wired into `src/views/home.tsx` yet — both live only as a
  standalone demo under `public/`.
