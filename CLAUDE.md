# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A personal single-page planning site for a May 16–22, 2026 Disney World family trip (6 nights; 4 adults + 2 kids ages 2 & 4; Disney's Saratoga Springs Resort & Spa, 2BR Villa Preferred; one park per day). Deployed as a **private-repo GitHub Pages** site — access is unlisted-URL only (no paid plan / no real access control), so treat the served URL as public-ish and don't commit personal identifiers (confirmation numbers, full names, addresses, payment info).

The repo is **just `index.html`** — one hand-authored, self-contained HTML file with inline CSS, inline vanilla JS, and park map images embedded as base64 `data:image` URLs. No Leaflet, no bundler, no package manager, no tests, no framework.

## Day structure

Six day cards (`<div class="day-content" id="dayN">`) driven by the `days` array in the inline `<script>` at the bottom of the file. Tab navigation is generated from that array; `document.getElementById('day1').classList.add('active')` activates the first tab on load. If you add/remove/reorder days, update **both** the array and the div IDs, and keep IDs sequential.

Current mapping:
- Day 1 — Sat May 16 — Arrival & Disney Springs (rest-day timeline layout)
- Day 2 — Sun May 17 — Magic Kingdom
- Day 3 — Mon May 18 — EPCOT
- Day 4 — Tue May 19 — Pool, Mini Golf & Disney Springs (rest-day timeline)
- Day 5 — Wed May 20 — Hollywood Studios
- Day 6 — Thu May 21 — Animal Kingdom
- Day 7 — Fri May 22 — Departure (rest-day timeline: pack, checkout, drive home to SW Ranches)

Park days use `.park-map-container` with a base64 PNG background; rest/arrival days use `.rest-day-container` with just the `.timeline` list.

## Editing

- `index.html` is ~3.7 MB, mostly from the four base64-embedded park maps. Always prefer `Edit` over `Write`, and read narrow ranges via `Read` with `offset`/`limit` rather than pulling the whole file into context.
- Sections in the file are roughly ordered: `<style>` → header/nav → per-day itinerary cards → per-park Leaflet map containers + scripts → budget/dining/crowd/weather data tables. Budget, crowds-and-weather, and dining-plan content lives **inside** this one page — they are not separate pages anymore.
- When adding map markers or route points, match the existing Leaflet pattern already in the file (don't introduce a new mapping lib).
- Keep the page fully self-contained: no new sibling HTML files, no references to local assets outside the repo. External CDN links (fonts, Leaflet) are fine.

## Serving / previewing

- Open `index.html` directly in a browser — everything is inline.
- GitHub Pages serves from the default branch root, so no config file is needed. Changes go live on push once Pages is enabled in repo settings.

## Trip timeline

Today is 2026-04-19; the trip is 2026-05-18 through 2026-05-22. Expect iterative updates as the trip approaches — reservation times shifting, Lightning Lane choices firming up, weather forecasts arriving inside the 10-day window, etc.
