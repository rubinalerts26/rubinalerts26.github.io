# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static website for the Rubin Alerts & AI Hackathon (April 1–3, 2026, SkAI Institute, Chicago IL). Pure HTML/CSS — no build step, no package manager, no JavaScript framework.

## Structure

- `index.html` — Home page (vision, hackathon goals, important dates)
- `program.html` — Hackathon schedule
- `participants.html` — Participant cards and registration info
- `travel.html` — Travel and lodging (Marriott Downtown Magnificent Mile, Chicago)
- `css/styles.css` — Single stylesheet with all CSS custom properties
- `assets/images/` — Site images

## Deployment

GitHub Pages from `main` branch at `https://rubinalerts26.github.io/`. Push to main to deploy.

Jekyll runs passively (no Liquid templates or front matter used) — `_config.yml` exists solely
to exclude non-web files from the built site: `CLAUDE.md`, `README.md`, `_admin/`, `*.py`.
Do not add a `.nojekyll` file — it would re-expose those files.

To preview locally:
```
python3 -m http.server 8000
```

## Common Content Updates

**Add a participant** (`participants.html`):
```html
<div class="participant-card">
    <div class="participant-avatar">AB</div>
    <h4>Full Name</h4>
    <p class="participant-affiliation">Institution — In-Person</p>
</div>
```
Keep participants sorted by last name (A → Z). Attendance mode is shown in the affiliation line as `— In-Person`, `— Hybrid`, or `— Remote`. The source of truth for registrations is the Google Sheet: https://docs.google.com/spreadsheets/d/1kyWDkPsqkCn5lqblyAj7ksjKjrgEvStIAT80hrosEM0/edit

To sync participants from the sheet, fetch it as CSV (follow the redirect):
```
https://docs.google.com/spreadsheets/d/1kyWDkPsqkCn5lqblyAj7ksjKjrgEvStIAT80hrosEM0/export?format=csv
```
Compare the sheet's name list against `participants.html` and add any missing entries. As of 2026-03-17 there are 38 confirmed participants.

**Add a schedule row** (`program.html`):
```html
<tr>
    <td class="schedule-time">09:00 - 10:00</td>
    <td>Session Title</td>
    <td class="schedule-speaker">Speaker Name</td>
</tr>
```
Use `class="schedule-break"` on `<tr>` for breaks, with `colspan="2"` on the content cell.

**Add an important date** (`index.html`):
```html
<div class="date-item">
    <div class="date-badge">
        <span class="month">Apr</span>
        <span class="day">1</span>
    </div>
    <div class="date-content">
        <h4>Event Title</h4>
        <p>Description.</p>
    </div>
</div>
```

## Post-Event Admin

**Registration fees**: $100 in-person, $25 hybrid (per Elise Ahn; not on website).

**Unpaid registrants**: determined from red-highlighted rows in the registration Google Sheet
(organizer ground truth — self-reported form field is unreliable). 12 people did not pay.

**Refund calculations** (finalized 2026-04-08, verified with Erin Cox):
- Full details: `_admin/rubinalerts26_refunds.md`
- Local pool list (UIUC/NU/UC): `_admin/rubinalerts26_refunds_local.md`
- Non-local pool list: `_admin/rubinalerts26_refunds_nonlocal.md`
- SOC signoff message: `_admin/rubinalerts26_soc_message.md`

`_admin/` is in `.gitignore` — not pushed to the public repo.

**Pool 1 — Local SkAI (UIUC/NU/UC), $1,034.17**: equal split among 16 non-faculty/staff who
paid the in-person fee. $64.64/$64.63 each.

**Pool 2 — Non-local, $7,500**: fee refund (what each person paid) + flat travel honorarium
($6,150 ÷ 15 actual in-person attendees = $410.00 each). Remote attendees get fee refund only.

**Status**: Elise Ahn and Jay Alameda notified 2026-04-08 to begin processing.

**Key contacts**: Elise Ahn (fee records), Erin Cox (payment verification), Jay Alameda (processing).

**Wynn Jacobson-Galan** (Caltech postdoc): lives in Chicago with courtesy NU appointment —
treated as local, gets $0 (did not pay fee, no travel expenses to offset).

## Design Constraints

- No white backgrounds — all sections use blue tints
- Colors are CSS custom properties in `css/styles.css` under `:root`; always use variables (e.g. `var(--color-accent)`) rather than hardcoded hex values
- Navigation links use class `jiggle-link` for hover animation
- Color palette is derived from SkAI Institute branding (blues `#0a1628`–`#90cdf4`, purple accent `#8b5cf6`)
- Hero background uses the Vera C. Rubin telescope image (external URL in `.hero` CSS) with a semi-transparent gradient overlay for text legibility
- Contact email throughout: `rubinalerts@lists.skai-institute.org`
